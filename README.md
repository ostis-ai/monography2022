# Monography 2022

## Quick start

To build this repo you need latexmk installed.

```sh
git submodule update --init --recursive
latexmk -pdf -bibtex ./book.tex
```
If you're experiencing any problems with compilation, please refer to [full guide](#full-guide) section

## Full guide

> The main latex problem --- if compiler says that there is an error on line 52, it means that error might be even in another file.

### Choosing compiler

We strongly recommend you to use **latexmk** with **pdflatex** on back to compile this monography. Of course you can use plain **pdflatex** compiler as well, but keep in mind that in this case you need to run compilation several times to get all parts of document rendered. We also provide basic `latexmkrc` configuration, so if you'd like to use plain **pdflatex** ensure that `TEXINPUTS` environment variable is configured correctly (it's very important for [scn-latex-plugin](https://github.com/ostis-ai/scn-latex-plugin) support). In terminal `TEXINPUTS` might be configured right before compilation, e.g.
```sh
TEXINPUTS=./scn: latexmk -pdf -bibtex ./book.tex
```

Unfortunately, a lot of IDEs has their own configuration systems for LaTeX so this configuration is up to you. The main idea of that configuration is to add `./scn` folder to list of paths, where latex searches for packages.

**Note**: Compilation with **xelatex** and **lualatex** wasn't tested, so we can't guarantee that you'll get the correctly rendered version with their usage.

### Preambule

[scn-latex-plugin](https://github.com/ostis-ai/scn-latex-plugin) is used here as package, so to start using SCn frames in text you need to import it via `\usepackage{scn}`

**Note**: <u>NEVER</u> try to import this package as `\usepackage{scn/scn}`. Latex compilers are totally fail in relative paths resolving (they just can't). The fact is that it works, but it's just an error of compiler.

### Troubleshooting
* `scn.sty` not found
  + If you get such error message, please ensure that you have submodule content in `./scn` directory (run `git submodule update --init --recursive`)
  + Ensure that compiler and `TEXINPUTS` are configured correctly ([guide is there](#choosing-compiler))
