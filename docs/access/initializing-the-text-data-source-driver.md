---
title: "Initializing the Text Data Source Driver"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- acmain11.chm1032166
  
localization_priority: Normal
ms.assetid: cba0864e-5f94-bf43-4708-b1981e3acaff
description: "The same database driver is used for both Text Data sources and for HTML data sources."
---

# Initializing the Text Data Source Driver

The same database driver is used for both Text Data sources and for HTML data sources.
  
When you install the Text Data Source database driver, the Setup program writes a set of default values to the Microsoft® Windows® Registry in the Engines and ISAM Formats subkeys. You should not modify these settings directly; use the setup program for your application to add, remove, or change these settings. The following sections describe initialization and ISAM Format settings for the Text Data Source database driver.
  
## Text Data Source Initialization Settings

The **Access Connectivity Engine\ISAM Formats\Text folder** includes initialization settings for the Acetxt.dll driver, used for external access to text data files. Typical settings for the entries in this folder are shown in the following example. 
  
```
win32=<path>\ ACETXT.DLL 
MaxScanRows=25 
FirstRowHasNames=True 
CharacterSet= ANSI 
Format=CSVDelimited 
Extensions= txt,csv,tab,asc 
ExportCurrencySymbols=Yes
```

The Microsoft Access database engine uses the Text folder entries as follows.
  
|**Entry**|**Description**|
|:-----|:-----|
|win32  <br/> |The location of Acetxt.dll. The full path is determined at the time of installation. Values are of type REG_SZ.  <br/> |
|MaxScanRows  <br/> |The number of rows to be scanned when guessing the column types. If set to 0, the entire file will be searched. The default is 25. Values are of type REG_DWORD.  <br/> |
|FirstRowHasNames  <br/> |A binary value that indicates whether the first row of the table contains column names. A value of 01 indicates that, during import, column names are taken from the first row.  <br/> |
|CharacterSet  <br/> | An indicator of how text pages are stored. Possible settings are:  <br/>  ANSI — The ANSI code page of the machine. AnsiToUnicode and UnicodeToAnsi conversions done.  <br/>  OEM — The OEM code page of the machine. OemToUnicode and UnicodeToOem conversions done.  <br/>  Unicode — codepage conversions not done.  <br/>  \<decimal number\> — The code page number of a specific character set. Conversions to and from Unicode will be done.  <br/>  The default is ANSI. Values are of type REG_SZ.  <br/> |
|Format  <br/> |Can be any of the following: TabDelimited, CSVDelimited, Delimited (\<single character\>). The single-character delimiter in the Delimited format can be any single character except a double quotation mark ("). The default is CSVDelimited. Values are of type REG_SZ.  <br/> |
|Extensions  <br/> |The extension of any files to be browsed when looking for text-based data. The default is txt, csv, tab, asc. Values are of type REG_SZ.  <br/> |
|ExportCurrencySymbols  <br/> |A binary value that indicates whether the appropriate currency symbol is included when currency fields are exported. A value of 01 indicates that the symbol is included. A value of 00 indicates that only the numeric data is exported. The default is 01. Values are of type REG_BINARY.  <br/> |
   
## Text Data Source ISAM Formats

The **Access Connectivity Engine\ISAM Formats\Text** folder contains the following entries. 
  
|**Entry name**|**Type**|**Value**|
|:-----|:-----|:-----|
|Engine  <br/> |REG_SZ  <br/> |Text  <br/> |
|ExportFilter  <br/> |REG_SZ  <br/> |Text Files (\*.txt; \*.csv; \*.tab; \*.asc)  <br/> |
|ImportFilter  <br/> |REG_SZ  <br/> |Text Files (\*.txt; \*.csv; \*.tab; \*.asc)  <br/> |
|CanLink  <br/> |REG_BINARY  <br/> |01  <br/> |
|OneTablePerFile  <br/> |REG_BINARY  <br/> |01  <br/> |
|IsamType  <br/> |REG_DWORD  <br/> |2  <br/> |
|IndexDialog  <br/> |REG_BINARY  <br/> |00  <br/> |
|CreateDBOnExport  <br/> |REG_BINARY  <br/> |00  <br/> |
|ResultTextImport  <br/> |REG_SZ  <br/> |Import data from the external file into the current database. Changing data in the current database will not change data in the external file.  <br/> |
|ResultTextLink  <br/> |REG_SZ  <br/> |Create a table in the current database that is linked to the external file. Changing data in the current database will change data in the external file.  <br/> |
|ResultTextExport  <br/> |REG_SZ  <br/> |Export data from the current database into a text file. This process will overwrite the data if exported to an existing file.  <br/> |
|SupportsLongNames  <br/> |REG_BINARY  <br/> |01  <br/> |
   
> [!NOTE]
> When you change Windows Registry settings, you must exit and then restart the database engine for the new settings to take effect. 
  
## HTML Import ISAM Formats

The **Access Connectivity Engine\ISAM Formats\HTML Import** folder contains the following entries. 
  
|**Entry name**|**Type**|**Value**|
|:-----|:-----|:-----|
|Engine  <br/> |REG_SZ  <br/> |Text  <br/> |
|ImportFilter  <br/> |REG_SZ  <br/> |HTML Files (\*.ht\*)  <br/> |
|CanLink  <br/> |REG_BINARY  <br/> |01  <br/> |
|OneTablePerFile  <br/> |REG_BINARY  <br/> |00  <br/> |
|IsamType  <br/> |REG_DWORD  <br/> |2  <br/> |
|IndexDialog  <br/> |REG_BINARY  <br/> |00  <br/> |
|CreateDBOnExport  <br/> |REG_BINARY  <br/> |00  <br/> |
|ResultTextImport  <br/> |REG_SZ  <br/> |Import data from the external file into the current database. Changing data in the current database will not change data in the external file.  <br/> |
|ResultTextLink  <br/> |REG_SZ  <br/> |Create a table in the current database that is linked to the external file. Changing data in the current database will change data in the external file.  <br/> |
|SupportsLongNames  <br/> |REG_BINARY  <br/> |01  <br/> |
   
> [!NOTE]
> When you change Windows Registry settings, you must exit and then restart the database engine for the new settings to take effect. 
  
## HTML Export ISAM Formats

The **Access Connectivity Engine\ISAM Formats\HTML Export** folder contains the following entries. 
  
|**Entry name**|**Type**|**Value**|
|:-----|:-----|:-----|
|Engine  <br/> |REG_SZ  <br/> |Text  <br/> |
|ExportFilter  <br/> |REG_SZ  <br/> |HTML Files (\*.htm)  <br/> |
|CanLink  <br/> |REG_BINARY  <br/> |00  <br/> |
|OneTablePerFile  <br/> |REG_BINARY  <br/> |01  <br/> |
|IsamType  <br/> |REG_DWORD  <br/> |2  <br/> |
|IndexDialog  <br/> |REG_BINARY  <br/> |00  <br/> |
|CreateDBOnExport  <br/> |REG_BINARY  <br/> |00  <br/> |
|ResultTextExport  <br/> |REG_SZ  <br/> |Export data from the current database into a text file. This process will overwrite the data if exported to an existing file.  <br/> |
|SupportsLongNames  <br/> |REG_BINARY  <br/> |01  <br/> |
   
> [!NOTE]
> When you change Windows Registry settings, you must exit and then restart the database engine for the new settings to take effect. 
  
## Customizing the Schema.ini File for Text and HTML Data

To read, import, or export text and HTML data, you need to create a Schema.ini file in addition to including the Text ISAM information in the .ini file. Schema.ini contains the specifics of a data source: how the text file is formatted, how it is read at import time, and what the default export format is for files. The following examples show the layout for a fixed-width file, Filename.txt:
  
```
[Filename.txt] 
ColNameHeader=False 
Format=FixedLength 
FixedFormat= RaggedEdge 
MaxScanRows=25 
CharacterSet=OEM 
Col1=columnname Char Width 24 
Col2=columnname2 Date Width 9 
Col3=columnname7 Float Width 10 
Col4=columnname8 Integer Width 10 
Col5=columnname9 LongChar Width 10
```

Similarly, the format for a delimited file is specified as follows:
  
```
[Delimit.txt] 
ColNameHeader=True 
Format=Delimited() 
MaxScanRows=0 
CharacterSet=OEM 
Col1=username char width 50 
Col2=dateofbirth Date width 9
```

If you are exporting data into a delimited text file, specify the format for that file as well:
  
```
[Export: My Special Export] 
ColNameHeader=True 
Format=TabDelimited 
MaxScanRows=25 
CharacterSet=OEM 
DateTimeFormat=mm.dd.yy.hh.mm.ss 
CurrencySymbol=Dm 
CurrencyPosFormat=0 
CurrencyDigits=2 
CurrencyNegFormat=0 
CurrencyThousandSymbol=, 
CurrencyDecimalSymbol=. 
DecimalSymbol=, 
NumberDigits=2 
NumberLeadingZeros=0 
TextDelimeter="
```

The My Special Export example refers to a specific export option; you can specify any variation of export options at connect time. This last example also corresponds to a data source name (DSN) that can be optionally passed at connect time. All three format sections can be included in the same .ini file.
  
The Microsoft Access database engine uses the Schema.ini entries as follows.
  
|**Entry**|**Description**|
|:-----|:-----|
|ColNameHeader  <br/> |Can be set to either **True** (indicating that the first record of data specifies the column names) or **False**.  <br/> |
|Format  <br/> |Can be set to one of the following values: TabDelimited, CSVDelimited, Delimited (\<single character\>), or FixedLength. The delimiter specified for the Delimited file format can be any single character except a double quotation mark (").  <br/> |
|FixedFormat  <br/> |Only used when the Format is FixedLength, this can be set to one of the following values: RaggedEdge or TrueFixedLength. RaggedEdge allows rows to be terminated with a Carriage Return character. TrueFixedLength requires each row to be an exact number of characters, and any Carriage Return characters not at a row boundary are assumed to be embedded in a field. If this setting is not present, the default value is RaggedEdge.  <br/> |
|MaxScanRows  <br/> |Indicates the number of rows to be scanned when guessing the column data types. If this is set to 0, the entire file is searched.  <br/> |
|CharacterSet  <br/> |Can be set to OEM, ANSI, UNICODE, or the decimal number of a valid code page, and indicates the character set of the source file.  <br/> |
|DateTimeFormat  <br/> |Can be set to a format string indicating dates and times. This entry should be specified if all date/time fields in the import/export are handled with the same format. All of the Microsoft Jet database engine formats except AM and PM are supported. In the absence of a format string, the Windows Control Panel short date picture and time options are used.  <br/> |
|CurrencySymbol  <br/> |Indicates the currency symbol to be used for currency values in the text file. Examples include the dollar sign ($) and Dm. If this entry is absent, the default value in the Windows Control Panel is used.  <br/> |
|CurrencyPosFormat  <br/> |Can be set to any of the following values: Currency symbol prefix with no separation ($1) Currency symbol suffix with no separation (1$) Currency symbol prefix with one character separation ($ 1) Currency symbol suffix with one character separation (1 $) If this entry is absent, the default value in the Windows Control Panel is used.  <br/> |
|CurrencyDigits  <br/> |Specifies the number of digits used for the fractional part of a currency amount. If this entry is absent, the default value in the Windows Control Panel is used.  <br/> |
|CurrencyNegFormat  <br/> |Can be one of the following values: ($1) -$1 $-1 $1- (1$) -1$ 1-$ 1$- -1 $ -$ 1 1 $- $ 1- $ -1 1- $ ($ 1) (1 $) The dollar sign is shown for purposes of this example, but it should be replaced with the appropriate CurrencySymbol value in the actual program. If this entry is absent, the default value in the Windows Control Panel is used.  <br/> |
|CurrencyThousandSymbol  <br/> |Indicates the single-character symbol to be used for separating currency values by thousands in the text file. If this entry is absent, the default value in the Windows Control Panel is used.  <br/> |
|CurrencyDecimalSymbol  <br/> |Can be set to any single character that is used to separate the whole from the fractional part of a currency amount. If this entry is absent, the default value in the Windows Control Panel is used.  <br/> |
|DecimalSymbol  <br/> |Can be set to any single character that is used to separate the integer from the fractional part of a number. If this entry is absent, the default value in the Windows Control Panel is used.  <br/> |
|NumberDigits  <br/> |Indicates the number of decimal digits in the fractional portion of a number. If this entry is absent, the default value in the Windows Control Panel is used.  <br/> |
|NumberLeadingZeros  <br/> |Specifies whether a decimal value less than 1 and greater than -1 should contain leading zeros; this value can either be False (no leading zeros) or True.  <br/> |
|Col1, Col2, …  <br/> |Lists the columns in the text file to be read. The format of this entry should be: *Coln*  =  *columnName*  type [Width  *#*  ]  *columnName*  : Column names with embedded spaces should be enclosed in quotation marks.  *type*  : Can be Bit, Byte, Short, Long, Decimal, Currency, Single, Double, DateTime. Binary, OLE, Text, or Memo. In addition, the following ODBC Text Driver types are supported: Char (same as Text) Float (same as Double) Integer (same as Short) LongChar (same as Memo) Date  *date format*  In the case of a Memo type an additional format marker [Attribute Hyperlink] can be used to specify columns that should be active URLs in Microsoft Access. In the case of a Decimal type the additional format markers [Scale #] Precision #] should be used.  <br/> |
|TextDelimiter  <br/> |Can be set to any single character that is used to delimit strings that contain any of the other special characters. E.g. "abc","xyz,pqr","hij" If this entry is not present the default delimiter is a double quote. If this entry is the string "none" then no characters will be treated as delimiters.  <br/> |
   
> [!NOTE]
> When you change Schema.ini file settings, you must exit and then restart the database engine for the new settings to take effect. 
  

