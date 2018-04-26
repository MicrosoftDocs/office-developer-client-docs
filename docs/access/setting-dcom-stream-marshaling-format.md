---
title: "Setting DCOM Stream Marshaling Format"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
  
localization_priority: Normal
ms.assetid: 5f75fc59-a9f8-6686-07f9-de292e4da787
description: "A client computer using components from RDS 1.5 or earlier is not compatible with a server using components from RDS 2.0 or later. When using DCOM as the underlying protocol, the support for RDS 2.0 or later is more efficient in transporting Recordset objects. If your client is running components from RDS 1.5 or earlier, you can set your server to work with the previous RDS support (called RDS 1.0) or the newer RDS support (called RDS 2.0 or later). Set either of the following registry entries:"
---

# Setting DCOM Stream Marshaling Format

A client computer using components from RDS 1.5 or earlier is not compatible with a server using components from RDS 2.0 or later. When using DCOM as the underlying protocol, the support for RDS 2.0 or later is more efficient in transporting [Recordset](recordset-object-ado.md) objects. If your client is running components from RDS 1.5 or earlier, you can set your server to work with the previous RDS support (called RDS 1.0) or the newer RDS support (called RDS 2.0 or later). Set either of the following registry entries: 
  
```
 
[HKEY_CLASSES_ROOT] 
\CLSID 
 \[58ECEE30-E715-11CF-B0E3-00AA003F000F} 
 \ADTGOptions]"MarshalFormat"="RDS10" 

```

-or-
  
```
 
[HKEY_CLASSES_ROOT] 
\CLSID 
 \[58ECEE30-E715-11CF-B0E3-00AA003F000F} 
 \ADTGOptions]"MarshalFormat"="RDS20" 

```


