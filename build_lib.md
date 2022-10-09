## Build

branch forked from release/5.1 (2022/8/1)

Dependencies: 
- make
- gcc / mingw32-w64-gcc (MinGW) / mingw64-x86_64-gcc (Cygwin)
- yasm
- nasm
- libvpx

Command: 

- Windows (MinGW / Cygwin)
```
./configure --enable-cross-compile --enable-shared --arch=x86_64 --target-os=mingw64 --cross-prefix=x86_64-w64-mingw32- \
  --disable-everything \
  --enable-decoder=amv,flv,h264,h264_qsv,hevc,mpegvideo,mpeg1video,mpeg2video,mpeg4,msmpeg4v1,msmpeg4v2,msmpeg4v3,vp8,vp9,webp,wmv1,wmv2,wmv3,vc1,av1 \
  --enable-demuxers \
  --enable-parsers \
  --enable-protocol=file \
  --enable-filter=fps,setpts

make -jN

cp -t lib/x64/ \
  libavcodec/avcodec-59.dll \
  libavcodec/avcodec.lib \
  libavdevice/avdevice-59.dll \
  libavdevice/avdevice.lib \
  libavfilter/avfilter-8.dll \
  libavfilter/avfilter.lib \
  libavformat/avformat-59.dll \
  libavformat/avformat.lib \
  libswresample/swresample-4.dll \
  libswresample/swresample.lib \
  libavutil/avutil-57.dll \
  libavutil/avutil.lib \
  libswscale/swscale-6.dll \
  libswscale/swscale.lib
```


should output binaries under LGPL 2.1

------

### notes



BGAs around 2010 mostly use mpeg1 / mpeg2, while recent ones involves wmv2 / wmv3 / h264, etc

hwaccels are disabled for now
