---
title: "FieldDefinition stream structure"
description: This article describes the FieldDefinition stream structure and interaction with data elements.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: 93acdbc8-381f-45d5-be6c-0cad066269fe
---

# FieldDefinition stream structure

**Applies to**: Outlook 2013 | Outlook 2016 
  
A FieldDefinition stream structure contains either the field definition of a user-defined field, or a set of data-binding settings for a built-in field.
  
You can programmatically manipulate a FieldDefinition stream structure if the structure contains the field definition of a user-defined field. You should not attempt to programmatically create or modify a FieldDefinition structure if the structure contains settings for a built-in field. You should use the Microsoft Outlook Forms Designer to maintain such settings for built-in fields.
  
> [!NOTE]
> Outlook supports two formats of field definitions: PropDefV1 and PropDefV2. The PropDefV1 format of field definitions contains the following data elements: Flags, VT, DispId, NmidNameLength, NmidName, NameANSI, FormulaANSI, ValidationRuleANSI, ValidationTextANSI, and ErrorANSI. The PropDefV2 format contains the same elements and the InternalType and SkipBlocks elements. 
>
> Outlook does not maintain a Unicode version for the FormulaANSI, ValidationRuleANSI, and ValidationTextANSI data elements in the PropDefV2 field definition format. If these elements contain non-ASCII characters, those characters may be interpreted inconsistently depending on the ANSI Code Page of the computer on which Outlook is running. Therefore, you should use only string values that consist entirely of ASCII characters for these data elements. 
  
Data elements in this stream are stored in little-endian byte order, immediately following each other in the order specified below.
  
- Flags: DWORD (4 bytes), a combination of zero or more flags whose values and meanings are listed in the following table.
    
    |**Flag name**|**Value**|**Description**|
    |:-----|:-----|:-----|
    |PDO_IS_CUSTOM  <br/> |0x00000001  <br/> |The FieldDefinition structure contains a definition of a user-defined field. |
    |PDO_REQUIRED  <br/> |0x00000002  <br/> |For a form control bound to this field, the check box for **A value is required for this field** is selected in the **Validation** tab of the **Properties** dialog box. |
    |PDO_PRINT_SAVEAS  <br/> |0x00000004  <br/> |For a form control bound to this field, the check box for **Include this field for printing and Save As** is selected in the **Validation** tab of the **Properties** dialog box. |
    |PDO_CALC_AUTO  <br/> |0x00000008  <br/> |For a form control bound to this field, the check box for **Calculate this formula automatically** is selected in the **Value** tab of the **Properties** dialog box. |
    |PDO_FT_CONCAT  <br/> |0x00000010  <br/> |This is a field of type **Combination** and it has the **Joining fields and any text fragments with each other** option selected in its **Combination Formula Field** dialog box. |
    |PDO_FT_SWITCH  <br/> |0x00000020  <br/> |This field is of type **Combination** and has the **Showing only the first non-empty field, ignoring subsequent ones** option selected in the **Combination Formula Field** dialog box. |
    |PDO_PRINT_SAVEAS_DEF  <br/> |0x00000040  <br/> |This flag is not used by Outlook, but it is included for all user-defined field definitions. |
   
- VT: WORD (2 bytes), the data type of the field, which is a constant from the [VARENUM](https://msdn.microsoft.com/library/system.runtime.interopservices.varenum.aspx) enumeration. 
    
- DispId: DWORD (4 bytes), the dispatch identifier of the field. For a user-defined field, the value is 0.
    
- NmidNameLength: WORD (2 bytes), the number of elements in the NmidName array.
    
- NmidName: An array of WCHAR. For a user-defined field definition, this is the Unicode (UTF-16) representation of the field name. The count of this array is equal to NmidNameLength.
    
- NameANSI: A [PackedAnsiString](packedansistring-stream-structure.md) stream structure. This is the ANSI representation of the field name. 
    
- FormulaANSI: A PackedAnsiString stream structure. This is an ANSI representation of the calculation formula for the field. It is shown in the **Initial Value** section of the **Value** tab of the **Properties** dialog box of a form control bound to this field. 
    
- ValidationRuleANSI: A PackedAnsiString stream structure. This is an ANSI representation of the field's validation formula. It is shown in the text box for **Validation Formula** on the **Validation** tab of the **Properties** dialog box of a form control bound to this field. 
    
- ValidationTextANSI: A PackedAnsiString stream structure. This is an ANSI representation of the field's validation failure text. It is shown in the text box for **Display this message if the validation fails** on the **Validation** tab of the **Properties** dialog box of a form control bound to this field. 
    
- ErrorANSI: A PackedAnsiString stream structure. Outlook does not use this element; you should set this element to an empty string.
    
- InternalType: DWORD (4 bytes), the internal type of the field. This data element is present only if the field definition format is PropDefV2. The internal type is one of the following values, each of which corresponds to a type in the **New Field** dialog box for user-defined fields. 
    
    |**Internal type name**|**Value**|**Corresponding type in **New Field** dialog box**|
    |:-----|:-----|:-----|
    |iTypeString  <br/> |0  <br/> |**Text** <br/> |
    |iTypeNumber  <br/> |1  <br/> |**Number** <br/> |
    |iTypePercent  <br/> |2  <br/> |**Percent** <br/> |
    |Currency  <br/> |3  <br/> |**Currency** <br/> |
    |iTypeBool  <br/> |4  <br/> |**Yes/No** <br/> |
    |iTypeDateTime  <br/> |5  <br/> |**Date/Time** <br/> |
    |iTypeDuration  <br/> |6  <br/> |**Duration** <br/> |
    |iTypeCombination  <br/> |7  <br/> |**Combination**, with the **Showing only the first non-empty field, ignoring subsequent ones** option selected in the **Combination Formula Field** dialog box. |
    |iTypeFormula  <br/> |8  <br/> |**Formula** <br/> |
    |iTypeResult  <br/> |9  <br/> |This type is not used for user-defined fields. |
    |iTypeVariant  <br/> |10  <br/> |This type is not used for user-defined fields. |
    |iTypeFloatResult  <br/> |11  <br/> |This type is not used for user-defined fields. |
    |iTypeConcat  <br/> |12  <br/> |**Combination**, with the **Joining fields and any text fragments with each other** option selected in the **Combination Formula Field** dialog box. |
    |iTypeKeywords  <br/> |13  <br/> |**Keyword** <br/> |
    |iTypeInteger  <br/> |14  <br/> |**Integer** <br/> |
   
- SkipBlocks: A series of one or more [SkipBlock](skipblock-stream-structure.md) stream structures. This data element is present only if the field definition format is PropDefV2. If the field definition format is PropDefV2, the series should contain at least one SkipBlock structure, the SkipBlock structure that has the Size data element equal to 0, and the series should begin and terminate with this SkipBlock structure. 
    
   The purpose of a SkipBlock structure depends on its relative position in the SkipBlocks series. If the field definition is in PropDefV2 format, and the first structure is not the terminating structure (the Size data element is greater than 0), Outlook assumes the first SkipBlock structure specifies the field name in Unicode (UTF-16). 
    
   > [!IMPORTANT]
   > If the first SkipBlock is the terminating structure, the NameANSI data element is used to determine the field name. If that string contains any non-ASCII characters, those characters may be interpreted inconsistently depending on the ANSI code page of the computer on which Outlook is running. To prevent such inconsistencies, be sure you always specify the first SkipBlock in field definitions that you create, at least when the field name includes non-ASCII characters. 
  
   If a future version of a field definition format introduces additional pieces of data in the FieldDefinition stream, this data can be stored as additional SkipBlock stream structures in the SkipBlocks series before the terminating SkipBlock structure that has the Size data element equal to 0. Earlier versions of Outlook can safely ignore these extra SkipBlock structures up to the terminating SkipBlock structure and still correctly process all the blocks that they support.
    
## See also

- [Outlook Items and Fields](outlook-items-and-fields.md)
- [Stream Structures](stream-structures.md)
- [PropertyDefinition Stream Structure](propertydefinition-stream-structure.md)

