# FFmpeg wrapper scripts for Linux and macOS

These are Bash script wrappers for `ffmpeg`, `ffplay`, and `ffprobe`, designed to work seamlessly with `yt-dlp` and
[Stacher][stacher]. They address potential issues that may arise when using `yt-dlp` to download videos, especially when
dealing with video files missing an audio track.

Sometimes `yt-dlp` invokes `ffmpeg` with options such as `-map 0:a:0` while the file doesn't have an audio track. This
causes most `ffmpeg` versions to crash. By including these wrappers in the home directory of Stacher, these scripts fix
bypass the issue on Linux and macOS.


## About the wrappers

### ffmpeg

This script is a wrapper for `ffmpeg`. It accepts the same command-line arguments as `ffmpeg` but alters the commands so
that every "map" argument has a question mark added to the end. This modification helps ensure that processing of
video files downloaded with `yt-dlp` does not crash when merging video and audio tracks.

### ffplay

This script serves as a wrapper for `ffplay`. It simply passes the provided arguments to `ffplay` without making any
modifications.

### ffprobe

This script acts as a wrapper for `ffprobe`. Similar to `ffplay.sh`, it passes the provided arguments to `ffprobe`
without making any modifications.

## Usage

To use these wrapper scripts with Stacher, simply download them and put them in the Stacher home directory. Then,
set the _ffmpeg location_ parameter in the settings.


## What about _Postprocessing_ errors on Windows?

Most builds of `ffmpeg` encounter a similar issue, even [those provided by the yt-dlp project][yt_dlp_builds]. However,
there are a few builds that seem to work well with `yt-dlp` and Stacher, even for missing audio tracks.


[stacher]: https://stacher.io/
[yt_dlp_builds]: https://github.com/yt-dlp/FFmpeg-Builds/releases/
