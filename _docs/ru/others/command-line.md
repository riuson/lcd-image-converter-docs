---
title: Командная строка
---
В данном режиме преобразование нового документа может быть выполнено без использования GUI, используя заранее подготовленные настройки.

Внимание

  *  В версии для Windows не выводятся сообщения в консоль. Если они необходимы, надо пересобрать приложение с включённой опцией `CONFIG += console` в файле проекта (lcd-image-converter.pro);
  *  Требуется версия Qt >= 5.2.

Вызов общей справки:

```
$ ./lcd-image-converter --help
Usage: ./lcd-image-converter [options]
Tool to create image and font source files for embedded applications.

Options:
  -?, -h, --help               Displays this help.
  -v, --version                Displays version information.
  -m, --mode <mode>            Conversion mode for application,
                               "convert-image", "convert-font" or "hex2bin".
  --config-application <file>  Path to main configuration file. If not
                               specified, default is used.
  --config-presets <file>      Path to presets configuration file. If not
                               specified, default is used.
  --config-initialize          Reset all settings to default state.
 ```
 
 Опции
  * **-v**, **--version** - вывод версии приложения;
  * **-m**, **--mode** - выбор режим преобразования;
    * **convert-image** - изображение в текст;
    * **convert-font** - шрифт в текст;
    * **hex2bin** - текст в бинарный файл.
  * **--config-application** - путь к файлу настроек приложения;
  * **--config-presets** - путь к файлу заготовок;
  * **--config-initialize** - сброк используемых настроек на значения по умолчанию.
  
Если опции **--config-application** и **--config-presets** не указаны, соответствующие настройки сохраняются в хранилище по умолчанию (реестр на Windows). Если указаны, то в указанных файлах в формате XML.
Это позволяет, при необходимости, хранить заготовки под управлением системы контроля версий того проекта, в котором используются результаты преобразования.
