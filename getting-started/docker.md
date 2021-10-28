# Docker

For ease of deployment, Streamwell works with **Docker**. This lets you deploy or update a server on any hardware or virtual machine, in seconds. Docker can be installed on your platform of choice for free at [www.docker.com](http://www.docker.com).

macOS and Windows have their own GUI-based install procedures, but here is an example of installing Docker on Ubuntu 20.04 using the snap package manager. If you’re using a virtual machine, a barebones build of Ubuntu 20.04 should work great.

_`apt-get update `_

_`apt-get install snapd `_

_`snap refresh && snap install docker `_

Once Docker is installed and running, hit the command prompt or terminal. Don’t be scared, it’s just text!&#x20;

On any platform, you can pull the latest available docker image or a particular version:

_`docker pull beamwell/streamwell:latest`_

_OR_

_`docker pull beamwell/streamwell:1.0.9 `_

Linux:

_`docker run -d --name Streamwell --restart always -e SYSTEM_KEY="yourSecretKey" --network host -v ~/ssl:/etc/letsencrypt -v ~/rec:/rec -v ~/log:/log -v ~/files:/files beamwell/streamwell:latest` _

Windows and macOS:

_`docker run -d --name Streamwell --restart always -e SYSTEM_KEY="yourSecretKey" —p 80:80 -p 443:443 -p 1935:1935 -p 3333-3334:3333-3334 -p 3478-3479:3478-3479 -p 10010-10011:10010-10011/udp -p 8000:8000 -p 8081-8082:8081-8082 -p 9999:9999/udp -p 20081:20081 -v ~/ssl:/etc/letsencrypt -v ~/rec:/rec -v ~/log:/log -v ~/files:/files beamwell/streamwell:latest` _

Testing (Minimum required commands, but nothing persists outside of the container):

_`docker run -d --name Streamwell --restart always` `--network host beamwell/streamwell:latest`_

### **What do these commands mean?**

_docker pull _= downloads the application image and version specified (e.g. mycompany/myapp:version).

_docker run -d  --name Streamwell = _runs a detached container (so we can close the terminal) and calls it Streamwell

_--restart always = _If the container crashes or is rebooted due to a power failure / system restart, it will automatically restart itself

\-e = Environment Variable. Pass a ‘SYSTEM\_KEY’ and we’ll use that as the encryption key inside the application, to secure your links and stream keys. If you don’t pass a key in, one will be created for you and printed a single time in the startup logs (use _docker container logs Streamwell _to view said logs).

_-p_ = Connect this port from the outside world to the container. On Linux hosts, you don’t need to do this. Instead you can use the argument _--network host _in your command. Or connect the ports manually if you prefer. Most of the ports like RTMP, SRT etc are currently fixed but you could use different ports for 80 / 443, the 'web ports' that serve the web client interface, e.g. `-p 8080:80 -p 8443:443`

_-v_ = Connect this folder from the computer running Docker to the container

The -v flag is particularly useful since that lets you house things like logs, SSL certificates, the database, and stream recordings on the host server rather than in the running container. So when you need to update the application it is as simple as replacing the running container with one run from an updated image. While not absolutely required, you should create these directories for data persistence / management outside of the Docker container:

_-v /your/path/to/SSL:/etc/letsencrypt_

_-v /your/path/to/LOGS:/log_

_-v /your/path/to/RECORDINGS:/rec_

_-v /your/path/to/FILES:/files_

You can even store the database outside of the container:

_-v /your/path/to/DATABASE:/var/lib/mysql _(note: if you store the database outside of the container, you must update it manually by running the update .SQL scripts in order starting from the version after the one you are updating from. The update scripts are located in the root directory of the container. Otherwise, just backup before you update, restore the database in the web admin and it will automatically update like magic.)

BEST PRACTICE: Once you figure out the run command for your system, tuck it away somewhere so you can easily re-deploy whenever you [Update Streamwell](../help-and-support/how-to-update.md)\
