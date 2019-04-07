# JPPack

**A small collection of VCL components for Delphi XE2 - 10.2 Tokyo**

- [Overview](#overview)
- [Components](#components)
  * [TJppPanel](#tjpppanel)
  * [TJppBasicPanel](#tjppbasicpanel)
  * [TJppPngButton](#tjpppngbutton)
  * [TJppBasicPngButton](#tjppbasicpngbutton)
  * [TJppBasicSpeedButton](#tjppbasicspeedbutton)
  * [TJppColorComboBox](#tjppcolorcombobox)
  * [TJppColorListBox](#tjppcolorlistbox)
  * [TJppLinkLabel](#tjpplinklabel)
  * [TJppTimer](#tjpptimer)
  * [TJppStorageCtrl](#tjppstoragectrl)
- [TagExt](#tagext)
- [Installation](#installation)


## Overview

**JPPack** is a small collection of VCL components for Delphi.  
Supported Delphi versions: **XE2**, **XE3**, **XE4**, **XE5**, **XE6**, **XE7**, **XE8**, **10.0 Seattle**, **10.1 Berlin**, **10.2 Tokyo**.

<p align="center">
<img src="./docs/img/JPPack.png">
</p>

These components were created within a few years, they were repeatedly modified, improved, and extended with the functions needed in the implementation of specific projects. Generally, there is a small chaos, but I think everything works OK (I hope!).

I am no expert on writing VCL components and helped myself by analyzing the source codes (and using fragments) of various free Delphi components, especially [Cindy Components](https://sourceforge.net/projects/tcycomponents/) and [PngComponents](https://bitbucket.org/uweraabe/pngcomponents).

### Cindy Components

Some of the functions and procedures related to graphics processing were taken from the *Cindy Components*. The gradient related routines were almost entirely taken from this package (`VCL.cyGraphics.pas` file).

The author of the *Cindy Component*s is Júlio Maurício Antunes Piao. The sources are available at https://sourceforge.net/projects/tcycomponents/  
In the source files in which I use functions written by Júlio, I have added relevant information with a link to his page.

### PngComponents

After *long and fierce battles* with various buttons from different packages of components for Delphi (commercial and free), I finally found ones that displays the PNG files correctly - **TPngBitBtn** and **TPngSpeedButton** from the *PngComponents* package. I have never had problems with them, unlike many, many others. For this reason, in the implementation of my buttons I decided to rely on the code from this package.

The original author of the *PngComponents* package is Martijn Saly (`www.thany.org`). The project is currently maintained by [Uwe Raabe](http://www.uweraabe.de/Blog/). Sources are available at https://bitbucket.org/uweraabe/pngcomponents

In the folder [3rd-party](3rd-party) you can find the ZIP file with the *PngComponents* ver. 1.4.1. This is the latest version of the *PngComponents* available when writing this document and it works fine with the *JPPack*.

## Components

### TJppPanel

A highly customizable panel. `TCustomPanel` descendant.  
It was written on the basis of one of the panels included in the *Cindy Components* package (but I do not remember exactly which one).  

<p align="center">
<img src="./docs/img/TJppPanel.png">
</p>

The panel is divided into two parts - upper and lower. For each of them you can define colors (gradient or solid) separately.

All panel borders are configured separately. You can set different color, thickness, style, visibility for each border.

The panel has a built-in support for the unlimited collection of captions. Each caption has its own property `Font: TFont`, and can be centered or positioned relative to the corners of the panel.

Moreover, the `TJppPanel` has a built-in support for the unlimited collection of horizontal lines, vertical lines and horizontal bars.

[More info...](./docs/TJppPanel.md)

### TJppBasicPanel

A truncated version of the `TJppPanel`. It does not have built-in collections of captions, vertical lines, horizontal lines, and horizontal bars.

### TJppPngButton

`TJppPngButton` is an extended `TPngBitBtn` button from the **PngComponents** package.  

<p align="center">
<img src="./docs/img/TJppPngButtons.png">
</p>

The button can be in one of **five states**: *normal*, *hot*, *down* (pressed), *focused* and *disabled*. For each state you can set a whole range of display parameters: upper and bottom gradient/solid color (similarly to `TJppPanel`), border color, style and width, font parameters (color, name, size, style).

If you want the button to be displayed in system colors, set property `Appearance.DefaultDrawing` to `True` (all custom colors defined in the `Appearance.<STATES>` will then be ignored).

The number of all colors for all button states is really big, so I decided to make it easier to manage the displayed colors using ready-to-use color schemes (color maps).

I have created 36 different color schemes for `TJppPngButton`. To change the active color scheme, select one of the schemes available in the `ColorMapType` property in the *Object Inspector*.

Color schemes can be edited with the `TJppPngButton Color Maps Designer` program, which is located in the repository in the `demos` directory.

[More info...](./docs/TJppPngButton.md)

### TJppBasicPngButton

This button is a slightly truncated version of the `TJppPngButton`. It has only one gradient for each button state and does not support color schemes.

### TJppBasicSpeedButton

This button is very similar to `TJppBasicPngButton`, but it is based on `TGraphicControl`, so it does not take the focus (it has no *focused* state).

### TJppColorComboBox

A highly customizable *ComboBox* displaying a list of predefined and/or user-defined colors.

<p align="center">
<img src="./docs/img/TJppColorComboBox_1.png">
<br><br>
<img src="./docs/img/TJppColorComboBox_4.png">
<br><br>
<img src="./docs/img/TJppColorComboBox_2.png">
<br><br>
<img src="./docs/img/TJppColorComboBox_5.png">
</p>


The `TJppColorComboBox` has 4 built-in components: one label and 3 buttons to change, copy and paste color.

Colors can be displayed in three formats: **RGB Int** (eg. 051,102,255), **RGB Hex** (eg. #3366FF), and **BGR Hex** (eg. $00FF6633). If you need to display the color in a different format, you can do this in the `OnGetColorStrValue` event handler.

In addition to standard items (displaying color) you can also add separators and *ChangeColor* items.

Each color selected by the user, but not yet in the color list, can be automatically added to the end or top of the list. Thanks to this the user of your application has access to the *history* of previously selected colors.

[More info...](./docs/TJppColorComboBox.md)

### TJppColorListBox

A highly customizable *ListBox* displaying a list of predefined and/or user-defined colors.

<p align="center">
<img src="./docs/img/TJppColorListBox_1.png">
<br><br>
<img src="./docs/img/TJppColorListBox_2.png">
</p>

It is very similar to `TJppColorComboBox`, but it has no built-in components.


### TJppLinkLabel

Label with additional fonts (`TFont`) for 5 states: *normal*, *visited-normal*, *hot*, *visited-hot* and *disabled*. It is inherited from `TCustomLabel`.

[More info...](./docs/TJppLinkLabel.md)

### TJppTimer

A standard `TTimer` component with a few additional properties and methods:
1. `RepeatCountLimit` property.  
Here you can set how many times the time interval specified in the `Interval` property can be reached. The value `0` means no limit.
1. `Counter` property.  
Each time the time interval specified in the `Interval` property expires, the` Counter` property is incremented by 1. When the `Counter` reaches the value of `RepeatCountLimit`, the timer is stopped and the `OnRepeatCountLimitReached` event handler is triggered (if assigned).
1. `ClearCounterOnStart` property. If is set to `True`, then the `Start` method resets the `Counter`.
1. `Start` method. Sets `Enabled` to `True`. If `ClearCounterOnStart` is set to `True` then the `Start` sets the `Counter` property to `0`.
1. `Stop` method. Sets the `Enabled` to `False`.
1. `OnRepeatCountLimitReached` event - fired when the `Counter` reaches the value of `RepeatCountLimit`.

Example: Displaying the counter every one second. Display the message after 10 seconds and switch off of the `Timer`.
```delphi
procedure TForm1.FormCreate(Sender: TObject);
begin
  JppTimer1.Interval := 1000;
  JppTimer1.RepeatCountLimit := 10; //JppTimer1 will stop automatically after 10 seconds.
  JppTimer1.Start;
end;

procedure TForm1.JppTimer1Timer(Sender: TObject);
begin
  Label1.Caption := JppTimer1.Counter.ToString;
end;

procedure TForm1.JppTimer1RepeatCountLimitReached(Sender: TObject);
begin
  ShowMessage('10 seconds elapsed!');
end;
```

### TJppStorageCtrl

`TJppStorageCtrl` is a non-visual component that allows you to store information of different types in the collection. Each item of the collection stores the following data:
- 4 String values,
- 2 Integer values,
- 2 Int64 values,
- 2 float values (Double),
- 2 Boolean values,
- 2 TColor values,
- 2 Byte values,
- 2 Pointer values.

Items are accesible from the *Object Inspector* using `StorageCollection` property.
The values of each item of the collection, except pointers, can also be set in the *Object Inspector*. Pointer values can only be set in the code and they are initialized by default to `nil`.

To acces the collection items in the code you can use the `Items` property, eg:
```delphi
JppStorageCtrl.Items[0].IntValue1 := 1;
JppStorageCtrl.Items[0].PointerValue1 := SomePointer;
```
But, since `Items` is set as the **default** property, you can write it simply:
```delphi
JppStorageCtrl[0].IntValue1 := 1;
JppStorageCtrl[0].PointerValue1 := SomePointer;
```
This component can be useful if you want to have access to some global data, and you do not want to create global variables.

I sometimes use this component in the early stages of writing applications. In later stages, a definitely better way to store and manage data is to design specialized records, classes, generic/pointer containers, etc.

## TagExt

Each component in the **JPPack** package has the `TagExt` property. Here you can store one integer value (`IntValue`), string (`StrValue`), float number (`RealValue`), pointer (`PointerValue`) and date (`DateValue`). The first three values are available from the `Object Inspector` and in the code, the last two - only in the code.

Default values:

Property | Default value
-------- |------
`TagExt.IntValue` | `0`
`TagExt.StrValue` | `''`
`TagExt.RealValue` | `0`
`TagExt.PointerValue` | **`nil`**
`TagExt.DateValue` | `Now`


## Installation

Before installing the **JPPack** package, you must first install 2 another packages:
1. **JPLib** from https://github.com/jackdp/JPLib
1. **PngComponents** from https://bitbucket.org/uweraabe/pngcomponents  
You can use *PngComponents* ver. 1.4.1 package from the [3rd-party](3rd-party) folder. I tested *JPPack* with this version and it looks like everything works OK.

In the [packages](packages) folder you can find installation packages for all Delphi versions from **XE2** to **10.2 Tokyo**.  
Go to the subfolder with the name of your Delphi version (eg `Delphi_XE7` for XE7 version) and open the file `JPPackVCL.dproj` or `JPPackVCL.dpk`. In the *Project Manager*, right-click the `JPPackVCL.bpl` file, then select `Install` in the popup menu. After a short time, a message should appear displaying information about the correct installation of the package and with the list of newly installed components. All components you can find ont the **JPPack** page in the *Tool Palette*.

After installing the package, it is best to add the `source` folder to the **library path**:
1. Select menu `Tools` --> `Options`.
1. In the tree view on the left, go to `Environment Options` --> `Delphi Options` --> `Library`.
1. In the **Library path** combo box (on the right), add `;` (semicolon) and the path to the `source` directory.
