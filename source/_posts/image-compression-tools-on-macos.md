---
title: Command line and GUI image compression tools on macOS
date: 2018-09-23 17:24:53
tags:
---

GUI or commandline tools that converts image formats and compresses on Mac. Use it to reduce the size of the image.

## GUI tool
[ImageOptim](https://imageoptim.com/mac) is an easy-to-use GUI tool is a GUI tool for compressing image. This tool can compress all the images contained in the folder at once. But, processing may take a while.

## Commandline tools
Commandline tools are easy-to-use and speedy to compress or convert images, if you are familiar with the command line.

### Compress png images
[pngquant](https://pngquant.org) is good tool.

#### Install pngquant

```shell
$ brew install pngquant
```

#### How to use pngquant

##### Compress and save it as a another file leaving the original image

```shell
$ pngquant image.png
$ pngquant dir/*.png
```

##### Compress and overwrite the original image

```shell
$ pngquant --ext .png --force image.png
$ pngquant --ext .png --force dir/*.png
```

##### Other option

For other detailed options refer to the official website : [pngquant](https://pngquant.org).

### Compress jpeg images
[jpegoptim](https://github.com/tjko/jpegoptim) is good tool.

#### Install jpegoptim

```shell
$ brew install jpegoptim
```

#### How to use pngquant

##### Compress and save it as a another file leaving the original image

```shell
$ jpegoptim fff.jpeg
$ jpegoptim dir/*.jpeg
```

##### Compress and overwrite the original image

```shell
$ jpegoptim --ext .png --force image.png
$ jpegoptim --ext .png --force dir/*.png
```

To erase all the meta data (location,date,etc...) contained in jpeg and compress it and save it, use the `-s` option.

```shell
$ jpegoptim -s image.jpeg
```

##### Other option

For other detailed options refer to the `--help` option.

```shell
$ jpegoptim --help
```

##### Other tools to compress jpg images

There are other tools such as [Guetzli](https://github.com/google/guetzli) and [Mozjpeg](https://github.com/mozilla/mozjpeg), so it may be good to use it.Both tools can be installed with `brew` command.

```shell
$ brew install guetzli
$ brew install mozjpeg
```


### webp に変換

For images in jpg or png format, converting the format to WebP is often the smallest size.

#### Install webp

```shell
$ brew install webp
```

#### How to use webp

```shell
$ cwebp image.png -o image.webp
```

##### Other option

```shell
$ cwebp -longhelp
```
