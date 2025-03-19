# libvsync benchmarks for SV-COMP

This directory builds a set of SV-COMP benchmarks based on libvsync.
With these benchmarks we hope to reduce the gap between academic tools and
industry needs.

The benchmark code is modified in a few ways:

1. all atomic accesses are upgraded to be **sequentially consistent**,
2. some algorithms have **injected bugs** that cause safety violations.

Use `make svcomp` (after running `cmake`) to build the benchmark.  The result
is published in

  https://gitlab.com/sosy-lab/benchmarking/sv-benchmarks

To run tests, it's better to use the same docker images used in SVCOMP. These
images contain quite outdated compilers (gcc 5 and clang 3.9), and that might
influence the tests. Here is how to run the clang compiler used in SVCOMP:


    cd sv-benchmarks
    docker-runs registry.gitlab.com/sosy-lab/benchmarking/sv-benchmarks/ci/clang:3.9
    make -C c/libvsync -j2 CC=clang-3.9

