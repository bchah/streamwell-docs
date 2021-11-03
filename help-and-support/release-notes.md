# Release Notes

v1.0.10 - November 3, 2021

* Improvements to video chat
* Expand free license features
* Fixed issues with iOS 15 / 15.1



v1.0.9 - October 19, 2021

Fixes:

* Fix audio sync issues in Safari
* Fix issues with engine config reset
* Fix issues with recording status not updating
* Fix issue where only one SRT stream could be received at a time
* Fix issue where thumbnails were not deleted when their main file was
* Fix issue where some backend operations slowed down the UI
* Fix BeamBOX toggle not showing when editing existing creator
* Other bug and visual fixes

Improvements:

* Stream playback starts faster (Specify ICE Candidate)
* Added free license tier for personal use
* Redesigned video chat with better performance and UI
* Added support for Screen Sharing and HD webcam resolution on Chrome
* Replaced Emoji placeholders with actual icons
* File uploads now show progress
* File list now automatically refreshes
* Improved page loading performance
* Added some fun Easter eggs (Hints: the boat of a chocolate maker; a cheat from Shadows of the Empire)\


Security Improvements:

* Allow use of a SYSTEM\_KEY environment variable at the docker level, to allow persistent keys between updates. If not present, a random system key will be issued but your old public links will have expired.
* Limit BeamBOX to certain registered users only as it is an obscure and somewhat insecure feature.

Known Issues with Video Chat:

* Video chat is not yet supported in Firefox or Edge due to poor WebRTC reliability. Additionally, Safari on iOS 15.1 introduces breaking changes to WebRTC and the application will crash if you attempt to transmit video. This in mind, it is recommended to participate in video chat from Chrome or Safari on Desktop only. As the WebRTC standard is more uniformly adopted across browsers, this will improve. When in doubt, use Chrome.

\


v1.0.8 - September 30, 2021

Fixes:

* Fixed issue where pressing enter to submit a form might cause the page to reload
* Fixed issue where certain characters in user / channel names could prevent changes from saving
* Fixed logo image caching so new logo shows without browser cache reset
* Fixed issue where login panel gets too narrow when the logo image is narrow
* Fixed issue where Safari on iOS 15 destroyed the entire universe
* Fixed disappearing player when promoting live chat stream but no stream was live

Improvements:

* User and Admin experience improvements
* Reduced network activity when chat, recording, stats modules are not visible
* Users will now be shown a ‘live stream offline’ warning instead of an empty player, if there is no live stream
* Main player is now vertically responsive and will always fit on the page regardless of vertical height limitations
* Uploaded files now receive itty bitty thumbnails where possible
* Stream and chat connections now more reliable (TCP relay)
* Media tags like \<img> \<video> etc are no longer allowed in custom welcome messages, as they presented a cross-site scripting vulnerability
* Closed a loophole where the test stream URL could be used to execute a malicious command\


Known Issues:

* There is an issue with SRT streams where only one stream is processed at a time. WORKAROUND: Use the \<WorkerCount> flag in the SRT port binding settings to increase the worker count to the number of incoming SRT streams needed, up to the number of CPU cores available. This will be fixed in the next release.



v1.0.7 - September 22, 2021

* Add HLS streaming for universal playback compatibility
* Add drag-drop file upload support
* Bug fixes and performance improvements\


Note to iOS users: iOS 15.0 includes breaking changes to web sockets in Safari, which prevents Streamwell from functioning. We are exploring ways to get around these new changes but as Apple does from time to time, the change is significantly limiting and they have not provided any alternatives yet. For now, Streamwell (and a number of other web apps which use secure sockets) will only work up to iOS 14.8.\




v1.0.6 - September 17, 2021

* Video chat is somewhat less experimental!
* In-browser streaming now supported via video chat
* Added ability to dynamically swap videos in and out of the main player without reloading them
* Added ability to view most uploaded image / mp4 / mov files in the browser
* Bug fixes and performance improvements
* Improved application security (better input validation)
* Improved database restores
* Improvements to text chat (e.g. URL highlighting)
* Optimize default network / server configurations
* Update Engine to 0.12.5 and Player to 0.10.3\


v1.0.5 - Jun 4, 2021\


Add File Sharing module

* Add Chat module
* Add ‘classic mode’ HLS stream option
* Add engine config editor to Admin panel
* Improvements and additions to video conferencing (still experimental)
* Fix engine config issue on reboot
* Improve custom color scheme
* Fixes for other minor bugs and UI issues\


v1.0.4 - May 17, 2021

* Many UI/UX improvements
* Auto-rotate log files on admin login
* Fix crackling audio on recordings
* Auto-recover failed recordings
* Add Autoplay on/off option
* Add secure SRT input
* Add TCP/UDP toggle to player ('Safe Mode')
* Expand custom color scheme
* Fix users and channels showing in random order
* Add experimental video chat feature\


v1.0.3 - April 21, 2021

* Expand licensing
* Implement database updates
* Implement test stream
* Implement live stream statistics
* Bug fixes and architecture improvements



v1.0.2 - April 15, 2021

* Many small UI/UX fixes
* Add automatic HTTPS certificate in Administration
* Auto-rotate log files
* Fix player background not updating due to caching issue
* Application security keys are now randomized on deployment
* Allow reset of public links and stream keys
* Improved session & password reset security
* Recordings now require a minimum of 12GB disk space to start
* Changed default application name to 'live' instead of 'streamwell'
* Add PHPShadow code protection for production environment



v1.0.1 - April 6, 2021

* Update OvenMediaEngine (0.11.2.x) and OvenPlayer components for improved performance
* Add Engine Restart / System Log controls in the Admin Panel
* Now fully containerized and ready for automated deployment with Build Script + Dockerfile\


v1.0.0 - March 26, 2021 (Initial Release)

Streamwell Studio is a decentralized, self-hosted streaming server that puts creators back in control. With this application running on a local server or in a cloud of your choosing, you can:

* Create private and secure live streaming channels, viewable from any modern web browser
* Control visibility of channels to approved clients and creators only
* Stream with sub-second latency for live collaboration and 'in the moment' experiences
* Fully brand the experience with your organization's logo and identity
* Share convenient one-touch public links for absolute ease of use
* Record, playback and download streams for future use
