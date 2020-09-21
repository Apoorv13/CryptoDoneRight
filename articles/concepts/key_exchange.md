---
layout: page1
title: Key Exchange Concepts
type: concepts
update: Last Updated Mon,  24 Aug 2020 21:07:22 +0000
permalink: "articles/concepts/key_exchange.html"
alerts:

further-reading:

related-articles:

warnings:
  - name: Never Use ECB.
    description: "Do NOT use the Electronic Code Book (ECB) mode of operation. This is only for testing!"

best_practices:
  - name: Use combined modes of operation.
    description: "Combined modes of operation both encrypt the data and protect it from modifications. Modes, such as GCM or CCM, are almost always a good choice."

---

#### Introduction: Key Exchange