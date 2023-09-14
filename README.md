<!-- Copyright 2023 Thomas Brown -->
<!-- Distributed under the Boost Software License, Version 1.0. (See -->
<!-- accompanying file LICENSE_1_0.txt or copy at -->
<!-- http://www.boost.org/LICENSE_1_0.txt) -->

# Boost.Build module for Protocol Buffers

## Overview

This project adds support for the Protocol Buffers to Boost.Build.

The following is the simplest approach to using this module.  It
assumes a main program named `example.cpp` and two Protocol Buffers
protocol definition files named `a.proto` and `b.proto`.

```jam
import pkg-config ;

# Jamroot
exe example
  : # sources
    example.cpp

    a.proto
    b.proto

    protobuf
  ;

pkg-config protobuf ;
```

## Requirements

* Boost.Build from Boost C++ Libraries 1.71.0 (or later)
* AsciiDoctor (for documentation)
* Protocol Buffers (`protobuf` and `protoc`)

## Documentation

The documentation is contained within the Boost.Build module file
(*e.g.*, `protoc.jam`) using inline documentation based on AsciiDoc.  A
top-level document brings in documentation from each module.

Run the following command to build an HTML version of the
documentation.

```shell
b2
```

Run the following command to view the help in the terminal.

```shell
b2 --help protoc
```

This requires that the root directory of this project is reflected in
the Boost.Build path.  This can be done by setting the
`BOOST_BUILD_PATH` environment variable.

## Testing

There are several test projects in the `test` directory.  All tests
are run by default using the default build configuration when
Boost.Build is run in the `test` directory.  Each test can also be run
individually by running Boost.Build in the directory of the desired
test to run.

Run the following command to run all the tests using the default build
configuration.  This adds the directory containing the `protoc.jam`
file to the Boost.Build path.

```shell
cd test && BOOST_BUILD_PATH="$(pwd)"/.. b2 --verbose-test -j 8
```
