---
title: "Tor Overview"
icon: 'pg/tor'
---

Tor is a free to use, decentralized network designed for using the internet with as much privacy as possible. If used properly, the network enables private and anonymous browsing and communications.

## Path Building

Tor works by routing your traffic through a network comprised of thousands of volunteer-run servers called nodes (or relays).

Every time you connect to Tor, it will choose three nodes to build a path to the internet—this path is called a "circuit." Each of these nodes has its own function:

- **The Entry Node**: Often called the guard node, this is the first node your computer connects to. The entry node sees your IP address, but does not see what you are connecting to. Unlike the other nodes, the Tor client will randomly select an entry node, and stick with it for 2 to 3 months to protect you from certain attacks.
- **The Middle Node**: The second node to which your Tor client connects. This node can see which node traffic came from (the entry node) and which it goes to next. It does not, however, see your IP address, or the domain you are connecting to. This node is randomly picked from all Tor nodes for each circuit.
- **The Exit Node**: This is where your traffic leaves the Tor network and is forwarded to your desired destination. The exit node does not know your IP (who you are) but it knows what you are connecting to. The exit node will, like the middle node, be chosen at random from the Tor nodes (if it runs with an exit flag).

<figure markdown>
  ![Tor path](../assets/img/how-tor-works/tor-path.svg#only-light)
  ![Tor path](../assets/img/how-tor-works/tor-path-dark.svg#only-dark)
  <figcaption>Tor circuit pathway</figcaption>
</figure>

## Encryption

Tor encrypts each packet three times, with the keys from the exit, middle, and entry node in that order. Once Tor has built a circuit, browsing is done as follows:

1. When the packet arrives at the entry node the first layer of encryption is removed. In this encrypted packet it will find another encrypted packet with the middle node’s address. The entry node will then forward that to the middle node.

2. When the middle node receives the packet from the entry node, it too will remove a layer of encryption with its key, and find an encrypted packet with the exit nodes address. The middle node will then forward the packet to exit node.

3. When the exit node receives its packet, it will remove the last layer of encryption with its key. The exit node will see the destination address and forward the packet to that address.

Here is an alternative visualization of the process. Note how each node removes its own layer of encryption, and when the destination website returns data, the same process happens entirely in reverse. For example, the exit node does not know who you are, but it does know which node it came from, and so it adds its own layer of encryption and sends it back.

<figure markdown>
  ![Tor encryption](../assets/img/how-tor-works/tor-encryption.svg#only-light)
  ![Tor encryption](../assets/img/how-tor-works/tor-encryption-dark.svg#only-dark)
  <figcaption>Sending and receiving data through the Tor Network</figcaption>
</figure>

So, what do we learn from this? We learn that Tor allows us to connect to a website without any single party knowing the entire path. The entry node knows who you are, but not where you are going; the middle node doesn’t know who you are or where you are going; and the exit node knows where you are going, but not who you are. Because the exit node makes the connection, the destination website will never know who you are (your IP address).

## Drawbacks

Even with the strong privacy guarantees that Tor provides, one must be aware that Tor is not infallible. Global adversaries with the capability to passively watch most network traffic over the globe have a chance of deanonymizing Tor via advanced traffic analysis. Furthermore, Tor does not protect you from exposing yourself. If you share to much data about your real identity, you may be deanonymized.

Another downside is that exit nodes can watch your traffic, even if they do not know where it came from. This is especially problematic for websites which do not utilize HTTPS, meaning that the exit node can read all data that’s being sent through it. This in turn can lead to deanonymization if the traffic contains personal data.

We recommend using HTTPS over Tor where possible, but do not alter any settings inside Tor Browser aside from the [security settings](https://tb-manual.torproject.org/security-settings/) in the upper right corner of the Tor Browser, including not manually enabling HTTPS only mode, as this can be used for browser fingerprinting.

If you are interested in trying out Tor we recommend using the official Tor Browser. Keep in mind that you should expect added network latency and reduced bandwidth because of the multi-hop routing nature of Tor.

## Further Reading

- [Tor Browser manual](https://tb-manual.torproject.org/about/)
- Tor network [video explanation](https://www.youtube-nocookie.com/embed/QRYzre4bf7I) by Computerphile
- Hidden service [video explanation](https://www.youtube-nocookie.com/embed/lVcbq_a5N9I) by Computerphile
