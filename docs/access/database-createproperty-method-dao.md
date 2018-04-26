---
title: "Database.CreateProperty Method (DAO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: f2039be9-5fd8-f673-dfbf-0a71540cdc98
description: "Creates a new user-defined Property object (Microsoft Access workspaces only). ."
---

# Database.CreateProperty Method (DAO)

Creates a new user-defined **[Property](property-object-dao.md)** object (Microsoft Access workspaces only). . 
  
## Syntax

 *expression*  . **CreateProperty**( ** *Name* **, ** *Type* **, ** *Value* **, ** *DDL* ** ) 
  
 *expression*  A variable that represents a **Database** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Name_ <br/> |Optional  <br/> |**Variant** <br/> |A **String** that uniquely names the new **Property** object. See the **Name** property for details on valid **Property** names.  <br/> |
| _Type_ <br/> |Optional  <br/> |**Variant** <br/> | A constant that defines the data type of the new **Property** object. See the **[Type](field-type-property-dao.md)** property for valid data types.  <br/> |
| _Value_ <br/> |Optional  <br/> |**Variant** <br/> |A **Variant** containing the initial property value. See the **[Value](field-value-property-dao.md)** property for details.  <br/> |
| _DDL_ <br/> |Optional  <br/> |**Variant** <br/> |A **Variant** ( **Boolean** subtype) that indicates whether or not the **Property** is a DDL object. The default is  _False_. If  _DDL_ is  _True_, users can't change or delete this **Property** object unless they have  _dbSecWriteDef_ permission.  <br/> |
   
### Return Value

Property
  
## Remarks

You can create a user-defined **Property** object only in the **[Properties](properties-collection-dao.md)** collection of an object that is persistent. 
  
If you omit one or more of the optional parts when you use **CreateProperty**, you can use an appropriate assignment statement to set or reset the corresponding property before you append the new object to a collection. After you append the object, you can alter some but not all of its property settings. See the **Name**, **Type**, and **Value** property topics for more details. 
  
If  _name_ refers to an object that is already a member of the collection, a run-time error occurs when you use the **[Append](fields-append-method-dao.md)** method. 
  
To remove a user-defined **Property** object from the collection, use the **[Delete](fields-delete-method-dao.md)** method on the **Properties** collection. You can't delete built-in properties. 
  
> [!NOTE]
> If you omit the  _DDL_ argument, it defaults to  _False_ (non-DDL). Because no corresponding DDL property is exposed, you must delete and re-create a **Property** object you want to change from DDL to non-DDL. 
  
## Example

This example tries to set the value of a user-defined property. If the property doesn't exist, it uses the **CreateProperty** method to create and set the value of the new property. The SetProperty procedure is required for this procedure to run. 
  
```
Sub CreatePropertyX() 
 
   Dim dbsNorthwind As Database 
   Dim prpLoop As Property 
 
   Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 
   ' Set the Archive property to True. 
   SetProperty dbsNorthwind, "Archive", True 
    
   With dbsNorthwind 
      Debug.Print "Properties of " &amp; .Name 
       
      ' Enumerate Properties collection of the Northwind  
      ' database. 
      For Each prpLoop In .Properties 
         If prpLoop <> "" Then Debug.Print "  " &amp; _ 
            prpLoop.Name &amp; " = " &amp; prpLoop 
      Next prpLoop 
 
      ' Delete the new property since this is a  
      ' demonstration. 
      .Properties.Delete "Archive" 
 
      .Close 
   End With 
 
End Sub 
 
Sub SetProperty(dbsTemp As Database, strName As String, _ 
   booTemp As Boolean) 
 
   Dim prpNew As Property 
   Dim errLoop As Error 
 
   ' Attempt to set the specified property. 
   On Error GoTo Err_Property 
   dbsTemp.Properties("strName") = booTemp 
   On Error GoTo 0 
 
   Exit Sub 
 
Err_Property: 
 
   ' Error 3270 means that the property was not found. 
   If DBEngine.Errors(0).Number = 3270 Then 
      ' Create property, set its value, and append it to the  
      ' Properties collection. 
      Set prpNew = dbsTemp.CreateProperty(strName, _ 
         dbBoolean, booTemp) 
      dbsTemp.Properties.Append prpNew 
      Resume Next 
   Else 
      ' If different error has occurred, display message. 
      For Each errLoop In DBEngine.Errors 
         MsgBox "Error number: " &amp; errLoop.Number &amp; vbCr &amp; _ 
            errLoop.Description 
      Next errLoop 
      End 
   End If 
 
End Sub 

```


