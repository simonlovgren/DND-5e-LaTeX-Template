# D&D 5e LaTeX Template

This is LaTeX template for typesetting *Dungeons & Dragons* 5th Edition (D&D 5e) material.

## Features

* Color schemes and fonts are close to the core books.
* TeX Live includes the default fonts.
* Compiles with `pdflatex`.

![Preview](https://github.com/evanbergeron/DND-5e-LaTeX-Template/raw/master/scrot.png)

## Installation

### User install using `TEXMFHOME` (recommended)

This will install the template for your current user in one of the following locations:

* Linux: `~/.texmf/tex/latex`
* OS X / macOS: `~/Library/texmf/tex/latex`
* Windows: `C:\Users\{username}\texmf\tex\latex`

LaTeX will find the package automatically.

1. Prepare your `TEXMFHOME` directory.

    ```sh
    mkdir "$(kpsewhich -var-value TEXMFHOME)/tex/latex/"
    ```
2. Download the [latest release](https://github.com/evanbergeron/DND-5e-LaTeX-Template/releases/latest) and extract it in `$TEXMFHOME/tex/latex/`.

    ```sh
    wget https://github.com/evanbergeron/DND-5e-LaTeX-Template/releases/download/v0.5/dnd-0.5.tar.gz
    tar -xzvf dnd-0.5.tar.gz -C "$(kpsewhich -var-value TEXMFHOME)/tex/latex/"
    ```

    Alternatively, clone the repo to the same location:

    ```sh
    git clone https://github.com/evanbergeron/DND-5e-LaTeX-Template.git "$(kpsewhich -var-value TEXMFHOME)/tex/latex/dnd"
    ```

### Project install using `TEXINPUTS`

You can also clone a copy of the repository to each LaTeX project. For example, to clone the repository to a `lib/` directory in your project:

```sh
mkdir lib/
git clone https://github.com/evanbergeron/DND-5e-LaTeX-Template.git lib/dnd
```

LaTeX will not find the template automatically. Set `TEXINPUTS` when compiling your project to locate the package:

```sh
TEXINPUTS=./lib//: pdflatex project.tex
```

## Usage

Load the template in your preamble:

```tex
\documentclass[10pt,twoside,twocolumn,openany]{book}

\usepackage[english]{babel}
\usepackage[utf8]{inputenc}
\usepackage{dnd}

\begin{document}
% ...
```

### Package options

| Option      | Description                                                       | Default |
|-------------+-------------------------------------------------------------------+:-------:|
| `bg-letter` | Loads a letter-sized background image                             |    ✓    |
| `bg-a4`     | Loads an A4-sized background image                                |         |
| `bg-print`  | Loads a printer-friendly background-image (only the footer image) |         |
| `bg-full`   | Loads the full background image                                   |    ✓    |
| `justified` | Justifies column copy                                             |         |

## Dependencies

If you don't have LaTeX installed, we recommend installing a complete TeX Live distribution.

### Ubuntu

```sh
sudo apt-get install texlive-full
```

### Arch

```sh
sudo pacman -S texlive-bin texlive-core texlive-latexextra
```

## Contributing

### Preparing a new release

1. Run `./bin/bump-version` to tag the new version.

    ```sh
    ./bin/bumpversion <version>
    ```
2. Run `./bin/package` to build the example PDF and zip file for distribution.

    ```sh
    ./bin/package
    ```
    N.B. The `package` script requires `latexmk`.
3. Push changes.

    ```sh
    git push && git push --tags
    ```
4. [Create a new release](https://help.github.com/articles/creating-releases/) and attach the zip file and PDF.

    N.B. Attaching the PDF separately means users can link to it directly.

## Credits

* Background image from [Lost and Taken](https://lostandtaken.com/)

## License

MIT
