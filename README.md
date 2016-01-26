# Apparent Pixels

#### Abstract

How do I make a truly display-independent design?  This is a problem that is repeatedly encountered today, and there doesn't seem to be a satisfactory solution yet.  I propose a new unit of measure, the apparent pixel, to address shortcomings in current layout and rendering systems.

#### Existing Display Measurements

	* Pixel - A point sample of an image or the smallest rendering element of a display.  There is no inherent size or shape associated with a pixel.
	* Inch / centimeter / millimeter - Physical dimensions of size.
	* CSS Pixel - A reference pixel attempting to be scale-independent. There are approximately 96 pixels/inch.
	* Point - A reference dimension attempting to be scale-independent.  There are approximately 72 points/inch.
	* Pica - A reference dimension equal to 12 Points.
	* VH - A reference dimension, equal to 1/100th of the viewport height.
	* VW - A reference dimension, equal to 1/100th of the viewport width.

#### The Problem

Why do existing units of measurement fail?  They are incapable of accurately representing _apparent size_, or the size we percieve objects to be.

Why are they incapable of this? The human eye uses a curved lens, which means that to the eye, apparent size is a measure of _angle_ and not _length_.  Length, by itself, is meaningless!

Unfortunately, this is not easily solved, as it involves figuring out the apparent size of a display with respect to the observer, but there are some simplifications we can make to get a decent approximation:

	1)  We can assume that the observer is looking at a display from head-on.
	2)  We can assume that the display is roughly flat.
	3)  We can assume that the display is not so large, or so close, that it takes a significant poriton of your field-of-view.

All of these equate to making a _small-angles approximation_.  That is, we can say that all parts of the display are roughly equidistant from the observer.  If this is true, then we can approximate apparent size using only two variables:

	1) The size of the display.
	2) The distance from the display to the observer.


#### Apparent Pixel


Keeping these simplifications in mind, I propose a new measurement, the apparent pixel.  The apparent pixel is defined as:

The apparent size of a 1 millimeter by 1 millimeter square, 1 meter in front of your eye.

	EYE ) - - - - 1m - - - - [ ] 1mm X 1mm SQUARE.

Or, if you don't like to square pixels, imagine what a grid of points spaced 1mm apart looks like from 1 meter away.

#### Some Examples

	*1mm at a distance of 1m from your eye is roughly 0.057 degrees of your viewing angle.
	*A 1mm X 1mm square at a distance of 1m away is rougly 1/1,000,000 steradians, or 1 microsteradian.
	*The field of view of a human is roughly 200 degrees on the horizontal, and 130 degrees on the vertical, which is very roughly 3500ap X 2250ap.
	*A 13 inch display, with a 4:3 aspect ratio, at a distance of 1 meter away has an apparent size of rougly 264ap X 198ap.
	*A big screen TV, with a 50 inch disply, a 16:9 aspect ratio, at a distance of 3 meters away has an apparent size of roughly 369ap X 208ap.
	*A smartphone with a 5 inch display, a 9:16 aspect ratio, at a distanct of 1/3 of a meter away has an apparent size of roughly 189ap X 332ap.
	*Hold your thumb out in front of you!  Very roughly, the average human has about a 2 foot long arm and a thumb about 2cm wide.  This means your thumb is very roughly 32ap wide, when you look at it.

#### Estimating Distances

The biggest issue in accurately calculating AP is that we don't know the distance from display to observer.  However, for the most part, we can estimate it very roughly.

	* Most people sit roughly 1m away from their laptop or desktop.
	* Most people hold their smartphone in their hand, roughly 30cm away.
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


#### Why a square?

A few reasons:

	1) A reference shape easier to visualize than something like visual angle.
	2) Squares correspond pretty well to how displays work today.
	3) It holds as valid unit of measurement for non-point cameras as well (orthographic projections).
	4) It has historical precedent!  Painters and artists have long used their outstretched thumbs as a reference when trying to reproduce a scene.
