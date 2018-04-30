---
title: "TNEF Stream Syntax"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 1353d494-c266-4715-afe7-14543a1bbe1b
description: "Last modified: July 23, 2011"
---

# TNEF Stream Syntax

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
This topic presents a Bakus-Nauer like description of the TNEF stream syntax. In this description, nonterminal elements that have a further definition are in italics. Constants and literal items are in bold. Sequences of elements are listed in order on a single line. For example, the  _Stream_ item consists of the constant **TNEF_SIGNATURE**, followed by a  _Key_, followed by an  _Object_. When an item has more than one possible implementation, the alternatives are listed on consecutive lines. For example, an  _Object_ can consist of a  _Message_Seq_, a  _Message_Seq_ followed by an  _Attach_Seq_, or just an  _Attach_Seq_.
  
 _TNEF_Stream:_
  
> **TNEF_SIGNATURE** _Key_ _Object_
    
 _Key:_
  
> a nonzero 16-bit unsigned integer
    
TNEF enabled transports generate this value before using the TNEF implementation to generate a TNEF stream.
  
 _Object:_
  
>  _Message_Seq Message_Seq Attach_Seq Attach_Seq_
    
 _Message_Seq:_
  
>  _attTnefVersion attTnefVersion Msg_Attribute_Seq attTnefVersion attMessageClass attTnefVersion attMessageClass Msg_Attribute_Seq attMessageClass attMessageClass Msg_Attribute_Seq Msg_Attribute_Seq_
    
 _attTnefVersion:_
  
> **LVL_MESSAGE attTnefVersion sizeof(ULONG)** **0x00010000** checksum 
    
 _attMessageClass:_
  
> **LVL_MESSAGE attMessageClass** _msg_class_length msg_class_ checksum 
    
 _Msg_Attribute_Seq:_
  
>  _Msg_Attribute Msg_Attribute Msg_Attribute_Seq_
    
 _Msg_Attribute:_
  
> **LVL_MESSAGE** attribute-ID attribute-length attribute-data checksum 
    
Attribute-ID is one of the TNEF attribute identifiers, such as **attSubject**. Attribute-length is the length in bytes of the attribute data. Attribute-data is the data associated with the attribute.
  
 _Attach_Seq:_
  
>  _attRenddata attRenddata Att_Attribute_Seq_
    
 _attRenddata:_
  
> **LVL_ATTACHMENT attRenddata** **sizeof(RENDDATA)** renddata checksum 
    
Renddata is the data associated with the **RENDDATA** structure that contains the rendering information for the corresponding attachment. The **RENDDATA** structure is defined in the TNEF.H header file. 
  
 _Att_Attribute_Seq:_
  
>  _Att_Attribute Att_Attribute Att_Attribute_Seq_
    
 _Att_Attribute:_
  
> **LVL_ATTACHMENT** attribute-ID attribute-length attribute-data checksum 
    
Attribute-ID, attribute-length, and attribute-data have the same meanings as for the Msg_Attribute item.
  

