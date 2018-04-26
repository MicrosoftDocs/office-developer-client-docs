---
title: "SubmitChanges Method (RDS)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: ecaea12d-7e1a-095d-17e7-d631ef230b90

---

# SubmitChanges Method (RDS)

Submits pending changes of the locally cached and updatable [Recordset](recordset-object-ado.md) to the data source specified in the [Connect](connect-property-rds.md) property or the [URL](url-property-rds.md) property. 
  
## Syntax

 *DataControl*  . **SubmitChanges**
  
 *DataFactory*  . **SubmitChanges** *Connection*  ,  *Recordset* 
  
## Parameters

-  *DataControl* 
    
- An object variable that represents an [RDS.DataControl](datacontrol-object-rds.md) object. 
    
-  *DataFactory* 
    
- An object variable that represents an [RDSServer.DataFactory](datafactory-object-rdsserver.md) object. 
    
-  *Connection* 
    
- A **String** value that represents the connection created with the **RDS.DataControl** object's **Connect** property. 
    
-  *Recordset* 
    
- An object variable that represents a **Recordset** object. 
    
## Remarks

The [Connect](connect-property-rds.md), [Server](server-property-rds.md), and [SQL](http://msdn.microsoft.com/library/210adcbb-5c89-150b-4c61-6a52dea9af56%28Office.15%29.aspx) properties must be set before you can use the **SubmitChanges** method with the **RDS.DataControl** object. 
  
If you call the [CancelUpdate](cancelupdate-method-rds.md) method after you have called **SubmitChanges** for the same **Recordset** object, the **CancelUpdate** call fails because the changes have already been committed. 
  
Only the changed records are sent for modification, and either all of the changes succeed or all of them fail together.
  
You can use **SubmitChanges** only with the  *default* **RDSServer.DataFactory** object. Custom business objects can't use this method. 
  
If the **URL** property has been set, **SubmitChanges** will submit changes to the location specified by the URL. 
  

