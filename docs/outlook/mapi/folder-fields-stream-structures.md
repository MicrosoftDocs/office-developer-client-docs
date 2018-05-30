---
title: "Folder Fields Stream Structures"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
localization_priority: Normal
ms.assetid: edbc9e6c-008c-4c13-9a0c-cb47ac0f3686
description: "Last modified: March 09, 2015"
---

# Folder Fields Stream Structures

**Applies to**: Outlook 
  
A message's [PidTagUserFields](pidtaguserfields-canonical-property.md) property contains a binary stream, FolderUserFields, which contains the folder user-defined field definitions. This topic describes the stream structures for folder user-defined field definitions. 

A FolderUserFields stream structure consists of either a FolderUserFieldsA structure or a FolderUserFieldsA structure followed by a FolderUserFieldsW structure.
  
Data elements in this stream are stored immediately following each other in the following specified order:
  
- **FolderUserFieldsAnsi**: A FolderUserFieldsA stream structure.
    
- **FolderUserFieldsUnicode** (optional): A FolderUserFieldsW stream structure.
    
The presence of FolderUserFieldsUnicode is detected by the total length of the FolderUserFields being greater than the length of FolderUserFieldsAnsi.
  
> [!IMPORTANT]
> FolderUserFieldsAnsi is used for compatibility with older, non-Unicode, versions of MAPI clients, therefore if FolderUserFieldsUnicode is present, the contents of FolderUserFieldsAnsi is ignored. To avoid possible data loss in ANSI conversion, when creating a FolderUserFields stream always include the FolderUserFieldsW part. 
  
## FolderUserFieldsA Stream Structure

A FolderUserFieldsA stream structure is an array of FolderFieldDefinitionA stream structures that contain definitions for all user-defined fields in an Outlook folder, unless overridden by the FolderUserFieldsW part of the FolderUserFields structure.
  
Data elements in this stream are stored in little-endian byte order, immediately following each other in the following specified order:
  
- **FieldDefinitionCount**: DWORD (4 bytes), the number of field definitions in this stream. This is the count of elements in the **FieldDefinitions** array.
    
- **FieldDefinitions**: An array of FolderFieldDefinitionA stream structures. The count of this array is equal to the **FieldDefinitionCount** data element.
    
Unless this FolderUserFieldsA is overridden by the FolderUserFieldsW part of the FolderUserFields structure, the **FieldDefinitions** array must be "null-terminated" by having its last FolderFieldDefinitionA element's Common.FieldType field equal to ftNull.
  
## FolderUserFieldsW Stream Structure

A FolderUserFieldsW stream structure is an array of FolderFieldDefinitionW stream structures that contain definitions for all user-defined fields in an Outlook folder.
  
Data elements in this stream are stored in little-endian byte order, immediately following each other in the following specified order:
  
- **FieldDefinitionCount**: DWORD (4 bytes), the number of field definitions in this stream. This is the count of elements in the **FieldDefinitions** array.
    
- **FieldDefinitions**: An array of FolderFieldDefinitionW stream structures. The count of this array is equal to the **FieldDefinitionCount** data element.
    
The **FieldDefinitions** array must be "null-terminated" by having its last FolderFieldDefinitionW element's Common.FieldType field equal to ftNull.
  
## FolderFieldDefinitionA Stream Structure

A FolderFieldDefinitionA stream structure contains a definition of a user-defined field with the field name stored in ANSI.
  
Data elements in this stream are stored in little-endian byte order, immediately following each other in the following specified order:
  
- **FieldType**: FldType (4 bytes), the type of this field.
    
- **FieldNameLength**: WORD (2 bytes), the number of elements in the **FieldName** array.
    
- **FieldName**: An array of CHAR. This is the ANSI CP_ACP codepage representation of the field name. The count of this array is equal to **FieldNameLength**. The field name must satisfy the restrictions on the Name parameter as specified in the [UserProperties.Add](http://msdn.microsoft.com/en-us/library/microsoft.office.interop.outlook.userproperties.add.aspx) Method. 
    
   > [!NOTE]
   > For reasons of legacy compatibility, Outlook may be able to handle some **FieldName** values not satisfying these restrictions, however such cases are not covered by this topic. 
  
- **Common**: A FolderFieldDefinitionCommon stream structure.
    
## FolderFieldDefinitionW Stream Structure

A FolderFieldDefinitionW stream structure contains a definition of a user-defined field with the field name stored in Unicode.
  
Data elements in this stream are stored in little-endian byte order, immediately following each other in the following specified order:
  
- **FieldType**: FldType (4 bytes), the type of this field.
    
- **FieldNameLength**: WORD (2 bytes), the number of elements in the **FieldName** array.
    
- **FieldName**: An array of WCHAR. This is the Unicode (UTF-16) representation of the field name. The count of this array is equal to **FieldNameLength**. The field name must satisfy the restrictions on the Name parameter as specified in the [UserProperties.Add](http://msdn.microsoft.com/en-us/library/microsoft.office.interop.outlook.userproperties.add.aspx) Method. 
    
   > [!NOTE]
   > For reasons of legacy compatibility, Outlook may be able to handle some **FieldName** values not satisfying these restrictions, but such cases are not covered by this topic. 
  
- **Common**: A FolderFieldDefinitionCommon stream structure.
    
## FldType Enumeration

**FldType** enumeration values are listed in the following table. 
  
|Name|Value|Meaning|
|:-----|:-----|:-----|
|ftNull  <br/> |0x0  <br/> |This field type is used to null-terminate an array of field definitions.  <br/> |
|ftString  <br/> |0x1  <br/> |Text  <br/> |
|ftInteger  <br/> |0x3  <br/> |Integer  <br/> |
|ftTime  <br/> |0x5  <br/> |Date/Time  <br/> |
|ftBoolean  <br/> |0x6  <br/> |Yes/No  <br/> |
|ftDuration  <br/> |0x7  <br/> |Duration  <br/> |
|ftMultiString  <br/> |0xB  <br/> |Keywords  <br/> |
|ftFloat  <br/> |0xC  <br/> |Number or Percent  <br/> |
|ftCurrency  <br/> |0xE  <br/> |Currency  <br/> |
|ftCalc  <br/> |0x12  <br/> |Formula  <br/> |
|ftSwitch  <br/> |0x13  <br/> |Combination of type showing only the first non-empty field - ignoring subsequent ones.  <br/> |
|ftConcat  <br/> |0x17  <br/> |Combination of type joining fields and any text fragments to each other.  <br/> |
   
## FolderFieldDefinitionCommon Stream Structure

A FolderFieldDefinitionCommon stream structure contains the data of a user-defined field definition that is common to both a FolderFieldDefinitionA and a FolderFieldDefinitionW.
  
Data elements in this stream are stored in little-endian byte order, immediately following each other in the following specified order:
  
- **PropSetGuid**: GUID (16 bytes), the property set GUID of the folder field's corresponding MAPI property name. This field's value must be equal to PS_PUBLIC_STRINGS, unless the field type is **ftNone** in which case this field's value must be equal to GUID_NULL. 
    
   > [!NOTE]
   > For reasons of legacy compatibility, Outlook may be able to handle some **PropSetGuid** values not satisfying this restriction, however such cases are not covered by this topic. 
  
- **fcapm**: DWORD (4 bytes), a combination of zero or more flags the values of which and meanings are listed in the following table. Flags with the same value have meanings dependent on the field's type, that is, FldType value.
    
    |Flag name|Value|Meaning|
    |:-----|:-----|:-----|
    |FCAPM_CAN_EDIT  <br/> |0x00000001  <br/> |The field is editable.  <br/> |
    |FCAPM_CAN_SORT  <br/> |0x00000002  <br/> |The field is sortable.  <br/> |
    |FCAPM_CAN_GROUP  <br/> |0x00000004  <br/> |The field is groupable.  <br/> |
    |FCAPM_MULTILINE_TEXT  <br/> |0x00000100  <br/> |The field can hold multiple lines of text.  <br/> |
    |FCAPM_PERCENT  <br/> |0x01000000  <br/> |This field of the type ftFloat is a percentage field.  <br/> |
    |FCAPM_DATEONLY  <br/> |0x01000000  <br/> |This field of the type ftTime is a date-only time field.  <br/> |
    |FCAPM_UNITLESS  <br/> |0x01000000  <br/> |For this field of the type ftInteger, no unit is allowed in display format; for example such formats as "Computer - 640 K…" are not allowed.  <br/> |
    |FCAPM_CAN_EDIT_IN_ITEM  <br/> |0x80000000  <br/> |The field can be edited in the item: This is specifically for custom forms.  <br/> |
   
- **dwString**: DWORD (4 bytes). See the first following Note.
    
- **dwBitmap**: DWORD (4 bytes). See the first following Note.
    
- **dwDisplay**: DWORD (4 bytes). See the first following Note.
    
- **iFmt**: INT (4 bytes). For the field types that have the "Format:" combo box in the "New Field", "Edit Field", and "Field Properties" dialogs, the 0-based index of the format selected in that combo box. For the field types without that combo box, this must be 0. The field's value together with the field type uniquely determine the values of the **dwString**, **dwBitmap**, and **dwDisplay** fields, see the first following Note.
    
- **wszFormulaLength**: WORD (2 bytes), the number of elements in the **wszFormulaLength** array.
    
- **wszFormulaLength**: An array of WCHAR. This is the Unicode (UTF-16) representation of the field's formula string in its standard format. See the second following Note for the description of the standard and UI formats of a field's formula. The count of this array is equal to **wszFormulaLength**. The formula string must be an empty string unless the field type is **ftCalc**, **ftSwitch** or **ftConcat**.
    
> [!NOTE]
> Although the values of **dwString**, **dwBitmap**, and **dwDisplay** are uniquely determined based on the **FldType** value and the **iFmt** value, which are redundant, their correct values are still necessary for correct processing of the field definition by Outlook. There is no simple description of the algorithm that performs this determination. 
> 
> Therefore, to find out which **dwString**, **dwBitmap**, and **dwDisplay** values correspond to a given **FldType** value and **iFmt** value, perform a test by creating a user-defined field of that type, and with that format selected in the **Format** combo box, assuming its applicability, inspect the resulting **FolderUserFields** stream that Outlook creates for that user-defined field. 
  
The field's formula in its UI format is edited in the **Formula** text box of the **New Field**, **Edit Field**, and **Field Properties** dialogs for the user-defined field. The algorithm to convert a formula from the UI format to the standard format depends on the field type as described in the following: 
- For fields of types **ftCalc** and **ftSwitch**, the standard format for built-in fields, which corresponding MAPI properties are not named properties of the kind MNID\_STRING, is obtained by replacing field name fragments, that is `[<field_name>]` with fragments `[_<field_dispid_decimal>]`. 

  For example, if the UI format of a formula for a field of the type **Formula**, that is **ftCalc**, with the Office UI language being US English, is `[Business Phone] & [My custom field]`, where `My custom field` is the name of a user-defined field, the standard format of such a formula would be `[_14856] & [My custom field]`.

- For fields of the type **ftConcat**, the standard format is obtained by performing the following:

  1. Truncate leading and trailing whitespace. 
  2. Parse the formula into a sequence of fragments of the following two kinds: 
     - A field name in square brackets, that is, `[<field_name>]`. 
     - A substring not containing any square brackets.   
      Assure that no two fragments of the second kind are adjacent in the sequence. If the formula cannot be parsed this way, it is considered invalid. 
  3. Perform the same replacement for fragments of the first kind as for the **ftCalc** and **ftSwitch** fields. 
  4. For each fragment of the second kind, escape all double-quote (""") characters, if any, with two consecutive double-quote characters, and enclose it in double quotes. 
  5. Insert an ampersand string (`&`) between each pair of adjacent fragments.
 
  For example, using the Office UI language US English, if the UI format of a formula for a field of the type **ftConcat** is `text1 [Business Phone] "text2" [My custom field]`, where `My custom field` is the name of a user-defined field, the standard format for such a formula would be `""text1" & [_14856] & """text2""" & [My custom field]"`. 
  
## See also

- [FolderUserFields Stream Sample](folderuserfields-stream-sample.md)
- [Add a Definition for a New User-Defined Field](how-to-add-a-definition-for-a-new-user-defined-field.md)

