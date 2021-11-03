# How to Update

**You can update Streamwell in 2 minutes or less! **

**1.** Backup the database under Administration -> Server -> Database -> Backup. It will produce a .SQL file with lots of text in it. Note that the free version of Streamwell does not include the database backup feature as it is for personal use only, therefore data persistence should not matter. If you require data persistence on the free version, make sure you are storing your database outside of the container (See [Installing with Docker](../getting-started/installing-with-docker.md#storing-the-database) for more on how to do this)

**2.** Stop and remove the running container on the server:

`docker rm -f Streamwell`

**3.** Pull the new version you want to update to (or use latest):

`docker pull beamwell/streamwell:1.0.9`

**4.** Run the updated container, connecting it to your existing data folders and passing the same encryption key in an enviroment variable. You can pass a new key, or no key at all if you don’t mind the existing links expiring.

docker run -d --name Streamwell --restart always -e SYSTEM\_KEY=“yourSecretKey”—p 80:80 -p 443:443 -p 1935:1935 -p 3333:3333 -p 3334:3334 -p 3478-3479:3478-3479 -p 10010-10011:10010-10011/udp -p 8081:8081 -p 8082:8082 -p 9999:9999 -p 20081:20081 -v \~/ssl:/etc/letsencrypt -v \~/rec:/rec -v \~/log:/log -v \~/files:/files beamwell/streamwell:1.0.9

**5. **Login and license the ‘new’ install, then restore your database and get back to work! If you were using HTTPS you can [re-enable](../getting-started/hello-outside-world.md) it now. If your browser is being stubborn about temporarily connecting back to the HTTP version, clear your browser cache and use the http:// prefix in the address bar.

Note: If you are under a support agreement, please leverage us to update and check the health of your server.
