---
title: Сборка
---
<div class="alert alert-warning">
Обратите внимание, что файл русского перевода <b>.qm</b> не находится под контролем версий, потому что он <u>бинарный</u> (внезапно!) и является <u>производным</u> от файла <b>.ts</b>, который как раз и находится под контролем версий.<br>
Ошибку (типа <a href="https://github.com/riuson/lcd-image-converter/issues/45">Cannot build on Mac OS 10.12.4 # 45</a>) на этапе <b>qmake</b> следует <u>игнорировать</u>. Файл будет создан автоматически на этапе <b>make</b>.
</div>

Клонировать репозиторий:

```bash
git clone https://github.com/riuson/lcd-image-converter.git
```

Qt Creator:

  *  Установить Qt SDK;
  *  Открыть проект "lcd-image-converter.pro" в Qt Creator;
  *  Пересобрать проект.

Консоль:

```bash
cd lcd-image-converter
qmake
make
# запустить приложение
./_linux/release/lcd-image-converter
```

Ubuntu 19.04:
```bash
user@vmachine:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 19.04
Release:        19.04
Codename:       disco
user@vmachine:~$ sudo apt-get install git qt5-default libqt5xmlpatterns5-dev qtdeclarative5-dev libqt5svg5-dev qttools5-dev-tools
user@vmachine:~$ git clone https://github.com/riuson/lcd-image-converter.git ./lic
user@vmachine:~$ cd ./lic/
user@vmachine:~/lic$ qmake
user@vmachine:~/lic$ make -j2
user@vmachine:~/lic$
```

Пример вывода:

```bash
user@desktop:~/workspace/lcd-image-converter (git: develop)
➜ qmake
RCC: Error in 'resources/resources.qrc': Cannot find file 'lcd-image-converter-ru.qm'
user@desktop:~/workspace/lcd-image-converter (git: develop)
➜ make
Updating './resources/lcd-image-converter-ru.qm'...
    Generated 168 translation(s) (168 finished and 0 unfinished)
    Ignored 5 untranslated source text(s)
Updating './resources/lcd-image-converter-ru.qm'...
    Generated 168 translation(s) (168 finished and 0 unfinished)
/usr/bin/uic-qt4 controls/mainwindow.ui -o .uic/ui_mainwindow.h

...

g++ -m64 -Wl,-O1 -o _linux/release/lcd-image-converter .obj/main.o .obj/bitmapcontainer.o .obj/mainwindow.o 
.obj/widgetbitmapeditor.o .obj/editortabimage.o .obj/editortabfont.o .obj/dialogsavechanges.o .obj/bitmaphelper.o 
.obj/dialogresize.o .obj/fontcontainer.o .obj/charactersmodel.o .obj/dialogfontselect.o .obj/dialogabout.o 
.obj/recentlist.o .obj/starttab.o .obj/actionimagehandlers.o .obj/actionhandlersbase.o .obj/actionfonthandlers.o 
.obj/actionhelphandlers.o .obj/actionsetuphandlers.o .obj/actionfilehandlers.o .obj/dialogfontpreview.o 
.obj/revisionlabel.o .obj/revisioninfo.o .obj/converterhelper.o .obj/conversionmatrixoptions.o .obj/bitstream.o 
.obj/dialogpreview.o .obj/matrixpreviewmodel.o .obj/conversionmatrix.o .obj/dialogconvert.o .obj/dialogsetup.o 
.obj/parser.o .obj/matrixitemdelegate.o .obj/moc_bitmapcontainer.o .obj/moc_mainwindow.o 
.obj/moc_widgetbitmapeditor.o .obj/moc_editortabimage.o .obj/moc_editortabfont.o .obj/moc_dialogsavechanges.o 
.obj/moc_dialogresize.o .obj/moc_fontcontainer.o .obj/moc_charactersmodel.o .obj/moc_dialogfontselect.o 
.obj/moc_dialogabout.o .obj/moc_recentlist.o .obj/moc_starttab.o .obj/moc_actionimagehandlers.o 
.obj/moc_actionhandlersbase.o .obj/moc_actionfonthandlers.o .obj/moc_actionhelphandlers.o 
.obj/moc_actionsetuphandlers.o .obj/moc_actionfilehandlers.o .obj/moc_dialogfontpreview.o .obj/moc_revisionlabel.o 
.obj/moc_conversionmatrixoptions.o .obj/moc_dialogpreview.o .obj/moc_matrixpreviewmodel.o .obj/moc_conversionmatrix.o 
.obj/moc_dialogconvert.o .obj/moc_dialogsetup.o .obj/moc_parser.o .obj/qrc_resources.o    
-L./_linux/release -L/usr/lib/x86_64-linux-gnu -lQtXmlPatterns -lQtXml -lQtGui -lQtCore -lpthread
```

Лог сборки программы можно посмотреть на <a href="https://travis-ci.org/riuson/lcd-image-converter" target="_blank">Travis CI</a>.
