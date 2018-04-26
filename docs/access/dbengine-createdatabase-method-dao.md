---
title: "DBEngine.CreateDatabase Method (DAO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
f1_keywords:
- dao360.chm1052972
  
localization_priority: Normal
ms.assetid: d5821a4b-483a-b8fa-e929-5f036057d8c4
description: "Creates a new Database object, saves the database to disk, and returns an opened Database object (Microsoft Access workspaces only). ."
---

# DBEngine.CreateDatabase Method (DAO)

Creates a new **[Database](database-object-dao.md)** object, saves the database to disk, and returns an opened **Database** object (Microsoft Access workspaces only). . 
  
## Syntax

 *expression*  . **CreateDatabase**( ** *Name* **, ** *Locale* **, ** *Option* ** ) 
  
 *expression*  A variable that represents a **DBEngine** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Name_ <br/> |Required  <br/> |**String** <br/> |A String up to 255 characters long that is the name of the database file that you're creating. It can be the full path and file name. If your network supports it, you can also specify a network path, such as "\\server1\share1\dir1\db1". You can only create Microsoft Access database files with this method.  <br/> |
| _Locale_ <br/> |Required  <br/> |**String** <br/> | A string expression that specifies a collating order for creating the database, as specified in Settings. You must supply this argument or an error occurs.  <br/>  You can also create a password for the new **Database** object by concatenating the password string (starting with  `";pwd="`) with a constant in the  *locale*  argument, like this:  <br/>  `dbLangSpanish &amp; ";pwd=NewPassword"` <br/>  If you want to use the default  *locale*  , but specify a password, simply enter a password string for the  *locale*  argument:  <br/>  `";pwd=NewPassword"` <br/>  Use strong passwords that combine upper- and lowercase letters, numbers, and symbols. Weak passwords don't mix these elements. Strong password: Y6dh!et5. Weak password: House27. Use a strong password that you can remember so that you don't have to write it down.  <br/> |
| _Option_ <br/> |Optional  <br/> |**Variant** <br/> |A constant or combination of constants that indicates one or more options, as specified in Settings. You can combine options by summing the corresponding constants.  <br/> |
   
## Remarks

You can use one of the following constants for the locale argument to specify the **[CollatingOrder](database-collatingorder-property-dao.md)** property of text for string comparisons. 
  
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
   
You can use one or more of the following constants in the options argument to specify which version the data format should have and whether or not to encrypt the database.
  
|**Constant**|**Description**|
|:-----|:-----|
|**dbEncrypt** <br/> |Creates an encrypted database.  <br/> |
|**dbVersion10** <br/> |Creates a database that uses the Microsoft Jet database engine version 1.0 file format.  <br/> |
|**dbVersion11** <br/> |Creates a database that uses the Microsoft Jet database engine version 1.1 file format.  <br/> |
|**dbVersion20** <br/> |Creates a database that uses the Microsoft Jet database engine version 2.0 file format.  <br/> |
|**dbVersion30** <br/> |Creates a database that uses the Microsoft Jet database engine version 3.0 file format (compatible with version 3.5).  <br/> |
|**dbVersion40** <br/> |Creates a database that uses the Microsoft Jet database engine version 4.0 file format.  <br/> |
|**dbVersion120** <br/> |Creates a database that uses the Microsoft Access database engine version 12.0 file format.  <br/> |
   
If you omit the encryption constant, **CreateDatabase** creates an un-encrypted database. 
  
Use the **CreateDatabase** method to create and open a new, empty database, and return the **Database** object. You must complete its structure and content by using additional DAO objects. If you want to make a partial or complete copy of an existing database, you can use the **[CompactDatabase](dbengine-compactdatabase-method-dao.md)** method to make a copy that you can customize. 
  

