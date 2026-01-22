# wdas-brdf
The original [wdas/brdf](https://github.com/wdas/brdf) repo is a qmake project, and I couldn't compile it. So I've slapped some CMakeLists.txt files around, and it should now be buildable with

```
cmake -S . -B build -DCMAKE_PREFIX_PATH="$(brew --prefix qt@5)"
```

The project will compile with more errors than there are atoms in the observable universe. However it should run just fine. If it does not compile, then make sure you have all the dependencies installed (these are listed in [`README-WIN32`](./README-WIN32)).
