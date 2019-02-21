---
title: Initializing the Microsoft Excel driver
TOCTitle: Initializing the Microsoft Excel driver
ms:assetid: 06c7f823-8e74-0811-cc00-e6b32075ef11
ms:mtpsurl: https://msdn.microsoft.com/library/Ff844939(v=office.15)
ms:contentKeyID: 48543054
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- acmain11.chm1032159
f1_categories:
- Office.Version=v15
localization_priority: Normal
---

# Initializing the Microsoft Excel driver

**Applies to**: Access 2013 | Office 2013

When you install the Excel driver, the Setup program writes a set of default values to the Windows Registry in the Engines and ISAM Formats subkeys. You should not modify these settings directly; use the setup program for your application to add, remove, or change these settings. The following sections describe initialization and ISAM Format settings for the Microsoft Excel database driver.

## Excel initialization settings

The **Access Connectivity Engine\\Engines\\Excel** folder includes initialization settings for the Aceexcl.dll driver, used for external access to Microsoft Excel worksheets. Typical settings for the entries in this folder are shown in the following example.

```vb
    win32=<path>\ Aceexcl.dll  
    
    TypeGuessRows=8 
    
    ImportMixedTypes=Text 
    
    AppendBlankRows=1 
    
    FirstRowHasNames=Yes
```

The Microsoft Access database engine uses the Excel folder entries as follows.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Entry</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>win32</p></td>
<td><p>The location of msexcl40.dll. The full path is determined at the time of installation. Values are of type REG_SZ.</p></td>
</tr>
<tr class="even">
<td><p>TypeGuessRows</p></td>
<td><p>The number of rows to be checked for the data type. The data type is determined given the maximum number of kinds of data found. If there is a tie, the data type is determined in the following order: Number, Currency, Date, Text, Boolean. If data is encountered that does not match the data type guessed for the column, it is returned as a <strong>Null</strong> value. On import, if a column has mixed data types, the entire column will be cast according to the ImportMixedTypes setting. The default number of rows to be checked is 8. Values are of type REG_DWORD.</p></td>
</tr>
<tr class="odd">
<td><p>ImportMixedTypes</p></td>
<td><p>Can be set to MajorityType or Text. If set to MajorityType, columns of mixed data types will be cast to the predominate data type on import. If set to Text, columns of mixed data types will be cast to Text on import. The default is Text. Values are of type REG_SZ.</p></td>
</tr>
<tr class="even">
<td><p>AppendBlankRows</p></td>
<td><p>The number of blank rows to be appended to the end of a Version 3.5 or Version 4.0 worksheet before new data is added. For example, if AppendBlankRows is set to 4, Microsoft Jet will append 4 blank rows to the end of the worksheet before appending rows that contain data. Integer values for this setting can range from 0 to 16; the default is 01 (one additional row appended). Values are of type REG_DWORD.</p></td>
</tr>
<tr class="odd">
<td><p>FirstRowHasNames</p></td>
<td><p>A binary value that indicates whether the first row of the table contains column names. A value of 01 indicates that, during import, column names are taken from the first row. A value of 00 indicates no column names in the first row; column names appear as F1, F2, F3, and so on. The default is 01. Values are of type REG_BINARY.</p></td>
</tr>
</tbody>
</table>

<br/>

The **Access Connectivity Engine\\Engines\\Excel 8.0** folder contains the following entries, which apply to Microsoft Excel 97.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Entry name</p></th>
<th><p>Type</p></th>
<th><p>Value</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Engine</p></td>
<td><p>REG_SZ</p></td>
<td><p>Excel</p></td>
</tr>
<tr class="even">
<td><p>ExportFilter</p></td>
<td><p>REG_SZ</p></td>
<td><p>Microsoft Excel 97-2000 (*.xls)</p></td>
</tr>
<tr class="odd">
<td><p>CanLink</p></td>
<td><p>REG_BINARY</p></td>
<td><p>01</p></td>
</tr>
<tr class="even">
<td><p>OneTablePerFile</p></td>
<td><p>REG_BINARY</p></td>
<td><p>00</p></td>
</tr>
<tr class="odd">
<td><p>IsamType</p></td>
<td><p>REG_DWORD</p></td>
<td><p>1</p></td>
</tr>
<tr class="even">
<td><p>IndexDialog</p></td>
<td><p>REG_BINARY</p></td>
<td><p>00</p></td>
</tr>
<tr class="odd">
<td><p>CreateDBOnExport</p></td>
<td><p>REG_BINARY</p></td>
<td><p>01</p></td>
</tr>
<tr class="even">
<td><p>ResultTextExport</p></td>
<td><p>REG_SZ</p></td>
<td><p>Export data from the current database into a Microsoft Excel 97 file. This process will overwrite the data if exported to an existing file.</p></td>
</tr>
<tr class="odd">
<td><p>SupportsLongNames</p></td>
<td><p>REG_BINARY</p></td>
<td><p>01</p></td>
</tr>
</tbody>
</table>

## Using the TypeGuessRows setting for Excel Driver
When you use Microsoft Excel Driver, you can use the **TypeGuessRows** registry value to configure how many rows are to be checked for the data type. The **TypeGuessRows** value is located under the following registry subkey:

# [Office 2016](#tab/office-2016)

For an MSI installation of Office

- For 32-bit Office on 32-bit Windows or 64-bit Office on 64-bit Windows:
    
**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\16.0\Access Connectivity Engine\Engines\Excel**

- For 32-bit Office on 64-bit Windows:

**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Office\16.0\Access Connectivity Engine\Engines\Excel**
    
For a Click-to-Run installation of Office

- For 32-bit Office on 32-bit Windows or 64-bit Office on 64-bit Windows:
    
**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\REGISTRY\MACHINE\Software\Microsoft\Office\16.0\Access Connectivity Engine\Engines\Excel**

- For 32-bit Office on 64-bit Windows:
    
**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\REGISTRY\MACHINE\Software\Wow6432Node\Microsoft\Office\16.0\Access Connectivity Engine\Engines\Excel**

The default number of rows to be checked is **8** (eight). When you set the **TypeGuessRows** value to **0** (zero), Excel Driver checks the first 16,384 rows for the data type. If you want to check more than 16,384 rows, set **TypeGuessRows** to a value that is based on your desired range. To check all rows, set **TypeGuessRows** to 1,048,576 (the maximum number of rows that are allowed in Excel).
 
The data type is determined by the maximum number of kinds of data that is found. If there is a tie, the data type is determined in the following order:

- Number
- Currency
- Date
- Text
- Boolean

If data is encountered that doesn’t match the guessed data type for the column, that data is returned as a **Null** value. During an import, if a column has mixed data types, the whole column is cast to the data type that’s set by the **ImportMixedTypes** setting.

# [Office 2013](#tab/office-2013)

For 32-bit Office on 32-bit Windows or 64-bit Office on 64-bit Windows:

**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Access Connectivity Engine\Engines\Excel**

For 32-bit Office on 64-bit Windows:

**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Office\15.0\Access Connectivity Engine\Engines\Excel**

The default number of rows to be checked is **8** (eight). When you set the **TypeGuessRows** value to **0** (zero), Excel Driver checks the first 16,384 rows for the data type. If you want to check more than 16,384 rows, set **TypeGuessRows** to a value that is based on your desired range. To check all rows, set **TypeGuessRows** to 1,048,576 (the maximum number of rows that are allowed in Excel).
 
The data type is determined by the maximum number of kinds of data that is found. If there is a tie, the data type is determined in the following order:

- Number
- Currency
- Date
- Text
- Boolean

If data is encountered that doesn’t match the guessed data type for the column, that data is returned as a **Null** value. During an import, if a column has mixed data types, the whole column is cast to the data type that’s set by the **ImportMixedTypes** setting.

# [Office 2010](#tab/office-2010)

For 32-bit Office on 32-bit Windows or 64-bit Office on 64-bit Windows:

**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Access Connectivity Engine\Engines\Excel**

For 32-bit Office on 64-bit Windows:

**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Office\15.0\Access Connectivity Engine\Engines\Excel**

The default number of rows to be checked is **8** (eight). When you set the **TypeGuessRows** value to **0** (zero), Excel Driver checks the first 16,384 rows for the data type. If you want to check more than 16,384 rows, set **TypeGuessRows** to a value that is based on your desired range. To check all rows, set **TypeGuessRows** to 1,048,576 (the maximum number of rows that are allowed in Excel).
 
The data type is determined by the maximum number of kinds of data that is found. If there is a tie, the data type is determined in the following order:

- Number
- Currency
- Date
- Text
- Boolean

If data is encountered that doesn’t match the guessed data type for the column, that data is returned as a **Null** value. During an import, if a column has mixed data types, the whole column is cast to the data type that’s set by the **ImportMixedTypes** setting.

---
> [!NOTE]
> When you change Windows Registry settings, you must exit and then restart the database engine for the new settings to take effect.

## See also

- [Using the TypeGuessRows setting for Excel Driver](https://support.office.com/en-us/article/using-the-typeguessrows-setting-for-excel-driver-6aa3e101-2a90-47ac-bf0f-7d4109a5708b?ui=en-US&rs=en-US&ad=US)
