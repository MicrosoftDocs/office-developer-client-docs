---
title: "Microsoft Cursor Service for OLE DB (ADO Service Component)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 6818fc05-9c9f-9b67-07d2-e622c93133c2

description: "The Microsoft Cursor Service for OLE DB supplements the cursor support functions of data providers. As a result, the user perceives relatively uniform functionality from all data providers."
---

# Microsoft Cursor Service for OLE DB (ADO Service Component)

The Microsoft Cursor Service for OLE DB supplements the cursor support functions of data providers. As a result, the user perceives relatively uniform functionality from all data providers.
  
The Cursor Service makes dynamic properties available and enhances the behavior of certain methods. For example, the [Optimize](optimize-property-dynamic-ado.md) dynamic property enables the creation of temporary indexes to facilitate certain operations, such as the [Find](find-method-ado.md) method. 
  
The Cursor Service enables support for batch updating in all cases. It also simulates more capable cursor types, such as dynamic cursors, when a data provider can only supply less capable cursors, such as static cursors.
  
## Keyword

To invoke this service component, set the [Recordset](recordset-object-ado.md) or [Connection](connection-object-ado.md) object's [CursorLocation](cursorlocation-property-ado.md) property to **adUseClient**. 
  
```
connection.CursorLocation=adUseClientrecordset.CursorLocation=adUseClient
```

## Dynamic Properties

When the Cursor Service for OLE DB is invoked, the following dynamic properties are added to the **Recordset** object's [Properties](properties-collection-ado.md) collection. The full list of **Connection** and **Recordset** object dynamic properties is listed in the [ADO Dynamic Property Index](ado-dynamic-property-index.md). The associated OLE DB property names, where appropriate, are included in parenthesis after the ADO property name.
  
Changes to some dynamic properties are not visible to the underlying data source after the Cursor Service has been invoked. For example, setting the  *Command Time out*  property on a **Recordset** will not be visible to the underlying data provider. 
  
```
 
... 
Recordset1.CursorLocation = adUseClient 'invokes cursor service 
Recordset1.Open "authors", _ 
 "Provider=SQLOLEDB;Data Source=DBServer;User Id=usr;" &amp; _ 
 "Password=pwd;Initial Catalog=pubs;",,adCmdTable 
Recordset1.Properties.Item("Command Time out") = 50 
' 'Command Time out' property on DBServer is still default (30). 
... 

```

If your application requires the Cursor Service, but you need to set dynamic properties on the underlying provider, set the properties before invoking the Cursor Service. Command object property settings are always passed to the underlying data provider regardless of cursor location. Therefore, you can also use a command object to set the properties at any time.
  
> [!NOTE]
> The dynamic property DBPROP_SERVERDATAONINSERT is not supported by the cursor service, even if it is supported by the underlying data provider. 
  
|**Property Name**|**Description**|
|:-----|:-----|
|Auto Recalc          (DBPROP_ADC_AUTORECALC)  <br/> |For recordsets created with the Data Shaping Service, this value indicates how often calculated and aggregate columns are calculated. The default (value=1) is to recalculate whenever the Data Shaping Service determines that the values have changed. If the value is 0, the calculated or aggregate columns are only calculated when the hierarchy is initially built.  <br/> |
|Batch Size          (DBPROP_ADC_BATCHSIZE)  <br/> |Indicates the number of update statements that can be batched before being sent to the data store. The more statements in a batch, the fewer round trips to the data store.  <br/> |
|Cache Child Rows          (DBPROP_ADC_CACHECHILDROWS)  <br/> |For recordsets created with the Data Shaping Service, this value indicates whether child recordsets are stored in a cache for later use.  <br/> |
|Cursor Engine Version          (DBPROP_ADC_CEVER)  <br/> |Indicates the version of the Cursor Service being used.  <br/> |
|Maintain Change Status          (DBPROP_ADC_MAINTAINCHANGESTATUS)  <br/> |Indicates the text of the command used for resynchronizing a one or more rows in a multiple table join.  <br/> |
|[Optimize](optimize-property-dynamic-ado.md) <br/> |Indicates whether an index should be created. When set to **True**, authorizes the temporary creation of indexes to improve the execution of certain operations.  <br/> |
|[Reshape Name](reshape-name-property-dynamic-ado.md) <br/> |Indicates the name of the **Recordset**. May be referenced within the current, or subsequent, data shaping commands.  <br/> |
|[Resync Command](resync-command-property-dynamic-ado.md) <br/> |Indicates a custom command string that is used by the [Resync](resync-method-ado.md) method when the [Unique Table](unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) property is in effect.  <br/> |
|[Unique Catalog](unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) <br/> |Indicates the name of the database containing the table referenced in the **Unique Table** property.  <br/> |
|[Unique Schema](unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) <br/> |Indicates the name of the owner of the table referenced in the **Unique Table** property.  <br/> |
|[Unique Table](unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) <br/> |Indicates the name of the one table in a **Recordset** created from multiple tables that may be modified by insertions, updates, or deletions.  <br/> |
|Update Criteria          (DBPROP_ADC_UPDATECRITERIA)  <br/> |Indicates which fields in the **WHERE** clause are used to handle collisions occurring during an update.  <br/> |
|[Update Resync](update-resync-property-dynamic-ado.md)(DBPROP_ADC_UPDATERESYNC)  <br/> |Indicates whether the **Resync** method is implicitly invoked after the [UpdateBatch](updatebatch-method-ado.md) method (and its behavior), when the **Unique Table** property is in effect.  <br/> |
   
You may also set or retrieve a dynamic property by specifying its name as the index to the **Properties** collection. For example, get and print the current value of the [Optimize](optimize-property-dynamic-ado.md) dynamic property, then set a new value, like this: 
  
```
 
Debug.Print rs.Properties("Optimize") 
rs.Properties("Optimize") = True 

```

## Built-in Property Behavior

The Cursor Service for OLE DB also affects the behavior of certain built-in properties.
  
|**Property Name**|**Description**|
|:-----|:-----|
|[CursorType](cursortype-property-ado.md) <br/> |Supplements the types of cursors that are available for a **Recordset**.  <br/> |
|[LockType](locktype-property-ado.md) <br/> |Supplements the types of locks available for a **Recordset**. Enables batch updates.  <br/> |
|[Sort](sort-property-ado.md) <br/> |Specifies one or more field names that the **Recordset** is sorted on, and whether each field is sorted in ascending or descending order.  <br/> |
   
## Method Behavior

The Cursor Service for OLE DB enables or affects the behavior of the [Field](field-object-ado.md) object's [Append](append-method-ado.md) method; and the **Recordset** object's [Open](open-method-ado-recordset.md), [Resync](resync-method-ado.md), [UpdateBatch](updatebatch-method-ado.md), and [Save](save-method-ado.md) methods. 
  

