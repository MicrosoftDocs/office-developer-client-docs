---
title: "TableDef.CreateField Method (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1052971
  
localization_priority: Normal
ms.assetid: a83d797f-ea42-4a07-dd9e-b254755f0891
description: "Creates a new Field object (Microsoft Access workspaces only)."
---

# TableDef.CreateField Method (DAO)

Creates a new **[Field](field-object-dao.md)** object (Microsoft Access workspaces only). 
  
## Syntax

 *expression*  . **CreateField**( ** *Name* **, ** *Type* **, ** *Size* ** ) 
  
 *expression*  A variable that represents a **TableDef** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Name_ <br/> |Optional  <br/> |**Variant** <br/> |A String that uniquely names the new **Field** object. See the **[Name](connection-name-property-dao.md)** property for details on valid **Field** names.  <br/> |
| _Type_ <br/> |Optional  <br/> |**Variant** <br/> | A constant that determines the data type of the new **Field** object. See the **[Type](field-type-property-dao.md)** property for valid data types.  <br/> |
| _Size_ <br/> |Optional  <br/> |**Variant** <br/> |An **Integer** that indicates the maximum size, in bytes, of a **Field** object that contains text. See the **[Size](field-size-property-dao.md)** property for valid  _size_ values. This argument is ignored for numeric and fixed-width fields.  <br/> |
   
### Return Value

Field
  
## Remarks

You can use the **CreateField** method to create a new field, as well as specify the name, data type, and size of the field. If you omit one or more of the optional parts when you use **CreateField**, you can use an appropriate assignment statement to set or reset the corresponding property before you append the new object to a collection. After you append the new object, you can alter some but not all of its property settings. See the individual property topics for more details. 
  
The  _type_ and  _Size_ arguments apply only to **Field** objects in a **TableDef** object. These arguments are ignored when a **Field** object is associated with an **Index** or **Relation** object. 
  
If  _Name_ refers to an object that is already a member of the collection, a run-time error occurs when you use the **[Append](fields-append-method-dao.md)** method. 
  
To remove a **Field** object from a **Fields** collection, use the **[Delete](fields-delete-method-dao.md)** method on the collection. You can't delete a **Field** object from a **TableDef** object's **Fields** collection after you create an index that references the field. 
  
 **Link provided by:**![Community Member Icon](media/8b9774c4-6c97-470e-b3a2-56d8f786444c.png) The [UtterAccess](http://www.utteraccess.com) community | [About the Contributors](#AboutContributors)
  
- [Adding a hyperlink field to an existing table with DAO](http://www.utteraccess.com/wiki/index.php/Adding_a_hyperlink_field_to_an_existing_table_with_DAO)
    
## Example

The following example shows how to create a calculated field. The **CreateField** method creates a field named **FullName**. The **Expression** property is then set to the expression that calculates the value of the field. 
  
 **Sample code provided by:** The [Microsoft Access 2010 Programmer's Reference](http://www.wrox.com/WileyCDA/WroxTitle/Access-2010-Programmer-s-Reference.productCd-0470591668.mdl) | [About the Contributors](#AboutContributors)
  
```
Sub CreateCalculatedField()
    Dim dbs As DAO.Database
    Dim tdf As DAO.TableDef
    Dim fld As DAO.Field2
    
    ' get the database
    Set dbs = CurrentDb()
    
    ' create the table
    Set tdf = dbs.CreateTableDef("tblContactsCalcField")
    
    ' create the fields: first name, last name
    tdf.Fields.Append tdf.CreateField("FirstName", dbText, 20)
    tdf.Fields.Append tdf.CreateField("LastName", dbText, 20)
    
    ' create the calculated field: full name
    Set fld = tdf.CreateField("FullName", dbText, 50)
    fld.Expression = "[FirstName] &amp; "" "" &amp; [LastName]"
    tdf.Fields.Append fld
    
    ' append the table and cleanup
    dbs.TableDefs.Append tdf
    
Cleanup:
    Set fld = Nothing
    Set tdf = Nothing
    Set dbs = Nothing
End Sub
```

## About the Contributors
<a name="AboutContributors"> </a>

UtterAccess is the premier Microsoft Access wiki and help forum. Click here to join. 
  
Wrox Press is driven by the Programmer to Programmer philosophy. Wrox books are written by programmers for programmers, and the Wrox brand means authoritative solutions to real-world programming problems. 
  

