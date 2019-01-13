# Static vectors for Futhark [![Build Status](https://travis-ci.org/athas/vector.svg?branch=master)](https://travis-ci.org/athas/vector) [![Documentation](https://futhark-lang.org/pkgs/github.com/athas/vector/status.svg)](https://futhark-lang.org/pkgs/github.com/athas/vector/latest/)

A Futhark library for efficient statically-sized vectors.  This is
useful when working with many small vectors that do not need to be
individually stored in memory.

## Installation

```
$ futhark-pkg add github.com/athas/vector
$ futhark-pkg sync
```

## Usage example

```
import "lib/github.com/athas/vector/vector"
module vector_2 = cat_vector vector_1 vector_1
module vector_3 = cat_vector vector_2 vector_1
module vector_5 = cat_vector vector_2 vector_3
module vector_8 = cat_vector vector_5 vector_3

let main (xs: [8]i32) =
  xs
  |> vector_8.from_array
  |> vector_8.map (+1)
  |> vector_8.to_array
```
