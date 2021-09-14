---
title: "About the MAPI-MIME Conversion API"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: ffdfdff8-985d-35de-73b1-c34e1932cb9f
description: "Last modified: July 23, 2011"
 
 
---

# About the MAPI-MIME Conversion API

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The MAPI-MIME Conversion API allows mail providers to convert between MIME objects and MAPI messages. It provides constant definitions, class identifiers, and interface identifiers as shown in [MAPI Constants](mapi-constants.md). Mail providers must cocreate an instance of **[IConverterSession](iconvertersessioniunknown.md)** by calling the **CoCreateInstance** function. 
  

