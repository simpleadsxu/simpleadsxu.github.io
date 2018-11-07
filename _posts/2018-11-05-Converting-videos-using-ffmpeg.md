---
layout: single
title:  "Converting videos using ffmpeg"
date:   2018-11-05 21:03:38 -0400
author: JS
categories: software
tags:
  - ffmpeg 
  - mov
  - video editting
  - H265
excerpt: Converting videos using ffmpeg
---

Recently, I starting taking videos using iPhone and quickly realize how large the video files are. A quick question is does it really need to be that large? Especially I am a pro.


If you are not comfortable with programing, you probably want to skip the following and just search and download a video converter. A "better" solution is to use [ffmpeg](https://ffmpeg.org/), a free software for *A complete, cross-platform solution to record, convert and stream audio and video*. 


After some research, the first conclusion is that the most common compressed (or say lossy) video format is mp4 and mov. To achieve the similar video quality, seems the compression ratio is not really determined by video format, but rather by encoding method. The recent trend is using [H.265 (or HEVC)](https://en.wikipedia.org/wiki/High_Efficiency_Video_Coding), which is said to have roughly double compression ratio (or to result half of the file size) compared with its predecessor (H.264). 
 
Below is the command line I end up using (more details can be found [here](https://trac.ffmpeg.org/wiki/Encode/H.265):


{% highlight shell %}
ffmpeg -i [input.mov] -c:v libx265 -crf 25 -c:a aac -b:a 128k -pix_fmt yuv420p -tag:v hvc1 -movflags faststart [output.mov]
{% endhighlight %}


 - First, a variable you need to specify is `-crf 25`, where `crf` stands for **Constant Rate Factor (CRF)** . Basically it controls the compression ratio. The value ranges between 0~51 where 0 is lossless. The official doc says default 28 gives good visual quality. So far good enough for me.
 - Special flags `-pix_fmt yuv420p -tag:v hvc1 -movflags faststart` are for iOS according to [Dan](https://danconnor.com/posts/21d8bd7c22f6ae6b423c3c09/how_to_encode_h_265_hevc_video_that_will_play_in_quicktime_on_macos_using_ffmpeg).  "*The hvc1 tag clues Apple in that the video should indeed play with Quicktime. The pixel format is also important for Apple-compatibility. movflags moves the metadata to the beginning, which helps in scrubbing on iOS and streaming over networks.*" Otherwise, the converted video won't be played on iOS, at least as of 2018.
 
Ok, the remaining is just some simple scripting. Loop over all the video files in your folder and convert them. 

One thing I realize is that ffmpeg is pretty good at multi-processing. It utilizes all my CPU, so there is no real point of writing your own mult-process logic. Nice!




