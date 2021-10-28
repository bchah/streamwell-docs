# Streaming

The streaming engine takes an SRT or RTMP stream with H264 video + AAC audio, baseline or main profile and a keyframe interval of 1 second.

The easiest way to stream in is using [OBS](http://obsproject.com), a free open-source video mixer application. If you are new to OBS, here are some quick steps to get you moving.

* Once installed, open OBS and bypass any setup wizards.
* Add a source like a Webcam (Video Capture Device) or drag a video file in.
* Click Settings => Output, and change the Output Mode to **Advanced**
* Set the streaming options as shown, or leave them as default if not shown

![](<../../.gitbook/assets/Screen Shot 2021-10-28 at 10.58.38 AM.jpg>)

* Click Settings => Stream, and set the Service to ‘Custom…’
* Enter your Server URL under Server, and copy/paste a Stream Key of your choosing for the channel you’d like to stream to. For SRT URLs just copy/paste the full URL in the 'Server' field and leave the 'Stream Key' field blank. For RTMP URLs the server URL is everything up to and including 'live', and the Stream Key is everything after the slash (do not include the "/").

![In general, you should use SRT URLs wherever possible as they are encrypted, whereas RTMP is a more compatible but unencrypted protocol.](<../../.gitbook/assets/Screen Shot 2021-10-28 at 11.07.38 AM.jpg>)

* Click ‘Start Streaming’ and you should now be live - hello world!

![What a lovely mountain view!](<../../.gitbook/assets/Screen Shot 2021-10-28 at 11.10.49 AM.jpg>)



Whether you are using OBS or another software or hardware encoder, always keep these requirements in mind for the low-latency streaming to function correctly:

* H264 video (RTMP + SRT) or H265 video (SRT only)
* AAC, OPUS or MP3 audio
* Baseline or Main encoding profile
* Keyframe interval of 1 second (higher interval will cause playback issues)
* No B-Frames (use of B-Frames will cause playback issues)
* (Optional) 'zerolatency' x264 tuning option

**Mobiles Too!**

You can also stream in from a mobile device. There are a number of free applications out there but the best one seems to be [Larix Broadcaster ](https://softvelum.com/larix/)which** **is excellent and free, for iOS or Android devices. We tested a \*ton\* with Larix during Streamwell’s development, and successfully streamed from a 7-year old iPhone 5S for more than 72 hours straight, stopping only out of boredom and hunger. On iPad, Teradek offers a more full-featured app called [Airmix Solo](https://apps.apple.com/us/app/airmix-solo/id1051147032)** **which also works quite well, plus a paid version.

**Hardware: It’s the Hard Truth**

Finally, any hardware encoder which supports RTMP can send in a stream. For years we have used off-the-shelf encoders which are now easily found on Amazon from companies like Uray, Orivision, ISEEVY, and countless others. We find them to offer a ton of value, matched only by the latest ATEM Mini Pro / Extreme offerings from [Blackmagic Design](https://www.blackmagicdesign.com/products/atemmini). On the higher end, a Teradek, DataVideo or Epiphan encoding system would be a fine choice. If you are serious about live streaming or high quality transmission, a hardware-based encoder fed a signal from a video camera or playout feed is the only way to go.

\
