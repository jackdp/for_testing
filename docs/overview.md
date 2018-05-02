# JPPack

[JPPack](https://github.com/jackdp/JPPack) / [Docs](./index.md) / Overview

---

## Overview

**JPPack** is a small collection of VCL components for Delphi.  
Supported Delphi versions: **XE2**, **XE3**, **XE4**, **XE5**, **XE6**, **XE7**, **XE8**, **10.0 Seattle**, **10.1 Berlin**, **10.2 Tokyo**.

<p align="center">
<img src="img/JPPack.png">
</p>

These components were created within a few years, they were repeatedly modified, improved, and expanded with the functions needed in the implementation of specific projects. Generally, there is a small chaos, but I think everything works OK (I hope!).

I am no expert on writing VCL components and helped myself by analyzing the source codes (and using fragments) of various free Delphi components, especially [Cindy Components](https://sourceforge.net/projects/tcycomponents/) and [PngComponents](https://bitbucket.org/uweraabe/pngcomponents).

### Cindy Components

Some of the functions and procedures related to graphics processing were taken from the *Cindy Components*. The gradient related routines were almost entirely taken from this package (`VCL.cyGraphics.pas` file).

The author of the *Cindy Component*s is Júlio Maurício Antunes Piao. The sources are available at https://sourceforge.net/projects/tcycomponents/  
In the source files in which I use functions written by Júlio, I have added relevant information with a link to his page.

### PngComponents

After *long and fierce battles* with various buttons from different packages of components for Delphi (commercial and free), I finally found ones that displays the PNG files correctly - **TPngBitBtn** and **TPngSpeedButton** from the *PngComponents* package. I have never had problems with them, unlike many, many others. For this reason, in the implementation of my buttons I decided to rely on the code from this package.

In my buttons, I use 3 files from the *PngComponent* package: **PngFunctions.pas**, **PngButtonFunctions.pas** and **PngImageList.pas**.

In order to not force potential users to install the full *PngComponents* package (although I recommend doing it), I decided to include these three files in the *JPPack*. To prevent any name conflicts, I added the prefix `PNGC.` to the name of each file (and unit).

The original author of the *PngComponents* package is Martijn Saly (`www.thany.org`). The project is currently maintained by [Uwe Raabe](http://www.uweraabe.de/Blog/). Sources are available at https://bitbucket.org/uweraabe/pngcomponents

In the folder [PngComponents_Docs_License](../PngComponents_Docs_License) you can find *PngComponents* package license, changelog and documentation.

---

[JPPack](../) / [Docs](./index.md) / Overview
