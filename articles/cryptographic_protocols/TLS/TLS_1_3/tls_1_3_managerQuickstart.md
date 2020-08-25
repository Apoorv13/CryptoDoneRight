---
layout: quickstart
title: "Manager's QuickStart"
type: TLS 1.3
qtype: manager
image: /static_files/common/NewDevLogo.png
note: "A guide to adoption and use of TLSv1.3 in your projects and organization."
col: col-md-8 col-sm-8 col-xs-8 infoBlocks
best-practices:
  - name: "Use Strong Key Exchange"
    description: "For the key exchange, public sites can typically choose between the classic ephemeral Diffie-Hellman key exchange (DHE) and its elliptic curve variant, ECDHE. There are other key exchange algorithms, but they're generally insecure in one way or another. The RSA key exchange is still very popular, but it doesn't provide forward secrecy."
  - name: "Disable Compression"
    description: "TLS compression should be disabled in order to protect against a vulnerability (nicknamed CRIME) which could potentially allow sensitive information such as session cookies to be recovered by an attacker"
  - name: "Only Support Strong Ciphers"
    description: "There are a large number of different ciphers (or cipher suites) that are supported by TLS, that provide varying levels of security. Where possible, only GCM ciphers should be enabled. However, if it is necessary to support legacy clients, then other ciphers may be required. At a minimum, the following types of ciphers should always be disabled: Null ciphers, Anonymous ciphers, EXPORT ciphers"
---

Hi there! This page is currently under construction. If you would like to share your expertise relating to this topic with us , please <a href="CONTRIBUTING-template.md">click here!</a>

<img src="/static_files/common/under_construction.jpg" style="width:70%;height:70%;" alt="under construction image">
