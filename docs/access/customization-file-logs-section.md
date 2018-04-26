---
title: "Customization File Logs Section"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: de331a97-c9cd-5f02-692b-d7afd9e9342a
description: "The logs section contains a log file entry, which specifies the name of a file that records errors during the operation of the DataFactory ."
---

# Customization File Logs Section

The **logs** section contains a log file entry, which specifies the name of a file that records errors during the operation of the **DataFactory**. 
  
## Syntax

A log file entry is of the form:
  
```
err=FileName
```

|**Part**|**Description**|
|:-----|:-----|
|**err** <br/> |A literal string that indicates this is a log file entry.  <br/> |
| *FileName*  <br/> |A complete path and file name. The typical file name is **c:\msdfmap.log**.  <br/> |
   
The log file will contain the user name, HRESULT, date, and time of each error.
  

