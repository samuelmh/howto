# How to manipulate video files

```
AUTHOR: Samuel M.H.
DATE: 02-JUL-2024
LICENCE: all rights reserved.
```

## Audio

### Extract audio
* `-i`: input video.
* `-vn`: no video.
* `-acodec copy`: same audio, no re-encoding.
* `-ss`, `-t`, `-to`: to set the time range.
* Example:
```bash
ffmpeg -i input.mp4 i -vn -acodec copy output-audio.aac
```

### Merge audio and video
* Keep the same encoding for audio and video.
* Example:
```bash
ffmpeg -i video.mp4 -i audio.mp3 -c:v copy -c:a copy  output.mp4
```


## Cut/trim

###  Using a duration
* `-i`: input, original video.
* `-ss`: starting position.
* `-t`: **duration** from the start position.
* `-c:v copy`: copy original video, no re-encoding.
* `-c:a copy`: copy original audio, no re-encoding.
* Example:
```bash
$ ffmpeg -i input.mp4 -ss 00:05:20 -t 00:10:00 -c:v copy -c:a copy output1.mp4
```

## Using a specific time
* `-i`: input, original video.
* `-ss`: starting position (from the beginning).
* `-to`: ending position (from the beginning).
* `-c:v copy`: copy original video, no re-encoding.
* `-c:a copy`: copy original audio, no re-encoding.
* Example:
```bash
$ ffmpeg -i input.mp4 -ss 00:05:10 -to 00:15:30 -c:v copy -c:a copy output2.mp4
```


## Resources
* [1] []()
