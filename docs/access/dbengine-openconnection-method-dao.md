---
title: "DBEngine.OpenConnection Method (DAO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
f1_keywords:
- dao360.chm1053574
  
localization_priority: Normal
ms.assetid: 778a581f-be42-94ee-e5c6-4cbc1843450d
---

# DBEngine.OpenConnection Method (DAO)

## Syntax

 *expression*  . **OpenConnection**( ** *Name* **, ** *Options* **, ** *ReadOnly* **, ** *Connect* ** ) 
  
 *expression*  A variable that represents a **DBEngine** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Name_ <br/> |Required  <br/> |**String** <br/> |A string expression. See the discussion under Remarks.  <br/> |
| _Options_ <br/> |Optional  <br/> |**Variant** <br/> |sets various options for the connection, as specified in Remarks. Based on this value, the ODBC driver manager prompts the user for connection information such as data source name (DSN), user name, and password.  <br/> |
| _ReadOnly_ <br/> |Optional  <br/> |**Variant** <br/> |**True** if the connection is to be opened for read-only access and **False** if the connection is to be opened for read/write access (default).  <br/> |
| _Connect_ <br/> |Optional  <br/> |**Variant** <br/> |An ODBC connection string. See the **[Connect](connection-connect-property-dao.md)** property for the specific elements and syntax of this string. A prepended "ODBC;" is required.  <br/> |
   
### Return Value

Connection
  
## Remarks

Use the **OpenConnection** method to establish a connection to an ODBC data source from an ODBCDirect workspace. The **OpenConnection** method is similar but not equivalent to **OpenDatabase**. The main difference is that **OpenConnection** is available only in an ODBCDirect workspace. 
  
If you specify a registered ODBC data source name (DSN) in the  _connect_ argument, then the  _name_ argument can be any valid string, and will also provide the **Name** property for the **Connection** object. If a valid DSN is not included in the  _connect_ argument, then  _name_ must refer to a valid ODBC DSN, which will also be the **Name** property. If neither  _name_ nor  _connect_ contains a valid DSN, the ODBC driver manager can be set (via the  _options_ argument) to prompt the user for the required connection information. The DSN supplied through the prompt then provides the **Name** property. 
  
The  _options_ argument determines if and when to prompt the user to establish the connection, and whether or not to open the connection asynchronously. You can use one of the following constants. 
  
|**Constant**|**Description**|
|:-----|:-----|
|**dbDriverNoPrompt** <br/> |The ODBC Driver Manager uses the connection string provided in  *dbname*  and  *connect*  . If you don't provide sufficient information, a run-time error occurs.  <br/> |
|**dbDriverPrompt** <br/> |The ODBC Driver Manager displays the **ODBC Data Sources** dialog box, which displays any relevant information supplied in  *dbname*  or  *connect*  . The connection string is made up of the DSN that the user selects via the dialog boxes, or, if the user doesn't specify a DSN, the default DSN is used.  <br/> |
|**dbDriverComplete** <br/> |Default. If the  *connect*  argument includes all the necessary information to complete a connection, the ODBC Driver Manager uses the string in  *connect*  . Otherwise it behaves as it does when you specify **dbDriverPrompt**.  <br/> |
|**dbDriverCompleteRequired** <br/> |This option behaves like **dbDriverComplete** except the ODBC driver disables the prompts for any information not required to complete the connection.  <br/> |
|**dbRunAsync** <br/> |Execute the method asynchronously. This constant may be used with any of the other  *options*  constants.  <br/> |
   
 **OpenConnection** returns a **Connection** object which contains information about the connection. The **Connection** object is similar to a **[Database](database-object-dao.md)** object. The principal difference is that a **Database** object usually represents a database, although it can be used to represent a connection to an ODBC data source from a Microsoft Access workspace. 
  

