## RcppParallel Package

High level functions for doing parallel programming with Rcpp. For example, the `parallelFor` function can be used to convert the work of a standard serial "for" loop into a parallel one and the `parallelReduce` function can be used for accumulating aggregate or other values.

The high level interface enables safe and robust parallel programming without direct manipulation of operating system threads. The underlying implementation differs by platform: on Linux and Mac systems the [Intel TBB](https://www.threadingbuildingblocks.org/) (Threading Building Blocks) are used while on Windows systems the [TinyThread](http://tinythreadpp.bitsnbites.eu/) library is used.

### Examples

Here are links to three examples that illustrate using RcppParallel:

[Parallel Matrix Transform](inst/examples/parallel-matrix-transform.cpp) --- Demonstrates using `parallelFor` to transform a matrix (take the square root of each element) in parallel. In this  example the parallel version performs about 2.5x faster than the serial version on a 4-core machine.

[Parallel Vector Sum](inst/examples/parallel-vector-sum.cpp) --- Demonstrates using `parallelReduce` to take the sum of a vector in parallel. In this example the parallel version performs 4x faster than the serial version on a 4-core machine.

[Parallel Inner Product](inst/examples/parallel-inner-product.cpp) --- Demonstrates using `parallelReduce` to compute the inner product of two vectors in parallel. In this example the parallel version performs 2.5x faster than the serial version on a 4-core machine.

Note that the benchmark times above are for the TBB back-end (Posix systems only). Performance on Windows is about 30% slower.

### Usage

You can install the RcppParallel package from GitHub as follows:

```s
devtools::install_github("jjallaire/RcppParallel")
```

#### sourceCpp

You can use the RcppParallel library from within a standalone C++ source file as follows:

```cpp
// [[Rcpp::depends(RcppParallel)]]
#include <RcppParallel.h>
```

#### Packages

If you want to use RcppParallel from within an R package you add the following to your DESCRIPTION file:

```yaml
Imports: RcppParallel
LinkingTo: RcppParallel
```

And the following to your NAMESPACE file:

```s
import(RcppParallel)
```

### License

The RcppParallel package is made available under the [GPLv2](http://www.gnu.org/licenses/old-licenses/gpl-2.0.html).

The TinyThread library is licensed under the [zlib/libpng](http://www.opensource.org/licenses/zlib-license.php) license as described [here](https://gitorious.org/tinythread/tinythreadpp/source/master:README.txt).

The Intel TBB Library is licensed under the GPLv2 (as described at https://www.threadingbuildingblocks.org/Licensing):

TBB and other open-source software available from this site is licensed under GPLv2 with the (libstdc++) runtime exception. Specifically, the TBB open-source license is the same license used by the GNU libstdc++ library in gcc 4.2.1 (and earlier). For a complete description of the license, please visit the official GNU website for [GPLv2](http://www.gnu.org/licenses/old-licenses/gpl-2.0.html) and for the [runtime exception](https://www.threadingbuildingblocks.org/licensing#runtime-exception). 

**Runtime Exception**

```
As a special exception, you may use this file as part of a free software
library without restriction.  Specifically, if other files instantiate
templates or use macros or inline functions from this file, or you compile
this file and link it with other files to produce an executable, this
file does not by itself cause the resulting executable to be covered by
the GNU General Public License.  This exception does not however
invalidate any other reasons why the executable file might be covered by
the GNU General Public License.
```

