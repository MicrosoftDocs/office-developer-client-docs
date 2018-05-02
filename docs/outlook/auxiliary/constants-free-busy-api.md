---
title: "Constants (Free/busy API)"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
ms.assetid: ff756bf1-9395-5e50-4f55-1eb0365a84ed
description: "This topic contains constant definitions, class identifiers, and interface identifiers for the Free/Busy API."
 
 
---

# Constants (Free/busy API)

This topic contains constant definitions, class identifiers, and interface identifiers for the Free/Busy API.
  
## Constants

|**Constant**|**Definition**|
|:-----|:-----|
|E_NOTIMPL  <br/> | *As defined in the Microsoft Windows Software Development Kit (SDK) header file winerror.h.*  <br/> |
|E_OUTOFMEMORY  <br/> | *As defined in the Windows SDK header file winerror.h.*  <br/> |
|S_FALSE  <br/> | *As defined in the Windows SDK header file winerror.h.*  <br/> |
|S_OK  <br/> | *As defined in the Windows SDK header file winerror.h.*  <br/> |
   
## Interface Identifiers

For the following interface identifiers, assume the DEFINE_GUID macro defined in the Windows SDK header file guiddef.h to associate the GUID symbolic name with its value.
  
//{00067064-0000-0000-C000-000000000046}
  
DEFINE_GUID(IID_IEnumFBBlock, 0x00067064, 0x0, 0x0, 0xc0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x46);
  
//{00067066-0000-0000-C000-000000000046}
  
DEFINE_GUID(IID_IFreeBusyData, 0x00067066, 0x0, 0x0, 0xc0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x46);
  
//{00067067-0000-0000-C000-000000000046}
  
DEFINE_GUID(IID_IFreeBusySupport, 0x00067067, 0x0, 0x0, 0xc0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x46);
  

