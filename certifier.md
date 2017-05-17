---
layout: home
---


Certifier Implementation Guide
========================

This document, while not a formal RFC, should serve as a guide for implementors
of future NETCDL Certifier Software.
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",
"SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in [RFC2119](https://www.ietf.org/rfc/rfc2119.txt).

A NETCDL certifier MUST recognize and parse a body of text that conforms to the official NETCDL grammar specification.
If a parse error occurs, the certifier SHOULD inform the user the cause of the error, so that they may fix it.

During certification the certifier SHALL evaluate every assertion in the input document. 
The certifier MAY carry out the assertions in any order.
The certifier SHOULD attempt to minimize the total assertion time, or the performance impact on the network, according to user preferences.

After certification activities have completed, the certifier SHALL provide the user with a report of certification, by some means.
The report MUST show overall success, where greater than zero failures results in failed certification, and zero failures results in passed certification.
The report SHOULD indicate to the user the cause of the failures.
After certification activities have completed, the software SHOULD release any resources acquired, such as DHCP leases, 
slots on bandwidth limited servers, and other such limited resources. 

Certifiers MAY provide a graphical user interface for the user. 
Certifiers MAY be loaded onto dedicated hardware platforms that carry out certification functions.

Certifier implementations MAY be proprietary in nature. 
