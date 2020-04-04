# GCOMP, an open KiCad component library

Agregates all the components I ever needed.

## Credits

Most designs and datasheets I used are from [DigiKey Electronics](https://www.digikey.com/)
therefore the intellectual property belongs to them and their partners.

**You must comply with [DigiKey's Terms and Conditions](https://www.digikey.com/en/terms-and-conditions)!**

## Naming pattern

An almost standard naming pattern is applied to each component metadata and file name.

Note: terms enclosed in braces (`{` and `}`) are placeholders (e.g. `{placeholder}`).

### Metadata fields

KiCad format provides few default fields:

* Reference
* Value
* Footprint
* Documentation

In addition, there are a few added fields:

* *{product_value}* (optional)
* Series (optional)
* Vendor
* DigiKey product

 Field             | Should be displayed | Optional | Description / Recommended value
:-----------------:|:-------------------:|:--------:|:------------------------------------------
 Reference         | Yes                 | No       | See next table [here](#reference-field).
 Value             | Yes                 | No       | The component manufacturer reference.
 Footprint         | No                  | No       | The component footprint link.
 Documentation     | No                  | No       | The datasheet link (or drawings at least).
 *{product_value}* | Yes if existent     | Yes      | This field's name depends on the "Reference" value. See [here](#reference-field) for details.
 Series            | No                  | Yes      | The product series if specified.
 Vendor            | No                  | No       | The product manufacturer name.
 DigiKey product   | No                  | No       | A link to the DigiKey product page.

#### Reference field
 
The reference field is used as prefix to recognise which type of component it is.

 Reference prefix | *{product_value}* name | *{product_value}* value  | Meaning
:----------------:|:----------------------:|:------------------------:|:--------------------------
 B                | -                      | -                        | Battery
 BR               | -                      | -                        | Bridge Rectifier
 C                | Capacity               | The capacity with unit   | Capacitor
 D                | -                      | -                        | Diode (including LED)
 F                | Calibre                | The fuse maximum current | Fuse
 H                | -                      | -                        | Header connector
 J                | -                      | -                        | Connector
 K                | -                      | -                        | Relay
 L                | Inductance             | The inductance value     | Inductor
 M                | -                      | -                        | Motor
 N                | -                      | -                        | Network (containing multiple passive components - usually resistors or capacitors)
 Q                | -                      | -                        | Transistor
 P                | Resistance             | The resistance value     | Potentiometer
 R                | Resistance             | The resistance value     | Resistor
 S                | -                      | -                        | Switch
 T                | -                      | -                        | Transformer
 TP               | -                      | -                        | Test point
 U                | -                      | -                        | Chip or integrated circuit
 V                | -                      | -                        | Varistor / MOV
 X                | Frequency              | The frequency value      | Crystal
 
All those values are taken from [a stackexchange answer](https://electronics.stackexchange.com/questions/154232/component-naming-conventions).

### File names

*STEP* and *KiCad modules (footprints)* must follow the below defined pattern:

```
{vendor}_{product_reference}.{extension}
```

with

* `{vendor}` replaced by the vendor stub, see [this table](#vendors).
* `{product_reference}` replaced by the transformed value of the "Value" [metadata field](#metadata-fields) following this rule:
  * the name must contain only alphanumeric characters (matching regular expression: `[a-zA-Z0-9]`) and dashes (`-`). All other characters must be converted to dashes.
* `{extension}` must be one of:
  * `stp` for STEP 3D model files.
  * `kicad_mod` for KiCad modules (footprints) files.

Those files are located in the [footprints](/footprints) folder.

*KiCad library* is named `symbols.{extension}` where `{extension}` is one of `lib` or `dcm` as described [here](https://en.wikibooks.org/wiki/Kicad/file_formats#File_formats).

## Vendors

All vendors are listed in the following table.

 Vendor name          | Vendor stub         | Vendor website
:--------------------:|:--------------------|:---------------
Espressif Systems     | `espressif-systems` | [www.espressif.com](https://www.espressif.com/)
Molex                 | `molex`             | [www.molex.com](https://www.molex.com/)
Vishay Semiconductors | `vishay`            | [www.vishay.com](http://www.vishay.com/)

## Installation

Here are the installation steps.

You can either use git or a downloaded zip distribution.

### Using Git

First you need to clone this repository, in a console:

```console
git clone https://github.com/Axelandre42/GCOMP.git
```

Then you may checkout a specific tag (optional):

```console
git checkout tags/{tag}
```

with `{tag}` one of the tag you want.

#### Using as submodule

You may use this repository as submodule for another project managed by Git.

Make sure all references to GCOMP paths are relative to the project directory.

### Using a distribution

Unzip the distribution in an empty folder.

### Configuring KiCad

Configuration steps are rather easy too:

1. Setup library location,
   1. Go to the path settings,
   2. Add a path named `GCOMP` pointing to where you installed the library,
2. Setup symbols library,
   1. Go to symbols library settings,
   2. Add either a global library or a project specific library,
   3. Set the name to `Gcomp` and the library path to `${GCOMP}/symbols.lib`,
3. Setup footprints library,
   1. Go to footprints library settings,
   2. Add either a global library or a project specific library,
   3. Set the name to `Gcomp` and the library path to `${GCOMP}/footprints`,

#### Configuration script

Coming soon.
