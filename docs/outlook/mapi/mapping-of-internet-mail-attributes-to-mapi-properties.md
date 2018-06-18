---
title: "Mapping of Internet Mail Attributes to MAPI Properties"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 79d1d2ba-34fe-4851-918f-adbc69c20eee
description: "Last modified: July 23, 2011"
 
 
---

# Mapping of Internet Mail Attributes to MAPI Properties

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
This appendix describes how a MAPI transport provider or MAPI-aware gateway which connects to the Internet should translate between MAPI message properties and Simple Mail Transport Protocol (SMTP) message attributes. SMTP is the messaging protocol used on much of the Internet. SMTP defines a set of message headers — the message envelope — and a message content format. SMTP is fully documented in a set of two documents, RFC 821 and RFC 822, which can be found at a number of FTP and WWW sites on the Internet.
  
For information on the SMTP protocol used to communicate with SMTP-based mail agents, see RFC 821, "Simple Mail Transfer Protocol," at [http://www.rfc-editor.org](http://www.rfc-editor.org).
  
For addressing and standard message headers, see RFC 822, "Standard for the Format of ARPA Internet Text Messages," at [http://www.rfc-editor.org](http://www.rfc-editor.org).
  
For MIME, see RFC 1521, "MIME (Multipurpose Internet Mail Extensions) Part One: Mechanisms for Specifying and Describing the Format of Internet Message Bodies," at [http://www.rfc-editor.org](http://www.rfc-editor.org).
  
The goal of mapping SMTP message attributes to MAPI properties (and vice versa) is to ensure that the full content of MAPI messages, over and above that which can be encoded using native SMTP message attributes, can be reliably exchanged among different MAPI components that must communicate over the Internet. This document is based on work already done on such components at Microsoft. 
  
This document assumes familiarity with MAPI transports, TNEF, and SMTP mail. It strives to be concise rather than abundantly clear.
  
As a convention, "outbound" refers to mail traveling from a MAPI-compliant UA or MTA to the Internet, and "inbound" refers to mail traveling from the Internet to a MAPI component.
  

