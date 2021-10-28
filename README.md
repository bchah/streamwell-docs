# Welcome to Streamwell

Streamwell is your private virtual suite, built to put creators back in control of their content. With Streamwell’s privacy, high quality and incredibly low latency streams, you can power experiences like creative sessions, presentations, footage review, remote directorial, live monitoring, and more!

Streamwell lets you:

* Create private live streams, viewable from any modern web browser.
* Stream with virtually no delay for live collaboration and other 'in the moment' experiences.
* Share convenient one-click links for absolute ease of access.
* Customize the look and feel of the app with your own logo and brand identity.
* Record, playback and download your streams.
* Upload files related to your project, and share public download links
* Collaborate live using instant messaging and video chat.
* Manage logins for clients (viewers) and creators (streamers), with precise control over who sees what.

**How is Streamwell different?**

Regular streaming tools cannot possibly offer these promises, because of the way they are built. On huge services like YouTube, Facebook and Twitch, your stream gets processed first by an ‘Edge’ server which distributes the content to a global network of redundant, monolithic servers. Along the way, they perform video transcoding, image analysis, and scanning for copyrighted content.&#x20;

On the flip side, instant meeting services like Boom, WubUx, Stype, GoForGreeting, et al are fantastic for instant communications. However they all perform heavy processing on video which leads to performance, latency and major quality issues. They are also packed with a ton of confusing features and require either an app download, meeting registration or other configuration to participate. Not to mention they generally can’t be self-branded or self-hosted.

Enter Streamwell... the perfect mix of privacy, low latency, and high quality.

**How does it work? (For nerds)**

For the video track, Streamwell accepts an RTMP or SRT stream directly passes the bits of the incoming stream into an mp4 container, which is streamed to the video player. For the audio track, the incoming stream is transcoded on the fly into the OPUS codec for compatibility with WebRTC, the technology used to deliver such low latency. No analysis or content recognition is performed.

The typical latency you will see with a proper incoming stream is 6 frames of video, or 200 milliseconds, versus as high as 20 seconds on mainstream services. This matches almost perfectly to a telephone call or online meeting, so you can run any sort of chat you’d like on the side while you view a high-quality, private stream.
