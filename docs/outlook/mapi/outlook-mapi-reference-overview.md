---
title: "Outlook MAPI Reference Overview"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 4c126d0c-d7c0-45c0-801c-c9f1e44c9db6
description: "Last modified: February 01, 2013"
---

# Outlook MAPI Reference Overview

**Applies to**: Outlook 2013 | Outlook 2016 
  
This topic provides overview information about the Outlook 2013 MAPI Reference documentation.
  
## About this documentation

This documentation applies to the implementation of the Messaging API (MAPI) in Microsoft Outlook 2013. 
  
Previous to Microsoft Office Outlook 2007, the MAPI Programmer's Reference was part of the Microsoft Exchange documentation.
  
> [!NOTE]
> Because Exchange has deemphasized the use of MAPI since Microsoft Exchange Server 2007, support for the Exchange implementation is limited. 
  
The Outlook implementation of MAPI differs from the Microsoft Exchange implementation. The Outlook implementation is optimized for running on client computers and emphasizes low latency. The Exchange implementation is intended for servers where high availability and better multithreading are important.
  
Use this documentation for applications running on end-user systems. For server applications, use the Exchange implementation of MAPI if appropriate, or use current Exchange APIs such as Exchange Web Services. For more information on Exchange Web Services, see the [Exchange Web Services Reference](http://msdn.microsoft.com/en-us/library/bb204119.aspx).
  
It may be possible to write applications that work with either the Outlook or Exchange implementations of MAPI. For example, MFCMAPI works well on either platform. The implementations have many common features, but there are differences both obvious and subtle. You will have to test carefully on both platforms if you intend for your application to work in all environments. This testing will require two systems because running both implementations on the same operating system installation is not supported.
  
Be aware that MAPI is appropriate for low-level access to data in a MAPI store or for building a transport, message store, or address book provider. Because MAPI bypasses Outlook's business logic, you should also consider the use of the Outlook object model when you evaluate APIs for building your solution. The Outlook object model does encapsulate Outlook business logic but is not suitable for multithreaded code, sync providers, or Windows Service applications.
  
For information about what is new in this edition, see the following topics:
  
- [What's New in This Edition](what-s-new-in-this-edition.md)
    
- [API Elements Deprecated in This Edition](api-elements-deprecated-in-this-edition.md)
    
If you are new to developing MAPI applications for Outlook, see the following topics:
  
- [Selecting an API or technology for developing solutions for Outlook 2013](http://msdn.microsoft.com/en-us/library/jj900714.aspx)
    
- [Commonly Used Header Files](commonly-used-header-files.md)
    
- [Commonly Used Properties](commonly-used-properties.md)
    
- [Commonly Used Objects](commonly-used-objects.md)
    
The rest of this reference is categorized into the following three types of information:
  
- [MAPI Samples](mapi-samples.md) - Directs you to many code samples that show the use of various API elements and how to implement basic MAPI providers and create Outlook items. 
    
- [MAPI Concepts](mapi-concepts.md) - Explains the concepts and architecture of MAPI. 
    
- [MAPI Reference](mapi-reference.md) - Provides detailed information about the functions, interfaces, structures, and properties in MAPI. 
    
## See also

- [Getting Started with the Outlook MAPI Reference](getting-started-with-the-outlook-mapi-reference.md)
- [MAPI Samples](mapi-samples.md)
- [MAPI Concepts](mapi-concepts.md)

