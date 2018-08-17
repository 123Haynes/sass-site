---
title: Comments
---

The way Sass comments work differs substantially between SCSS and the indented
syntax. Both syntaxes support two types of comments: comments defined using `/*`
that are (usually) compiled to CSS, and comments defined using `//` that are
not.

## In SCSS

Comments in SCSS work similarly to comments in other languages like JavaScript.
**Single-line comments** start with `//`, and go until the end of the line.
Nothing in a single-line comment is evaluated as CSS; as far as Sass is
concerned, they may as well not exist.

**Multi-line comments** start with `/*` and end at the next `*/`. If a
multi-line comment is written somewhere that a [statement][] is allowed, it's
compiled to a CSS comment. A multi-line comment that's compiled to CSS may
contain [interpolation][], which will be evaluated before the comment is compiled.

By default, multi-line comments be stripped from the compiled CSS in [compressed
mode][]. If a comment begins with `/*!`, though, it will always be included in
the CSS output.

[statement]: structure#statements
[interpolation]: ../interpolation
[compressed mode]: ../output-styles

```scss
// This comment won't be included in the CSS.

/* But this comment will, except in compressed mode. */

/*! This comment will be included even in compressed mode. */

p /* Multi-line comments can be written anywhere
   * whitespace is allowed. */ .sans {
  font: Helvetica, // So can single-line commments.
        sans-serif;
}
```
