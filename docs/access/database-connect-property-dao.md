---
title: "Database.Connect Property (DAO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: c3e511a6-baef-3758-cfb1-3459b0b19cf3
description: "Sets or returns a value that provides information about the source an open database. Read/write String ."
---

# Database.Connect Property (DAO)

Sets or returns a value that provides information about the source an open database. Read/write **String**. 
  
## Syntax

 *expression*  . **Connect**
  
 *expression*  A variable that represents a **Database** object. 
  
## Remarks

The **Connect** property setting is a **String** composed of a database type specifier and zero or more parameters separated by semicolons. The **Connect** property passes additional information to ODBC and certain ISAM drivers as needed. 
  
To perform an SQL pass-through query on a table linked to your Microsoft Access database file, you must first set the **Connect** property of the linked table's database to a valid ODBC connection string. 
  
The path as shown in the following table is the full path for the directory containing the database files and must be preceded by the identifier  `DATABASE=`. In some cases (as with Microsoft Excel and Microsoft Access database engine databases), you should include a specific file name in the database path argument.
  
The following table shows possible database types and their corresponding database specifiers and paths for the **Connect** property setting. 
  
|**Database type**|**Specifier**|**Example**|
|:-----|:-----|:-----|
|Microsoft Access Database  <br/> |[database];  <br/> |drive:\path\filename  <br/> |
|dBASE III  <br/> |dBASE III;  <br/> |drive:\path  <br/> |
|dBASE IV  <br/> |dBASE IV;  <br/> |drive:\path  <br/> |
|dBASE 5  <br/> |dBASE 5.0;  <br/> |drive:\path  <br/> |
|Paradox 3.x  <br/> |Paradox 3.x;  <br/> |drive:\path  <br/> |
|Paradox 4.x  <br/> |Paradox 4.x;  <br/> |drive:\path  <br/> |
|Paradox 5.x  <br/> |Paradox 5.x;  <br/> |drive:\path  <br/> |
|Microsoft Excel 3.0  <br/> |Excel 3.0;  <br/> |drive:\path\filename.xls  <br/> |
|Microsoft Excel 4.0  <br/> |Excel 4.0;  <br/> |drive:\path\filename.xls  <br/> |
|Microsoft Excel 5.0 or Microsoft Excel 95  <br/> |Excel 5.0;  <br/> |drive:\path\filename.xls  <br/> |
|Microsoft Excel 97  <br/> |Excel 8.0;  <br/> |drive:\path\filename.xls  <br/> |
|Lotus 1-2-3 WKS and WK1  <br/> |Lotus WK1;  <br/> |drive:\path\filename.wk1  <br/> |
|Lotus 1-2-3 WK3  <br/> |Lotus WK3;  <br/> |drive:\path\filename.wk3  <br/> |
|Lotus 1-2-3 WK4  <br/> |Lotus WK4;  <br/> |drive:\path\filename.wk4  <br/> |
|HTML Import  <br/> |HTML Import;  <br/> |drive:\path\filename  <br/> |
|HTML Export  <br/> |HTML Export;  <br/> |drive:\path  <br/> |
|Text  <br/> |Text;  <br/> |drive:\path  <br/> |
|ODBC  <br/> |ODBC; DATABASE=database; UID=user; PWD=password; DSN= datasourcename; [LOGINTIMEOUT=seconds;]  <br/> |None  <br/> |
|Microsoft Exchange  <br/> |Exchange 4.0; MAPILEVEL=folderpath; [TABLETYPE={ 0 | 1 }];[PROFILE=profile;] [PWD=password;] [DATABASE=database;]  <br/> |drive:\path\filename  <br/> |
   
If the specifier is only  `"ODBC;"`, the ODBC driver displays a dialog box listing all registered ODBC data source names so that the user can select a database.
  
If a password is required but not provided in the **Connect** property setting, a login dialog box is displayed the first time a table is accessed by the ODBC driver and again if the connection is closed and reopened. 
  
For data in Microsoft Exchange, the required MAPILEVEL key should be set to a fully-resolved folder path (for example, "Mailbox - Pat SmithIAlpha/Today"). The path does not include the name of the folder that will be opened as a table; that folder's name should instead be specified as the name argument to the **CreateTable** method. The TABLETYPE key should be set to "0" to open a folder (default) or "1" to open an address book. The PROFILE key defaults to the profile currently in use. 
  
You can set the **Connect** property for a **Database** object by providing a source argument to the **OpenDatabase** method. You can check the setting to determine the type, path, user ID, password, or ODBC data source of the database. 
  
> [!NOTE]
>  You must set the **Connect** property before you set the **ReturnsRecords** property. >  You must have access permissions to the computer that contains the database server you're trying to access. 
  

