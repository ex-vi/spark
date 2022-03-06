# spark

[![Go Version](https://img.shields.io/github/go-mod/go-version/ex-vi/spark?style=flat-square)](https://go.dev/doc/devel/release#go1.17)
[![Go Doc](https://img.shields.io/badge/go-documentation-blue.svg?style=flat-square)](https://godoc.org/github.com/ex-vi/spark)
[![Circle CI](https://img.shields.io/circleci/build/github/ex-vi/spark?style=flat-square&token=43ac30b3ed4bdc39ba8c5f1129263612676a1de5)](https://circleci.com/gh/ex-vi/spark)

Spark library includes common tools for working with data in Go. It will be updated whenever I need new utils or someone wants to bring new ones.

## Usage

### spark/structs - utilities for structs

**Map** function converts the given struct to a `map[string]interface{}`, where the keys of the map are the field names and the values of the map the associated values of the fields. The default key string is the struct field name but can be changed in the struct field's tag value. The `structs` key in the struct's field tag value is the key name.

```go
s := struct {
    Age  int
    Name string
}{
    Age:  25,
    Name: "John Doe",
}

m := structs.Map(s)

age := m["Age"]
name := m["Name"]
```

```go
s := struct {
    Age  int    `structs:"my-age"`
    Name string `structs:"my-name"`
}{
    Age:  25,
    Name: "John Doe",
}

m := structs.Map(s)

age := m["my-age"]
name := m["my-name"]
```
