---
title: "Initializing the Microsoft Exchange Data Source Driver"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- acmain11.chm1032667
  
localization_priority: Normal
ms.assetid: cf87a746-f846-1a01-f4ec-20a25e335193
description: "When you install the Microsoft® Exchange Data Source driver, the Setup program writes a set of default values to the Microsoft Windows® Registry in the Engines and ISAM Formats subkeys. You should not modify these settings directly; use the setup program for your application to add, remove, or change these settings. The following sections describe initialization and ISAM Format settings for the Microsoft Exchange Data Source driver."
---

# Initializing the Microsoft Exchange Data Source Driver

When you install the Microsoft® Exchange Data Source driver, the Setup program writes a set of default values to the Microsoft Windows® Registry in the Engines and ISAM Formats subkeys. You should not modify these settings directly; use the setup program for your application to add, remove, or change these settings. The following sections describe initialization and ISAM Format settings for the Microsoft Exchange Data Source driver.
  
## Microsoft Exchange Data Source Initialization Settings

The **Access Connectivity Engine\Engines\Exchange** folder includes initialization settings for the Aceexch.dll driver, used for external access to Microsoft Outlook and Microsoft Exchange folders. The only entry in this folder is the following: 
  
```
win32=<path>\ACEEXCH.DLL

```

The Microsoft Access database engine uses this setting to indicate the location of Aceexch.dll. The full path is determined at the time of installation. Values are of type REG_SZ.
  
The results of using the Outlook ISAM format and of using the Exchange client ISAM format are similar. The only difference is that the two different clients use different names for the same columns. The two ISAM formats have been created so that the Microsoft Access database engine can return the column names in the particular style that the user desires.
  
## Microsoft Outlook Client ISAM Formats

The **Access Connectivity Engine\ISAM Formats\Outlook 9.0** folder contains the following entries. 
  
|**Entry name**|**Type**|**Value**|
|:-----|:-----|:-----|
|Engine  <br/> |REG_SZ  <br/> |Exchange  <br/> |
|ImportFilter  <br/> |REG_SZ  <br/> |Outlook()  <br/> |
|CanLink  <br/> |REG_BINARY  <br/> |01  <br/> |
|OneTablePerFile  <br/> |REG_BINARY  <br/> |00  <br/> |
|IsamType  <br/> |REG_DWORD  <br/> |3  <br/> |
|IndexDialog  <br/> |REG_BINARY  <br/> |00  <br/> |
|CreateDBOnExport  <br/> |REG_BINARY  <br/> |00  <br/> |
|SupportsLongNames  <br/> |REG_BINARY  <br/> |01  <br/> |
   
> [!NOTE]
> When you change Windows Registry settings, you must exit and then restart the database engine for the new settings to take effect. 
  
## Microsoft Exchange Client ISAM Formats

The **Access Connectivity Engine\ISAM Formats\Exchange 4.0** folder contains the following entries. 
  
|**Entry name**|**Type**|**Value**|
|:-----|:-----|:-----|
|Engine  <br/> |REG_SZ  <br/> |Exchange  <br/> |
|ImportFilter  <br/> |REG_SZ  <br/> |Exchange()  <br/> |
|CanLink  <br/> |REG_BINARY  <br/> |01  <br/> |
|OneTablePerFile  <br/> |REG_BINARY  <br/> |00  <br/> |
|IsamType  <br/> |REG_DWORD  <br/> |3  <br/> |
|IndexDialog  <br/> |REG_BINARY  <br/> |00  <br/> |
|CreateDBOnExport  <br/> |REG_BINARY  <br/> |00  <br/> |
|SupportsLongNames  <br/> |REG_BINARY  <br/> |01  <br/> |
   
> [!NOTE]
> When you change Windows Registry settings, you must exit and then restart the database engine for the new settings to take effect. 
  
## Customizing the Schema.ini File for Outlook and Exchange Data

The Schema.ini file is used by the Outlook and Exchange ISAM in much the same way that it is used by the Text ISAM. Schema.ini contains the specifics of a data source: how the data is formatted, and the names of columns that should be accessed.
  
It is not necessary to modify the Schema.ini file before data can be read, imported, or exported for Outlook and Exchange. Many of the settings inside the Schema.ini file for Outlook and Exchange are specific to internal tags that MAPI requires. You should not attempt to modify those tag values.
  

