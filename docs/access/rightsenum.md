---
title: "RightsEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 7647b9d5-5271-fdcf-489d-5a8beb931ca5

---

# RightsEnum

Specifies the rights or permissions for a group or user on an object.
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adRightCreate** <br/> |16384          (&amp;H4000)  <br/> |The user or group has permission to create new objects of this type.  <br/> |
|**adRightDelete** <br/> |65536          (&amp;H10000)  <br/> |The user or group has permission to delete data from an object. For objects such as **Tables**, the user has permission to delete data values from records.  <br/> |
|**adRightDrop** <br/> |256          (&amp;H100)  <br/> |The user or group has permission to remove objects from the catalog. For example, **Tables** can be deleted by a DROP TABLE SQL command.  <br/> |
|**adRightExclusive** <br/> |512          (&amp;H200)  <br/> |The user or group has permission to access the object exclusively.  <br/> |
|**adRightExecute** <br/> |536870912          (&amp;H20000000)  <br/> |The user or group has permission to execute the object.  <br/> |
|**adRightFull** <br/> |268435456          (&amp;H10000000)  <br/> |The user or group has all permissions on the object.  <br/> |
|**adRightInsert** <br/> |32768          (&amp;H8000)  <br/> |The user or group has permission to insert the object. For objects such as **Tables**, the user has permission to insert data into the table.  <br/> |
|**adRightMaximumAllowed** <br/> |33554432 (&amp;H2000000)  <br/> |The user or group has the maximum number of permissions allowed by the provider. Specific permissions are provider-dependent.  <br/> |
|**adRightNone** <br/> |0  <br/> |The user or group has no permissions for the object.  <br/> |
|**adRightRead** <br/> |-2147483648          (&amp;H80000000)  <br/> |The user or group has permission to read the object. For objects such as [Tables](table-object-adox.md), the user has permission to read the data in the table.  <br/> |
|**adRightReadDesign** <br/> |1024          (&amp;H400)  <br/> |The user or group has permission to read the design for the object.  <br/> |
|**adRightReadPermissions** <br/> |131072          (&amp;H20000)  <br/> |The user or group can view, but not change, the specific permissions for an object in the catalog.  <br/> |
|**adRightReference** <br/> |8192          (&amp;H2000)  <br/> |The user or group has permission to reference the object.  <br/> |
|**adRightUpdate** <br/> |1073741824          (&amp;H40000000)  <br/> |The user or group has permission to update the object. For objects such as **Tables**, the user has permission to update the data in the table.  <br/> |
|**adRightWithGrant** <br/> |4096          (&amp;H1000)  <br/> |The user or group has permission to grant permissions on the object.  <br/> |
|**adRightWriteDesign** <br/> |2048          (&amp;H800)  <br/> |The user or group has permission to modify the design for the object.  <br/> |
|**adRightWriteOwner** <br/> |524288          (&amp;H80000)  <br/> |The user or group has permission to modify the owner of the object.  <br/> |
|**adRightWritePermissions** <br/> |262144          (&amp;H40000)  <br/> |The user or group can modify the specific permissions for an object in the catalog.  <br/> |
   

