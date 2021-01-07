## Requirements

Building the book requires [mdBook]:

[mdbook]: https://github.com/rust-lang-nursery/mdBook

```bash
$ cargo install mdbook
```

## Building

To build the book, type:

```bash
$ mdbook build
```

The output will be in the book subdirectory. To check it out, open it in your web browser.

## Usage

mdBook is primarily used as a command line tool, even though it exposes
all its functionality as a Rust crate for integration in other projects.

Here are the main commands you will want to run. For a more exhaustive
explanation, check out the [User Guide].

- `mdbook init <directory>`

  The init command will create a directory with the minimal boilerplate to
  start with. If the `<directory>` parameter is omitted, the current
  directory will be used.

  ```
  book-test/
  ├── book
  └── src
      ├── chapter_1.md
      └── SUMMARY.md
  ```

  `book` and `src` are both directories. `src` contains the markdown files
  that will be used to render the output to the `book` directory.

  Please, take a look at the [CLI docs] for more information and some neat tricks.

- `mdbook build`

  This is the command you will run to render your book, it reads the
  `SUMMARY.md` file to understand the structure of your book, takes the
  markdown files in the source directory as input and outputs static html
  pages that you can upload to a server.

- `mdbook watch`

  When you run this command, mdbook will watch your markdown files to rebuild
  the book on every change. This avoids having to come back to the terminal
  to type `mdbook build` over and over again.

- `mdbook serve`

  Does the same thing as `mdbook watch` but additionally serves the book at
  `http://localhost:3000` (port is changeable) and reloads the browser when a
  change occurs.

- `mdbook clean`

  Delete directory in which generated book is located.
