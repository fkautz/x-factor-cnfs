---
title: "II. Dependencies"
date: 2018-10-09T15:10:51-07:00
draft: true
---
### Explicitly declare and isolate dependencies

Most programming languages support versioned modules or packages for distributing support libraries, such as [SemVer](https://semver.org/) for Go or [Crates.io](https://crates.io/) for Rust.  Libraries installed through a packaging system can be installed system-wide (known as "site packages") or scoped into the directory containing the app (known as "vendoring" or "bundling"). In compiled languages such as C or Go, the distributed support library may be statically compiled into the application or linked through an explicitly vendored package. 

**A X-factor CNF never relies on implicit existence of system-wide packages.**  It declares all dependencies, completely and exactly, via a *dependency declaration* manifest.  Furthermore, it uses a *dependency isolation* tool during execution to ensure that no implicit dependencies "leak in" from the surrounding system.  The full and explicit dependency specification is applied uniformly to both production and development.

Go has [go modules](https://github.com/golang/go/wiki/Modules) for dependency declaration and static linking can provide dependency isolation. Rust has [Cargo](https://doc.rust-lang.org/cargo/index.html) for both dependency declaration and isolation.  C has [Autoconf](http://www.gnu.org/s/autoconf/) for dependency declaration, and static linking can provide dependency isolation.  No matter what the toolchain, dependency declaration and isolation must always be used together -- only one or the other is not sufficient to satisfy X-factor.

One benefit of explicit dependency declaration is that it simplifies setup for developers new to the CNF.  The new developer can check out the CNF's codebase onto their development machine, requiring only the language runtime and dependency manager installed as prerequisites.  They will be able to set up everything needed to run the CNF's code with a deterministic *build command*.  For example, the build command for Rust/cargo is `cargo build`, while for Go/modules it is `go build`.

X-factor CNFs also do not rely on the implicit existence of any system tools.  Examples include shelling out to ImageMagick or `curl**.  While these tools may exist on many or even most systems, there is no guarantee that they will exist on all systems where the CNF may run in the future, or whether the version found on a future system will be compatible with the CNF.  If the CNF needs to shell out to a system tool, that tool should be vendored into the CNF.

Operational dependencies such as payload types and local mechanisms are not explicitly defined in the build requirements or vendored packages. E.g. the existence of [libmemif](https://docs.fd.io/vpp/17.10/libmemif_doc.html) in the dependency list does not imply that the CNF is capable of communicating over memif. These types of dependencies are covered in Rule XIV, XV and XVI.

### TODO
* Provide guidance for building CNFs which require hardware such as SR-IOV.
