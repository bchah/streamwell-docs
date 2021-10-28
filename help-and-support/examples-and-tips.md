# Examples and Tips

At this point you are either thinking "Wow, this is really simple" or "Wow, I have no idea what any of that just was". Either way, we feel you.

The hardest parts of setting up any server application are:

* Making it so people can access it from the outside world.
* Setting up reliable hardware and networking so the server is robust under heavy usage.

If the examples provided here are not enough or if you are feeling apprehensive about managing your own server, please consider our [subscription service](https://streamwell.net) where we deploy and manage a Streamwell server in the cloud for you, or [contact us](mailto:help@beamwell.com) for professional services where we can assist with your onsite deployment. Then all you have to do is use it :)

### Port Forwarding Example

Here is an example of enabling port forwarding in the popular TP-Link Archer C7 router:

![](<../.gitbook/assets/Screen Shot 2021-10-23 at 10.12.20 AM.jpg>)

In this example, our Streamwell server has a local IP address of 192.168.0.133. Without port forwarding, the server functions but only on the local network. For some installations where video is only intended to be broadcast locally, this might make sense. However in most cases, you will want to forward the ports listed [here](../getting-started/requirements.md) to the server.

Another key piece of info you can find here is your public IP address - that is, the IP address your router has on the internet:

![](<../.gitbook/assets/Screen Shot 2021-10-23 at 10.12.41 AM.jpg>)

For many business and enterprise-grade connections, this IP address remains _static _and does not change. For home and consumer-grade connections, it normally refreshes every time you restart your router. See the Dynamic DNS example below for a solution around this.

### Domain Registration Example

Virtually all websites run with TLS encryption, which gives you that nice secure 'lock' icon at the top and requires a domain name. Here is an example of a domain purchased from namecheap.com:

![](../.gitbook/assets/IMG\_8D41BF4F57D6-1.jpeg)

Regardless of which registrar you choose (and there are _thousands _to choose from), they will provide an interface for managing your DNS records. Here you want to add two records:

* A Record: @ => Public IP
* URL Redirect: www => https://your.domain

This simplifies the certificate creation process and accounts for the old habit of typing 'www' before a website (which has not been required for years, but old habits die hard.)

### Dynamic DNS Example

If you are an individual or home-based user, you might be thinking "it seems like a lot of work to update my domains DNS settings every time my public IP changes". Consider use of a Dynamic DNS provider, like [dyn.com](https://pages.dyn.com/dyndns-remote-access/). They provide a domain and multiple methods of updating the public IP automatically, like this [updater application](https://help.dyn.com/updater/) you can run on any computer on your network.

Here is an example of setting up a DynDNS domain:

![](<../.gitbook/assets/Screen Shot 2021-10-23 at 10.54.00 AM.jpg>)

Most routers provide a few Dynamic DNS integrations - for example, the TP-Link Archer C7:

![](<../.gitbook/assets/Screen Shot 2021-10-23 at 11.05.40 AM.jpg>)

With this and the port forwarding configuration set, you should be able to access your server remotely!

### Cloud Server Example

If you prefer not to manage your own server hardware, there are many cloud providers available which can set you up with a virtual private server (VPS). The pricing and features of these providers cover a wide spectrum, and the process of deploying them is beyond the scope of this document. However here is an example of a virtual server purchased from servercheap.net:

![](../.gitbook/assets/IMG\_1AD06421CA72-1.jpeg)

Note the minimal Linux build chosen. Once running, the Main IP Address would be equivalent to the Public IP address in earlier examples. Open any terminal and use the IP and root password to connect:

`ssh root@your.domain `

Then use the built-in package manager apt to install snap, which in turn is used to install docker:

`apt-get update`

`apt-get install snapd`

`snap install docker`

With the Docker daemon running, it's time for "Hello World" with the pull/run commands we saw earlier:

_`docker pull beamwell/streamwell:latest`_

Since this is a new system, don't forget to create the directories outside of the Docker container which will hold our persistent data:

_`mkdir ~/ssl ~/rec ~/log ~/files`_

This gives us the flexibility to use any storage location we want for the various data components. And with no further ado, the run command:

_`docker run -d --name Streamwell --restart always -e SYSTEM_KEY=“yourSecretKey” --network host -v ~/ssl:/etc/letsencrypt -v ~/rec:/rec -v ~/log:/log -v ~/files:/files beamwell/streamwell:latest` _

