---
layout: page
title: Certificates
type: infrastructure
update: Last Updated Thu, 12 Dec 2018 12:00:01 -0400
permalink: "articles/infrastructure/Certificates/Certificates.html"
alerts:

further-reading:

related-articles:

warnings:

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
A digital certificate, or just "certificate," is a combination of three basic components: an asymmetric public key, metadata related to the key (including an identity associated with the key's owner), and a digital signature over the rest of the data. The signature must come from the public key of the "Certificate Authority" (CA) that signs (issues) the certificate. In cryptography, a certificate is used for one party to determine that another party is who they claim to be. 

In an idealized and simplified example, a browser connects to "https://example.com" and the webserver responds. The webserver is claiming to be "example.com" but the browser needs to verify this and make sure that the response is not from an imposter. To prove its identity, the webserver sends a certificate to the browser that includes the name "example.com", a public key, and a signature from a certificate authority (CA). The browser must already have another certificate for the CA stored internally. Using the CA's public key (from its certificate), the browser verifies the signature on the certificate for "example.com" to prove that it was issued by the CA.

As a final step, the browser and the webserver engage in a handshake in which the webserver proves that it has the private key associated with the certificate. Now the browser "knows" that a trusted third party (the CA) has approved the webserver to claim the identity "example.com."

In actuality, this description is over-simplified and there are a number of ways for imposters to try and fool the system. The quick-start guides provide more details about the types of protections and policies that are necessary for certificates to be used correctly.