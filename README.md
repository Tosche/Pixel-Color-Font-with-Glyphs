<img src="https://raw.githubusercontent.com/Tosche/Pixel-Color-Font-with-Glyphs/master/Images/Title.png" alt="Title">

# INTRO

This is a demo of how you can make your own coloured pixel fonts using glyphs.

## How to set up pixel fonts

You can skip the pixel part if you are just interested in the color bit.

For me, the easiest way is to lock the movement by increasing the Grid Spacing dramatically (100 in this case). And the vertical metrics should be multiples of that. The UPM doesn't need to be 1000 nowadays, and I was using UPM=800 for my arcade pixel fonts. One down side to this approach is that your pixel shape will be locked to the square. If you want to change it, maybe it's a good idea to use a pixel component, finalise the design, and then change the Grid Spacing back to 1, after which you can modify the pixel shape.

For the maximum convenience to draw pixels, I would advise using my [Pixel Pen tool](https://github.com/Tosche/PixelPenTool).

## How to set up colour fonts

There are multiple ways to make color fonts, and this font is set up for making the colour fonts the Microsoft way, using COLR/CPAL. You set up the colours you're going to use (found in Font Info > Master > Color Palettes custom parameter). You can have multiple palettes but only the first one is viewable during design.

You add a layer in each glyph, and name it "Color X" (X being the index of the color. And you need a space inbetween) for it to be coloured. The default layer works as fallback which should be shown when an environment does not support colour font. It has to be designed in a certain way though (read Web)

Alternate colour palette can be exported by choosing a palette index using the custom parameter found in the instance tab.

The instances are set up for web and desktop, since the browser/desktop support for each colour format is not consistent. You can use transparency in both formats, but you need to be careful about how you are overlapping the shapes (see the third palette whose results could be improved by cleaning the overlaps).

### Web

The web version has to be COLR/CPAL, and the Web instances in this file are set up that way. Ideally you would want to use embedded SVG format, but Chrome is hell-bent on not supporting it. The only format supported by all browsers is the COLR/CPAL format. Some websites say colour web fonts are not possible merely because SVG is not supported by Chrome, but COLR/CPAL is universally supported. Although it has graphical limitation, some form of color fonts are certainly possible.

In the instance, you need to specify which color palette you're going to use. That's the custom parameter called "Color Palette for CPAL". Remember, computers count from zero and the first palette has to be 0.

Chrome and Firefox use the default layer (i.e. fallback) in a particular way. Basically its bounds has to cover the sum of all Color layers outlines, and the fallback layer works kind of like a mask. For demonstration purpose, I have put a lowercase "a" in the same Color design but smaller area of default outline. You can see that the "a" appears clipped in Chrome and Firefox. Maybe the easiest solution (laziest) is to put a big-enough rectangle in every glyph.

<img src="https://raw.githubusercontent.com/Tosche/Pixel-Color-Font-with-Glyphs/master/Images/COLR_Clipping.gif" alt="COLR_Clipping">

### Desktop

The most consistently supported color format is SVG, in fact SVG-embedded OTF is so close to being universally supported (the only outlier being Chrome). Creative Cloud and Core Text apps (TextEdit, Pages, etc.) support the SVG format, so that's the way.

The normal way to make an SVG-embedded color font with Glyphs is to make a new layer in a glyph, rename it as "svg", and drop an SVG file, and repeat that to all glyphs. However, Glyphs can generate an SVG-embedded OTF using the COLR/CPAL source. All you need to do is to add "Color Layers to SVG" instance custom parameter in order to declare that you're going to export it as such, and specify which palette you're going to use, via "Color Palette for SVG". Remember, computers count from zero and the first palette has to be 0.

Unlike the web solution, the fallback outline does not have to cover the whole area of your color design (at least where I tested)

##### License

Copyright 2020 Toshi Omagari *@Tosche_E*

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

See the License file included in this repository for further details.