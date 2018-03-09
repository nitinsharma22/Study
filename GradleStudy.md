On CI machines the benefit you can expect from the daemon depends on your setup. If you have long-lived CI agents and you build lots of small projects that all use the same Gradle version and JVM arguments, then the daemon can reduce your turnarounds. If your projects are big or more diverse, you probably won’t see much benefit. Generally it is safe to leave the daemon on, as Gradle 3.0 introduced health monitoring which will shut daemons down on memory pressure.

https://guides.gradle.org/performance/

Gradle has a few ways to help your tests complete faster:
  [x]Parallel test execution
  [x]Process forking options
  [x]Disable report generation

Gradle will happily run multiple test cases in parallel, which is useful when you have several CPU cores and don’t want to waste most of them.

test.maxParallelForks = Runtime.runtime.availableProcessors().intdiv(2) ?: 1
test.maxParallelForks = Runtime.runtime.availableProcessors().intdiv(2) ?: 1

fork a new test VM after a certain number of tests have run. You can do this with the forkEvery setting:
test.forkEvery = 100
