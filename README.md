# SnowBoardTV Documentation ( WORK IN PROGRESS )

![SnowBoard Icon](https://i.imgur.com/du1jZL7.png)

**Please Note: This document is a work in progress.**

This is SnowBoardTV, the worlds first tvOS theming engine.

SnowBoardTV can be installed from: XXX

## Features
SnowBoardTV includes the following features (✅ - Complete | ⚠️ - In Development | ⛔️- Coming Soon) 
- App Icon Theming ✅
- App Icon Masks ✅
- App Icon Shadow Customisation ✅
- App Icon Label Customisation ✅
- Glyph Theming ⛔️
- Respring Logos ⚠️
- Fonts ⛔️

## Pre-Requirements
```
- A Jailbroken AppleTV
```

## Example Theme
This repository includes an "Example Theme.theme" folder, which contains an example of all of the features detailed below. Looking through this example theme will give you a much better understanding of how to put a SnowBoardTV theme together.
This "Example Theme.theme" folder can be placed in "/Library/Themes" on your AppleTV to try it out for yourself.

## App Icon Theming
It is very simple to build a simple theme to change app icons with SnowBoardTV.
If you are familar with theming on iOS you will have no issues here, however tvOS supports one icon feature that iOS does not - Parallax.
Parallax allows you to have multiple layers to your icon, giving it a 3D look when in focus.
SnowBoardTV fully supports parallax, and can be created by giving each icon multiple 'layers'.

The format for App Icon theming is as follows:

Theme folder:
```
/Library/Themes/[YOUR THEME NAME].theme/
```

In the theme folder you may include an optional "Info.plist" file. This file can control further theming options as well as identifying your theme.

An example Info.plist file would look like this:
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>PackageName</key>
	<string>Example Theme</string>
</dict>
</plist>
```
This will simply ensure your theme has the correct name when it is shown in the SnowBoardTV application.

Once you have these base folders set up, you can start adding images for your theme. Within the ".theme" folder you can create a "/IconBundles" folder, where your icons will be stored. Each file needs to conform to the following file name format:

For App Icons:
```
(400px x 240px)
{Bundle Identifier}_AppIconLayer{LayerNumber}@1x.png
Example: com.apple.TVSettings_AppIconLayer0@1x.png

(800px x 480px)
{Bundle Identifier}_AppIconLayer{LayerNumber}@2x.png
Example: com.apple.TVSettings_AppIconLayer0@2x.png
```
The background layer starts at 0. You can then add as many layers as you with beyond this to create a parallax effect (However, only the background layer is required if you do not want a parallax effect).

Example of an applied App Icon image:
![App Icon Image Example](https://i.imgur.com/2GpNWPA.png)


For Top Shelf Image:
```
(1920px x 720px)
{Bundle Identifier}_TopShelf@1x.png
Example: com.apple.TVSettings_TopShelf@1x.png

(3840px x 1440px)
{Bundle Identifier}_TopShelf@2x.png
Example: com.apple.TVSettings_TopShelf@2x.png
```

Example of an applied Top Shelf image:
![Top Shelf Image Example](https://i.imgur.com/9uOICx8.png)

## App Icon Shadow Settings
Within your "Info.plist" file (Mentioned in the previous section), you can add various settings for app icon shadows. These must be in a 'dict' under the "ShadowSettings" key.

| Key        | Description           | Default  |
| ------------- |:-------------| -----:|
| ShadowColor      | The shadow's colour (Hex or Rgb) | #000000 |
| ShadowHorizontalOffset      | Shadow offset X      |   0.0 |
| ShadowVerticalOffset | Shadow offset Y      |    6.0 |
| ShadowRadius | Shadow Radius      |    5.0 |
| ShadowOpacity | The opacity of the shadow      |    0.2 |

Example:
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>ShadowSettings</key>
	<dict>
		<key>ShadowColor</key>
		<string>#00b7ff</string>
		<key>ShadowHorizontalOffset</key>
		<integer>1</integer>
		<key>ShadowVerticalOffset</key>
		<real>6</real>
		<key>ShadowRadius</key>
		<real>5</real>
		<key>ShadowOpacity</key>
		<real>0.4</real>
	</dict>
	<key>PackageName</key>
	<string>Example Theme</string>
</dict>
</plist>
```
Example of Shadow Customisation:
![Shadow Customisation](https://i.imgur.com/btWPWTd.png)


## App Icon Label Settings
Within your "Info.plist" file (Mentioned in the previous section), you can add various settings for app icon labels. These must be in a 'dict' under the "LabelSettings" key.

| Key        | Description           | Default  |
| ------------- |:-------------| -----:|
| FontName      | The name of the font used for icon labels | .SFUIText-Medium |
| FontSize      | The size of the font used for icon labels | 31.0 |
| HideLabels	| Hide all app labels | false |

Note: Here is a good resource for finding different font names https://github.com/lionhylra/iOS-UIFont-Names

Example:
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>LabelSettings</key>
	<dict>
		<key>FontName</key>
		<string>.SFUIText-Medium</string>
		<key>FontSize</key>
		<real>31.0</real>
		<key>HideLabels</key>
		<false />
	</dict>
	<key>PackageName</key>
	<string>Example Theme</string>
</dict>
</plist>
```
Example of Font Customisation:

![Font Customisation](https://i.imgur.com/risdejf.png)

## Icon Masking
SnowBoardTV also supports masking application icons, this can be done with a simple mask image.
Each file needs to conform to the following file name format:
```
(400px x 240px)
AppIconMask@1x.png

(800px x 480px)
AppIconMask@2x.png

These go in /Library/Themes/[YOUR THEME NAME].theme/IconBundles/
```

An Example Mask Image:
![Example Mask Image](https://i.imgur.com/anebrje.png)

Example Mask Image Applied:
![Example Mask Image Applied](https://i.imgur.com/S7g8igw.png)

## Unthemed Icons
It is possible to set a stack of images to be applied to 'non-themed' icons, that you haven't provided a custom icon for.
This is most useful to replace the backgrounds of all 'parallax' stock icons.
This is done in the same way as setting an app icon, however instead of a bundle identifier you use 'UnthemedApps'. So for example: 'UnthemedApps_AppIconLayer0@2x.png'.

Example Unthemed Icon:
![Example Unthemed Icon](https://i.imgur.com/uJhJsiD.png)

Example Applied Unthemed Icon:
![Example Applied Unthemed Icon](https://i.imgur.com/2ZGOzS0.png)

## SnowBoard Theme Icon
You can also set an icon for your theme to be displayed in the SnowBoardTV application. This is set like so:

```
(400px x 240px)
DefaultIcon@1x.png

(800px x 480px)
DefaultIcon@2x.png
```

Example SnowBoardTV Icon:
![Example SnowBoardTV Icon](https://i.imgur.com/xrJYb34.png)


## Authors
SparkDev 2019

App Icon by Dennis D. Bednarz

## Support
For further help please contact me on Twitter (https://twitter.com/SparkDev_) or join my Discord server (https://discord.gg/aYgD69T)