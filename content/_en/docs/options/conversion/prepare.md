---
title: Prepare
order: 1
---
This settings specifies the transformation prior to converting images to text.

By default, each image is treated as a color, and is stored as a color. This conversion allows you to change the type of image before processing:

  *  Monochrome;
    *  Edge;
      *  Edge value;
    *  Diffuse Dither;
    *  Ordered Dither;
    *  Threshold Dither;
  *  Grayscale (function [qGray](http://doc.qt.io/qt-5/qcolor.html#qGray-2));
  *  Color (no changes);
  *  Custom format.

You can also invert the colors.

## Scanning
The order of scanning points of the image is controlled by script. There are 16 predefined scripts. Also, you can use your own script, based on the most suitable of the predefined.

In the right pane displays a simple animation showing the scanning order of the points in the specified script. The parameters of time are the total period of the animation and the update interval.

![Prepare dialog - scanning]({{ '/assets/images/options/conversion/prepare-1.png' | relative_url }} "Prepare dialog"){:class="img-fluid"}

Additionally, possible to set scan bands, which can be convenient for some LCD with a specific memory allocation.

## Preprocessing

Here you can select type of image
  *  Color
  *  Monochrome
  *  Grayscale
  *  Custom

When choosing a monochrome format, you can select its algorithm and parameters.

In the case of a custom format, you can enter your own script, through which the pixel value will be recalculated.

![Prepare dialog - preprocessing]({{ '/assets/images/options/conversion/prepare-2.png' | relative_url }} "Prepare dialog"){:class="img-fluid"}

## Example of scanning sequence

E.g. this sequence:

![Scan direction example]({{ '/assets/images/options/conversion/prepare-3.png' | relative_url }} "Scan direction example"){:class="img-fluid"}

For display with following memory allocation:

![Memory allocation example]({{ '/assets/images/options/conversion/prepare-4.png' | relative_url }} "Memory allocation example"){:class="img-fluid"}
