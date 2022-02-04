---
title: "Basic benchmarking"
author: Jens Petersen
date: Aug 29, 2020
tags: [haskell]
description: Using criterion for simple Haskell benchmarking
---

My first blog post using slick and in a long while...

[Bench](https://hackage.haskell.org/package/bench) is a cool tool written
in Haskell using
the [criterion](https://hackage.haskell.org/package/criterion) for
benchmarking commands in the shell.
(_edit:_ In 2022 you might also consider to use the simpler Haskell
[tasty-bench](https://hackage.haskell.org/package/tasty-bench) library
instead.)

A while back hlint got me [interested](https://github.com/juhp/hs-reverse-sort)
in different ways to do reverse (descending) sort in Haskell,
from a [2016 article](https://ro-che.info/articles/2016-04-02-descending-sort-haskell)
by Roman Cheplyaka.

As I am starting to work on adding
[typed-process](https://hackage.haskell.org/package/typed-process) to
the next major version of
[simple-cmd](https://hackage.haskell.org/package/simple-cmd) and I had
noticed a slowdown while experimenting with `typed-process` in
[rpmbuild-order](https://hackage.haskell.org/package/rpmbuild-order),
I thought I would try to
[measure](https://github.com/juhp/hs-processes-bench) the overhead of
using `typed-process` compared to just `process` for simple command
output.

So this is not really a very fair comparison since `typed-process`
uses heavier machinery like `stm` and `async` to correctly buffer and
pipe input and output, but for short lived commands there is
measureable overhead. I need to experiment more (maybe I should try
ghc profiling too) but I may end up using a hybrid approach of
`process` for simple commands and `typed-process` for more
sophisticated I/O stream handling: for example to fix bugs in the
current piping commands in simple-cmd and also add a `tee` function,
etc. I wonder if there could be any lower hanging fruit that could
improve the performance of `typed-process`? but so far that looks hard
to see.

ps _(added in 2022)_ For an example of using tasty-bench, see my tiny
[hs-string-bench](https://github.com/juhp/hs-string-bench) project.
