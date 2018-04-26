---
title: "DBEngine.OpenDatabase Method (DAO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
f1_keywords:
- dao360.chm1052979
  
localization_priority: Normal
ms.assetid: 49fca321-5955-3e69-64ea-da191536eadb
description: "Opens a specified database and returns a reference to the Database object that represents it."
---

# DBEngine.OpenDatabase Method (DAO)

Opens a specified database and returns a reference to the **[Database](database-object-dao.md)** object that represents it. 
  
## Syntax

 *expression*  . **OpenDatabase**( ** *Name* **, ** *Options* **, ** *ReadOnly* **, ** *Connect* ** ) 
  
 *expression*  A variable that represents a **DBEngine** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Name_ <br/> |Required  <br/> |**String** <br/> |the name of an existing Microsoft Access database file, or the data source name (DSN) of an ODBC data source. See the **[Name](connection-name-property-dao.md)** property for more information about setting this value.  <br/> |
| _Options_ <br/> |Optional  <br/> |**Variant** <br/> |Sets various options for the database, as specified in Remarks.  <br/> |
| _ReadOnly_ <br/> |Optional  <br/> |**Variant** <br/> |**True** if you want to open the database with read-only access, or **False** (default) if you want to open the database with read/write access.  <br/> |
| _Connect_ <br/> |Optional  <br/> |**Variant** <br/> |Specifies various connection information, including passwords.  <br/> |
   
### Return Value

Database
  
## Remarks

You can use the following values for the  _options_ argument. 
  
|**Setting**|**Description**|
|:-----|:-----|
|**True** <br/> |Opens the database in exclusive mode.  <br/> |
|**False** <br/> |(Default) Opens the database in shared mode.  <br/> |
   
When you open a database, it is automatically added to the **Databases** collection. 
  
Some considerations apply when you use  _dbname_:
  
- If it refers to a database that is already open for access by another user, an error occurs.
    
- If it doesn't refer to an existing database or valid ODBC data source name, an error occurs.
    
- If it's a zero-length string ("") and  *connect*  is  `"ODBC;"`, a dialog box listing all registered ODBC data source names is displayed so the user can select a database.
    
To close a database, and thus remove the **Database** object from the **Databases** collection, use the **[Close](connection-close-method-dao.md)** method on the object. 
  
> [!NOTE]
> When you access a Microsoft Access database engine-connected ODBC data source, you can improve your application's performance by opening a **Database** object connected to the ODBC data source, rather than by linking individual **[TableDef](tabledef-object-dao.md)** objects to specific tables in the ODBC data source. 
  

