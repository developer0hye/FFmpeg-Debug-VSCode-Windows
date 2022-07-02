# FFmpeg-Debug-VSCode-Windows

This guide is a modern version of [neptune46/ffmpeg-vscode](https://github.com/neptune46/ffmpeg-vscode) written four years ago.

## Preparation

### 1. Download MSYS2

Just follow [the official installation guide](https://www.msys2.org/#installation).

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

## Debug FFmpeg on VSCode!

If you downloaded MSYS2 following official guide, your FFmpeg project may be located in `C:\msys64\home\{user_name}\FFmpeg`.

These commands must be ran on **Commpand Prompt** of Windows not MSYS2.

```bash
cd C:\msys64\home\{user_name}\FFmpeg
mkdir .vscode
cd .vscode
type NUL > launch.json
code .
```

Install [C/C++ Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) on your VSCode.

Set `.vscode/launch.json`.
```

```
