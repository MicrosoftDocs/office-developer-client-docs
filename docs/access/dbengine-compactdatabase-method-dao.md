---
title: "DBEngine.CompactDatabase Method (DAO)"
  
  
manager: soliver
ms.date: 10/24/2016
ms.audience: Developer
 
f1_keywords:
- dao360.chm1052936
  
localization_priority: Normal
ms.assetid: 03f3a156-005a-4b71-81b0-598f326f7d42
description: "Copies and compacts a closed database, and gives you the option of changing its version, collating order, and encryption. (Microsoft Access workspaces only)."
---

# DBEngine.CompactDatabase Method (DAO)

Copies and compacts a closed database, and gives you the option of changing its version, collating order, and encryption. (Microsoft Access workspaces only).
  
> [!NOTE]
> When using encrypted linked tables for action, update, and SQL queries [such as a SQL UPDATE statement (CurrentDb.Execute "UPDATE...")], you must supply the encryption key. Also, linked tables have a 19-character limit for the encryption key. See the  *Encrypted linked tables*  section at the end of this topic. 
  
## Syntax

 *expression*  . **CompactDatabase**( ** *SrcName* **, ** *DstName* **, ** *DstLocale* **, ** *Options* **, ** *password* ** ) 
  
 *expression*  An expression that returns a **DBEngine** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _SrcName_ <br/> |Required  <br/> |**String** <br/> |Identifies an existing, closed database. It can be a full path and file name, such as "C:\db1.mdb". If the file name has an extension, you must specify it. If your network supports it, you can also specify a network path, such as "\\server1\share1\dir1\db1.mdb"  <br/> |
| _DstName_ <br/> |Required  <br/> |**String** <br/> |the file name (and path) of the compacted database that you're creating. You can also specify a network path. You can't use this argument to specify the same database file as SrcName.  <br/> |
| _DstLocale_ <br/> |Optional  <br/> |**Variant** <br/> | A string expression that specifies a collating order for creating DstName, as specified in Remarks.  <br/>  If you omit this argument, the locale of DstName is the same as SrcName.  <br/>  You can also create a password for DstName by concatenating the password string (starting with "  `;pwd=`") with a constant in the DstLocale argument, like this:  `dbLangSpanish &amp; ";pwd=NewPassword"`.  <br/>  If you want to use the same DstLocale as SrcName (the default value), but specify a new password, simply enter a password string for DstLocale:  `";pwd=NewPassword"` <br/> |
| _Options_ <br/> |Optional  <br/> |**Variant** <br/> |Optional. A constant or combination of constants that indicates one or more options, as specified in Remarks. You can combine options by summing the corresponding constants.  <br/> |
| _password_ <br/> |Optional  <br/> |**Variant** <br/> |A string expression containing an encryption key, if the database is encrypted. The string ";pwd=" must precede the actual password. If you include a password setting in DstLocale, this setting is ignored.  <br/> > [!NOTE]> This is deprecated parameter and is not supported in .ACCDB format. To encrypt an .ACCDB file, use the "pwd=" option string. Use strong passwords that combine upper- and lowercase letters, numbers, and symbols. Weak passwords don't mix these elements. Strong password: Y6dh!et5. Weak password: House27. Use a strong password that you can remember so that you don't have to write it down.           |
   
## Remarks

You can use one of the following constants for the DstLocale argument to specify the **CollatingOrder** property for string comparisons of text. 
  
|**Constant**|**Collating order**|
|:-----|:-----|
|**dbLangGeneral** <br/> |English, German, French, Portuguese, Italian, and Modern Spanish  <br/> |
|**dbLangArabic** <br/> |Arabic  <br/> |
|**dbLangChineseSimplified** <br/> |Simplified Chinese  <br/> |
|**dbLangChineseTraditional** <br/> |Traditional Chinese  <br/> |
|**dbLangCyrillic** <br/> |Russian  <br/> |
|**dbLangCzech** <br/> |Czech  <br/> |
|**dbLangDutch** <br/> |Dutch  <br/> |
|**dbLangGreek** <br/> |Greek  <br/> |
|**dbLangHebrew** <br/> |Hebrew  <br/> |
|**dbLangHungarian** <br/> |Hungarian  <br/> |
|**dbLangIcelandic** <br/> |Icelandic  <br/> |
|**dbLangJapanese** <br/> |Japanese  <br/> |
|**dbLangKorean** <br/> |Korean  <br/> |
|**dbLangNordic** <br/> |Nordic languages (Microsoft Jet database engine version 1.0 only)  <br/> |
|**dbLangNorwDan** <br/> |Norwegian and Danish  <br/> |
|**dbLangPolish** <br/> |Polish  <br/> |
|**dbLangSlovenian** <br/> |Slovenian  <br/> |
|**dbLangSpanish** <br/> |Traditional Spanish  <br/> |
|**dbLangSwedFin** <br/> |Swedish and Finnish  <br/> |
|**dbLangThai** <br/> |Thai  <br/> |
|**dbLangTurkish** <br/> |Turkish  <br/> |
   
You can use one of the following constants in the options argument to specify whether to encrypt or to decrypt the database while it's compacted.
  
> [!NOTE]
> The constants dbEncrypt and dbDecrypt are deprecated and not supported in .ACCDB file formats. 
  
|**Constant**|**Description**|
|:-----|:-----|
|**dbEncrypt** <br/> |Encrypt the database while compacting.  <br/> |
|**dbDecrypt** <br/> |Decrypt the database while compacting.  <br/> |
   
If you omit an encryption constant or if you include both **dbDecrypt** and **dbEncrypt**, DstName will have the same encryption as SrcName. 
  
You can use one of the following constants in the options argument to specify the version of the data format for the compacted database. This constant affects only the version of the data format of DstName and doesn't affect the version of any Microsoft Access-defined objects, such as forms and reports.
  
|**Constant**|**Description**|
|:-----|:-----|
|**dbVersion10** <br/> |Creates a database that uses the Microsoft Jet database engine version 1.0 file format while compacting.  <br/> |
|**dbVersion11** <br/> |Creates a database that uses the Microsoft Jet database engine version 1.1 file format while compacting.  <br/> |
|**dbVersion20** <br/> |Creates a database that uses the Microsoft Jet database engine version 2.0 file format while compacting.  <br/> |
|**dbVersion30** <br/> |Creates a database that uses the Microsoft Jet database engine version 3.0 file format (compatible with version 3.5) while compacting.  <br/> |
|**dbVersion40** <br/> |Creates a database that uses the Microsoft Jet database engine version 4.0 file format while compacting.  <br/> |
|**dbVersion120** <br/> |Creates a database that uses the Microsoft Access database engine version 12.0 file format while compacting.  <br/> |
   
You can specify only one version constant. If you omit a version constant, DstName will have the same version as SrcName. You can compact DstName only to a version that is the same or later than that of SrcName.
  
As you change data in a database, the database file can become fragmented and use more disk space than is necessary. Periodically, you can use the **CompactDatabase** method to compact your database to defragment the database file. The compacted database is usually smaller and often runs faster. You can also change the collating order, the encryption, or the version of the data format while you copy and compact the database. 
  
You must close SrcName before you compact it. In a multiuser environment, other users can't have SrcName open while you're compacting it. If SrcName isn't closed or isn't available for exclusive use, an error occurs.
  
Because **CompactDatabase** creates a copy of the database, you must have enough disk space for both the original and the duplicate databases. The compact operation fails if there isn't enough disk space available. The DstName duplicate database doesn't have to be on the same disk as SrcName. After successfully compacting a database, you can delete the SrcName file and rename the compacted DstName file to the original file name. 
  
The **CompactDatabase** method copies all the data and the security permission settings from the database specified by SrcName to the database specified by DstName. 
  
> [!NOTE]
> Because the **CompactDatabase** method doesn't convert Microsoft Access objects, you shouldn't use **CompactDatabase** to convert a database containing such objects. 
  
## Encrypted linked tables

Encrypted passwords are dependent on the file format of the database that you are using. If you are using an Access 2003 (.mdb) or earlier database, you will have one password to protect the database, and a separate password to encrypt the database. For Access 2007 (.accdb) and later (.mdb) databases, the only option is to encrypt and protect the database with one password, as the option to have two separate passwords has been removed.
  
> [!NOTE]
> For Access 2007 (.accdb) databases, the password is the encryption key 
  
You can use the following example VBA code for a command button:
  
```
Private Sub Command0_Click()
Dim strSourcePath As String
Dim strDestPath As String
strSourcePath = "<path>\sourceDb.accdb"
strDestPath = "<path>\destDb.accdb"
DBEngine.CompactDatabase strSourcePath, strDestPath, dbLangGeneral &amp; ";pwd=Access", dbVersion120, ";pwd=Access"
Set CurrentDatabase = CurrentDb
Set LinkedTableDef = CurrentDatabase.CreateTableDef 
("My Linked Table")
LinkedTableDef.Connect = "MS Access;pwd=Access";database=" &amp; strDestPath
LinkedTableDef.RefreshLink
MsgBox "Finished"
End Sub 

```

The code sample below shows how to use **CompactDatabase** with a password (encryption key) and then link to a table in that compacted database. Note that a password must be supplied. 
  
```
Private Sub CompactAndLink_Click() 
 
Dim strSourcePath As String
Dim strDestPath As String
Dim strSourceTableName As String
Dim strDestTableName As String
Dim tdf As TableDef
 
strSourcePath = "<path>\<database>.accdb"
strDestPath = "<path>\<database>.accdb"
strSourceTableName = "<table name in destination database>"
strDestTableName = "<linked table name>"
 
' Compact source database into new destination database with encrypted password
DBEngine.CompactDatabase strSourcePath, strDestPath, dbLangGeneral &amp; ";pwd=Access", dbVersion120, ";pwd=Access"
 
' Link to one of the tables in the destination database
' Password must be provided in the Connect property
 
Set CurrentDatabase = CurrentDb
Set tdf = CurrentDatabase.CreateTableDef(strDestTableName)
   
    With tdf
        .Connect = ";pwd=Access" &amp; ";DATABASE=" &amp; strDestPath
        .SourceTableName = strSourceTableName
    End With
    
CurrentDatabase.TableDefs.Append tdf
 
MsgBox "Database compacted and encrypted password applied. Link to table also completed."
 
End Sub

```

