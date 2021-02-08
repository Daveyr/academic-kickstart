---
title: Building a CI pipeline for R packages in gitlab
author: ''
date: '2021-02-06'
slug: building-a-ci-pipeline-for-r-packages-in-gitlab
categories:
  - Guide
tags:
  - Docker
  - Git
  - Gitlab
  - R
subtitle: ''
summary: ''
authors: []
lastmod: '2021-02-06T15:07:39Z'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: ['Gitlab Runner']
---


Continuous Integration (CI) is not a tool but a practice of continually merging in new behaviour/features into a released product. To facilitate this practice without exposing end users to unstable behaviour and bugs, testing needs to be standardised and automated. It's no wonder then that CI is often associated with Test Driven Development (TDD), which mandates that you write your tests *first*, working backwards to the write the minimal code that should pass each test.

At first glance CI is not directly relevant to consultancy projects or products for internal use, which I tend to spend most of my time working on. However, it is a good discipline to foster ahead of developing packages for wider use, saves time when bug squashing and gives a framework for collaborating with other people (protect the master branch!).

The version control tool of choice (for the moment at least) for my company's team is Gitlab. I had noticed on the platform there is the option to use inbuilt CI/CD tools on projects and products. I was generally aware of CI and agreed with the idea of standardising and streamlining tests on code so I thought I would give it a go. 

I went to [Stack Overflow](https://stackoverflow.com/a/51874023/10960765) for inspiration (as usual). From there I built the pipeline in yaml syntax, below.

``` bash
image: rocker/r-base
stages:
    - test
    - quality
test:
   stage: test
   script:
    - apt-get update
    - apt-get install --yes --no-install-recommends r-cran-testthat r-cran-devtools
    - R -e "devtools::install_deps(dependencies = TRUE)"
    - R CMD build . --no-build-vignettes --no-manual
    - PKG_FILE_NAME=$(ls -1t *.tar.gz | head -n 1)
    - R CMD check "${PKG_FILE_NAME}" --no-build-vignettes --no-manual
      cache:
    paths:
     - $R_LIBS_USER
   artifacts:
    paths:
     - ${PKG_FILE_NAME}.tar.gz
   only:
    - master
    - dev

quality:
   stage: quality
   include:
    template: Jobs/Code-Quality.gitlab-ci.yml
```  

What does it do? Well, we start with the base R docker image from the _rocker_ project, making sure that the package lists are up to date (pretty sure this is built on Debian linux, so the package manager would be dpkg). 

Next we focus on the test job. We install the bare minimum R libraries on top of base R so that we can test the package: `testthat` and `devtools`. Note we elect to install no recommended packages alongside to make sure the container is as debloated as possible.

After this we install all the dependencies that are specified in the DESCRIPTION file you wrote as part of your R package. When I used the original Stack answer above, it did not have the `dependencies = TRUE` argument, which meant that none of my suggested packages were installed. This caused my build to fail because some of my tests depended on them; however, for most use cases you may not need this argument.

The last three lines in the script build the package source as a _tar.gz_ compressed file, store the package name from this file into a variable, and then use it to call `CMD check`. This final line tests both for whether all unit tests described in the _/tests_ folder have passed, and whether the package can be built without errors. Note that for building the source and checking it we specify that we will not build vignettes or man pages. Although testing these might be useful they take a long time to run. In lieu of testing the vignette, I will often run a battery of unit tests using `context("Testing according to the vignette")`, replicating each line of the vignette in tests.

Caches are useful insofar as we can store the contents of a folder (in our case, the R library folder) so we don't have to download and install the R libraries each time. This should trim down the run time.

Artifacts are files that can be downloaded after the job is successfully run. We specify the compressed source file as an artifact.

The `only:` section within the test job refers to only the branches we wish to run the job on. Instead of whitelisting branches we could instead have dealt by exception, using `except:` instead. The configuration above only runs the test job on the master and dev branches.

The last job is from a Gitlab template that tests for code quality. I'm not sure how useful it is for R but it is a good illustration of how to chain jobs into a CI pipeline. Both test and code quality jobs must succeed for the pipeline to pass.

## DIY runners
A note on using CI pipelines on the Gitlab free tier: it is **very** easy to chew through the 200 free minutes per month. I managed to consume around 70% of this in a day and a half of experimenting, which spurred me on to make my own runner to get around this limitation.

The [Gitlab-runner project](https://www.algorist.co.uk/project/internal-project/gitlab-runner/) is the result of this experimentation. I successfully set up a runner on a Raspberry Pi 4 with 8gb of RAM but since the _rocker/r-base_ image is not arm compatible then the job failed. One possibility is to change the image; the other is to use a computer with compatible architecture. In the end I used my other laptop and it ran just fine. No more limited pipeline minutes!