## Installation

In the [packages](packages) folder you can find installation packages for all Delphi versions from **XE2** to **10.2 Tokyo**.
Go to the subfolder with the name of your Delphi version (eg `Delphi_XE7` for XE7 version) and open the file `JPPack2.dproj` or `JPPack2.dpk`. In the *Project Manager*, right-click the `JPPack2.bpl` file, then select `Install` in the popup menu. After a short time, a message should appear displaying information about the correct installation of the package and with the list of newly installed components. All components you can find ont the **JPPack** page in the *Tool Palette*.

After installing the package, it is best to add the `source` folder to the **library path**:
1. Select menu `Tools` --> `Options`.
1. In the tree view on the left, go to `Environment Options` --> `Delphi Options` --> `Library`.
1. In the **Library path** combo box (on the right), add `;` (semicolon) and the path to the `source` directory.
