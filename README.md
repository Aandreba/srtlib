# srtlib

[![Build Status](https://img.shields.io/github/workflow/status/galenkod/srtlib/Rust)](https://github.com/galenkod/srtlib/actions?query=workflow%3ARust)
[![Version](https://img.shields.io/crates/v/srtlib)](https://crates.io/crates/srtlib)
[![Documentation](https://docs.rs/srtlib/badge.svg)](https://docs.rs/srtlib)
![License](https://img.shields.io/crates/l/srtlib)

A simple Rust library for handling .srt subtitle files.

* [`srtlib` documentation](https://docs.rs/srtlib)

srtlib allows you to handle subtitle files as collections of multiple subtitle structs, letting you modify the subtitles without directly messing with the .srt files.

Subtitle collections can be generated by parsing strings or files, but also from the ground up, enabling total control of all the elements of each subtitle.  

## Usage

Add this to your Cargo.toml:
```toml
[dependencies]
srtlib = "0.1"
```
To read a .srt file:
```rust
use srtlib::Subtitles;

// Parse subtitles from file that uses the utf-8 encoding.
let mut subs = Subtitles::parse_from_file("subtitles.srt", None).unwrap();
```

You can now perform any action you want on the subtitles.
For example to move all subtitles 10 seconds forward in time:

```rust
// Move every subtitle 10 seconds forward in time.
for s in &mut subs {
    s.add_seconds(10);
}
```

Finally we can write the subtitles back to a .srt file:

```rust
subs.write_to_file("subtitles_fixed.srt", None).unwrap();
```
For more examples refer to the [documentation](https://docs.rs/srtlib).

## License

Licensed under either of

 * Apache License, Version 2.0
   ([LICENSE-APACHE](LICENSE-APACHE) or http://www.apache.org/licenses/LICENSE-2.0)
 * MIT license
   ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)

at your option.

## Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.
