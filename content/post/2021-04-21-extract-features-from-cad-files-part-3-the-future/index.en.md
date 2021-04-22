---
title: 'Extract features from CAD files Part 3: The future'
author: ''
date: '2021-04-21'
slug: extract-features-from-cad-files-part-3-the-future
categories:
  - Blog
tags:
  - Built Environment
  - CAD
  - Python
subtitle: ''
summary: ''
authors: []
lastmod: '2021-04-21T16:46:59+01:00'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---

In this third part of the series of posts on extracting objects from a CAD document, I’ll discuss how you might develop this CAD extraction tool and the problems you might be able to solve.

# Prologue
In [Part 1](https://www.algorist.co.uk/post/extract-features-from-cad-documents-part-1-a-primer/) we looked at the structure of a CAD file and built up a strategy to extract seat types and locations from an architect's floor plan. The motivation for this is to provide seat location data to a model that creates a stack plan with optimal locations of teams to office amenities and other teams they collaborate with.

In [Part 2](https://www.algorist.co.uk/post/extract-features-from-cad-documents-part-2-using-ezdxf/) we built an extraction tool based on the Python `ezdxf` package that can read, query, and write DXF files. We loaded a floor plan in DXF, printed the block types in a layer, extracted all block inserts that matched a layer and/or block type query and outputted them to a pandas dataframe.

## Additional feature extraction

As long as a CAD drawing is segregated by block type and/or layer, several floor features can be extracted with their own query and appended to the dataframe of floor features. Currently only assignable seating has been extracted from a single layer, but what else might you want to extract?

### Floor features a team may need

Often teams will use meeting rooms. Some teams use meeting rooms more than others, or need more meeting rooms simultaneously. Large teams will typically require larger meeting rooms compared with small teams. The typical meeting room layout is to have a single table in the centre of the room, which means that running a query for, e.g., "small conference table" and "large conference table" will return you the count and the centre point of every small and large conference room, respectively. Alternatively, if the seats in a meeting room are stored on a layer separate to assignable desk seats then this could be a way of tracking the location and seating capacity of a meeting room.

A similar approach could be used to extract printers, breakout rooms, kitchen facilities and everything else a team may have a preference for. It could even be used to track accessibility requirements (e.g., proximity to a lift, disabled toilets, etc.).

### Neighbourhoods/zoning

A related - but more complicated - concept is to define neighbourhoods or zones within a floor. 

## Generative design	

```python
# ezdxf draw features

# ezdxf write to file
```