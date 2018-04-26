---
title: "URL Property (RDS)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 722765dc-f89c-0131-73b1-69c56a795546

---

# URL Property (RDS)

Indicates a string that contains a relative or absolute URL.
  
You can set the **URL** property at design time in the [DataControl](datacontrol-object-rds.md) object's OBJECT tag, or at run time in scripting code. 
  
## Syntax

Design time:  `<PARAM NAME="URL" VALUE="Server">`
  
Run time:  `DataControl.URL="Server"`
  
## Parameters

-  *Server* 
    
- A **String** value that contains a valid URL. 
    
-  *DataControl* 
    
- An object variable that represents a **DataControl** object. 
    
## Remarks

Typically, the URL identifies an Active Server Page (.asp) file that can produce and return a [Recordset](recordset-object-ado.md). Therefore, the user can obtain a **Recordset** without having to invoke the server-side [DataFactory](datafactory-object-rdsserver.md) object, or program a custom business object. 
  
If the **URL** property has been set, [SubmitChanges](submitchanges-method-rds.md) will submit changes to the location specified by the URL. 
  

