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
1. CBC MAC (Cyclic Block Redundancy Message Authentication Code)
CBC MAC is based on a pseudorandom function working similarly to encryption performed in the CBC mode, with a difference that intermediate values not being returned. Additionally, after encryption of the last data block, an additional encryption of the current result is performed using the second secret key.
![CBCMAC](https://upload.wikimedia.org/wikipedia/commons/thumb/b/bf/CBC-MAC_structure_%28en%29.svg/2880px-CBC-MAC_structure_%28en%29.svg.png "CBC-MAC Scheme")

CBC MAC can protect a message consisting of any length, spanning over multiple blocks. To ensure security, while using *CBC MAC one should change the secret periodically*. 
Note: It can be proved that after sending the number of messages that is equal roughly to the square of the number of all possible values of data blocks, the key is no longer safe.
ECBC MAC is used in various applications, for example in banking systems (ANSI X9.9, X9.19 and FIPS 186-3 standards). It is often based on the AES algorithm, that is used as F function.

2. NMAC (Nested MAC)
Although fundamentally similar to the CBC-MAC which we talked about, NMAC uses a slightly different pseudorandom function F returning numbers that are correct values of secret keys and not of the data blocks.
![NMAC] (http://www.crypto-it.net/Images/theory/mac/nmac_eng.png "N-MAC")