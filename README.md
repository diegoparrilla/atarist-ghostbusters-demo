# atari-st-ghostbusters-intro
Source code of my old 'ghostbusters' intro or cracktro demo for #AtariST from 1989

## Introduction

This repository contains the source code and resources for an intro or cracktro demo developed by me back in 1989 for the Atari ST platform. The demo showcases various graphical effects, sound, and other features typical of the time. The Atari ST was a popular home computer in the late 1980s, known for its 16/32-bit architecture, graphical capabilities, and gaming scene. This demo was designed to showcase my 68000 development skills when I was a teenager and the potential of the Atari ST. Probably it had to serve as an introduction or cracktro for cracked software (don't judge me, it was in the '80s and I was too young to go to jail). At that time, my nickname was **Canal 23**.

The demo includes:

- Graphical effects (e.g., sprites, scrolling text, and transitions)
- Sound and music
- Other features (e.g., rasters)

I have uploaded to YouTube the demo running in an Atari ST emulator (Hatari). You can watch the videos here: https://www.youtube.com/watch?v=A5K8tscK6Dw


## Requirements

- An Atari ST computer (or emulator). There are several emulators available for Windows, Linux, and Mac. I recommend [Hatari](http://hatari.tuxfamily.org/), and I'm also a big fan of [MiSTer](https://misterfpga.org/). It should work on any Atari ST with at least 512KB of RAM.

- The [atarist-toolkit-docker](https://github.com/diegoparrilla/atarist-toolkit-docker): You should read first how to install it and how to use it. It's very easy.

- A `git` client. You can use the command line or a GUI client.


## Building the demo

Actually there are two demos in one:
- The intro (or cracktro) demo: `dist/intro.tos` (this is the one I used to introduce my cracked software)
- The ghostbusters sampling demo: `dist/ghots.prg` (this is the one I used to show the sampling capabilities of the Atari ST with a Ghostbusters theme)

Once you have your real Atari ST computer, Hatari emulator or MiSTer Atari ST up and running, you can build the demo using the following steps:

1. Clone this repository:

```
$ git clone https://github.com/diegoparrilla/atarist-ghostbusters-demo
```

2. Export the `ST_WORKING_FOLDER` environment variable with the absolute path of the folder where you cloned the repository:

```
export ST_WORKING_FOLDER=<ABSOLUTE_PATH_TO_THE_FOLDER_WHERE_YOU_CLONED_THE_REPO>
```

3. Build the demos. Enter the `atarist-ghostbusters-demo` folder and run the `make` script:

For the intro demo:
```
cd atarist-ghostbusters-demo
stcmd make -f Makefile_intro
```

For the ghostbusters sampling demo:
```
cd atarist-ghostbusters-demo
stcmd make -f Makefile_sampling
```

4. Copy ALL THE CONTENT of the `dist` folder to your Atari ST computer, Hatari emulator or MiSTer Atari ST.

5. Run the demos!

## How to configure Hatari and FFMPEG to record the demos

1. To configure the Hatari emulator, I followed the instructions in the [Dead Hackers Society site](https://www.dhs.nu/videorecording.php).

2. Install FFMPEG. In my case, I installed it with Brew:

```
brew install chromaprint amiaopensource/amiaos/decklinksdk
brew tap homebrew-ffmpeg/ffmpeg
brew install homebrew-ffmpeg/ffmpeg/ffmpeg --with-chromaprint
```

3. I started Hatari adding the following command line parameters:

```
--avi-file ./demos.avi --avi-vcodec png --png-level 1
```

The `--png-level 1` guarantees that the PNG files are not very compressed, which is important to avoid issues in the video in slow computers.

4. After recording the demo, I used the following command to convert the PNG files to a video that can be processed with Quicktime before uploading to YouTube or Twitter:

```
ffmpeg -i demos.avi -vf "scale=1600:1000, pad=1920:1080:160:40:black, format=yuv420p" -sws_flags neighbor -vcodec libx264 -acodec copy demos.mov
```

## Resources 

Honestly I can't even barely remember when and how I developed the code, but I was able to rebuild it in a few minutes using the (atarist-toolkit-docker](https://github.com/diegoparrilla/atarist-toolkit-docker) VASM.

## License
When I develope the intro I shared the code under a 'public domain' license... whatever that means. But I'm releasing the code under the GNU General Public License v3.0. See the [LICENSE](LICENSE) file for details.
