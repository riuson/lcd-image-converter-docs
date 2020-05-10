---
title: External editor
---
This feature allows you to edit the image in an external editor.

Algorithm:

  *  The image is saved to a temporary file PNG;
  *  Graphical editor called with the first argument - the name of the file;
  *  While an external editor is running, this application is blocked;
  *  After closing of the editor, this application checks for changes in a temporary file;
  *  If there is a changes, then original image will be replaced by temporary file.

The path to the external editor is specified in the **Options -> External Editor**:

![Dialog]({{ '/assets/images/image/external-1.png' | relative_url }} "Dialog"){:class="img-fluid"}
