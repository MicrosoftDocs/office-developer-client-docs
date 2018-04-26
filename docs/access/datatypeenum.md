---
title: "DataTypeEnum"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: a8ab7616-552f-ed5f-ed55-95254cfb374a
---

# DataTypeEnum

Specifies the data type of a [Field](field-object-ado.md), [Parameter](parameter-object-ado.md), or [Property](property-object-ado.md). The corresponding OLE DB type indicator is shown in parentheses in the description column of the following table. For more information about OLE DB data types, see Chapter 13 and Appendix A of the  *OLE DB Programmer's Reference*  . 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**AdArray         ** (Does not apply to ADOX.)  <br/> |0x2000  <br/> |A flag value, always combined with another data type constant, that indicates an array of that other data type.  <br/> |
|**adBigInt** <br/> |20  <br/> |Indicates an eight-byte signed integer (DBTYPE_I8).  <br/> |
|**adBinary** <br/> |128  <br/> |Indicates a binary value (DBTYPE_BYTES).  <br/> |
|**adBoolean** <br/> |11  <br/> |Indicates a boolean value (DBTYPE_BOOL).  <br/> |
|**adBSTR** <br/> |8  <br/> |Indicates a null-terminated character string (Unicode) (DBTYPE_BSTR).  <br/> |
|**adChapter** <br/> |136  <br/> |Indicates a four-byte chapter value that identifies rows in a child rowset (DBTYPE_HCHAPTER).  <br/> |
|**adChar** <br/> |129  <br/> |Indicates a string value (DBTYPE_STR).  <br/> |
|**adCurrency** <br/> |6  <br/> |Indicates a currency value (DBTYPE_CY). Currency is a fixed-point number with four digits to the right of the decimal point. It is stored in an eight-byte signed integer scaled by 10,000.  <br/> |
|**adDate** <br/> |7  <br/> |Indicates a date value (DBTYPE_DATE). A date is stored as a double, the whole part of which is the number of days since December 30, 1899, and the fractional part of which is the fraction of a day.  <br/> |
|**adDBDate** <br/> |133  <br/> |Indicates a date value (yyyymmdd) (DBTYPE_DBDATE).  <br/> |
|**adDBTime** <br/> |134  <br/> |Indicates a time value (hhmmss) (DBTYPE_DBTIME).  <br/> |
|**adDBTimeStamp** <br/> |135  <br/> |Indicates a date/time stamp (yyyymmddhhmmss plus a fraction in billionths) (DBTYPE_DBTIMESTAMP).  <br/> |
|**adDecimal** <br/> |14  <br/> |Indicates an exact numeric value with a fixed precision and scale (DBTYPE_DECIMAL).  <br/> |
|**adDouble** <br/> |5  <br/> |Indicates a double-precision floating-point value (DBTYPE_R8).  <br/> |
|**adEmpty** <br/> |0  <br/> |Specifies no value (DBTYPE_EMPTY).  <br/> |
|**adError** <br/> |10  <br/> |Indicates a 32-bit error code (DBTYPE_ERROR).  <br/> |
|**adFileTime** <br/> |64  <br/> |Indicates a 64-bit value representing the number of 100-nanosecond intervals since January 1, 1601 (DBTYPE_FILETIME).  <br/> |
|**adGUID** <br/> |72  <br/> |Indicates a globally unique identifier (GUID) (DBTYPE_GUID).  <br/> |
|**adIDispatch** <br/> |9  <br/> |Indicates a pointer to an **IDispatch** interface on a COM object (DBTYPE_IDISPATCH).  <br/> > [!NOTE]> This data type is currently not supported by ADO. Usage may cause unpredictable results.           |
|**adInteger** <br/> |3  <br/> |Indicates a four-byte signed integer (DBTYPE_I4).  <br/> |
|**adIUnknown** <br/> |13  <br/> |Indicates a pointer to an **IUnknown** interface on a COM object (DBTYPE_IUNKNOWN).  <br/> > [!NOTE]> This data type is currently not supported by ADO. Usage may cause unpredictable results.           |
|**adLongVarBinary** <br/> |205  <br/> |Indicates a long binary value.  <br/> |
|**adLongVarChar** <br/> |201  <br/> |Indicates a long string value.  <br/> |
|**adLongVarWChar** <br/> |203  <br/> |Indicates a long null-terminated Unicode string value.  <br/> |
|**adNumeric** <br/> |131  <br/> |Indicates an exact numeric value with a fixed precision and scale (DBTYPE_NUMERIC).  <br/> |
|**adPropVariant** <br/> |138  <br/> |Indicates an Automation PROPVARIANT (DBTYPE_PROP_VARIANT).  <br/> |
|**adSingle** <br/> |4  <br/> |Indicates a single-precision floating-point value (DBTYPE_R4).  <br/> |
|**adSmallInt** <br/> |2  <br/> |Indicates a two-byte signed integer (DBTYPE_I2).  <br/> |
|**adTinyInt** <br/> |16  <br/> |Indicates a one-byte signed integer (DBTYPE_I1).  <br/> |
|**adUnsignedBigInt** <br/> |21  <br/> |Indicates an eight-byte unsigned integer (DBTYPE_UI8).  <br/> |
|**adUnsignedInt** <br/> |19  <br/> |Indicates a four-byte unsigned integer (DBTYPE_UI4).  <br/> |
|**adUnsignedSmallInt** <br/> |18  <br/> |Indicates a two-byte unsigned integer (DBTYPE_UI2).  <br/> |
|**adUnsignedTinyInt** <br/> |17  <br/> |Indicates a one-byte unsigned integer (DBTYPE_UI1).  <br/> |
|**adUserDefined** <br/> |132  <br/> |Indicates a user-defined variable (DBTYPE_UDT).  <br/> |
|**adVarBinary** <br/> |204  <br/> |Indicates a binary value ( **Parameter** object only).  <br/> |
|**adVarChar** <br/> |200  <br/> |Indicates a string value.  <br/> |
|**adVariant** <br/> |12  <br/> |Indicates an Automation **Variant** (DBTYPE_VARIANT).  <br/> > [!NOTE]> This data type is currently not supported by ADO. Usage may cause unpredictable results.           |
|**adVarNumeric** <br/> |139  <br/> |Indicates a numeric value ( **Parameter** object only).  <br/> |
|**adVarWChar** <br/> |202  <br/> |Indicates a null-terminated Unicode character string.  <br/> |
|**adWChar** <br/> |130  <br/> |Indicates a null-terminated Unicode character string (DBTYPE_WSTR).  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.DataType.ARRAY  <br/> |
|AdoEnums.DataType.BIGINT  <br/> |
|AdoEnums.DataType.BINARY  <br/> |
|AdoEnums.DataType.BOOLEAN  <br/> |
|AdoEnums.DataType.BSTR  <br/> |
|AdoEnums.DataType.CHAPTER  <br/> |
|AdoEnums.DataType.CHAR  <br/> |
|AdoEnums.DataType.CURRENCY  <br/> |
|AdoEnums.DataType.DATE  <br/> |
|AdoEnums.DataType.DBDATE  <br/> |
|AdoEnums.DataType.DBTIME  <br/> |
|AdoEnums.DataType.DBTIMESTAMP  <br/> |
|AdoEnums.DataType.DECIMAL  <br/> |
|AdoEnums.DataType.DOUBLE  <br/> |
|AdoEnums.DataType.EMPTY  <br/> |
|AdoEnums.DataType.ERROR  <br/> |
|AdoEnums.DataType.FILETIME  <br/> |
|AdoEnums.DataType.GUID  <br/> |
|AdoEnums.DataType.IDISPATCH  <br/> |
|AdoEnums.DataType.INTEGER  <br/> |
|AdoEnums.DataType.IUNKNOWN  <br/> |
|AdoEnums.DataType.LONGVARBINARY  <br/> |
|AdoEnums.DataType.LONGVARCHAR  <br/> |
|AdoEnums.DataType.LONGVARWCHAR  <br/> |
|AdoEnums.DataType.NUMERIC  <br/> |
|AdoEnums.DataType.PROPVARIANT  <br/> |
|AdoEnums.DataType.SINGLE  <br/> |
|AdoEnums.DataType.SMALLINT  <br/> |
|AdoEnums.DataType.TINYINT  <br/> |
|AdoEnums.DataType.UNSIGNEDBIGINT  <br/> |
|AdoEnums.DataType.UNSIGNEDINT  <br/> |
|AdoEnums.DataType.UNSIGNEDSMALLINT  <br/> |
|AdoEnums.DataType.UNSIGNEDTINYINT  <br/> |
|AdoEnums.DataType.USERDEFINED  <br/> |
|AdoEnums.DataType.VARBINARY  <br/> |
|AdoEnums.DataType.VARCHAR  <br/> |
|AdoEnums.DataType.VARIANT  <br/> |
|AdoEnums.DataType.VARNUMERIC  <br/> |
|AdoEnums.DataType.VARWCHAR  <br/> |
|AdoEnums.DataType.WCHAR  <br/> |
   

