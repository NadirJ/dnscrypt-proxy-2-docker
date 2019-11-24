[![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/atemu12/dnscrypt-proxy-2.svg)](https://hub.docker.com/r/atemu12/dnscrypt-proxy-2)
[![MicroBadger Size (tag)](https://img.shields.io/microbadger/image-size/atemu12/dnscrypt-proxy-2/latest.svg)](https://hub.docker.com/r/atemu12/dnscrypt-proxy-2)
[![Docker Pulls](https://img.shields.io/docker/pulls/atemu12/dnscrypt-proxy-2.svg)](https://hub.docker.com/r/atemu12/dnscrypt-proxy-2)

This is a Docker image containing [DNSCrypt Proxy 2.x](https://github.com/DNSCrypt/dnscrypt-proxy). You can use this to set up a DNS resolver on your local network which resolves queries using DNSCrypt or DNS-over-HTTPS (DoH) rather than sending plaintext DNS queries over the internet.

This image comes with a modified configuration which:

* Looks up queries via DNS-over-HTTPS (DoH) to the fastest two resolvers out of a list of trusted DNSCrypt servers that support DNSSEC, don't filter and don't log
* Has all privacy and safety options enabled
* Has custom blacklist support

You can run it with this configuration:

`docker run -p 53:53/udp atemu12/dnscrypt-proxy-2`

If you wish to override the configuration:

`docker run -p 53:53/udp  -v /path/to/dnscrypt-proxy.toml:/config/dnscrypt-proxy.toml atemu12/dnscrypt-proxy-2`

If you wish to use a blacklist (for ad-blocking etc.):

`docker run -p 53:53/udp -v blacklist-volume:/blacklist/ atemu12/dnscrypt-proxy-2`  
Where blacklist-volume is a Docker volume with `./blacklist.txt` in it.
