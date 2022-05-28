---
title: VPN Overview
icon: material/vpn
---

Virtual Private Networks are a way of extending the end of your network to exit somewhere else in the world. An ISP can see the flow of internet traffic entering and exiting your network termination device (ie. modem).

Encryption protocols such as HTTPS are commonly used on the internet, so they may not be able to see exactly what you're posting or reading but they can get an idea of the [domains you request](/basics/dns.md/#why-shouldnt-i-use-encrypted-dns).

A VPN can help as it can shift trust to a server somewhere else in the world. As a result, the ISP then only sees that you are connected to a VPN and nothing about the activity that you're passing into it.

## Should I use a VPN?

**Yes**, unless you are already using Tor. A VPN does 2 things: shifting the risks from your Internet Service Provider to itself and hiding your IP from a third party service.

VPNs cannot encrypt data outside of the connection between your device and the VPN server. VPN providers can see and modify your traffic the same way your ISP could. And there is no way to verify a VPN provider's "no logging" policies in any way.

However, they do hide your actual IP from a third party service, provided that there are no IP leaks. They help you blend in with others and mitigate IP based tracking.

## What about encryption?

Encryption offered by VPN providers are between your devices and their servers. It guarantees that this specific link is secure. This is a step up from using unencrypted proxies where an adversary on the network can intercept the communications between your devices and said proxies and modify them. However, encryption between your apps or browsers with the service providers are not handled by this encryption.

In order to keep what you actually do on the websites you visit private and secure, you must use HTTPS. This will keep your passwords, session tokens, and queries safe from the VPN provider. Consider enabling "HTTPS everywhere" in your browser to mitigate downgrade attacks like [SSL Strip](https://www.blackhat.com/presentations/bh-dc-09/Marlinspike/BlackHat-DC-09-Marlinspike-Defeating-SSL.pdf).

## Should I use encrypted DNS with a VPN?

Unless your VPN provider hosts the encrypted DNS servers, **no**. Using DOH/DOT (or any other form of encrypted DNS) with third party servers will simply add more entities to trust, and does **absolutely nothing** to improve your privacy/security. Your VPN provider can still see which websites you visit based on the IP addresses and other methods. Instead of just trusting your VPN provider, you are now trusting both the VPN provider and the DNS provider.

A common reason to recommend encrypted DNS is that it helps against DNS spoofing. However, your browser should already be checking for [TLS certificates](https://en.wikipedia.org/wiki/Transport_Layer_Security#Digital_certificates) with **HTTPS** and warn you about it. If you are not using **HTTPS**, then an adversary can still just modify anything other than your DNS queries and the end result will be little different.

Needless to say, **you shouldn't use encrypted DNS with Tor**. This would direct all of your DNS requests through a single circuit, and would allow the encrypted DNS provider to deanonymize you.

## Should I use Tor *and* a VPN?

By using a VPN with Tor, you're creating essentially a permanent entry node, often with a money trail attached. This provides zero additional benefit to you, while increasing the attack surface of your connection dramatically. If you wish to hide your Tor usage from your ISP or your government, Tor has a built-in solution for that: Tor bridges. [Read more about Tor bridges and why using a VPN is not necessary](https://web.archive.org/web/20210116140725/https://write.privacytools.io/my-thoughts-on-security/slicing-onions-part-2-onion-recipes-vpn-not-required).

## What if I need anonymity?

VPNs cannot provide anonymity. Your VPN provider will still see your real IP address, and often has a money trail that can be linked directly back to you. You cannot rely on "no logging" policies to protect your data. Use [Tor](https://www.torproject.org/) instead.

## What about VPN providers that provides Tor nodes?

Do not use that feature. The point of using Tor is that you do not trust your VPN provider. Currently Tor only supports the [TCP](https://en.wikipedia.org/wiki/Transmission_Control_Protocol) protocol. [UDP](https://en.wikipedia.org/wiki/User_Datagram_Protocol) (used in [WebRTC](https://en.wikipedia.org/wiki/WebRTC) for voice and video sharing, the new [http3/QUIC](https://en.wikipedia.org/wiki/HTTP/3) protocol, etc), [ICMP](https://en.wikipedia.org/wiki/Internet_Control_Message_Protocol) and other packets will be dropped. To compensate for this, VPN providers typically will route all non TCP packets through their VPN server (your first hop). This is the case with [ProtonVPN](https://protonvpn.com/support/tor-vpn/). Additionally, when using this Tor over VPN setup, you do not have control over other important Tor features such as [Isolated Destination Address](https://www.whonix.org/wiki/Stream_Isolation) (using a different Tor circuit for every domain you visit).

Thus, this feature should be viewed as a convenient way to access the Tor Network, not to stay anonymous. For true anonymity, use the Tor Browser Bundle, TorSocks, or a Tor gateway.

## When are VPNs useful?

A VPN may still be useful to you in a variety of scenarios, such as:

1. Hiding your traffic from **only** your Internet Service Provider.
2. Hiding your downloads (such as torrents) from your ISP and anti-piracy organizations.
3. Hiding your IP from third party websites and services, preventing IP based tracking.

For use cases like these, or if you have another compelling reason, the VPN providers we listed above are who we think are the most trustworthy. However, using a VPN provider still means you're *trusting* the provider. In pretty much any other scenario you should be using a secure**-by-design** tool such as Tor.

## Sources and Further Reading

1. [VPN - a Very Precarious Narrative](https://schub.io/blog/2019/04/08/very-precarious-narrative.html) by Dennis Schubert
2. [The self-contained networks](self-contained-networks.md) recommended by Privacy Guides are able to replace a VPN that allows access to services on local area network
3. [Slicing Onions: Part 1 – Myth-busting Tor](https://medium.com/privacyguides/slicing-onions-part-1-myth-busting-tor-9ec188ae1904) by blacklight447
4. [Slicing Onions: Part 2 – Onion recipes; VPN not required](https://web.archive.org/web/20210116140725/https://write.privacytools.io/my-thoughts-on-security/slicing-onions-part-2-onion-recipes-vpn-not-required) by blacklight447
5. [IVPN Privacy Guides](https://www.ivpn.net/privacy-guides)
6. ["Do I need a VPN?"](https://www.doineedavpn.com), a tool developed by IVPN to challenge aggressive VPN marketing by helping individuals decide if a VPN is right for them.

## Related VPN Information

- [The Trouble with VPN and Privacy Review Sites](https://medium.com/privacyguides/the-trouble-with-vpn-and-privacy-review-sites-ae9b29eda8fd)
- [Proxy.sh VPN Provider Sniffed Server Traffic to Catch Hacker](https://torrentfreak.com/proxy-sh-vpn-provider-monitored-traffic-to-catch-hacker-130930/)
- [blackVPN announced to delete connection logs after disconnection](https://medium.com/@blackVPN/no-logs-6d65d95a3016)
- [Don't use LT2P IPSec, use other protocols.](https://gist.github.com/kennwhite/1f3bc4d889b02b35d8aa)
- [Free VPN App Investigation](https://www.top10vpn.com/free-vpn-app-investigation/)
- [Hidden VPN owners unveiled: 101 VPN products run by just 23 companies](https://vpnpro.com/blog/hidden-vpn-owners-unveiled-97-vpns-23-companies/)
- [This Chinese company is secretly behind 24 popular apps seeking dangerous permissions](https://vpnpro.com/blog/chinese-company-secretly-behind-popular-apps-seeking-dangerous-permissions/)

## VPN Security Breaches

Some examples of why external security auditing is important:

- ["Zero logs" VPN exposes millions of logs including user passwords, claims data is anonymous](https://www.comparitech.com/blog/vpn-privacy/ufo-vpn-data-exposure/) July 2020
- [NordVPN HTTP POST bug exposed customer information, no authentication required](https://www.zdnet.com/article/nordvpn-http-post-bug-exposed-sensitive-customer-information/) March 2020
- [Row erupts over who to blame after NordVPN says: One of our servers was hacked via remote management tool](https://www.theregister.com/2019/10/21/nordvpn_security_issue/) October 2019
- [VPN servers seized by Ukrainian authorities weren't encrypted and allowed authorities to impersonate Windscribe servers and capture and decrypt traffic passing through them](https://arstechnica.com/gadgets/2021/07/vpn-servers-seized-by-ukrainian-authorities-werent-encrypted/) July 2021

--8<-- "includes/abbreviations.en.md"
