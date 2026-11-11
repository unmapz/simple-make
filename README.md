# simple-make

A C++23 CLI tool for installing software directly from source.

Give it a package name or repository URL. simple-make finds the source,
detects the build system, builds the project and tracks installed files
so they can be removed later.

Supports Linux, macOS, BSD and Windows.

## Build

Requirements: C++23 compiler, CMake and Git.

```sh
git clone https://github.com/unmapz/simple-make.git
cd simple-make
cmake -B build -DCMAKE_BUILD_TYPE=Release
cmake --build build -j"$(nproc)"
cmake --install build --prefix ~/.local
```

Dependencies such as `cpr` and `nlohmann/json` are fetched by CMake
when they are not available on the system.

## Usage

```sh
simple-make ripgrep
simple-make fd bat
simple-make https://github.com/user/project
simple-make -s ripgrep
simple-make -r ripgrep
simple-make -u ripgrep
simple-make --self-update
simple-make --setup-config
```

- `-s` searches without installing.
- `-r` removes an installed package.
- `-u` rebuilds installed packages from their saved source URLs.
- `--self-update` checks for a newer simple-make release.
- `--setup-config` opens the configuration wizard.

The default install prefix is `~/.local`. No root privileges are needed
there. A system-wide prefix may require elevation for the final install
step, but builds themselves run as the invoking user.

## Build systems

CMake, Meson, Ninja, Make, Autotools, Cargo, Go, pip, Maven and Gradle.

Package names are resolved through the system package manager, the
built-in database, and then GitHub, GitLab or Codeberg.

## Configuration

The config file is located at:

```text
~/.config/simple-make/simple-make.conf
```

It controls the install prefix, confirmation prompts, source cleanup,
search providers, API tokens and update checks.

## Security

simple-make runs third-party build scripts without sandboxing. Those
scripts can execute code with your user's privileges and access the
network.

Builds do not run as root. See [SECURITY.md](SECURITY.md) for details.

## License

MIT. See [LICENSE](LICENSE).
