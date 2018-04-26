---
title: "Append Method (ADOX Columns)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: e256a478-abc0-f15b-fc29-1b52e354144a
---

# Append Method (ADOX Columns)

Adds a new [Column](column-object-adox.md) object to the [Columns](columns-collection-adox.md) collection. 
  
## Syntax

 *Columns*  . **Append** *Column*  [,  *Type*  ] [,  *DefinedSize*  ] 
  
## Parameters

-  *Column* 
    
- The **Column** object to append or the name of the column to create and append. 
    
-  *Type* 
    
- Optional. A **Long** value that specifies the data type of the column. The  *Type*  parameter corresponds to the [Type](http://msdn.microsoft.com/library/3e222e89-f57e-28f9-8488-81828f882643%28Office.15%29.aspx) property of a **Column** object. 
    
-  *DefinedSize* 
    
- Optional. A **Long** value that specifies the size of the column. The  *DefinedSize*  parameter corresponds to the [DefinedSize](definedsize-property-adox.md) property of a **Column** object. 
    
> [!NOTE]
> An error will occur when appending a **Column** to the **Columns** collection of an [Index](index-object-adox.md) if the **Column** does not exist in a [Table](table-object-adox.md) that is already appended to the [Tables](tables-collection-adox.md) collection. 
  

