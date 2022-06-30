# FFmpeg-Debug-VSCode-Windows

This guide is a modern version of [neptune46/ffmpeg-vscode](https://github.com/neptune46/ffmpeg-vscode) written four years ago.

## Preparation

### 1. Download MSYS2

Just follow [the official installation guide](https://www.msys2.org/#installation).

I recommend you run `pacman -Syu` command **several times** at `step 5` because downloading some packages can be failed due to some issues.

If the installation is finished sucessfully, you can see the results like the below.

```bash
Yonghye@DESKTOP-RNUFNCT MSYS ~
# pacman -Syu
:: Synchronizing package databases...
 mingw32 is up to date
 mingw64 is up to date
 ucrt64 is up to date
 clang32 is up to date
 clang64 is up to date
 msys is up to date
:: Starting core system upgrade...
 there is nothing to do
:: Starting full system upgrade...
 there is nothing to do
```

Install all mingw-w64-x86_64-* at `step 7`.

You will see the below text and get confused. Just press Enter!

```bash
:: There are 19 members in group mingw-w64-x86_64-toolchain:
:: Repository mingw64
   1) mingw-w64-x86_64-binutils  2) mingw-w64-x86_64-crt-git
   3) mingw-w64-x86_64-gcc  4) mingw-w64-x86_64-gcc-ada
   5) mingw-w64-x86_64-gcc-fortran  6) mingw-w64-x86_64-gcc-libgfortran
   7) mingw-w64-x86_64-gcc-libs  8) mingw-w64-x86_64-gcc-objc
   9) mingw-w64-x86_64-gdb  10) mingw-w64-x86_64-gdb-multiarch
   11) mingw-w64-x86_64-headers-git  12) mingw-w64-x86_64-libgccjit
   13) mingw-w64-x86_64-libmangle-git  14) mingw-w64-x86_64-libwinpthread-git
   15) mingw-w64-x86_64-make  16) mingw-w64-x86_64-pkgconf
   17) mingw-w64-x86_64-tools-git  18) mingw-w64-x86_64-winpthreads-git
   19) mingw-w64-x86_64-winstorecompat-git
Enter a selection (default=all):
```

Also, I recommend you run `pacman -S --needed base-devel mingw-w64-x86_64-toolchain` command **several times** at `step 7`.

If the installation is finished sucessfully, you can see the results like the below.
```bash
warning: base-devel-2022.01-2 is up to date -- skipping
warning: mingw-w64-x86_64-binutils-2.38-3 is up to date -- skipping
warning: mingw-w64-x86_64-crt-git-10.0.0.r32.g89bacd2be-1 is up to date -- skipping
warning: mingw-w64-x86_64-gcc-12.1.0-2 is up to date -- skipping
warning: mingw-w64-x86_64-gcc-ada-12.1.0-2 is up to date -- skipping
warning: mingw-w64-x86_64-gcc-fortran-12.1.0-2 is up to date -- skipping
warning: mingw-w64-x86_64-gcc-libgfortran-12.1.0-2 is up to date -- skipping
warning: mingw-w64-x86_64-gcc-libs-12.1.0-2 is up to date -- skipping
warning: mingw-w64-x86_64-gcc-objc-12.1.0-2 is up to date -- skipping
warning: mingw-w64-x86_64-gdb-12.1-2 is up to date -- skipping
warning: mingw-w64-x86_64-gdb-multiarch-12.1-2 is up to date -- skipping
warning: mingw-w64-x86_64-headers-git-10.0.0.r32.g89bacd2be-1 is up to date -- skipping
warning: mingw-w64-x86_64-libgccjit-12.1.0-2 is up to date -- skipping
warning: mingw-w64-x86_64-libmangle-git-10.0.0.r32.g89bacd2be-1 is up to date -- skipping
warning: mingw-w64-x86_64-libwinpthread-git-10.0.0.r32.g89bacd2be-1 is up to date -- skipping
warning: mingw-w64-x86_64-make-4.3-1 is up to date -- skipping
warning: mingw-w64-x86_64-pkgconf-1.8.0-2 is up to date -- skipping
warning: mingw-w64-x86_64-tools-git-10.0.0.r32.g89bacd2be-2 is up to date -- skipping
warning: mingw-w64-x86_64-winpthreads-git-10.0.0.r32.g89bacd2be-1 is up to date -- skipping
warning: mingw-w64-x86_64-winstorecompat-git-10.0.0.r32.g89bacd2be-1 is up to date -- skipping
 there is nothing to do
```

### 2. Install tools and packages for building FFmpeg

These commands must be ran on **MSYS2** prompt.

```bash
pacman -S git 
pacman -S nasm yasm
```
## Clone & Build FFmpeg

These commands must be ran on **MSYS2** prompt.

```bash
cd c:\msys64
./mingw64.exe
cd ~
git clone https://github.com/FFmpeg/FFmpeg.git
cd FFmpeg
./configure --enable-debug=3 --disable-optimizations
make -j8
```

After build, `ffmpeg_g.exe` will be genereated in `~/FFmpeg`. Congratulation!

```bash
yonghye@DESKTOP-OE4KJAL MINGW64 ~/FFmpeg
$ ls
CONTRIBUTING.md   LICENSE.md   config_components.h  fftools        libswscale
COPYING.GPLv2     MAINTAINERS  configure            libavcodec     presets
COPYING.GPLv3     Makefile     doc                  libavdevice    tests
COPYING.LGPLv2.1  README.md    ffbuild              libavfilter    tools
COPYING.LGPLv3    RELEASE      ffmpeg.exe           libavformat
CREDITS           compat       ffmpeg_g.exe         libavutil
Changelog         config.asm   ffprobe.exe          libpostproc
INSTALL.md        config.h     ffprobe_g.exe        libswresample
```

## Debug FFmpeg on VSCode!

Open FFmpeg project on VSCode

If you downloaded MSYS2 following official guide, your FFmpeg project may be located in `C:\msys64\home\{user_name}\FFmpeg`.

These commands must be ran on **Commpand Prompt** of Windows not MSYS2.

```bash
cd C:\msys64\home\{user_name}\FFmpeg
code .
```

## References
[neptune46/ffmpeg-vscode](https://github.com/neptune46/ffmpeg-vscode)
