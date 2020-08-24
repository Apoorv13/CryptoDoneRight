---
layout: page
title: TLS 1.3
type: cryptographic_protocols
update: Last Updated Tue,  7 Jan 2020 18:05:12 +00000
permalink: "articles/cryptographic_protocols/tls/tls_1_3.html"
alerts:
  - id: 1
    type: success
    description: This is the LATEST and RECOMMENDED Version of TLS. However, TLS 1.2 can also still be used for legacy support.
    link: ""
  - id: 2
    type: danger
    description: TLSv1.3 is still a fairly new protocol. Check back regularly for updates about potential issues.
    link: ""
  - id: 3
    type: danger
    description: ETS or eTLS is an artificially weakened version of TLS 1.3 and SHOULD NOT BE USED.
    link: "https://www.eff.org/deeplinks/2019/02/ets-isnt-tls-and-you-shouldnt-use-it"

warnings:
  - name: Turn off 0-RTT
    description: "0-RTT, or the zero round trip functionality that was written into the TLSv1.3 specification could allow for replay attacks. It is recommended to disable this functionality. These security concerns are documented near the end of the RFC, but attacks have also been presented at conferences. See the Further Reading section for links."
  - name: Disable RSA key exchange in TLS 1.2
    description: "Although TLS 1.3 has mechanisms in place to prevent downgrade attacks, these mechanisms can be bypassed if the downgrade is to TLS 1.2 and the key exchange is performed with RSA encryption. If you are running TLS 1.2 alongside TLS 1.3 (this is common!), you must ensure that TLS 1.2 does not provide RSA key exchange as an option."
    link: "https://www.nccgroup.trust/us/about-us/newsroom-and-events/blog/2019/february/downgrade-attack-on-tls-1.3-and-vulnerabilities-in-major-tls-libraries/"

further-reading:
  - name: "RFC 8446: The Transport Layer Security (TLS) Protocol Version 1.3"
    link: "https://tools.ietf.org/html/rfc8446"
  - name: "TLSv1.3 0-RTT Vulnerabilites"
    link: "https://www.ssl.com/faqs/security-concerns-0-rtt-mode/"

best-practices:
  - name: Remove weak keys, cipher suites and hashes
    description: Certificates contain public keys and signatures which could be vulnerable to attacks. Certificates with key lengths less than 2048 bits or that use older hashing algorithms like MD5 or SHA-1 are no longer permitted on public web servers. However, you might find these on your internal websites. If so, it’s vital that you upgrade them.
  - name: Control wildcard certificate issuance and distribution
    description: There are some concerns to be aware of with wildcard certificates. For one, if the private key of a wildcard certificate is stolen, attackers can then impersonate any system within that domain space. Another concern is that, if the wildcard is compromised, then you have to revoke and reissue all copies of the certificate at all locations where it has been installed. The more copies you have, the greater the headache.
  - name: Deploy appropriate certificate types
    description: While private TLS certificates can be used for internal systems, the private root must be successfully propagated to users. If you are securing a public site, we recommend either an OV or EV certificate. DV certificates are never recommended for sites transacting sensitive information.
  - name: Ensure private keys arent used when certificates are renewed
    description: Reusing private keys increases the risk of those keys being compromised.
  - name: Use caa to prevent unauthorized certificate requests
    description: The purpose of this is to allow domain owners to declare which CAs are allowed to issue a certificate for their domain. CAA also provides a way to receive notifications in case someone requests a certificate from an unauthorized CA.
  - name: Check ct logs for rogue certificates
    description: Any public certificate not logged in a public Certificate Transparency (CT) log will not be trusted by browsers. You can use a CT monitor to detect rogue certificates— much like a credit report—to quickly identify and remediate rogue certificates.
---
TLSv1.3 is the latest version of the Transport Layer Security, or TLS, protocol. This protocol was designed for securing internet traffic and is typically seen in client/server architectures like connecting to a website from a browser. It was officially made a standard by the IETF in 2018 as an improvement upon TLSv1.2, providing many security and performance enhancements.

Filippo Valsorda had a great talk describing the major benefits of TLS 1.3 vs that of TLS 1.2. Many products, services, and companies have migrated to TLSv1.3 as it is the recommended version of the protocol. Implementations can be found in many major TLS stacks, but some are listed [here](https://github.com/tlswg/tlswg-wiki/blob/master/IMPLEMENTATIONS.md).

One particularly valuable improvement of TLS 1.3 over 1.2 is simplicity of configuration. At the time of this writing, there are only five cipher suites for TLS 1.3. Each cipher suite uses an authenticated encryption algorithm, so no separate MAC algorithm is required. This greatly reduces the burden on IT and development professionals to figure out which parameters are recommended.
