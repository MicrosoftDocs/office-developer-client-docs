---
title: "ParentURL Property (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: ec7ec476-6f9e-8486-fe02-74995975df5c

---

# ParentURL Property (ADO)

Indicates an absolute URL string that points to the parent [Record](record-object-ado.md) of the current **Record** object. 
  
## Return Value

Returns a **String** value that indicates the URL of the parent **Record**. 
  
## Remarks

The **ParentURL** property depends upon the source used to open the **Record** object. For example, the **Record** may be opened with a source containing a relative path name of a directory referenced by the [ActiveConnection](activeconnection-property-ado.md) property. 
  
Suppose "second" is a folder contained under "first". Open the **Record** object with the following: 
  
```
record.ActiveConnection = "http://first"
record.Open "second"

```

Now, the value of  `the` **ParentURL** property is **ParentURL** property is  `"http://first"`, the same as **ActiveConnection**. 
  
The source may also be an absolute URL such as,  `"http://first/second"`. The **ParentURL** property is then  `"http://first"`, the level above . The **ParentURL** property is then  `"http://first"`, the level above  `"second"`.
  
This property may be a null value if:
  
- There is no parent for the current object; for example, if the **Record** object represents the root of a directory. 
    
- The **Record** object represents an entity that cannot be specified with a URL. 
    
This property is read-only.
  
> [!NOTE]
> This property is only supported by document source providers, such as the [Microsoft OLE DB Provider for Internet Publishing](microsoft-ole-db-provider-for-internet-publishing.md). For more information, see [Records and Provider-Supplied Fields](records-and-provider-supplied-fields.md). 
  
> [!NOTE]
> URLs using the http scheme will automatically invoke the [Microsoft OLE DB Provider for Internet Publishing](microsoft-ole-db-provider-for-internet-publishing.md). For more information, see [Absolute and Relative URLs](absolute-and-relative-urls.md). 
  
> [!NOTE]
> If the current record contains a data record from an ADO **Recordset**, accessing the **ParentURL** property causes a run-time error, indicating that no URL is possible. 
  

