---
layout: page1
title: Message Authentication Codes
type: concepts
update: Last Updated Fri,  7 March 2020 17:18:43 +0000
permalink: "articles/concepts/mac.html"
alerts:

further-reading:

related-articles:

warnings:
  - name:
    description: 

best_practices:
  - name: 
    description:

---
Although we know that we can calculate hashes and verify the integrity of messages, have you ever wondered how is any message authenticated? This is a very real threat that existing cryptographic systems face. 
This threat occurs when the user is not sure about the originator of the message. As a result, message authentication can be provided using cryptographic techniques that use secret keys as done in case of encryption.

The aim of a message authentication code is to prevent an adversary from modifying a message sent by one party to another, without the parties de- tecting that a modification has been made. As in the case of encryption, such a task is only possible if the communicating parties have some secret that the adversary does not know (otherwise nothing can prevent an adversary from impersonating the party sending the message). The setting that we con- sider here therefore assumes that the parties share the same secret key. Since the parties share the same key, the notion of a message authentication code belongs to the world of private-key cryptography.

Loosely speaking, a message authentication code is an algorithm that is applied to a message. The output of the algorithm is a MAC tag (or just tag) that is sent along with the message. Security is formulated by requiring that no adversary can generate a valid MAC tag on any message that was not sent by the legitimate communicating parties.

#### Common types of MAC schemes
1. CBC MAC
CBC MAC is based on a pseudorandom function working similarly to encryption performed in the CBC mode, with a difference that intermediate values not being returned. Additionally, after encryption of the last data block, an additional encryption of the current result is performed using the second secret key.
![CBCMAC](https://upload.wikimedia.org/wikipedia/commons/thumb/b/bf/CBC-MAC_structure_%28en%29.svg/2880px-CBC-MAC_structure_%28en%29.svg.png "CBC-MAC Scheme")

