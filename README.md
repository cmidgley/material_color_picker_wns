# Material Color Picker [![pub package](https://img.shields.io/pub/v/material_color_picker_wns.svg)](https://pub.dartlang.org/packages/material_color_picker_wns)

Material Color picker is a Flutter widget, that can be customizable.

By default, it's Material Colors, but you can define your own colors.

You can also use CircleColor widget to display color in your app. Example, you can set the color picker in a dialog and
display the selected color in a ListTile, for settings.

## Changes in this fork

This fork fixes a bug where the `onColorChange` was being triggered after the primary color was selected and before the
shade was selected, making it impossible to detect when a shade was selected. Now it only triggers `onColorChange` when
there are no shades in use, or when the shade itself is finally selected.

It also detects if there is only one shade (black and white cause this) and does not bring up the secondary shade color
circles (and also events on `onColorChange` when the primary color with only a single shades is selected).

## How to use it

These examples use a static color for 'selectedColor', but you can use a variable (state)

### Add to your Flutter project

You just need to add `material_color_picker_wns` as a
[dependency in your pubspec.yaml file](https://flutter.io/using-packages/).

```yaml
material_color_picker_wns: ^1.0.8
```

### Import

```dart
import 'package:material_color_picker_wns/material_color_picker_wns.dart';
```

### Basic

```dart
MaterialColorPicker(
    onColorChange: (Color color) {
        // Handle color changes
    },
    selectedColor: Colors.red
)
```

### Listen main color changes

```dart
MaterialColorPicker(
    onColorChange: (Color color) {
        // Handle color changes
    },
    onMainColorChange: (ColorSwatch color) {
        // Handle main color changes
    },
    selectedColor: Colors.red
)
```

### Disallow Shades

```dart
MaterialColorPicker(
    allowShades: false, // default true
    onMainColorChange: (ColorSwatch color) {
        // Handle main color changes
    },
    selectedColor: Colors.red
)
```

If `allowShades` is set to `false` then only main colors will be shown and allowed to be selected. `onColorChange` will
not be called, use `onMainColorChange` instead.

### Custom colors

In this example, custom colors are a list of Material Colors (class who extend of ColorSwatch). But you can create your
own list of ColorSwatch.

```dart
MaterialColorPicker(
    onColorChange: (Color color) {
        // Handle color changes
    },
    selectedColor: Colors.red,
    colors: [
        Colors.red,
        Colors.deepOrange,
        Colors.yellow,
        Colors.lightGreen
    ],
)
```

## Screenshot

### Color selection

There is two step, first choose the main color, and when you press it, you have to choose a shade of the main color. By
default it's all **Material Colors**, but you can define custom colors, a **list of ColorSwatch**.

<img title="Main color selection" src="https://raw.githubusercontent.com/ajumalp/material_color_picker_wns/master/demo/main_color.png" width="400" />

<img title="Shade color selection" src="https://raw.githubusercontent.com/ajumalp/material_color_picker_wns/master/demo/shade_color.png" width="400" />

### Example of usages

You can insert the color picker into a **Dialog**

<img title="Example main color in a dialog" src="https://raw.githubusercontent.com/ajumalp/material_color_picker_wns/master/demo/main_color_dialog.png" width="400" />

<img title="Example shade color in a dialog" src="https://raw.githubusercontent.com/ajumalp/material_color_picker_wns/master/demo/shade_color_dialog.png" width="400" />

### Display color

You can use CircleColor widget, to display the selected color into your settings for example.

<img title="Example of circlecolor widget in ListTile" src="https://raw.githubusercontent.com/ajumalp/material_color_picker_wns/master/demo/example_circle_color.png" width="400" />
