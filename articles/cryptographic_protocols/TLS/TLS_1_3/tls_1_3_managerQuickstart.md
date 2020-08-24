---
layout: quickstart
title: "Manager's QuickStart"
type: TLS 1.3
qtype: manager
image: /static_files/common/NewDevLogo.png
note: "A guide to adoption and use of TLSv1.3 in your projects and organization."
col: col-md-8 col-sm-8 col-xs-8 infoBlocks
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

Hi there! This page is currently under construction. If you would like to share your expertise relating to this topic with us , please <a href="CONTRIBUTING-template.md">click here!</a>

<img src="/static_files/common/under_construction.jpg" style="width:70%;height:70%;" alt="under construction image">
