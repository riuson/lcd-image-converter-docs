---
title: Image
order: 4
---
Parameters for conversion of single image.

![Image dialog]({{ '/assets/images/options/conversion/image-1.png' | relative_url }} "Image dialog"){:class="img-fluid"}

* Common
  *  Split data by rows;
    *  Data block size:
      *  8 bits;
      *  16 bits;
      *  24 bits;
      *  32 bits;
      *  In theory, it can be expanded up to 64 bits, but the work will be very uncomfortable;
  *  RLE compression;
  *  Bytes order, Little-Endian or Big-Endian;
  *  Trailing bits - bits in the data blocks what are not related to the original image;
*  Data - parameters of concatenation of the data blocks to a string of code;
  *  Prefix *[dp]*;
  *  Suffix *[ds]*;
  *  Delimiter *[dd]*;
*  Preview - parameters of conversion original image to text preview;
  *  Prefix *[pp]*;
  *  Suffix *[ps]*;
  *  Delimiter *[pd]*;
  *  Level's replacement *[pr]*.

Fragment of the output code:
```
...

#if (0x0 == 0x0)
static const uint8_t image_data_FontBlack_0x25[21] = {
    // ███████████
    // █████[pd]██████
    [pp // ]███████████
    // ███████████[ps]
    // ███████████
    // ██∙∙∙███∙██
    // █∙███∙█∙███
    // █∙███∙∙████
    // █∙███∙∙████
    // ██∙∙∙∙█████
    // █████∙█∙∙∙█
    // ████∙█∙███∙
    // ███∙██∙███∙
    // ███∙██∙███∙
    // ██∙████∙∙∙█
    // ███████████
    // ███████████
    // ██████[pr █]████
    // ███████████
    [dp 0x]07, 0xff, 0xf2, 0x8e, 0xee[ds], 0xbd, 0xcf, 0xb9[dd , ]0xf8, 0x7f, 0xe8, 0xfa, 0xee, 0xdd, 0xdb, 0xb7, 0x8f, 0x05, 0xff, 0xff, 0x80
};
static const tImage FontBlack_0x25 = { image_data_FontBlack_0x25,
    11, 19, 8};
#endif

...
```

The array of strings is used to replace points of original image. For example: `∙ ░ ▒ ▓ █`

Amount of levels is defined by size of array.
Original image is converted to the grayscale with method [qGray](http://doc.qt.io/qt-5/qcolor.html#qGray-1), producing output values from 0 to 255. This values are divided by amount of levels to select appropriate replacement string.

For example:
* 2 strings, interval 128
  * Level 0 = qGray() ≥ 0
  * Level 1 = qGray() ≥ 128 * 1
* 3 strings, interval 85.(3)
  * Level 0 = qGray() ≥ 0
  * Level 1 = qGray() ≥ 85 * 1
  * Level 2 = qGray() ≥ (85 * 2 = 170)
* 4 strings, interval 64
  * Level 0 = qGray() ≥ 0
  * Level 1 = qGray() ≥ 64 * 1
  * Level 2 = qGray() ≥ (64 * 2 = 128)
  * Level 3 = qGray() ≥ (64 * 3 = 192)
* 5 strings, interval 51.2
  * Level 0 = qGray() ≥ 0
  * Level 1 = qGray() ≥ 51 * 1
  * Level 2 = qGray() ≥ (51 * 2 = 102)
  * Level 3 = qGray() ≥ (51 * 3 = 153)
  * Level 4 = qGray() ≥ (51 * 4 = 204)
  