# Apparent Pixels

#### Abstract

How do I make a display-independent design?  Existing units for scale-invariance don't seem to provide a satisfactory solution.  I propose a new visual measue of size, the apparent pixel, and provide some simple formulae and examples of use.

#### Existing Display Measurements

* Pixel - A point sample of an image or the smallest rendering element of a display.  There is no inherent size or shape associated with a pixel.

* Inch / centimeter / millimeter - Physical dimensions of size.

* CSS Pixel - A reference pixel attempting to be scale-independent. There are approximately 96 pixels/inch.

* Point - A reference dimension attempting to be scale-independent.  There are approximately 72 points/inch.

* Pica - A reference dimension equal to 12 Points.

* VH - A reference dimension, equal to 1/100th of the viewport height.

* VW - A reference dimension, equal to 1/100th of the viewport width.

#### The Problem

The reason these units of measurement are incapable of providing true display-independent designs is that they fail to account for the apparent size of the display, from the viewpoint of the user.  The human eye (or a camera) uses a curved lens, which means the apparent size of an object, when seen by us, is a measure of _angle_ and not _length_.

This means, the apparent size of a display, from the human eye, is a function of the size and shape of the display, the curvature of the human eye, and the _distance_ between the display and the eye.  Note that none of the above units take into account viewing distance, thus they cannot be accurately converted to an angular measurement.


#### Apparent Pixel

Let's make some simplifying assumtions:

1) Displays are mostly flat, mostly rectangular, and mostly have square pixels.

2) We don't need to consider the change in viewing angle between different parts of the display (We can treat the edges of the screen the same as the center).

3) We don't need to consider changes in distance during use, for the most part we'll just assume the average distance from the display is good enough.

From these assumptions I propose a new measurement, the apparent pixel (ap).  The apparent pixel is defined as:

The apparent size of a 1 millimeter by 1 millimeter square, at a distance of 1 meter in front of your eye.

EYE ) - - - 1m - - - [] 1mm X 1mm SQUARE.

Or, if you don't like to square pixels, imagine what a grid of points spaced 1mm apart looks like from 1 meter away.

#### Some Examples

1mm at a distance of 1m from your eye is roughly 0.057 degrees of your viewing angle.

A 1mm X 1mm square at a distance of 1m away is rougly 1/1,000,000 steradians, or 1 microsteradian.

The field of view of a human is roughly 200 degrees on the horizontal, and 130 degrees on the vertical, which is very roughly 3500ap X 2250ap.

A 13 inch display, with a 4:3 aspect ratio, at a distance of 1 meter away has an apparent size of rougly 264ap X 198ap.

A big screen TV, with a 50 inch disply, a 16:9 aspect ratio, at a distance of 3 meters away has an apparent size of roughly 369ap X 208ap.

A smartphone with a 5 inch display, a 9:16 aspect ratio, at a distanct of 1/3 of a meter away has an apparent size of roughly 189ap X 332ap.

All of these devices, while drastically differing in size, have similar apparent sizes because of the change in viewing distance.

Hold your thumb out in front of you!  Very roughly, the average human has about a 2 foot long arm and a thumb about 2cm wide.  This means your thumb is very roughly 32ap wide, when you look at it.

#### Estimating Distances

The biggest issue in accurately calculating AP is changes in distance.  However, for the most part, we can estimate it very roughly.

* Most people sit roughly 1m away from their laptop or desktop.

* Most people hold their smartphone in their hand, or on the table in front of them.  This is very roughly about 30cm away.

* Most people sit roughly 2-3m away from their TV when they watch it.

What about more complicated setups, such as movie projectors, electronic billboards, and stadium displays?  These need to be visible at a wide range of distances, and there are generally two things to consider here:

	1) The average viewing distance, or what most people will see.

	2) The farthest viewing distance.

If you want to give a presentation in a meeting room with a projector, you want everyone to be able to read it clearly, so you should consider the fartherst person away.

In a movie theater, on the other hand, the difference in apparent size is so great between the first row and the last row, that it might be better to scale to the average distance away, and assume most people will try to sit in the center.

#### Calculate your Screen size in AP

You can easily calculate your own screen size

1 AP = 1mm / 1m = 1/1000, so

(Width in AP) = ((Width in mm)/(Distance in mm)) / (1/1000), or
(Width in AP) = 1000 * (Width in mm) / (Distance in mm)


