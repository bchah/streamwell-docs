# Hello Outside World

It is strongly recommended to run your server over HTTPS, unless you have a specific reason not to. Getting a certificate is simple - just set your server hostname then click ‘Enable’ under Administration -> Server -> Hostname. As long as your port and domain name forwarding are set up properly, it will ‘just work’!

![](<../.gitbook/assets/Screen Shot 2021-10-23 at 9.44.04 AM.jpg>) ![](<../.gitbook/assets/Screen Shot 2021-10-23 at 9.44.20 AM.jpg>)

Streamwell uses LetsEncrypt.org to generate a secure certificate, which must be renewed every 90 days by following the same instructions above. While HTTPS activates or renews, the server may become unresponsive for about 30 seconds.

You can also apply your own HTTPS certificate if you prefer. You should still activate HTTPS so the configuration switches over, but once activated you can replace the default PEM-encoded cert, private key, and chain files at these paths inside the docker container:

/etc/letsencrypt/live/YOURDOMAINHERE.COM/cert.pem                                      &#x20;

/etc/letsencrypt/live/YOURDOMAINHERE.COM/privkey.pem

/etc/letsencrypt/live/YOURDOMAINHERE.COM/chain.pem

Or if you’re feeling really brave, you can manually configure the included Apache server and change the above paths in the engine configuration to the appropriate location for your cert.

If the process fails, you will know because the page will remain insecure after the window refreshes, or the engine won’t respond. If this is the case, please consult the log files for further clues (they are available in the admin web interface).
