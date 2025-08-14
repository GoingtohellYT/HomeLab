### Why use Pi-hole?

Pi-hole acts as a DNS sinkhole, enhancing both security and speed by blocking trackers, adverts, and more at the network level. It’s a core part of my online security and privacy strategy.

### Installation Method

Pi-hole is installed directly on the host rather than in a Docker container, as Docker has poor IPv6 support. Its web interface runs on port 80 over HTTP.  
Since most clients don’t allow changing the port for DNS requests, Pi-hole also listens on port 53.

### Configuration

#### Forwarding Requests
Requests that are not blocked are forwarded to either `127.0.0.1#5335` for IPv4 or `::1#5335` for IPv6. These addresses correspond to the Unbound instance running on the server.

#### Blocking Requests
To decide which requests to block, Pi-hole checks if the requested domain appears on one of its blocklists. These lists can include domains serving adverts, phishing sites, and more.  
If a trusted domain is blocked, it can be added to the whitelist.

#### Allowed Interfaces
For security reasons, Pi-hole only accepts requests from the local network. Any request coming from outside the LAN is rejected.  
This means you must either be on the same local network or use a VPN to access it. This isn’t an issue for me, as the only way to communicate with the homelab from outside the LAN is through Twingate.
