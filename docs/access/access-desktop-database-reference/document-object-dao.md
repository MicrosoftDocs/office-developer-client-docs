---
title: Document Object (DAO)
TOCTitle: Document Object
ms:assetid: b51d4545-b157-4c7c-fdbe-16a25afffdb3
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff822082(v=office.15)
ms:contentKeyID: 48547247
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Document Object (DAO)


_**Applies to:** Access 2013 | Office 2013_

A **Document** object includes information about one instance of an object. The object can be a database, saved table, query, or relationship (Microsoft Access database engine databases only).

## Remarks

Each **Container** object has a **Documents** collection containing **Document** objects that describe instances of built-in objects of the type specified by the **Container**. The following table lists the type of object each **Document** describes, the name of its **Container** object, and what type of information **Document** contains.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Document</p></th>
<th><p>Container</p></th>
<th><p>Contains information about</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Database</p></td>
<td><p>Databases</p></td>
<td><p>Saved database</p></td>
</tr>
<tr class="even">
<td><p>Table or query</p></td>
<td><p>Tables</p></td>
<td><p>Saved table or query</p></td>
</tr>
<tr class="odd">
<td><p>Relationship</p></td>
<td><p>Relations</p></td>
<td><p>Saved relationship</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> <P>Don't confuse the <STRONG>Container</STRONG> objects listed in the preceding table with the collections of the same name. The Databases <STRONG>Container</STRONG> object refers to all saved database objects, but the <STRONG>Databases</STRONG> collection refers only to database objects that are open in a particular workspace.</P>



With a **Document** object, you can:

  - Use the **Name** property to return the name that a user or the Microsoft Access database engine gave to the object when it was created.

  - Use the **Container** property to return the name of the **Container** object that contains the **Document** object.

  - Use the **Owner** property to set or return the owner of the object. To set the **Owner** property, you must have write permission for the **Document** object, and you must set the property to the name of an existing **User** or **Group** object.

  - Use the **UserName** or **Permissions** properties to set or return the access permissions of a user or group for the object. To set these properties, you must have write permission for the **Document** object, and you must set the **UserName** property to the name of an existing **User** or **Group** object.

  - Use the **DateCreated** and **LastUpdated** properties to return the date and time when the **Document** object was created and last modified.

Because a **Document** object corresponds to an existing object, you can't create new **Document** objects or delete existing ones. To refer to a **Document** object in a collection by its ordinal number or by its **Name** property setting, use any of the following syntax forms:

  - **Documents**(0)

  - **Documents**("*name*")

  - **Documents**\!\[*name*\]

## Example

This example enumerates the **Documents** collection of the Tables container, and then enumerates the **Properties** collection of the first **Document** object in the collection.

``` 
Sub DocumentX() 
 
 Dim dbsNorthwind As Database 
 Dim docLoop As Document 
 Dim prpLoop As Property 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 
 With dbsNorthwind.Containers!Tables 
 Debug.Print "Documents in " & .Name & " container" 
 ' Enumerate the Documents collection of the Tables 
 ' container. 
 For Each docLoop In .Documents 
 Debug.Print " " & docLoop.Name 
 Next docLoop 
 With .Documents(0) 
 ' Enumerate the Properties collection of the first. 
 ' Document object of the Tables container. 
 Debug.Print "Properties of " & .Name & " document" 
 On Error Resume Next 
 For Each prpLoop In .Properties 
 Debug.Print " " & prpLoop.Name & " = " & _ 
 prpLoop 
 Next prpLoop 
 On Error GoTo 0 
 End With 
 End With 
 
 dbsNorthwind.Close 
 
End Sub 
 
```

This example uses the **Owner** and **SystemDB** properties to show the owners of a variety of **Document** objects.

``` 
Sub OwnerX() 
 
 ' Ensure that the Microsoft Access workgroup file is 
 ' available. 
 DBEngine.SystemDB = "system.mdw" 
 
 Dim dbsNorthwind As Database 
 Dim ctrLoop As Container 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 
 With dbsNorthwind 
 Debug.Print "Document owners:" 
 ' Enumerate Containers collection and show the owner 
 ' of the first Document in each container's Documents 
 ' collection. 
 For Each ctrLoop In .Containers 
 With ctrLoop 
 Debug.Print " [" & .Documents(0).Name & _ 
 "] in [" & .Name & _ 
 "] container owned by [" & _ 
 .Documents(0).Owner & "]" 
 End With 
 Next ctrLoop 
 
 .Close 
 End With 
 
End Sub 
 
```

