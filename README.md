# openmp_test
This is a demo of openmp + bazel + kythe

Make sure kythe release placed at /opt/kythe

Without Kythe
bazel build --linkopt="-fopenmp" //...

With Kythe
bazel build --linkopt="-fopenmp" --experimental_action_listener=:extract_cxx //...

error: unsupported option '-fopenmp'
main.cc:1:10: fatal error: 'omp.h' file not found
#include "omp.h"
         ^~~~~~~
         
         
(linkopt can be ignored if toolchain is set up properly, but this is a extremely simple demo)

