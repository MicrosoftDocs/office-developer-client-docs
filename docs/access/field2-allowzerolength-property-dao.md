---
title: "Field2.AllowZeroLength Property (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: d3795634-527f-b4c5-b606-50f9945cac12
description: "Sets or returns a value that indicates whether a zero-length string () is a valid setting for the Value property of the Field2 object with a Text or Memo data type (Microsoft Access workspaces only)."
---

# Field2.AllowZeroLength Property (DAO)

Sets or returns a value that indicates whether a zero-length string ("") is a valid setting for the **[Value](field-value-property-dao.md)** property of the **Field2** object with a Text or Memo data type (Microsoft Access workspaces only). 
  
## Syntax

 *expression*  . **AllowZeroLength**
  
 *expression*  A variable that represents a **Field2** object. 
  
## Remarks

For an object not yet appended to the **Fields** collection, this property is read/write. 
  
Once appended to a **Fields** collection, the availability of the **AllowZeroLength** property depends on the object that contains the **Fields** collection, as shown in the following table. 
  
|**If the Fields collection belongs to an**|**Then AllowZeroLength is**|
|:-----|:-----|
|**Index** object  <br/> |Not supported  <br/> |
|**QueryDef** object  <br/> |Read-only  <br/> |
|**Recordset** object  <br/> |Read-only  <br/> |
|**Relation** object  <br/> |Not supported  <br/> |
|**TableDef** object  <br/> |Read/write  <br/> |
   
You can use this property along with the **[Required](field-required-property-dao.md)**, **[ValidateOnSet](field-validateonset-property-dao.md)**, or **[ValidationRule](field-validationrule-property-dao.md)** property to validate a value in a field. 
  
## Example

In this example, the **AllowZeroLength** property allows the user to set the value of a **Field2** to an empty string. In this situation, the user can distinguish between a record where data is not known and a record where the data does not apply. 
  
```
Sub AllowZeroLengthX() 
 
 Dim dbsNorthwind As Database 
 Dim tdfEmployees As TableDef 
 Dim fldTemp As Field 
 Dim rstEmployees As Recordset 
 Dim strMessage As String 
 Dim strInput As String 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 Set tdfEmployees = dbsNorthwind.TableDefs("Employees") 
 ' Create a new Field object and append it to the Fields 
 ' collection of the Employees table. 
 Set fldTemp = tdfEmployees.CreateField("FaxPhone", _ 
 dbText, 24) 
 fldTemp.AllowZeroLength = True 
 tdfEmployees.Fields.Append fldTemp 
 
 Set rstEmployees = _ 
 dbsNorthwind.OpenRecordset("Employees") 
 
 With rstEmployees 
 ' Get user input. 
 .Edit 
 strMessage = "Enter fax number for " &amp; _ 
 !FirstName &amp; " " &amp; !LastName &amp; "." &amp; vbCr &amp; _ 
 "[? - unknown, X - has no fax]" 
 strInput = UCase(InputBox(strMessage)) 
 If strInput <> "" Then 
 Select Case strInput 
 Case "?" 
 !FaxPhone = Null 
 Case "X" 
 !FaxPhone = "" 
 Case Else 
 !FaxPhone = strInput 
 End Select 
 
 .Update 
 
 ' Print report. 
 Debug.Print "Name - Fax number" 
 Debug.Print !FirstName &amp; " " &amp; !LastName &amp; " - "; 
 
 If IsNull(!FaxPhone) Then 
 Debug.Print "[Unknown]" 
 Else 
 If !FaxPhone = "" Then 
 Debug.Print "[Has no fax]" 
 Else 
 Debug.Print !FaxPhone 
 End If 
 End If 
 
 Else 
 .CancelUpdate 
 End If 
 
 .Close 
 End With 
 
 ' Delete new field because this is a demonstration. 
 tdfEmployees.Fields.Delete fldTemp.Name 
 dbsNorthwind.Close 
 
End Sub 

```


