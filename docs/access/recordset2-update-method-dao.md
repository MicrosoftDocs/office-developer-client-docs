---
title: "Recordset2.Update Method (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1052882
  
localization_priority: Normal
ms.assetid: 1b47606a-e79c-23f1-b120-46d1429bc167

---

# Recordset2.Update Method (DAO)

## Syntax

 *expression*  . **Update**( ** *UpdateType* **, ** *Force* ** ) 
  
 *expression*  A variable that represents a **Recordset2** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _UpdateType_ <br/> |Optional  <br/> |**Long** <br/> |A **[UpdateTypeEnum](updatetypeenum-enumeration-dao.md)** constant indicating the type of update, as specified in Settings (ODBCDirect workspaces only).  <br/> |
| _Force_ <br/> |Optional  <br/> |**Boolean** <br/> | A **Boolean** value indicating whether or not to force the changes into the database, regardless of whether the underlying data has been changed by another user since the **[AddNew](recordset-addnew-method-dao.md)**, **[Delete](fields-delete-method-dao.md)**, or **[Edit](recordset2-edit-method-dao.md)** call. If **True**, the changes are forced and changes made by other users are simply overwritten. If **False** (default), changes made by another user while the update is pending will cause the update to fail for those changes that are in conflict. No error occurs, but the **[BatchCollisionCount](recordset-batchcollisioncount-property-dao.md)** and **BatchCollisions** properties will indicate the number of conflicts and the rows affected by conflicts, respectively (ODBCDirect workspaces only).  <br/> |
   
## Remarks

Use **Update** to save the current record and any changes you've made to it. 
  
> [!IMPORTANT]
> Changes to the current record are lost if: 
  
- You use the **Edit** or **AddNew** method, and then move to another record without first using **Update**. 
    
- You use **Edit** or **AddNew**, and then use **Edit** or **AddNew** again without first using **Update**. 
    
- You set the **[Bookmark](recordset2-bookmark-property-dao.md)** property to another record. 
    
- You close the **Recordset** without first using **Update**. 
    
- You cancel the **Edit** operation by using **[CancelUpdate](recordset2-cancelupdate-method-dao.md)**. 
    
To edit a record, use the **Edit** method to copy the contents of the current record to the copy buffer. If you don't use **Edit** first, an error occurs when you use **Update** or attempt to change a field's value. 
  
In an ODBCDirect workspace, you can do batch updates, provided the cursor library supports batch updates, and the **Recordset** was opened with the optimistic batch locking option. 
  
In a Microsoft Access workspace, when the **Recordset** object's **LockEdits** property setting is **True** (pessimistically locked) in a multiuser environment, the record remains locked from the time **Edit** is used until the **Update** method is executed or the edit is canceled. If the **LockEdits** property setting is **False** (optimistically locked), the record is locked and compared with the pre-edited record just before it is updated in the database. If the record has changed since you used the **Edit** method, the **Update** operation fails. Microsoft Access database engine-connected ODBC and installable ISAM databases always use optimistic locking. To continue the **Update** operation with your changes, use the **Update** method again. To revert to the record as the other user changed it, refresh the current record by using  `Move 0`.
  
> [!NOTE]
> To add, edit, or delete a record, there must be a unique index on the record in the underlying data source. If not, a "Permission denied" error will occur on the **AddNew**, **Delete**, or **Edit** method call in a Microsoft Access workspace, or an "Invalid argument" error will occur on the **Update** call in an ODBCDirect workspace. 
  

