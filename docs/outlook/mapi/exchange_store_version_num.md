---
title: "EXCHANGE_STORE_VERSION_NUM"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 88950eda-85ae-ad7a-46c6-0e1933d35e04
description: "Last modified: July 23, 2011"
---

# EXCHANGE_STORE_VERSION_NUM

  
  
**Applies to**: Outlook 
  
Stores version information for the Microsoft Exchange Server that accounts in a Microsoft Office Outlook profile are connected to.
  
## Quick Info

```cpp
typedef struct { 
    WORD wMajorVersion; 
    WORD wMinorVersion; 
    WORD wBuild; 
    WORD wMinorBuild; 
} EXCHANGE_STORE_VERSION_NUM; 

```

## Members

 _wMajorVersion_
  
- Major version number that is generally incremented when a release contains significant new features and changes in functionality.
    
 _wMinorVersion_
  
- Minor version number that corresponds to a specific major version number and that is generally incremented when a release contains minor new features or significant fixes.
    
 _wBuild_
  
- Major build number that corresponds to specific major and minor version numbers and that is generally incremented in an internal release that contains new features or fixes. This value is also incremented when the release is a major internal code branch or milestone, such as a release candidate.
    
 _wMinorBuild_
  
- Minor build number that is generally incremented in an internal release that contains new features or fixes corresponding to a specific major build that denotes a major code branch or milestone.
    
## See also

#### Concepts

[About MAPI Additions](about-mapi-additions.md)
  
[PidTagProfileServerFullVersion Canonical Property](pidtagprofileserverfullversion-canonical-property.md)

