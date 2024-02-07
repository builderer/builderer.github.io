---
layout: default
---
# Builderer
## Status
Builderer is currently classified as a research prototype but is capable of generating Visual Studio and Makefile build files that can target Windows, Linux and macOS.

Documentation is currently non-existant. APIs may change abruptly. Platform and toolchain support is currently limited (Windows/Linux/macOS, and MSBuild/Make).

Feel free to report [issues](https://github.com/builderer/builderer/issues), or join the [discussion](https://github.com/builderer/builderer/discussions) to help drive progress.

## Why Another Build System?
Build systems like Blaze, Bazel and Buck are great at managing large monolithic repositories, but they are heavy weight, and by default incapable of generating standalone build files which can sometimes make using certain developer tools difficult.

Build-file generators like CMake can generate build files for your local toolchain, but are typically not standalone/transferable, slow to generate and require system-level dependencies (which can create backwards compatability issues and/or redundant features to support legacy builds). Synax is often unfamiliar and/or exotic making it unapproachable and hard to extend.

Builderer runs inside Python without any other dependencies, and build files themselves are Python (not just Python-like). This means the syntax of the build configuration is based on one of the most popular programming languages in the world, making it both familiar and easy to extend... take advantage of Pythons fantastic standard library as well as practically any third party module.

Builderer is also designed to be embedded (either by simply copying it into your repository, as a submodule or using [Venv](https://docs.python.org/3/library/venv.html)) which allows each repository to use exactly the version that works for them.