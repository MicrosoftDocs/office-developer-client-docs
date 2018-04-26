---
title: "Microsoft OLE DB Provider for Internet Publishing"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: overview
  
localization_priority: Normal
ms.assetid: 5d1e8db5-dabb-0914-e11e-e2eac72bfa77
description: "The Microsoft OLE DB Provider for Internet Publishing allows ADO to access resources served by Microsoft FrontPage or Microsoft Internet Information Server. Resources include web source files such as HTML files, or Windows 2000 web folders."
---

# Microsoft OLE DB Provider for Internet Publishing

The Microsoft OLE DB Provider for Internet Publishing allows ADO to access resources served by Microsoft FrontPage or Microsoft Internet Information Server. Resources include web source files such as HTML files, or Windows 2000 web folders.
  
## Connection String Parameters

To connect to this provider, set the  *Provider*  argument of the [ConnectionString](connectionstring-property-ado.md) property to: 
  
```
 
MSDAIPP.DSO 

```

This value can also be set or read using the [Provider](provider-property-ado.md) property. 
  
## Typical Connection String

A typical connection string for this provider is:
  
```
 
"Provider=MSDAIPP.DSO;Data Source=ResourceURL ;User ID=userName ;Password=userPassword ;" 

```

-or-
  
```
 
"URL=ResourceURL ;User ID=userName ;Password=userPassword ;" 

```

The string consists of these keywords:
  
|**Keyword**|**Description**|
|:-----|:-----|
|**Provider** <br/> |Specifies the OLE DB Provider for Internet Publishing.  <br/> |
|**Data Source** -or- **URL** <br/> |Specifies the URL of a file or directory published in a Web Folder.  <br/> |
|**User ID** <br/> |Specifies the user name.  <br/> |
|**Password** <br/> |Specifies the user password.  <br/> |
   
If you set the  *ResourceURL*  value from the "URL=" in the connection string to an invalid value, by default the Internet Publishing Provider raises a dialog box to prompt for a valid value. This is undesirable behavior for a component in the middle tier of an application, because it suspends program execution until the dialog box is cleared and the client appears to freeze because it has not received a response from the component. 
  
> [!NOTE]
> If MSDAIPP.DSO is explicitly specified as the value of the provider, either with the  *Provider*  connection string keyword or the **Provider** property, you cannot use "URL=" in the connection string. If you do, an error will occur. Instead, simply specify the URL as shown in the topic [Using ADO with the OLE DB Provider for Internet Publishing](the-ole-db-provider-for-internet-publishing.md). 
  

