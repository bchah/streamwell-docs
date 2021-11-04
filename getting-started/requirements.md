# Requirements

**Server**

* macOS / Windows / Linux running Docker (ARM not yet supported)
* Minimum recommended spec: 4 cores / 8GB RAM
* A fast, wired network connection (Your server needs a hefty highway)
* Access to your modem/router port forwarding settings

**Web Client**

* Google Chrome is recommended for the best experience
* Safari, Firefox or Edge are also compatible for most functionality
* Video Chat works in Chrome & Safari only for now
* Screen Sharing works in Chrome only for now

**Network Ports**

* 80/443 (Web Interface HTTP/HTTPS)
* 3333/3334 (Web Sockets HTTP/HTTPS)
* 3478/3479 (TCP Relay)
* 1935 (RTMP)
* 8000 (HLS)
* 8081/8082 (API HTTP/HTTPS)
* 9999/UDP (SRT)
* 10010/10011/UDP (Stream Data)
* 20081 (Live Thumbnails)

Streamwell is built with / utilizes the following technologies:

**Containerization: **Docker

**Front-end:** HTML, CSS, Javascript

**Back-end: **Apache, PHP 7.4, MySQL 5.7

**Video components:** FFMPEG 4.2.1, [OvenMediaEngine](https://www.ovenmediaengine.com)**, **[OvenPlayer](https://ovenplayer.com)

All components are used under MIT, GPLv2 or a community License.&#x20;

Additional license information can be found in the web application directory in the Docker container.
