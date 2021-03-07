<div align="center">
  <h1><code>basic-text</code></h1>

  <p>
    <strong>Basic Text strings and I/O streams</strong>
  </p>

  <p>
    <a href="https://github.com/sunfishcode/basic-text/actions?query=workflow%3ACI"><img src="https://github.com/sunfishcode/basic-text/workflows/CI/badge.svg" alt="Github Actions CI Status" /></a>
    <a href="https://crates.io/crates/basic-text"><img src="https://img.shields.io/crates/v/basic-text.svg" alt="crates.io page" /></a>
    <a href="https://docs.rs/basic-text"><img src="https://docs.rs/basic-text/badge.svg" alt="docs.rs docs" /></a>
  </p>
</div>

This repository defines a text format called [Basic Text], a subset of Unicode
being developed to focus on *text*: it excludes unprintable control characters,
characters which depend on out-of-band information to interpret,
non-characters, and more, while aiming to preserve everything of use to plain
text and formats built on top of plain text.

It also includes a Rust crate which aims to implement the Basic Text format,
providing several utilities:

 - [`TextString`] and [`TextStr`] are similar to the standard library's [`String`]
   and [`str`], but use the Basic Text string format.

 - [`TextReader`] and [`TextWriter`] are input and output streams which use the
   Basic Text stream format. On input, content is converted in a way which is
   lossy with respect to the original bytestream. Output uses the "strict"
   conversion method, in which invalid content is diagnosed with errors.

 - [`TextDuplexer`] is a [`Duplex`] for reading and writing on an interactive
   stream using Basic Text.

The code here is usable, but fairly new and has not yet been optimized much. It
implements most of the Basic Text spec, though see the `TODO`s in the tests
directory for remaining missing pieces.

[`TextString`]: https://docs.rs/basic-text/latest/basic_text/struct.TextString.html
[`TextStr`]: https://docs.rs/basic-text/latest/basic_text/struct.TextStr.html
[`TextReader`]: https://docs.rs/basic-text/latest/basic_text/struct.TextReader.html
[`TextWriter`]: https://docs.rs/basic-text/latest/basic_text/struct.TextWriter.html
[`TextDuplexer`]: https://docs.rs/basic-text/latest/basic_text/struct.TextDuplexer.html
[`str`]: https://doc.rust-lang.org/std/primitive.str.html
[`String`]: https://doc.rust-lang.org/std/string/struct.String.html
[`Duplex`]: https://docs.rs/duplex/latest/duplex/trait.Duplex.html
[Basic Text]: docs/BasicText.md
