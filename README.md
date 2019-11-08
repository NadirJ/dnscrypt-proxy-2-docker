[![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/atemu12/dnscrypt-proxy-2-docker.svg)](https://hub.docker.com/r/atemu12/dnscrypt-proxy-2-docker)
[![MicroBadger Size (tag)](https://img.shields.io/microbadger/image-size/atemu12/dnscrypt-proxy-2-docker/latest.svg)](https://hub.docker.com/r/atemu12/dnscrypt-proxy-2-docker)
[![Docker Pulls](https://img.shields.io/docker/pulls/atemu12/dnscrypt-proxy-2-docker.svg)](https://hub.docker.com/r/atemu12/dnscrypt-proxy-2-docker)

This is a Docker image containing [DNSCrypt Proxy 2.x](https://github.com/DNSCrypt/dnscrypt-proxy). You can use this to set up a DNS server on your local network which resolves queries using DNSCrypt or DNS-over-HTTPS (DoH) rather than sending plaintext DNS queries over the Internet.

This image comes with a configuration which:

* Looks up queries via DNS-over-HTTPS (DoH) to the fastest two resolvers out of a list of trusted DNSCrypt servers that support DNSSEC, don't filter and don't log
* Has all privacy and safety options enabled
* Has custom blacklist support

You can run it with this configuration:

`docker run -p 53:53/udp atemu12/dnscrypt-proxy-2-docker`

If you wish to override the configuration:

`docker run -p 53:53/udp  -v /path/to/dnscrypt-proxy.toml:/config/dnscrypt-proxy.toml atemu12/dnscrypt-proxy-2-docker`

If you wish to use a blacklist (for ad-blocking etc.):

Have a Docker volume with `./blacklist.txt` in it:

`docker run -p 53:53/udp -v blacklist-volume:/blacklist/ atemu12/dnscrypt-proxy-2-docker`
