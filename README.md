# libbpg

libbpg contains the source code of the bpgenc and bpgdec command line utilities (for Linux) and the associated libbpg library (read the README file in the archive). It also includes the source code of the Javascript decoder.

## BPG Image format

### Introduction

BPG (Better Portable Graphics) is a new image format. Its purpose is to replace the JPEG image format when quality or file size is an issue. Its main advantages are:
High compression ratio. Files are much smaller than JPEG for similar quality.
Supported by most Web browsers with a small Javascript decoder (gzipped size: 71 KB).
Based on a subset of the HEVC open video compression standard.
Supports the same chroma formats as JPEG (grayscale, YCbCr 4:2:0, 4:2:2, 4:4:4) to reduce the losses during the conversion. An alpha channel is supported. The RGB, YCgCo and CMYK color spaces are also supported.
Native support of 8 to 14 bits per channel for a higher dynamic range.
Lossless compression is supported.
Various metadata (such as EXIF, ICC profile, XMP) can be included.

### Download

The following archive contains the source code of the bpgenc and bpgdec command line utilities (for Linux) and the associated libbpg library (read the README file in the archive). It also includes the source code of the Javascript decoder.
libbpg-0.9.2.tar.gz

Binary distribution for Windows: bpg-0.9.2-win32.zip

### Performance

Mozilla did a study of various lossy compressed image formats. HEVC (hence BPG) was a clear winner by a wide margin. BPG files are actually a little smaller than raw HEVC files because the BPG header is smaller than the corresponding HEVC header.
BPG natively supports 8 to 14 bits per channel when most other formats use 8 bits (including most of the JPEG implementations and WEBP). It gives a higher dynamic range (which is important for cameras and new displays) and a slightly better compression ratio (because there are less rounding errors in the decoder).
BPG uses high quality decimation (10 tap Lanczos filter) and interpolation (7 tap Lanczos filter) to handle the chroma samples in 4:2:2 and 4:2:0 formats.
BPG can be supported in hardware with standard HEVC decoders and encoders (it uses a subset of the Main 4:4:4 16 Still Picture Profile, Level 8.5).
Demo

Lena 512x512 image, visual comparison with JPEG
Nice visual comparison between BPG (x265 encoder), JPEG (mozjpeg encoder), JP2K and WebP
Wikipedia photos
Images with alpha channel
Technical information

The specification of the BPG file format is available here.

### Licensing

The BPG decoding library uses a modified version of FFmpeg released under the LGPL version 2.1 as HEVC decoder. The BPG decoding library excluding the FFmpeg code is released under the BSD license.
The BPG encoder is released under the BSD license. It optionally uses the JCTVC HEVC reference encoder which is also released under the BSD license or the x265 library released under the GPL license.
Some of the HEVC algorithms may be protected by patents in some countries (read the FFmpeg Patent Mini-FAQ for more information). Most devices already include or will include hardware HEVC support, so we suggest to use it if patents are an issue.
Fabrice Bellard - http://bellard.org/
