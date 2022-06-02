---
title: "Writing Form Server Code"
description: Outlines how to write form server code in Outlook 2013 and Outlook 2016, with additional reference materials.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: ff33badc-ceed-4364-b99c-8af3af83ceb6
 
 
---

# Writing Form Server Code

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
You can think of a form server as the following: 
  
- A Win32 program that displays an interface and handles windows messages by way of the standard Windows message pump mechanisms.
    
- An object that registers its class factory with OLE and is activated by OLE automation methods.
    
- A MAPI object that follows the MAPI rules for interactions with other MAPI components.
    
 Your code has to handle all three of those broad requirements simultaneously. 
  
See the COM and ActiveX Object Services section in the Windows SDK for details about registering your form server's class factory. Handling windows messages and displaying an interface are standard Windows programming techniques that do not have any special requirements with respect to MAPI forms. Again, the Windows SDK has details about Windows programming. This document contains what you need to know to implement the required and optional MAPI form interfaces so that they follow the MAPI rules for interactions with other MAPI components — primarily the MAPI form manager and messaging client applications.
  
All of the interfaces that you can use when you implement form servers are derived — either directly or indirectly — from the OLE base class [IUnknown](https://msdn.microsoft.com/library/33f1d79a-33fc-4ce5-a372-e08bda378332%28Office.15%29.aspx). This means that all your implementations of these interfaces will need to have **QueryInterface**, **AddRef**, and **Release** methods. You can save yourself a lot of work if you use multiple inheritance to implement all of the required interfaces in one new class of your own, so that all the interfaces you use can share a single implementation of the required **IUnknown** methods. For more information, see the [IUnknown::AddRef](https://msdn.microsoft.com/library/b4316efd-73d4-4995-b898-8025a316ba63%28Office.15%29.aspx), [IUnknown::QueryInterface](https://msdn.microsoft.com/library/54d5ff80-18db-43f2-b636-f93ac053146d%28Office.15%29.aspx), and [IUnknown::Release](https://msdn.microsoft.com/library/4b494c6f-f0ee-4c35-ae45-ed956f40dc7a%28Office.15%29.aspx) methods. There are no special considerations with respect to MAPI form servers for these methods. 
  
While not all of the MAPI form interfaces are mandatory for all form servers, the methods in any given interface are mandatory. That is, if you choose to implement a particular interface, you must implement all of the methods in the interface. This is different from the situation with some other MAPI components, such as message transports. Fortunately, the methods in the MAPI form interfaces are relatively straightforward, so implementing all of them does not put a great burden on developers.
  
The MAPI form interfaces are independent of the type of development tool used to create a form server. This allows forms to be created by using different development tools. The only requirement is that all form servers must support the required MAPI form interfaces.
  
Not all of the MAPI interfaces that relate to forms are required by all form servers. The optional interfaces allow you to implement some advanced form functions that are not needed by most form servers. The following table lists the interfaces, what they are for, and whether you must implement them.
  
|**Interface**|**Description**|**Status**|
|:-----|:-----|:-----|
|[IMAPIForm : IUnknown](imapiformiunknown.md) <br/> |The primary interface that clients use to load form servers, execute form verbs, and shut down form servers. This is also the interface derived from the OLE **IUnknown** that is used to inform other OLE components regarding what interfaces a form object implements. |Required  <br/> |
|[IPersistMessage : IUnknown](ipersistmessageiunknown.md) <br/> |Used when loading messages into and saving messages from form objects. |Required  <br/> |
|[IMAPIFormAdviseSink : IUnknown](imapiformadvisesinkiunknown.md) <br/> |Used by form objects to keep track of messaging client status and to find out whether the form object is capable of displaying the next or previous message in a folder. |Optional  <br/> |
|[IClassFactory](https://msdn.microsoft.com/library/f624f833-2b69-43bc-92cd-c4ecbe6051c5%28Office.15%29.aspx) <br/> |The OLE class factory interface used by form objects for compliance with the OLE class factory mechanism. |Required  <br/> |
|[IMAPIFormFactory : IUnknown](imapiformfactoryiunknown.md) <br/> |Used if your form server supports more than one type of form. In this case, the **IMAPIFormFactory** interface allows client applications to access the multiple **IClassFactory** interfaces (one per type of form that your form server supports) that your form server must also implement. |Optional  <br/> |
   
## See also



[Developing MAPI Form Servers](developing-mapi-form-servers.md)

