## What's a homelab ?
📕 The way I see it, a homelab can be anything from an old computer to a server. It's just something you use to self-host some software you use. It can be a search engine, a DNS server, a media server, a personal cloud, your online calendar, or all these things at the same time!

## Why a homelab ?

There are multiple reasons that led me to start this project. First of all, it is a great project to learn various technologies and tools.

Since I created this small server, I learned about containerisation with Docker and its limitations, got way better at networking through setting up and trying to understand how Pi-hole works (How does a DNS server work? What are DoT, DoH and DNSSEC?), discovered the world of meta-search engines and metrics scraping, but also how to monitor my server and the services running. While installing Jellyfin, I looked for the best compromise between quality/size/accessibility, I dipped my toes in the world of audio and video codecs, learned the difference between a codec and a container, and between transcoding and remuxing. I now also better understand the difference between x86 and ARM architectures. In summary, I learned a lot, which is a good thing both both personally and professionally.

Another reason is privacy. Indeed, the first services I self-hosted and that led me down this rabbit hole were SearXNG and Pi-hole, one to replace Google Search, the second to block ads and telemetry network-wide. Sure, I could have just used Startpage, Brave Search, DuckDuckGo, and NextDNS. But the way I see it, if you have the opportunity to enhance your internet usage and learn things you care about at the same time, there's no reason not to take that opportunity!

## My Homelab
### Hardware

Every homelab starts with the hardware. After all, you can't run software without a machine! Here's what I'm currently using:

#### Server

For this, I use a Raspberry Pi 400. It's got 4 cores and 4 GB of RAM, which might not sound like much, but is plenty of power to run all the services below without a single slowdown.

Why a Pi? Well, it's cheaper than a dedicated server, takes less space and, again, is plenty of power for my current needs. Moreover, if I decide to stop this project, I can convert it into pretty much anything else, like a retro gaming console or an on-the-go Linux PC. Plus compared to using an old laptop I had lying around, this consumes basically as much power as an LED lamp, making it cheaper in the long run.

#### Storage

You can't have a media server and not have a place to store all those movies and shows and music. For this purpose, I've selected a 1TB Crucial 2.5" SSD. Obviously, it's got SMART capabilities so I can monitor its health and hopefully change it before it lets me down.

### Provided functionalities
		- Private DNS
		- Private meta-search engine
		- Media server
		- Reading tracker
		- RSS aggregator
		- Remote access
		- Container management
		- Monitoring
		- Dashboard
		- CalDav and CardDav
  
### Hosted services
    - cAdvisor
    - FreshRSS
    - Grafana
    - Heimdall
    - Jellyfin
    - Jelu
    - node-exporter
    - Pi-hole
    - Portainer
    - Prometheus
    - Radicale
    - SearXNG
    - Unbound
    - Uptime-Kuma
    - Watchtower
    
### Remote access

Regarding remote access to the homelab, I use two different services, both based on zero-trust technology.

#### Cloudflare tunnel
The Cloudflare tunnel allows me to expose any service publicly using a domain name, without needing to open any port on the router. To do so, it is required to have Cloudflare as the domain name's DNS nameserver. Running the cloudflared Docker container on the server with the specific token creates a connection between the homelab and the Cloudflare servers. It is possible to match any subdomain to a specific service in the Cloudflare tunnel's web interface.

This method is used for any "user" service. This includes services that do not contain sensitive user information, with the exception of Radicale, as Apple needs an HTTPS connection with a valid certificate, whereas Radicale uses HTTP by default.

#### Twingate Connector

The Twingate Connector does not make the exposed services accessible from the web directly. It acts more like a VPN in the way that the client needs to run the Twingate client and to authenticate in order to access specific resources. Because it acts like a VPN, it is not required to have a domain name, making it completely free to use for anyone.

Twingate needs the homelab to run its connector. This connector keeps a connection with their servers. This way, when a client tries to connect, the Twingate server can have the client and homelab connect directly via peer-to-peer. Twingate itself is unable to see any traffic occurring between the homelab and the clients.

This method is used for services containing "sensitive" information or tools that allow you to control the homelab. For example, services like Portainer and Grafana use this method. Connecting to the homelab via ssh when outside the LAN also requires a Twingate connection.

#### Need an upgrade ?

When using Twingate to connect to some services, the domain name is not used. This means that some connections use plain old HTTP and others use HTTPS but without a valid certificate. In both cases, the browser sends a warning message that the connection is not secured.

Although this is not a security risk as the services communicate with the client either on the home network or through an encrypted tunnel, it is not very elegant. One way to fix this issue might be to run a reverse proxy like Traefik internally, but I have not yet taken a good look at that option.

Considering that this upgrade would be mostly aesthetic, it is not part of my top priorities.
