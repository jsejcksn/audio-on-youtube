# audio-on-youtube

Convert an audio file to a video for uploading to YouTube—without any video editing software!

This script uses [`ffmpeg`][1] to combine an audio file with a still image to produce a video that can be uploaded to YouTube.

> Don't upload anything you make unless you own the copyright to the audio/image.

## Requirements

  - a copy of the `ffmpeg` binary in your [$PATH][2] (use the link above if you need to get a copy)

  - an audio file

  - a [16:9 aspect ratio][3] image (blank png supplied) for the still visual part of the video

> The audio and image files can be any format supported by `ffmpeg`.

## Usage

  1. In the [`media`](media/) folder, replace [`audio.wav`](media/audio.wav) with your audio file (and [`image.png`](media/image.png) if you'd like).

  2. Open your terminal to the `media` directory of this repository and then run the following command:

  ```sh
  ffmpeg -loop 1 -i image.png -i audio.wav -c:v libx264 -tune stillimage -c:a aac -b:a 192k -pix_fmt yuv420p -vf scale=1280:720 -shortest video.mp4
  ```

  > When the script finishes converting your video, it will be saved to `media/video.mp4`.

  3. Upload your new video to YouTube and enjoy the audio.


[1]: https://ffmpeg.org/
[2]: https://en.wikipedia.org/wiki/PATH_(variable)
[3]: https://en.wikipedia.org/wiki/16:9
