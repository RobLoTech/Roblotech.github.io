# Piramid of Pain

This is a fairly new concept being applied by reputable companies with the goal of improving the effectiveness of Cyber Threat Intelligence (CTI), threat hunding, and Incident Response (IR)

Check out these resources for a general overview of its meaning, and how reputable companies are implementing it:

[Cisco Security](https://gblogs.cisco.com/ca/2020/08/26/the-canadian-bacon-cisco-security-and-the-pyramid-of-pain/)

[SentinelOne](https://www.sentinelone.com/blog/revisiting-the-pyramid-of-pain-leveraging-edr-data-to-improve-cyber-threat-intelligence/)

[SOCRadar](https://socradar.io/re-examining-the-pyramid-of-pain-to-use-cyber-threat-intelligence-more-effectively/)

## Hash Values

**Hash Value** - this is a fixed length numeric value that identifies a piece of data. This is possible through hashing algorigthms. 

**MD5 (Message Digest, RFC 1321)**

  - Designed by Ron Rivest, 1992
  - **128-bit** hash value
  - **Are NOT considered SECURE**
  - RFC 6151 - published attacks agains MD5 hashes (i.e. hash collision)

**SHA-1 (Secure Hash Algorithm 1, RFC 3174)**

  - Invented by National Security Agency (NSA) in 1995
  - **160-bit** hash value as a 40 digit hex number
  - Was deprecated by NIST in 2011 - susceptible by brute force attacks

**SHA-2 (Secure Hash Algorithm 2)**

  - Designed by NIST and NSA in 2001
  - Most common variants is **SHA-256** - returns a **256-bit** hash value as 64 digit hex number. 

Technically, two pieces of data could hash to the same hash value, but this is not considered cryptographically secure.  

Because altering a file by even a single bit could produce an entirely different hash value, this could become very difficult to analyze as a threat hunter.  Because of the hash value produced by hashing algorithms and how they can differ greatly by altering a single bit, its purpose is mainly used to ensure the integrity of files. 

## Importance of IP Addresses and Their Role in the Pyramid of Pain

- **IP Address:** Identifies devices on a network like desktops, servers, and cameras.
- **Sending and Receiving Data:** IP addresses are essential for transmitting data over a network.
- **Pyramid of Pain:** IP addresses are a green-level indicator, indicating their significance.

### Defense Perspective

- **Blocking IP Addresses:** A common defense tactic to prevent incoming requests from certain IPs.
- **Limitations:** This tactic isn't foolproof; experienced adversaries can easily switch to new IPs.
- **Challenge - Fast Flux:** Adversaries use techniques like Fast Flux to evade IP blocking.

### Fast Flux Technique

- **DNS Technique:** Used by botnets to hide malicious activities behind compromised hosts.
- **Purpose:** Concealing communication between malware and its command server.
- **Dynamic IP Association:** Multiple changing IPs associated with a domain name.
- **Akamai's Definition:** Fast Flux makes malware communication hard to detect.
- **Example:** Palo Alto's fictional scenario explains Fast Flux's resilience.


## Understanding Domain Names and Their Role in Cybersecurity

In this section, we explore the significance of domain names in the context of cybersecurity. Let's break down the key points:

### Domain Names - Simplified

- **Mapping to IP Addresses:** Domain names link to IP addresses, allowing users to access websites using text-based URLs. 
- **Structure:** Domain names can consist of a domain and top-level domain (e.g., evilcorp.com) or sub-domain, domain, and top-level domain (e.g., tryhackme.evilcorp.com).
- **Impact on Attackers and Defenders:** Changing domain names can be more cumbersome for attackers, involving purchasing, registering, and modifying DNS records. However, some loose standards and APIs make it easier for attackers to manipulate domains.

Although it can be harder for attackers to deal with Domain Names seeing that they would have to purchase, register, and modify a domain and its DNS records, DNS providers still provide APIs, which make it easier for attackers to change domains. 

### Punycode Attacks

**Punycode**

  - A method to encode non-ASCII characters into ASCII-compatible format.  
  - Its main purpose is to try and deceipt the human eye (obfuscation)
  - i.e. `adıdas.de` has a Punycode of `http://xn--addas-o4a.de/`

**Punycode Attacks**

  - Attackers use Punycode to create URLs that look legitimate but redirect users to malicious domains.

**Detection**

  - Modern browsers can translate obfuscated characters into Punycode, helping users identify such attacks.

**Malicious URL Shorteners**

  - Attackers hide malicious domains behind URL shortening services like bit.ly, goo.gl, etc.

**Detecting Malicious URLs**

  - Proxy logs or web server logs can help identify connections to malicious domains.
  - Examples of **URL Shortening services**:
    - bit.ly
    - goo.gl
    - ow.ly
    - s.id
    - smarturl.it
    - tiny.pl
    - tinyurl.com
    - x.co

### Analyzing Connections in Any.run

**Any.run Sandbox:** 

- Analyzing samples by executing them in a controlled environment.
  
**Monitoring Connections:**

- Any.run provides insight into HTTP requests, DNS requests, and communication processes.

**HTTP Requests:** 

- Shows resources retrieved from a webserver, like droppers or callbacks.

**Connections:** 

- Reveals communications between processes, such as C2 (Command and Control) traffic or file transfers.


**DNS Requests:** 

- Displays DNS requests made by malware to check internet connectivity.

Remember, these insights help defenders better understand the tactics attackers use, empowering us to stay vigilant and proactive in the ever-evolving landscape of cybersecurity.
