---
title: "Append Method (ADOX Keys)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 14d6e8d7-5c9e-a422-47d6-ebfd9dd7a120
---

# Append Method (ADOX Keys)

Adds a new [Key](key-object-adox.md) object to the [Keys](keys-collection-adox.md) collection. 
  
## Syntax

 *Keys*  . **Append** *Key*  [,  *KeyType*  ] [,  *Column*  ] [,  *RelatedTable*  ] [,  *RelatedColumn*  ] 
  
## Parameters

-  *Key* 
    
- The **Key** object to append or the name of the key to create and append. 
    
-  *KeyType* 
    
- Optional. A **Long** value that specifies the type of key. The  *Key*  parameter corresponds to the [Type](http://msdn.microsoft.com/library/119a39e3-a397-1afb-2588-8129140810bf%28Office.15%29.aspx) property of a **Key** object. 
    
-  *Column* 
    
- Optional. A **String** value that specifies the name of the column to be indexed. The  *Columns*  parameter corresponds to the value of the [Name](name-property-adox.md) property of a [Column](column-object-adox.md) object. 
    
-  *RelatedTable* 
    
- Optional. A **String** value that specifies the name of the related table. The  *RelatedTable*  parameter corresponds to the value of the **Name** property of a [Table](table-object-adox.md) object. 
    
-  *RelatedColumn* 
    
- Optional. A **String** value that specifies the name of the related column for a foreign key. The RelatedColumn parameter corresponds to the value of the **Name** property of a **Column** object. 
    
## Remarks

The  *Columns*  parameter can take either the name of a column or an array of column names. 
  

