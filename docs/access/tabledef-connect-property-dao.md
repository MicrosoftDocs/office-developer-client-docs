---
title: "TableDef.Connect Property (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1053064
  
localization_priority: Normal
ms.assetid: 4fbb324c-a358-8fad-60f2-fb8005cf74d9
description: "Sets or returns a value that provides information about a linked table. Read/write String ."
---

# TableDef.Connect Property (DAO)

Sets or returns a value that provides information about a linked table. Read/write **String**. 
  
## Syntax

 *expression*  . **Connect**
  
 *expression*  A variable that represents a **TableDef** object. 
  
## Remarks

The **Connect** property setting is a **String** composed of a database type specifier and zero or more parameters separated by semicolons. The **Connect** property passes additional information to ODBC and certain ISAM drivers as needed. 
  
For a **TableDef** object that represents a linked table, the **Connect** property setting consists of one or two parts (a database type specifier and a path to the database), each of which ends with a semicolon. 
  
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
   
If a password is required but not provided in the **Connect** property setting, a login dialog box is displayed the first time a table is accessed by the ODBC driver and again if the connection is closed and reopened. 
  
For data in Microsoft Exchange, the required MAPILEVEL key should be set to a fully-resolved folder path (for example, "Mailbox - Pat SmithIAlpha/Today"). The path does not include the name of the folder that will be opened as a table; that folder's name should instead be specified as the name argument to the **CreateTable** method. The TABLETYPE key should be set to "0" to open a folder (default) or "1" to open an address book. The PROFILE key defaults to the profile currently in use. 
  
For base tables in a Micorosoft Access database, the **Connect** property setting is a zero-length string (""). 
  
> [!NOTE]
>  You must set the **Connect** property before you set the **ReturnsRecords** property. >  You must have access permissions to the computer that contains the database server you're trying to access. 
  

