---
title: How to convert HEIC to JPEG on macOS
date: 2018-09-23 17:26:44
tags:
---

If you take a photo on iPhone and save it on your Mac, I think that the extension of the picture file is heic, not png or jpeg.
To convert heic to jpeg in such a case, use [iMazing HEIC Converter](https://itunes.apple.com/jp/app/imazing-heic-converter/id1292198261?mt=12) or the following command in macOS.

```shell
$ cd PHOTO_DIR

$ sips --setProperty format jpeg *.HEIC --out ./
```
