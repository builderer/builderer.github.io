---
layout: builderer
---
# Builderer

Builderer is a fast, dependency-free build file generator for C/C++/Objective-C projects. It generates native Makefiles and Visual Studio solutions from Python-based build descriptions.

## Status

Builderer is in early development and is actively used to maintain a multi-million line, multi-platform research monorepo. It currently supports Windows (MSBuild), Linux/macOS (Make), and WebAssembly (Emscripten). Additional platforms and build systems (Xcode, Ninja) are planned. APIs may change as the project evolves.

## Why Builderer?

Builderer bridges the gap between traditional project generators like CMake and build-and-execute systems like Bazel and Buck. It's fundamentally a project file generator, but includes convenience commands (`build`, `run`) that make working with C++ code more seamless.

**Compared to CMake:**

**CMake** is the industry standard with excellent IDE integration, mature tooling, and comprehensive documentation. However:

- CMake uses its own scripting language with a steep learning curve, while Builderer uses Python
- CMake requires system-wide installation, making version management difficult across teams. Projects fight over global versions, and package managers like `apt` often lack the version you need. Builderer embeds per-project, guaranteeing consistency for each project
- CMake's generated build files require CMake to regenerate on each platform, while Builderer generates truly standalone build files that can be shared and built without Builderer installed
- CMake generation can be slow for large projects, while Builderer typically generates in under 1 second

**Compared to Bazel and Buck:**

**Bazel and Buck** are powerful for massive monolithic repositories (tens of millions of lines) with sophisticated caching and distributed builds. They were designed at large tech companies for extreme scale. However:

- They require a Java Virtual Machine (JVM) to run
- They use background daemon processes to avoid repeated JVM startup overhead and maintain complex build graphs in memory
- They don't generate standalone IDE-compatible project files, making native debugger and profiler integration more complex
- The daemon architecture adds complexity that may be unnecessary for smaller teams

Builderer targets smaller teams and projects (up to a few million lines of code) where simplicity and lower complexity yield better developer efficiency than the infrastructure overhead required at massive scale

**Builderer's approach:**

- **Real Python syntax** - Build files are actual Python, immediately familiar and extensible
- **Lightweight** - No JVM, no background daemons, only Python 3.9+ required
- **Embeddable and version-controlled** - Each project can use its own Builderer version
- **Truly standalone output** - Generated Makefiles and Visual Studio solutions are self-contained and transferable
- **Fast generation** - Generation in milliseconds with smart incremental updates
- **Convenience commands** - `build` and `run` commands for seamless workflow without sacrificing IDE integration

Builderer is in early development and lacks the maturity, feature breadth, and community support of established tools. It's designed for projects that value simplicity, Python familiarity, lightweight tooling, and standalone build file generation.
