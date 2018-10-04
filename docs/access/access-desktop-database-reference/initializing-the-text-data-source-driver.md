---
title: Initializing the Text Data Source Driver
TOCTitle: Initializing the Text Data Source Driver
ms:assetid: cba0864e-5f94-bf43-4708-b1981e3acaff
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff834391(v=office.15)
ms:contentKeyID: 48547718
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- acmain11.chm1032166
f1_categories:
- Office.Version=v15
---

# Initializing the Text Data Source Driver


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Text Data Source Initialization Settings  
Text Data Source ISAM Formats  
HTML Import ISAM Formats  
HTML Export ISAM Formats  
Customizing the Schema.ini File for Text and HTML Data  

The same database driver is used for both Text Data sources and for HTML data sources.

When you install the Text Data Source database driver, the Setup program writes a set of default values to the Microsoft® Windows® Registry in the Engines and ISAM Formats subkeys. You should not modify these settings directly; use the setup program for your application to add, remove, or change these settings. The following sections describe initialization and ISAM Format settings for the Text Data Source database driver.

## Text Data Source Initialization Settings

The **Access Connectivity Engine\\ISAM Formats\\Text folder** includes initialization settings for the Acetxt.dll driver, used for external access to text data files. Typical settings for the entries in this folder are shown in the following example.

    win32=<path>\ ACETXT.DLL 
    
    MaxScanRows=25 
    
    FirstRowHasNames=True 
    
    CharacterSet= ANSI 
    
    Format=CSVDelimited 
    
    Extensions= txt,csv,tab,asc 
    
    ExportCurrencySymbols=Yes

The Microsoft Access database engine uses the Text folder entries as follows.

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
<td><p>The location of Acetxt.dll. The full path is determined at the time of installation. Values are of type REG_SZ.</p></td>
</tr>
<tr class="even">
<td><p>MaxScanRows</p></td>
<td><p>The number of rows to be scanned when guessing the column types. If set to 0, the entire file will be searched. The default is 25. Values are of type REG_DWORD.</p></td>
</tr>
<tr class="odd">
<td><p>FirstRowHasNames</p></td>
<td><p>A binary value that indicates whether the first row of the table contains column names. A value of 01 indicates that, during import, column names are taken from the first row.</p></td>
</tr>
<tr class="even">
<td><p>CharacterSet</p></td>
<td><p>An indicator of how text pages are stored. Possible settings are:</p>
<p></p>
<ul>
<li><p>ANSI — The ANSI code page of the machine. AnsiToUnicode and UnicodeToAnsi conversions done.</p></li>
<li><p>OEM — The OEM code page of the machine. OemToUnicode and UnicodeToOem conversions done.</p></li>
<li><p>Unicode — codepage conversions not done.</p></li>
<li><p>&lt;decimal number&gt; — The code page number of a specific character set. Conversions to and from Unicode will be done.</p></li>
</ul>
<p></p>
<p>The default is ANSI. Values are of type REG_SZ.</p></td>
</tr>
<tr class="odd">
<td><p>Format</p></td>
<td><p>Can be any of the following: TabDelimited, CSVDelimited, Delimited (&lt;single character&gt;). The single-character delimiter in the Delimited format can be any single character except a double quotation mark (&quot;). The default is CSVDelimited. Values are of type REG_SZ.</p></td>
</tr>
<tr class="even">
<td><p>Extensions</p></td>
<td><p>The extension of any files to be browsed when looking for text-based data. The default is txt, csv, tab, asc. Values are of type REG_SZ.</p></td>
</tr>
<tr class="odd">
<td><p>ExportCurrencySymbols</p></td>
<td><p>A binary value that indicates whether the appropriate currency symbol is included when currency fields are exported. A value of 01 indicates that the symbol is included. A value of 00 indicates that only the numeric data is exported. The default is 01. Values are of type REG_BINARY.</p></td>
</tr>
</tbody>
</table>


## Text Data Source ISAM Formats

The **Access Connectivity Engine\\ISAM Formats\\Text** folder contains the following entries.

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
<td><p>Text</p></td>
</tr>
<tr class="even">
<td><p>ExportFilter</p></td>
<td><p>REG_SZ</p></td>
<td><p>Text Files (*.txt; *.csv; *.tab; *.asc)</p></td>
</tr>
<tr class="odd">
<td><p>ImportFilter</p></td>
<td><p>REG_SZ</p></td>
<td><p>Text Files (*.txt; *.csv; *.tab; *.asc)</p></td>
</tr>
<tr class="even">
<td><p>CanLink</p></td>
<td><p>REG_BINARY</p></td>
<td><p>01</p></td>
</tr>
<tr class="odd">
<td><p>OneTablePerFile</p></td>
<td><p>REG_BINARY</p></td>
<td><p>01</p></td>
</tr>
<tr class="even">
<td><p>IsamType</p></td>
<td><p>REG_DWORD</p></td>
<td><p>2</p></td>
</tr>
<tr class="odd">
<td><p>IndexDialog</p></td>
<td><p>REG_BINARY</p></td>
<td><p>00</p></td>
</tr>
<tr class="even">
<td><p>CreateDBOnExport</p></td>
<td><p>REG_BINARY</p></td>
<td><p>00</p></td>
</tr>
<tr class="odd">
<td><p>ResultTextImport</p></td>
<td><p>REG_SZ</p></td>
<td><p>Import data from the external file into the current database. Changing data in the current database will not change data in the external file.</p></td>
</tr>
<tr class="even">
<td><p>ResultTextLink</p></td>
<td><p>REG_SZ</p></td>
<td><p>Create a table in the current database that is linked to the external file. Changing data in the current database will change data in the external file.</p></td>
</tr>
<tr class="odd">
<td><p>ResultTextExport</p></td>
<td><p>REG_SZ</p></td>
<td><p>Export data from the current database into a text file. This process will overwrite the data if exported to an existing file.</p></td>
</tr>
<tr class="even">
<td><p>SupportsLongNames</p></td>
<td><p>REG_BINARY</p></td>
<td><p>01</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> <P>When you change Windows Registry settings, you must exit and then restart the database engine for the new settings to take effect.</P>



## HTML Import ISAM Formats

The **Access Connectivity Engine\\ISAM Formats\\HTML Import** folder contains the following entries.

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
<td><p>Text</p></td>
</tr>
<tr class="even">
<td><p>ImportFilter</p></td>
<td><p>REG_SZ</p></td>
<td><p>HTML Files (*.ht*)</p></td>
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
<td><p>2</p></td>
</tr>
<tr class="even">
<td><p>IndexDialog</p></td>
<td><p>REG_BINARY</p></td>
<td><p>00</p></td>
</tr>
<tr class="odd">
<td><p>CreateDBOnExport</p></td>
<td><p>REG_BINARY</p></td>
<td><p>00</p></td>
</tr>
<tr class="even">
<td><p>ResultTextImport</p></td>
<td><p>REG_SZ</p></td>
<td><p>Import data from the external file into the current database. Changing data in the current database will not change data in the external file.</p></td>
</tr>
<tr class="odd">
<td><p>ResultTextLink</p></td>
<td><p>REG_SZ</p></td>
<td><p>Create a table in the current database that is linked to the external file. Changing data in the current database will change data in the external file.</p></td>
</tr>
<tr class="even">
<td><p>SupportsLongNames</p></td>
<td><p>REG_BINARY</p></td>
<td><p>01</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> <P>When you change Windows Registry settings, you must exit and then restart the database engine for the new settings to take effect.</P>



## HTML Export ISAM Formats

The **Access Connectivity Engine\\ISAM Formats\\HTML Export** folder contains the following entries.

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
<td><p>Text</p></td>
</tr>
<tr class="even">
<td><p>ExportFilter</p></td>
<td><p>REG_SZ</p></td>
<td><p>HTML Files (*.htm)</p></td>
</tr>
<tr class="odd">
<td><p>CanLink</p></td>
<td><p>REG_BINARY</p></td>
<td><p>00</p></td>
</tr>
<tr class="even">
<td><p>OneTablePerFile</p></td>
<td><p>REG_BINARY</p></td>
<td><p>01</p></td>
</tr>
<tr class="odd">
<td><p>IsamType</p></td>
<td><p>REG_DWORD</p></td>
<td><p>2</p></td>
</tr>
<tr class="even">
<td><p>IndexDialog</p></td>
<td><p>REG_BINARY</p></td>
<td><p>00</p></td>
</tr>
<tr class="odd">
<td><p>CreateDBOnExport</p></td>
<td><p>REG_BINARY</p></td>
<td><p>00</p></td>
</tr>
<tr class="even">
<td><p>ResultTextExport</p></td>
<td><p>REG_SZ</p></td>
<td><p>Export data from the current database into a text file. This process will overwrite the data if exported to an existing file.</p></td>
</tr>
<tr class="odd">
<td><p>SupportsLongNames</p></td>
<td><p>REG_BINARY</p></td>
<td><p>01</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> <P>When you change Windows Registry settings, you must exit and then restart the database engine for the new settings to take effect.</P>



## Customizing the Schema.ini File for Text and HTML Data

To read, import, or export text and HTML data, you need to create a Schema.ini file in addition to including the Text ISAM information in the .ini file. Schema.ini contains the specifics of a data source: how the text file is formatted, how it is read at import time, and what the default export format is for files. The following examples show the layout for a fixed-width file, Filename.txt:

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

Similarly, the format for a delimited file is specified as follows:

    [Delimit.txt] 
    
    ColNameHeader=True 
    
    Format=Delimited() 
    
    MaxScanRows=0 
    
    CharacterSet=OEM 
    
    Col1=username char width 50 
    
    Col2=dateofbirth Date width 9

If you are exporting data into a delimited text file, specify the format for that file as well:

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

The My Special Export example refers to a specific export option; you can specify any variation of export options at connect time. This last example also corresponds to a data source name (DSN) that can be optionally passed at connect time. All three format sections can be included in the same .ini file.

The Microsoft Access database engine uses the Schema.ini entries as follows.

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
<td><p>ColNameHeader</p></td>
<td><p>Can be set to either <strong>True</strong> (indicating that the first record of data specifies the column names) or <strong>False</strong>.</p></td>
</tr>
<tr class="even">
<td><p>Format</p></td>
<td><p>Can be set to one of the following values: TabDelimited, CSVDelimited, Delimited (&lt;single character&gt;), or FixedLength. The delimiter specified for the Delimited file format can be any single character except a double quotation mark (&quot;).</p></td>
</tr>
<tr class="odd">
<td><p>FixedFormat</p></td>
<td><p>Only used when the Format is FixedLength, this can be set to one of the following values: RaggedEdge or TrueFixedLength. RaggedEdge allows rows to be terminated with a Carriage Return character. TrueFixedLength requires each row to be an exact number of characters, and any Carriage Return characters not at a row boundary are assumed to be embedded in a field. If this setting is not present, the default value is RaggedEdge.</p></td>
</tr>
<tr class="even">
<td><p>MaxScanRows</p></td>
<td><p>Indicates the number of rows to be scanned when guessing the column data types. If this is set to 0, the entire file is searched.</p></td>
</tr>
<tr class="odd">
<td><p>CharacterSet</p></td>
<td><p>Can be set to OEM, ANSI, UNICODE, or the decimal number of a valid code page, and indicates the character set of the source file.</p></td>
</tr>
<tr class="even">
<td><p>DateTimeFormat</p></td>
<td><p>Can be set to a format string indicating dates and times. This entry should be specified if all date/time fields in the import/export are handled with the same format. All of the Microsoft Jet database engine formats except AM and PM are supported. In the absence of a format string, the Windows Control Panel short date picture and time options are used.</p></td>
</tr>
<tr class="odd">
<td><p>CurrencySymbol</p></td>
<td><p>Indicates the currency symbol to be used for currency values in the text file. Examples include the dollar sign ($) and Dm. If this entry is absent, the default value in the Windows Control Panel is used.</p></td>
</tr>
<tr class="even">
<td><p>CurrencyPosFormat</p></td>
<td><p>Can be set to any of the following values: Currency symbol prefix with no separation ($1) Currency symbol suffix with no separation (1$) Currency symbol prefix with one character separation ($ 1) Currency symbol suffix with one character separation (1 $) If this entry is absent, the default value in the Windows Control Panel is used.</p></td>
</tr>
<tr class="odd">
<td><p>CurrencyDigits</p></td>
<td><p>Specifies the number of digits used for the fractional part of a currency amount. If this entry is absent, the default value in the Windows Control Panel is used.</p></td>
</tr>
<tr class="even">
<td><p>CurrencyNegFormat</p></td>
<td><p>Can be one of the following values: ($1) –$1 $–1 $1– (1$) –1$ 1–$ 1$– –1 $ –$ 1 1 $– $ 1– $ –1 1– $ ($ 1) (1 $) The dollar sign is shown for purposes of this example, but it should be replaced with the appropriate CurrencySymbol value in the actual program. If this entry is absent, the default value in the Windows Control Panel is used.</p></td>
</tr>
<tr class="odd">
<td><p>CurrencyThousandSymbol</p></td>
<td><p>Indicates the single-character symbol to be used for separating currency values by thousands in the text file. If this entry is absent, the default value in the Windows Control Panel is used.</p></td>
</tr>
<tr class="even">
<td><p>CurrencyDecimalSymbol</p></td>
<td><p>Can be set to any single character that is used to separate the whole from the fractional part of a currency amount. If this entry is absent, the default value in the Windows Control Panel is used.</p></td>
</tr>
<tr class="odd">
<td><p>DecimalSymbol</p></td>
<td><p>Can be set to any single character that is used to separate the integer from the fractional part of a number. If this entry is absent, the default value in the Windows Control Panel is used.</p></td>
</tr>
<tr class="even">
<td><p>NumberDigits</p></td>
<td><p>Indicates the number of decimal digits in the fractional portion of a number. If this entry is absent, the default value in the Windows Control Panel is used.</p></td>
</tr>
<tr class="odd">
<td><p>NumberLeadingZeros</p></td>
<td><p>Specifies whether a decimal value less than 1 and greater than –1 should contain leading zeros; this value can either be False (no leading zeros) or True.</p></td>
</tr>
<tr class="even">
<td><p>Col1, Col2, …</p></td>
<td><p>Lists the columns in the text file to be read. The format of this entry should be: <em>Coln</em>=<em>columnName</em> type [Width <em>#</em>] <em>columnName</em>: Column names with embedded spaces should be enclosed in quotation marks. <em>type</em>: Can be Bit, Byte, Short, Long, Decimal, Currency, Single, Double, DateTime. Binary, OLE, Text, or Memo. In addition, the following ODBC Text Driver types are supported: Char (same as Text) Float (same as Double) Integer (same as Short) LongChar (same as Memo) Date <em>date format</em> In the case of a Memo type an additional format marker [Attribute Hyperlink] can be used to specify columns that should be active URLs in Microsoft Access. In the case of a Decimal type the additional format markers [Scale #] Precision #] should be used.</p></td>
</tr>
<tr class="odd">
<td><p>TextDelimiter</p></td>
<td><p>Can be set to any single character that is used to delimit strings that contain any of the other special characters. E.g. &quot;abc&quot;,&quot;xyz,pqr&quot;,&quot;hij&quot; If this entry is not present the default delimiter is a double quote. If this entry is the string &quot;none&quot; then no characters will be treated as delimiters.</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> <P>When you change Schema.ini file settings, you must exit and then restart the database engine for the new settings to take effect.</P>


