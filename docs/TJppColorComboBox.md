# TJppColorComboBox

A ComboBox displaying a list of user-defined colors.

<p align="center">
<img src="img/JppColorComboBox_1.png">
<br><br>
<img src="img/JppColorComboBox_4.png">
<br><br>
<img src="img/JppColorComboBox_2.png">
<br><br>
<img src="img/JppColorComboBox_3.png">
</p>

The current color can be read and set using property `Selected`: `TColor`.

The width of the colored rectangles displayed in the list can be changed using the `Param_ColorRectWidth` property.

If you do not want to display the RGB value of the colors, set `Param_ShowRGB` property to `False`.

## Internal controls

The `TJppColorComboBox` has a built-in label (`BoundLabel`) so there is no need to add a separate label describing the component's function, which is common practice.

In addition, the component has three built-in auxiliary buttons:
1. `ButtonChangeColor` - After clicking it, the system color selection window (`TColorDialog`) is displayed. If the user selects a color and presses OK, it will be stored in the `Selected` property.
1. `ButtonCopyColor` - After the user clicks, the currently selected color is copied to the system clipboard.
1. `ButtonPasteColor` - After clicking, the current color is set to the one from the clipboard (if it is correct).

All of these buttons are inherited from the `TJppBasicSpeedButton` class, so you can freely set PNG icons and background colors, borders, fonts, for all available button states: *normal*, *hot*, *down* and *disabled*.  
Moreover, these buttons have built-in support for the actions. In the `Action` property of each button you can set any action registered in the `TActionList` which is to be executed after clicking the button. But with one caveat, you must do this **at runtime**, eg:
```delphi
JppColorComboBox.ButtonChangeColor.Action := actMyAction; // actMyAction: Vcl.ActnList.TAction
```

The `ButtonSpacing` property specifies the space between these internal buttons.

## History

Each color selected by the user, but not yet in the color list, is automatically added to the end of the list. Thanks to this the user of your application has access to the *history* of previously selected colors.

## Adding colors
You can add colors to the list in two ways: using the `Items` property or `AddColor` procedure.

In the first method, you must add the appropriate entries to `Items`. Each entry should have the form:
```
color_name=R,G,B
```
where `R`, `G` and `B` denote the intensity of red, green and blue colors.  
The color name is optional. You can add color without a name using: `=R,G,B`.

Example:
```
Aquamarine=51,204,204
Purple=128,0,128
Pink=255,0,255
Plum=153,51,102
=50,100,150
=100,150,200
```
The last two colors have no names.

In the second way, you must call the `AddColors` method and pass the color name and color value, eg:
```delphi
JppColorComboBox.AddColor('Red', clRed);
JppColorComboBox.AddColor('Bright Yellow', RGB(252, 249, 225));
JppColorComboBox.AddColor('', RGB(75, 150, 225)); // <-- color wihout name
```

## Additional information

If you want to remove all default colors from the list and use only your own colors, you need to know about one thing: after selecting the **first element** of the list by the user, a dialog box for choosing a color is displayed. Therefore, the first element of the list should be `Select color...`, `Choose color...` or something similar.

The items with text `-` (one dash) are treated as **separators**. This allows you to create several separated color groups.

Example:

```delphi
  JppColorComboBox.Items.BeginUpdate;
  try
    JppColorComboBox.Clear;

    JppColorComboBox.Items.Add('Select color...'); // The first item
    JppColorComboBox.Items.Add('-'); // Separator

    // Blue colors
    JppColorComboBox.AddColor('Light Blue', RGB(173,216,230));
    JppColorComboBox.AddColor('Sky Blue', RGB(135,206,235));
    JppColorComboBox.AddColor('Deep Sky Blue', RGB(000,191,255));
    JppColorComboBox.AddColor('Dodger Sky Blue', RGB(030,144,255));
    JppColorComboBox.AddColor('Steel Blue', RGB(070,130,180));

    JppColorComboBox.Items.Add('-'); // Separator

    // Red colors
    JppColorComboBox.AddColor('Light Salmon', RGB(255,160,122));
    JppColorComboBox.AddColor('Salmon', RGB(250,128,114));
    JppColorComboBox.AddColor('Crimson', RGB(205,092,092));
    JppColorComboBox.AddColor('Red', RGB(255,000,000));

    JppColorComboBox.Items.Add('-'); // Separator

    // Gray colors
    JppColorComboBox.AddColor('Gainsboro', RGB(220,220,220));
    JppColorComboBox.AddColor('Silver', RGB(192,192,192));
    JppColorComboBox.AddColor('Gray', RGB(128,128,128));

  finally
    JppColorComboBox.Items.EndUpdate;
  end;

  JppColorComboBox.ItemIndex := 2;
```

Result:

<p align="center">
<img src="img/JppColorComboBox_ColorGroups.png">
</p>
