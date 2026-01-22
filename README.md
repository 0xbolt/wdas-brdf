# wdas-brdf
The original [wdas/brdf](https://github.com/wdas/brdf), but with some CMakeLists.txt files slapped around. You may build it with:

```
cmake -S . -B build -DCMAKE_PREFIX_PATH="$(brew --prefix qt@5)"
```

This project will compile with more warnings than there are atoms in the observable universe. However it should run just fine.

If it does not compile, then make sure you have all the dependencies installed (these are listed in [`README-WIN32`](./README-WIN32)).
