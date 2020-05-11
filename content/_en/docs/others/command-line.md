---
title: Command line
---
In this mode, a document's conversion can be performed without using of GUI, but with pre-defined settings.

<div class="alert alert-info">
Application version for Windows prints no messages to the console. If they are necessary, rebuild the application with the option `CONFIG += console` in the project file (lcd-image-converter.pro);<br>
Required Qt version >= 5.2.
</div>

# How to call this mode

Calling basic help:

```bash
$ ./lcd-image-converter --help
Usage: ./lcd-image-converter [options]
Tool to create image and font source files for embedded applications.

Options:
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
  
With **--config-application** и **--config-presets** options not specified, related settings are stored in default storage (registry on  Windows).
If options are specified, related settings are stored in specified XML files.
With this feature you can keep Presets under Version Control System together with other project files.
