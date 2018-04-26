---
title: "Field2.DefaultValue Property (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1053121
  
localization_priority: Normal
ms.assetid: 709c9580-520e-46ce-7d70-e409872184bb
description: "Sets or returns the default value of a Field2 object. For a Field2 object not yet appended to the Fields collection, this property is read/write (Microsoft Access workspaces only)."
---

# Field2.DefaultValue Property (DAO)

Sets or returns the default value of a **Field2** object. For a **Field2** object not yet appended to the **[Fields](fields-collection-dao.md)** collection, this property is read/write (Microsoft Access workspaces only). 
  
## Syntax

 *expression*  . **DefaultValue**
  
 *expression*  A variable that represents a **Field2** object. 
  
## Remarks

The setting or return value is a **String** data type that can contain a maximum of 255 characters. It can be either text or an expression. If the property setting is an expression, it can't contain user-defined functions, Microsoft Access database engine SQL aggregate functions, or references to queries, forms, or other **Field2** objects. 
  
> [!NOTE]
> You can also set the **DefaultValue** property of a **Field2** object on a **TableDef** object to a special value called "GenUniqueID( )". This causes a random number to be assigned to this field whenever a new record is added or created, thereby giving each record a unique identifier. The field's **Type** property must be **Long**. 
  
The availability of the **DefaultValue** property depends on the object that contains the **Fields** collection, as shown in the following table. 
  
|**If the Fields collection belongs to an**|**Then DefaultValue is**|
|:-----|:-----|
|Index object  <br/> |Not supported  <br/> |
|QueryDef object  <br/> |Read-only  <br/> |
|Recordset object  <br/> |Read-only  <br/> |
|Relation object  <br/> |Not supported  <br/> |
|TableDef object  <br/> |Read/write  <br/> |
   
When a new record is created, the **DefaultValue** property setting is automatically entered as the value for the field. You can change the field value by setting its **Value** property. 
  
The **DefaultValue** property doesn't apply to **AutoNumber** and **Long Binary** fields. 
  
## Example

This example uses the **DefaultValue** property to alert the user of a field's normal value while prompting for input. In addition, it demonstrates how new records will be filled using **DefaultValue** in the absence of any other input. The DefaultPrompt function is required for this procedure to run. 
  
```
Sub DefaultValueX() 
 
 Dim dbsNorthwind As Database 
 Dim tdfEmployees As TableDef 
 Dim strOldDefault As String 
 Dim rstEmployees As Recordset 
 Dim strMessage As String 
 Dim strCode As String 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 Set tdfEmployees = dbsNorthwind.TableDefs!Employees 
 
 ' Store original DefaultValue information and set the 
 ' property to a new value. 
 strOldDefault = _ 
 tdfEmployees.Fields!PostalCode.DefaultValue 
 tdfEmployees.Fields!PostalCode.DefaultValue = "98052" 
 
 Set rstEmployees = _ 
 dbsNorthwind.OpenRecordset("Employees", _ 
 dbOpenDynaset) 
 
 With rstEmployees 
 ' Add a new record to the Recordset. 
 .AddNew 
 !FirstName = "Bruce" 
 !LastName = "Oberg" 
 
 ' Get user input. If user enters something, the field 
 ' will be filled with that data; otherwise, it will be 
 ' filled with the DefaultValue information. 
 strMessage = "Enter postal code for " &amp; vbCr &amp; _ 
 !FirstName &amp; " " &amp; !LastName &amp; ":" 
 strCode = DefaultPrompt(strMessage, !PostalCode) 
 If strCode <> "" Then !PostalCode = strCode 
 .Update 
 
 ' Go to new record and print information. 
 .Bookmark = .LastModified 
 Debug.Print " FirstName = " &amp; !FirstName 
 Debug.Print " LastName = " &amp; !LastName 
 Debug.Print " PostalCode = " &amp; !PostalCode 
 
 ' Delete new record because this is a demonstration. 
 .Delete 
 .Close 
 End With 
 
 ' Restore original DefaultValue property because this is a 
 ' demonstration. 
 tdfEmployees.Fields!PostalCode.DefaultValue = _ 
 strOldDefault 
 
 dbsNorthwind.Close 
 
End Sub 
 
Function DefaultPrompt(strPrompt As String, _ 
 fldTemp As Field2) As String 
 
 Dim strFullPrompt As String 
 
 ' Ask user for new DefaultValue setting for the specified 
 ' Field object. 
 strFullPrompt = strPrompt &amp; vbCr &amp; _ 
 "[Default = " &amp; fldTemp.DefaultValue &amp; _ 
 ", Cancel - use default]" 
 DefaultPrompt = InputBox(strFullPrompt) 
 
End Function 

```


