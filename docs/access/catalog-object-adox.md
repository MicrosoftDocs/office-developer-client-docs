---
title: "Catalog Object (ADOX)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: d9e8d94b-9161-3eb6-abaf-00d1244d1f2d
---

# Catalog Object (ADOX)

Contains collections ([Tables](tables-collection-adox.md), [Views](views-collection-adox.md), [Users](users-collection-adox.md), [Groups](groups-collection-adox.md), and [Procedures](procedures-collection-adox.md)) that describe the schema catalog of a data source.
  
## Remarks

You can modify the **Catalog** object by adding or removing objects or by modifying existing objects. Some providers may not support all of the **Catalog** objects or may support only viewing schema information. 
  
With the properties and methods of a **Catalog** object, you can: 
  
- Open the catalog by setting the [ActiveConnection](activeconnection-property-adox.md) property to an ADO [Connection](connection-object-ado.md) object or a valid connection string. 
    
- Create a new catalog with the [Create](create-method-adox.md) method. 
    
- Determine the owners of the objects in a **Catalog** with the [GetObjectOwner](getobjectowner-method-adox.md) and [SetObjectOwner](http://msdn.microsoft.com/library/22c5d2d9-c7b2-3c3a-0b1f-a2e5bc46395c%28Office.15%29.aspx) methods. 
    

