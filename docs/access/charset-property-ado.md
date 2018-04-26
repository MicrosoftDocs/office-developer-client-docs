---
title: "Charset Property (ADO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 454f664e-6d62-eec9-487d-882c2f9503b0
---

# Charset Property (ADO)

Indicates the character set into which the contents of a text [Stream](stream-object-ado.md) should be translated for storage in the Stream objects internal buffer. 
  
## Settings and Return Values

Sets or returns a **String** value that specifies the character set into which the contents of the **Stream** will be translated. The default value is "Unicode". Allowed values are typical strings passed over the interface as Internet character set strings (for example, "iso-8859-1", "Windows-1252", etc.). For a list of the character set strings that is known by a system, see the subkeys of HKEY_CLASSES_ROOT\MIME\Database\Charset in the Windows Registry. 
  
## Remarks

In a text **Stream** object, text data is stored in the character set specified by the **Charset** property. The default is Unicode. The **Charset** property is used for converting data going into the **Stream** or coming out of the **Stream**. For example, if the **Stream** contains ISO-8859-1 data and that data is copied to a BSTR, the **Stream** object will convert the data to Unicode. The reverse is also true. 
  
For an open **Stream**, the current [Position](position-property-ado.md) must be at the beginning of the **Stream** (0) to be able to set **Charset**. 
  
 **Charset** is used only with text **Stream** objects ( [Type](type-property-ado-stream.md) is **adTypeText** ). This property is ignored if **Type** is **adTypeBinary**. 
  

