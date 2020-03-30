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
  - name: HMAC is generally one of the most widely implemented hash algorithm which constructs message authentication code from hash function.
    description: Although it is proven it's reliability, HMAC is not one of the fastest mechanism out there
  - name: Lately, MAC algorithms such as GMAC, VMAC and CMAC are implemented at production environments, attributing it's speed as one of the key factors.
    description: 
  

---
The aim of a message authentication code is to prevent an adversary from modifying a message sent by one party to another, without the parties detecting that a modification has been made. As in the case of encryption, such a task is only possible if the communicating parties have some secret that the adversary does not know (otherwise nothing can prevent an adversary from impersonating the party sending the message). The setting that we consider here therefore assumes that the parties share the same secret key. Since the parties share the same key, the notion of a message authentication code belongs to the world of private-key cryptography.

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

3. CMAC
The CMAC algorithm is similar to CBC MAC in a way that it uses the same pseudorandom function F, which returns numbers that are elements of the set of all possible values of data blocks. However,instead of the last additional encryption that uses a second key, CMAC uses two additional keys that are added to input bits to the last block of F function. Depending on whether the last message block is completely filled up with data bits, or it must be filled up with a previously determined sequence of padding characters, the corresponding encryption key should be used. CMAC is considered to be secure providing a safe way for message authentication. 
![CMAC] (http://www.crypto-it.net/Images/theory/mac/cmac_eng.png)

4. HMAC
HMAC is a popular system of checking message integrity quite similar to NMAC. It uses one-way hash functions to produce unique mac values.
The way in which it functions is as follows:
The input parameters *ipad* and *opad* are used to modify the secret key. It is recommended to choose the values that would make both inputs to the hash functions look as dissimilar as possible (that is, that modify the secret key in two different ways).
Using a secure hash function guarantees the security of the HMAC algorithm.
Uses of HMAC : SSL, IPSec, SSH etc
![HMAC] (http://www.crypto-it.net/Images/theory/mac/hmac_eng.png)


Additional Reading: 
https://crypto.stackexchange.com/questions/52009/fastest-algorithm-for-message-authentication
