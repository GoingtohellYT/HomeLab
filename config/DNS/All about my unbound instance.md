### Why use Unbound?

Although Unbound is not set up as a full recursive DNS server, it adds an extra layer of protection. While Pi-hole can forward requests to Quad9 and cache the answers, Unbound encrypts the requests using DoT (DNS over TLS) and ensures DNSSEC validation, which Pi-hole alone cannot do.

### Installation Method

Unbound is installed directly on the Raspberry Pi as an application. It listens for requests on port `5335` (only Pi-hole sends requests to this port).

### How It Works

When Unbound receives a DNS request from Pi-hole, it forwards the request to Quad9 using DoT and DNSSEC.  
Using a forwarder like Quad9 encrypts the request between the homelab and Quad9. The request is then mixed with traffic from all Quad9 users, preventing tracking by root DNS servers.

This setup requires trusting Quad9 not to inspect your requests or sell data to advertisers. Fortunately, Quad9 is based in Switzerland, complies with GDPR regulations, and is trusted by many privacy experts—they do not collect logs.
