# glutin_tao

Glutin rust package that uses tao with modified dependencies, for solving gdk-sys version conflicts

Cargo Build Error:
```
    Updating crates.io index
    Updating git repository `https://github.com/franzcrs/egui.git`
    Updating git repository `https://github.com/tauri-apps/glutin`
error: failed to select a version for `gdk-sys`.
    ... required by package `tao v0.23.0`
    ... which satisfies dependency `winit = "^0.23.0"` of package `eframe_tao v0.23.0 (https://github.com/franzcrs/egui.git?branch=dev-franzcrs#e258ec33)`
    ... which satisfies git dependency `eframe` of package `tauri-egui v0.3.0 (/path_to_tauri-egui)`
versions that meet the requirements `^0.18` are: 0.18.2, 0.18.0

the package `gdk-sys` links to the native library `gdk-3`, but it conflicts with a previous package which links to `gdk-3` as well:
package `gdk-sys v0.16.0`
    ... which satisfies dependency `gdk-sys = "^0.16"` of package `tao v0.19.0`
    ... which satisfies dependency `winit = "^0.19.0"` of package `glutin_tao v0.33.0 (https://github.com/tauri-apps/glutin?branch=0.31#e861174a)`
    ... which satisfies git dependency `glutin-winit` of package `eframe_tao v0.23.0 (https://github.com/franzcrs/egui.git?branch=dev-franzcrs#e258ec33)`
    ... which satisfies git dependency `eframe` of package `tauri-egui v0.3.0 (/path_to_tauri-egui)`
Only one package in the dependency graph may specify the same links value. This helps ensure that only one copy of a native library is linked in the final binary. Try to adjust your dependencies so that only one package uses the `links = "gdk-3"` value. For more information, see https://doc.rust-lang.org/cargo/reference/resolver.html#links.

failed to select a version for `gdk-sys` which could resolve this conflict
```

Glutin is a low-level library for OpenGL context creation, glutin_tao uses tao instead of winit.


[![](https://img.shields.io/crates/v/glutin.svg)](https://crates.io/crates/glutin)
[![Docs.rs](https://docs.rs/glutin/badge.svg)](https://docs.rs/glutin)

```toml
[dependencies]
glutin = "0.30.8"
```

## [Documentation](https://docs.rs/glutin_tao)

### Try it!

```bash
git clone https://github.com/tauri-apps/glutin
cd glutin
cargo run --example window
```

### Usage

Glutin is an OpenGL context creation library, and doesn't directly provide
OpenGL bindings for you.

For examples, please look [here](https://github.com/rust-windowing/glutin/tree/master/glutin_examples).

Note that glutin aims at being a low-level brick in your rendering
infrastructure. You are encouraged to write another layer of abstraction
between glutin and your application.

The minimum Rust version target by glutin is `1.65.0`.

## Platform-specific notes

### Wayland

Wayland is currently unsupported.
