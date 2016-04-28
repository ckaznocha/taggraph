# TagGraph

[![Build Status](http://img.shields.io/travis/ckaznocha/taggraph.svg?style=flat)](https://travis-ci.org/ckaznocha/taggraph)
[![Coverage Status](https://coveralls.io/repos/github/ckaznocha/taggraph/badge.svg?branch=master)](https://coveralls.io/github/ckaznocha/taggraph?branch=master)
[![License](http://img.shields.io/:license-mit-blue.svg)](http://ckaznocha.mit-license.org)
[![GoDoc](https://godoc.org/github.com/ckaznocha/taggraph?status.svg)](https://godoc.org/github.com/ckaznocha/taggraph)
[![Go Report Card](https://goreportcard.com/badge/ckaznocha/taggraph)](https://goreportcard.com/report/ckaznocha/taggraph)

TagGraph is a graph like data structure for creating tag hierarchies in Go apps.

You can:

*   Add/remove tags/edges to the graph at run time
*   Get a list of all possible paths leading to the selected tag.
*   Get all the parent tags of the selected tag
*   Get all the child tags of the selected tag

--
    import "github.com/ckaznocha/taggraph"

## Usage

### type TagGrapher

```go
type TagGrapher interface {
    GetTag(name string) (Tagger, bool)
    SetTag(name string)
    Delete(name string)
    AddChildToTag(child, parent string)
    RemoveChildFromTag(child, parent string)
}
```

TagGrapher is an interface for graph like collection of tags

### func  NewTagGaph

```go
func NewTagGaph() TagGraphercan
```

NewTagGaph returns a TagGrapher

### type Tagger

```go
type Tagger interface {
    Children() []string
    Parents() []string
    PathsToAllAncestors() [][]string
    PathsToAllAncestorsAsString(delim string) []string
    Name() string
}
```

Tagger is an interface for interacting with a node of a TagGrapher
