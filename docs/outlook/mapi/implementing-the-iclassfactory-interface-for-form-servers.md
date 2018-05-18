---
title: "Implementing the IClassFactory Interface for Form Servers"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 22402261-c0fc-49bd-a222-e31989d6ff30
description: "Last modified: March 09, 2015"
 
 
---

# Implementing the IClassFactory Interface for Form Servers

  
  
**Applies to**: Outlook 
  
[IClassFactory](http://msdn.microsoft.com/en-us/library/ms694364%28VS.85%29.aspx) is the OLE interface that client applications use to create new form objects of your form server's message class. The following table lists the **IClassFactory** methods that are required. 
  
|**Method**|**Description**|
|:-----|:-----|
|[CreateInstance](http://msdn.microsoft.com/en-us/library/ms682215%28v=VS.85%29.aspx) <br/> |Creates a new form object.  <br/> |
|[LockServer](http://msdn.microsoft.com/en-us/library/ms682332%28v=VS.85%29.aspx) <br/> |Locks the form server in memory so that startup overhead can be avoided when multiple form objects are created.  <br/> |
   
For all the information necessary to implement these methods, see the COM and ActiveX Object Services section in the Windows SDK.
  
## See also



[Writing Form Server Code](writing-form-server-code.md)

