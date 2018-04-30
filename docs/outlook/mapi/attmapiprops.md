---
title: "attMAPIProps"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 806270c1-30e4-494e-9b03-7d1f2fc04099
description: "Last modified: July 23, 2011"
---

# attMAPIProps

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
The **attMAPIProps** attribute is special in that it can be used to encode any MAPI property that does not have a counterpart in the set of existing TNEF-defined attributes. The attribute data is a counted set of MAPI properties laid end-to-end. The format of this encoding, which allows for any set of MAPI properties, is as follows:  
  
 _Property_Seq:_
  
> property-count  _Property_Value,..._
    
There must be as many  _Property_Value_ items as the property-count value indicates. 
  
 _Property_Value:_
  
> property-tag  _Property_property-tag  _Proptag_Name Property_
    
The property-tag is simply the value associated with the property identifier, such as 0x0037001F for **PR_SUBJECT** ( [PidTagSubject](pidtagsubject-canonical-property.md)).
  
 _Property:_
  
>  _Value_ value-count  _Value,..._
    
 _Value:_
  
> value-data value-size value-data padding value-size value-IID value-data padding
    
 _Proptag_Name:_
  
> name-guid name-kind name-id name-guid name-kind name-string-length name-string padding
    
The encapsulation of each property varies based on the property identifier and the property type. Property tags, identifiers, and types are defined in the Mapitags.h and Mapidefs.h header files.
  
If the property is a named property, then the property tag is immediately followed by the MAPI property name, consisting of a globally unique identifier (GUID), a type, and either an identifier or a Unicode string.
  
Multivalued properties and properties with variable length values, such as the PT_BINARY, PT_STRING8, PT_UNICODE, or PT_OBJECT property types, are treated in the following way. First the number of values, encoded as a 32-bit unsigned long, is placed in the TNEF stream, followed by the individual values. Each property's value-data is encoded as its size in bytes followed by the value-data itself. The value-data is padded out to a 4-byte boundary, although the amount of padding is not included in the value-size.
  
If the property is of type PT_OBJECT, the value-size is followed by the interface identifier of the object. The current implementation of TNEF only supports the IID_IMessage, IID_IStorage, and IID_Istream interface identifiers. The size of the interface identifier is included in the value-size.
  
If the object is an embedded message (that is, it has a property type of PT_OBJECT and an interface identifier of IID_Imessage), the value data is encoded as an embedded TNEF stream. The actual encoding of an embedded message in TNEF implementation is done by opening a second TNEF object for the original stream and processing the stream inline.
  

