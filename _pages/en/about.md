---
title: About project
redirect_from:
  - /
  - /pages/
---
This application allows you to create bitmaps and fonts, and transform them to “C” source format for embedded applications. The transformation of the images to the source code is made by using templates. Therefore, by modifying the templates, you can change the format of the output within certain limits.

*As a result, the output of the program by default may be not suitable for your needs. It can and will need to be adjusted.*

Features:

  * Create a single image;
  * Create fonts (set of images - characters):
    * Including unicode charset.
  * Create the data structures for displays:
    * Monochrome, grayscale, color;
    * With vertical and horizontal orientation of bytes;
    * 8, 16, 24, 32-bit data;
    * 1...32 bits per pixel;
    * RLE compression;
    * With different display controllers, not limited by one particular model.

![Main]({{ '/assets/images/main.png' | relative_url }}){:class="img-fluid"}

<div class="embed-responsive embed-responsive-16by9">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/-GVR6G2tyQo?rel=0" frameborder="0" allowfullscreen></iframe>
</div>