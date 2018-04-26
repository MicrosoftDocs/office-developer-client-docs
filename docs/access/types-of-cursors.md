---
title: "Types of Cursors"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 589f3755-3cf5-9470-bd66-8e8afa218fc5
description: "As a general rule, your application should use the simplest cursor that provides the required data access. Each additional cursor characteristic beyond the basics (forward-only, read-only, static, scrolling, unbuffered) has a price — in client memory, network load, or performance. In many cases, the default cursor options generate a more complex cursor than your application actually needs."
---

# Types of Cursors

As a general rule, your application should use the simplest cursor that provides the required data access. Each additional cursor characteristic beyond the basics (forward-only, read-only, static, scrolling, unbuffered) has a price — in client memory, network load, or performance. In many cases, the default cursor options generate a more complex cursor than your application actually needs.
  
Your choice of cursor type depends on how your application uses the result set and also on several design considerations, including the size of the result set, the percentage of the data likely to be used, sensitivity to data changes, and application performance requirements.
  
At its most basic, your cursor choice depends on whether you need to change or simply view the data:
  
- If you just need to scroll through a set of results, but not change data, use a [forward-only](forward-only-cursors.md) or [static](static-cursors.md) cursor. 
    
- If you have a large result set and need to select just a few rows, use a [keyset](keyset-cursors.md) cursor. 
    
- If you want to synchronize a result set with recent adds, changes, and deletes by all concurrent users, use a [dynamic](dynamic-cursors.md) cursor. 
    
Although each cursor type seems to be distinct, keep in mind that these cursor types are not so much different varieties as simply the result of overlapping characteristics and options.
  

