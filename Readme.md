# JPPack 

## Overview

JPPack is a small collection of Delphi VCL components.

These components were created within a few years, they were repeatedly modified, improved, and expanded with the functions needed in the implementation of specific projects. Generally, there is a small chaos, but I think everything works OK (I hope).

Many of my components, unfortunately, I can not share, because they are modified commercial components from different producers, and the license prohibits me from publishing the source codes of such modified components.

I am no expert on writing VCL components and helped myself by analyzing the source codes (and using fragments) of various free Delphi components, especially **Cindy Components** (https://sourceforge.net/projects/tcycomponents/) and **PngComponents** (https://bitbucket.org/uweraabe/pngcomponents).


## Components

### TJppPanel

A panel with several improvements. It was written on the basis of one of the panels included in the Cindy Components package (but I do not remember exactly which one).  
Additional properties: 
1. Upper and bottom part filled with a gradient (or solid color).  
The panel is divided into two parts - upper and lower. For each of them you can define colors separately. The size of the upper part (relative to the lower) can also be modified (property `Appearance.UpperGradientPercent`). For example, you can set the upper gradient size to 30%, then the bottom will automatically take up the rest of the panel surface (70%). You can also completely eliminate the bottom gradient by setting the `UpperGradientPercent` property to 100%.  
If you need to fill the upper part with a gradient and the bottom one with a solid color, set the desired gradient colors of the upper part, then set the same starting and ending color of the gradient in the lower part.  
If you do not want to use a gradient, you can easily turn it off by setting the `Appearance.DrawGradient` property to `False`, then the `Appearance.BackgroundColor` color will be used to fill the panel background with a solid color.
1. Borders.  
You can set the thickness, color, style and visibility of the panel borders. Each border is configured separately. For example, you can set the thickness of the upper edge to 10 pt, the lower one - 2 pt, and hide the left one completely.



## Installation


How to build:
1. Open `src\rmedir.ctpr` file with CodeTyphon or `src\rmedir.lpi` with Lazarus.
2. Set build mode for your destination system.  
Select menu `Project -> Project Options...` A new window will appear.
In the tree view (on the left), select `Compiler Options`.
At the top of this window you can select the build mode from the dropdown list.
Choose: `Release Win32`, `Release Win64`, `Release Lin32` or `Release Lin64`.
3. Build project (menu `Run->Build`).


