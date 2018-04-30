---
title: "TNEF Stream Structure"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 8eda1251-3858-4832-ac43-d817b4a7ea59
description: "Last modified: March 09, 2015"
---

# TNEF Stream Structure

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
A TNEF stream begins with a 32-bit signature that identifies the stream as a TNEF stream. Following the signature is a 16-bit unsigned integer that is used as a key to cross-reference attachments to their location in the tagged message text. The remainder of the stream is a sequence of TNEF attributes. Message attributes appear first in the TNEF stream, and attachment attributes follow. Attributes that belong to a particular attachment are grouped together, beginning with the **attAttachRenddata** attribute. 
  
Most of the constant values used in TNEF streams are defined in the TNEF.H header file. Notably, **TNEF_SIGNATURE**, **LVL_MESSAGE**, **LVL_ATTACHMENT**, and all the TNEF attribute identifiers are defined in this file. Other constants have the values indicated by their interpretation to a C language compiler. Typically, such constants are used to give the sizes of the following item. For example, **sizeof(ULONG)** in an item's definition indicates that an integer representing the size of the following unsigned long integer should occur in that place in the TNEF stream. 
  
All integers in a TNEF stream are stored in little-endian binary form, but are shown in hexadecimal throughout this section. Checksum values are simply 16-bit unsigned integers that are the sum, modulo 65536, of the bytes of data that the checksum applies to. All attribute lengths are unsigned long integers, including any terminating null characters.
  
The key is a nonzero, 16-bit unsigned integer that signifies the initial value of the attachment reference keys. The attachment reference keys are assigned to each attachment sequentially beginning with the initial value that is passed to the [OpenTnefStream](opentnefstream.md) function by the service provider that is using TNEF. The service provider should generate a random initial value for the key to minimize the chance that two messages use the same key. 
  
The TNEF implementation uses attribute identifiers to map attributes to their corresponding MAPI properties. An attribute identifier is a 32-bit unsigned integer made up of two word values. The high-order word indicates the data type, such as string or binary, and the low-order word identifies the particular attribute. The data types in the high order word are:
  
|**Type**|**Value**|
|:-----|:-----|
|atpTriples  <br/> |0x0000  <br/> |
|atpString  <br/> |0x0001  <br/> |
|atpText  <br/> |0x0002  <br/> |
|atpDate  <br/> |0x0003  <br/> |
|atpShort  <br/> |0x0004  <br/> |
|atpLong  <br/> |0x0005  <br/> |
|atpByte  <br/> |0x0006  <br/> |
|atpWord  <br/> |0x0007  <br/> |
|atpDword  <br/> |0x0008  <br/> |
|atpMax  <br/> |0x0009  <br/> |
   
The low-order word values for each attribute are defined in the TNEF.H header file.
  

