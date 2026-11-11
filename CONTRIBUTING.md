# Contributing

Bug reports and focused pull requests are welcome.

## Build

```sh
git clone https://github.com/unmapz/simple-make.git
cd simple-make
cmake -B build -DCMAKE_BUILD_TYPE=Release
cmake --build build -j"$(nproc)"
./build/simple-make --help
```

Requires a C++23 compiler, CMake and Git.

## Before submitting

- Make sure the project builds.
- Test the parts you changed.
- Keep each pull request focused on one topic.

Changes to `src/platform.cpp` or `src/build.cpp` should preserve
the privilege and shell-safety rules described in [SECURITY.md](SECURITY.md).

Match the surrounding code style: 4 spaces, `snake_case`, early returns
and no unnecessary comments.
