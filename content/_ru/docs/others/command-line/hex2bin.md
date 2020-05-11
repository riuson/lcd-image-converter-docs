---
title: "HEX&nbsp;в&nbsp;BIN"
---
# Способ вызова

Спрвка по режиму преобразования hex в bin:

```bash
$ ./lcd-image-converter --mode=hex2bin --help
Usage: ./lcd-image-converter [options]
Tool to create image and font source files for embedded applications.

Options:
  -h, --help           Displays this help.
  -v, --version        Displays version information.
  -m, --mode <mode>    Conversion mode for application, "convert-image",
                       "convert-font" or "hex2bin".
  -i, --input <path>   Full <path> to image in *.C format.
  -o, --output <path>  Full <path> to output binary result.
```

# Настройки преобразования

  *  Image -> Prefix = "0x"
  *  Image -> Suffix = ""
  *  Image -> Delimiter = " "

# Файл шаблона для изображения:

```cpp
$(start_block_images_table)
le
uint16 $(out_image_width)
uint16 $(out_image_height)
uint16 $(out_blocks_count)
uint$(img_data_block_size) $(out_image_data)
$(end_block_images_table)
```

uint8, uint16, uint24, uint32 - указывают размер данных.

le, be - порядок байт, little endian или big endian.

# Пример

```bash
$ ./lcd-image-converter --mode=hex2bin \
    --input=/temp/colors.c \
    --output=/temp/colors.bin
```

Файл "C" после преобразования в формат исходников (с обычным шаблоном):

```cpp
static const uint8_t image_data_colors[10] = {
    0xd0, 
    0xf0, 
    0x90, 
    0xf0, 
    0xd0, 
    0xb0, 
    0xd0, 
    0xf0, 
    0x90, 
    0xf0
};
const tImage colors = { image_data_colors, 10, 5};
```

С модифицированным шаблоном:

```cpp
le
uint16 10
uint16 5
uint16 10
uint8 0xd0 
    0xf0 
    0x90 
    0xf0 
    0xd0 
    0xb0 
    0xd0 
    0xf0 
    0x90 
    0xf0
```

Бинарный файл Binary после преобразования из hex в bin:

```
00000000: 0A 00 05 00 0A 00 D0 F0    90 F0 D0 B0 D0 F0 90 F0
```

# Другие форматы

Из данного бинарного файла можно создать файлы множества других форматов. Достаточно применить такой полезный набор утилит, как [SRecord](http://srecord.sourceforge.net/).
