## Overview

"Universal" assembly syntax definition for Sublime Text, suitable for:
- Intel-style assembly
- AT&T-style assembly
- ARM-style assembly
- Go-style assembly

(MASM numeric suffixes are not supported at the moment.)

## Why

There are many assembly formats, they conflict on the `.s` file extension, and you want one syntax definition suitable for all.

In addition, Go uses its own assembly format, which is mostly AT&T-style but with additional features and quirks. Other assembly syntaxes for ST can't handle it / don't support it.

## Features

The following is supported:

- Common comment types: `//`, `/**/`, `;`, and first-line shebang `#!`.
- Arbitrary preprocessor directives: `#include "some_file"`.
- Preprocessor macro definitions: `#define some_macro`.
- Arbitrary directives: `.some_directive`.
- Directive macro definitions: `.macro some_macro`.
- Arbitrary instructions: `mov x0, x1`.
- Labels: `some_label:`.
- Numeric literals (immediates) with optional unary operator prefixes.
  - Intel-style: `123` `-123`.
  - AT&T-style: `$123` `$-123`.
  - ARM-style: `#123` `#-123`.
- Numeric radix prefixes: `0b10` `0o10` `0x10`.
- String literals: single-quoted, double-quoted, backtick-quoted.
- Common operators: `+ - & |` and so on.
- Common delimiters: `() [] {}`.
- Common punctuation: `,` and `.`, as well as Go's `·`.
- AT&T-style register prefix: `%`.
- Go-style function definitions such as:
  - `TEXT morestack`.
  - `TEXT ·morestack`.
  - `TEXT runtime·morestack`.
  - `TEXT runtime·memhash<ABIInternal>`.

Some assemblers, including Clang, support comments starting with `#`. They are not supported here because of conflict with preprocessor directives and immediate prefixes.

## Installation

Clone this repository into ST's Packages folder. Find it using Sublime's menu → Preferences → Browse Packages. On MacOS, this is usually `"/Users/<user>/Library/Application Support/Sublime Text/Packages"`.

It will automatically pick up files with extensions `.s`, `.asm`, `.goasm`. The latter two are made-up as a way to disambiguate assembly formats.

## Misc

License: https://unlicense.org

I'm receptive to suggestions. If this package _almost_ satisfies you but needs changes, open an issue or chat me up. Contacts: https://mitranim.com/#contacts
