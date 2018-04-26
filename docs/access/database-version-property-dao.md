---
title: "Database.Version Property (DAO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 40faaa0c-e764-e968-f606-7e06ded80c3f
description: "In a Microsoft Access workspace, returns the vesion of the Microsoft Jet or Microsoft Access database engine that created the database. Read-only String ."
---

# Database.Version Property (DAO)

In a Microsoft Access workspace, returns the vesion of the Microsoft Jet or Microsoft Access database engine that created the database. Read-only **String**. 
  
## Syntax

 *expression*  . **Version**
  
 *expression*  A variable that represents a **Database** object. 
  
## Remarks

The return value is a String that evaluates to a version number, formatted as follows.
  
- Microsoft Access workspace represents the version number in the form " *major.minor*  ". For example, "3.0". The product version number consists of the version number (3), a period, and the release number (0). 
    
The following table shows which version of the database engine was included with various versions of Microsoft products.
  
|**Database Engine**|**Version (year released)**|**Microsoft Access**|**Microsoft Visual Basic**|**Microsoft Excel**|**Microsoft Visual C++**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|Microsoft Jet  <br/> |1.0 (1992)  <br/> |1.0  <br/> |N/A  <br/> |N/A  <br/> |N/A  <br/> |
|Microsoft Jet  <br/> |1.1 (1993)  <br/> |1.1  <br/> |3.0  <br/> |N/A  <br/> |N/A  <br/> |
|Microsoft Jet  <br/> |2.0 (1994)  <br/> |2.0  <br/> |N/A  <br/> |N/A  <br/> |N/A  <br/> |
|Microsoft Jet  <br/> |2.5 (1995)  <br/> |N/A  <br/> |4.0 (16-bit)  <br/> |N/A  <br/> |N/A  <br/> |
|Microsoft Jet  <br/> |3.0 (1995)  <br/> |'95 (7.0)  <br/> |4.0 (32-bit)  <br/> |'95 (7.0)  <br/> |4.x  <br/> |
|Microsoft Jet  <br/> |3.5 (1996)  <br/> |'97 (8.0)  <br/> |5.0  <br/> |'97 (8.0)  <br/> |5.0  <br/> |
|Microsoft Jet  <br/> |4.0 (2000)  <br/> |2000 (9.0)  <br/> ||2000 (9.0)  <br/> ||
|Microsoft Access database engine  <br/> |12.0 (2007)  <br/> |2007  <br/> ||||
   

