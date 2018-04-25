# DfmExtractor 

* [Overview](#overview)
* [Download](#download)
* [Usage](#usage)
	* [Input / Output options](#input--output-options)
	* [Information](#information)
* [Compilation](#compilation)
* [Changelog / Releases](#changelog--releases)

# Overview

DfmExtractor is a small command line utility which allows you to extract DFM, LFM and FRM forms from executable files compiled by Delphi, Lazarus and CodeTyphon.

# Download

Source: https://github.com/jackdp/DfmExtractor

Binary (Windows 32-bit): http://www.pazera-software.com/products/dfm-extractor/


# Usage

Usage: **DfmExtractor.exe** `-i=FILE [-n=NAME] [-idx=X] [-o=FILE] [-e=EXT] [-p=STR] [-a] [-d=DIR]
[-l] [-h] [-V] [--home]`

Mandatory arguments to long options are mandatory for short options too.  
Options are **case-sensitive**. Options in square brackets are optional.  

## Input / Output options

**`-i`, `--input-file=FILE`**  
An executable file containing Delphi, Lazarus or CodeTyphon forms (DFM, LFM, FRM).

**`-n`, `--form-name=NAME`**  
Form name or form class name to extract.

**`-idx`, `--form-index=X`**  
The index of the form to extract. Non-negative integer.

**`-o`, `--output-file=FILE`**  
The output file with extracted form.

**`-e`, `--extension=EXT`**  
The default extension of the output file(s). If not specified, DFM will be used.

**`-p`, `--prefix=STR`**  
Output file(s) name prefix (for the `-a` option).

**`-a`, `--save-all`**  
Saves all forms from the specified executable file to the given (or current) directory.

**`-d`, `--output-dir=DIR`**  
Output directory (for the `-a` option).

**`-l`, `--list`**  
Displays a list of all forms in the given input file.

## Information

**`-h`, `--help`**  
Show help.

**`-V`, `--version`**  
Show application version.

**`--home`**  
Opens program homepage in the default browser.

# Examples

1. List all forms in the file AudioExtractor64.exe:  
  `DfmExtractor.exe -i AudioExtractor64.exe -l`  
  Result:  
    ```
    Forms: 10
    Index |  Lines | Form name        | Form class
    -------------------------------------------------------
        0 |    451 | CustomizeFrm     | TCustomizeFrm
        1 |    343 | FormAbout        | TFormAbout
        2 |     49 | FormCmdLine      | TFormCmdLine
        3 |    345 | FormErrors       | TFormErrors
        4 |  1 621 | FormFileInfo     | TFormFileInfo
        5 |    474 | FormListFileEdit | TFormListFileEdit
        6 |  6 035 | FormMain         | TFormMain
        7 |    790 | FormOptions      | TFormOptions
        8 |    422 | FormProgress     | TFormProgress
        9 |    169 | FormToolsInfo    | TFormToolsInfo
    ```
1. sss

# Compilation

> Tested on CodeTyphon 6.40 with FPC 3.1.1 and Laraus 1.9.0 (trunk version) with FPC 3.1.1

To compile, you need:
1. [CodeTyphon](http://pilotlogic.com/sitejoom/) or [Lazarus](https://www.lazarus-ide.org/).
1. [JPL.CmdLineParser](https://github.com/jackdp/JPL.CmdLineParser) unit.
1. A several Pascal units from my library [JPLib](https://github.com/jackdp/JPLib/).
1. **JclPeImage** unit and it's dependencies from the [JEDI Code Library](https://github.com/project-jedi/jcl). (All necessary JCL unit are in the **jcl.7z** archive in the [src/jcl](src/jcl) directory.)

How to build:
1. Open `src\DfmExtractor.ctpr` file with CodeTyphon or `src\DfmExtractor.lpi` with Lazarus.
1. Set build mode.  
Select menu `Project -> Project Options...` A new window will appear.
In the tree view (on the left), select `Compiler Options`.
At the top of this window you can select the build mode from the dropdown list.
Choose: `Release Win32` or `Debug Win32`.
1. Build project (menu `Run->Build`).


# Changelog / Releases

**Version 1.1** (2018.02.28)
- Project ported from Delphi to Lazarus/CodeTyphon.
- The size of the executable file has been reduced twice.
- Internal enhancements.

**Version 1.0** (2018.01.11)  
Initial release.

# Note

This program was made for my private use, but it may also be useful to someone.

When translating one program written in Delphi, I needed DFM forms to make it easier to work with the [Poedit](https://github.com/vslavik/poedit) program, so I decided to write a small program to extract DFMs.