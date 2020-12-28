---
title: "Autocomplete Stream"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
localization_priority: Normal
ms.assetid: d4f380fa-2ed9-4c7c-9ef3-b32f8409f657
description: "Last modified: March 09, 2015"
 
 
---

# Autocomplete Stream

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
In addition to knowing how Microsoft Outlook interacts with the autocomplete stream, you must also understand the binary format of the autocomplete stream.
  
The autocomplete stream is a set of recipient property rows that are saved as a binary stream together with some bookkeeping metadata that is used only by Microsoft Outlook 2013, Microsoft Outlook 2010, Microsoft Office Outlook 2007, and Microsoft Outlook 2003. The metadata is relevant to Outlook interactions with the autocomplete stream so third parties must preserve what is in each metadata block when they save a modified autocomplete stream. In other words, third parties should modify only the row-set part of the binary format and preserve what was already in the metadata blocks of the autocomplete stream.
  
## Stream Visualization

The high-level layout of the autocomplete stream is as follows:
  
Metadata (4 bytes)
  
Major Version Number (4 bytes)
  
Minor Version Number (4 bytes)
  
Number of rows n (4 bytes)
  
Number of properties p in row one (4 bytes)
  
Property 1's property tag (4 bytes)
  
Property 1's reserved data (4 bytes)
  
Property 1's value union (8 bytes)
  
Property 1's value data (0 or variable bytes)
  
… (property 2 through property P-1)
  
Property p's property tag (4 bytes)
  
Property p's reserved data (4 bytes)
  
Property p's value union (8 bytes)
  
Property p's value data (0 or variable bytes)
  
Number of properties q in row two (4 bytes)
  
… (row two's properties)
  
… (row 3 through row n-1)
  
Number of properties r in row n (4 bytes)
  
… (row n's properties)
  
Extra information byte count EI (4 bytes)
  
Extra information (EI bytes)
  
Metadata (8 bytes)
  
For an example of a binary structure, see Binary Example in the [Outlook 2003/2007 NK2 File Format and Developer Guidelines.](https://portalvhds6gyn3khqwmgzd.blob.core.windows.net/files/NK2/NK2WithBinaryExample.pdf)
  
## High-level Layout

Broadly speaking, the layout of the autocomplete stream is as follows:
  
|**Value Data**|**Number of Bytes**|
|:-----|:-----|
|Metadata  <br/> |4  <br/> |
|Major Version Number  <br/> |4  <br/> |
|Minor Version Number  <br/> |4  <br/> |
|Row-set  <br/> |Variable  <br/> |
|Extra information byte count EI  <br/> |4  <br/> |
|Extra information  <br/> |EI  <br/> |
|Metadata  <br/> |8  <br/> |
   
When reading this stream, if the major version is different than 12, then this stream should not be read or written. The current minor version of the autocomplete stream is 0, which has the Extra Information Byte count set to 0. If the minor version is different than 0, then there will be information in the extra information that needs to be read when reading the stream and preserved when writing the stream. The minor version will also need to be preserved when writing the stream. If both of these are not preserved, instances of Outlook that wrote the extra information will lose data. 
  
> [!NOTE]
> Applications must not add custom data to the Extra Information field or change the minor version as this functionality is to support Outlook extensions to the format and not arbitrary third-party extensions. 
  
## Row-set Layout

The row-set layout is as follows: 
  
|**Value Data**|**Number of Bytes**|
|:-----|:-----|
|Number of rows  <br/> |4  <br/> |
|Rows  <br/> |Variable  <br/> |
   
The number of rows identifies how many rows come in the next part of the binary stream sequence.
  
## Row Layout

Each row is of the following format:
  
|**Value Data**|**Number of Bytes**|
|:-----|:-----|
|Number of properties  <br/> |4  <br/> |
|Properties  <br/> |Variable  <br/> |
   
The number of properties identifies how many properties come in the next part of the binary stream sequence.
  
## Property Layout

Each property is of the following format:
  
|**Value Data**|**Number of Bytes**|
|:-----|:-----|
|Property Tag  <br/> |4  <br/> |
|Reserved Data  <br/> |4  <br/> |
|Property Value Union  <br/> ||
|Value Data  <br/> |0 or variable (depending on the prop tag)  <br/> |
   
## Interpreting the Property Value

The Property Value Union and the Value Data are to be interpreted based on the property tag in the first 4 bytes of the property block. This property tag is in the same format as a MAPI property tag. Bits 0 through 15 of the property tag are the property's type. Bits 16 through 31 are the property's identifier. The property type determines how the rest of the property should be read.
  
## Static Value

Some properties have no Value Data and only have data in the union. The following property types (which come from the Property Tag) should interpret the 8-byte Property Union data as follows:
  
|**Prop Type**|**Property Union Interpretation**|
|:-----|:-----|
|PT_I2  <br/> |short int  <br/> |
|PT_LONG  <br/> |long  <br/> |
|PT_ERROR  <br/> |long  <br/> |
|PT_R4  <br/> |float  <br/> |
|PT_DOUBLE  <br/> |double  <br/> |
|PT_BOOLEAN  <br/> |short int  <br/> |
|PT_SYSTIME  <br/> |FILETIME  <br/> |
|PT_I8  <br/> |LARGE_INTEGER  <br/> |
   
## Dynamic Values

Other properties have data in a Value Data block after the first 16 bytes that contain the Property Tag, the Reserved Data, and the Property Value Union. Unlike static values, the data that is stored in the 8-byte Property Value union is irrelevant on reading. When writing, make sure that you fill these 8 bytes with something. However, the content of the 8 bytes is not important. In dynamic values, the property tag's type determines how to interpret the Value Data.
  
PT_STRING8 
  
|**Value Data**|**Number of Bytes**|
|:-----|:-----|
|Number of bytes n  <br/> |4  <br/> |
|Bytes to be interpreted as an ANSI string (includes NULL terminator)  <br/> |n  <br/> |
   
PT_CLSID
  
|**Value Data**|**Number of Bytes**|
|:-----|:-----|
|Bytes to be interpreted as a GUID  <br/> |16  <br/> |
|||
   
PT_BINARY 
  
|**Value Data**|**Number of Bytes**|
|:-----|:-----|
|Number of bytes n  <br/> |4  <br/> |
|Bytes to be interpreted as a byte array  <br/> |n  <br/> |
   
PT_MV_BINARY
  
|**Value Data**|**Number of Bytes**|
|:-----|:-----|
|Number of binary arrays X  <br/> |4  <br/> |
|A run of bytes that contains X binary arrays. Each array should be interpreted exactly like the PT_BINARY byte run.  <br/> |Variable  <br/> |
   
PT_MV_STRING8 (Outlook 2007, Outlook 2010, and Outlook 2013)
  
|**Value Data**|**Number of Bytes**|
|:-----|:-----|
|Number of ANSI strings X  <br/> |4  <br/> |
|A run of bytes that contains X ANSI strings. Each string should be interpreted exactly like the PT_STRING8 byte run.  <br/> |Variable  <br/> |
   
PT_MV_UNICODE (Outlook 2007, Outlook 2010, Outlook 2013)
  
|**Value Data**|**Number of Bytes**|
|:-----|:-----|
|Number of UNICODE strings X  <br/> |4  <br/> |
|A run of bytes that contains X UNICODE strings. Each string should be interpreted exactly like the PT_UNICODE byte run.  <br/> |Variable  <br/> |
   
## Significant properties

As mentioned previously in this topic, the binary blocks that represent properties have property tags that correspond to properties on address book recipients. For properties that are not listed here, you can look up the property description at https://msdn.microsoft.com/library/cc433490(EXCHG.80).aspx.
  
|**Property Name**|**Property Tag**|**Description (see MSDN for more information)**|
|:-----|:-----|:-----|
|PR_NICK_NAME_W (not transmitted on recipients, specific to autocomplete stream only)  <br/> |0x6001001f  <br/> |This property must be first in each recipient row. It functionally serves as a key identifier for the recipient row.  <br/> |
|PR_ENTRYID  <br/> |0x0FFF0102  <br/> |The address book entry identifier for the recipient.  <br/> |
|PR_DISPLAY_NAME_W  <br/> |0x3001001F  <br/> |The recipient's display name.  <br/> |
|PR_EMAIL_ADDRESS_W  <br/> |0x3003001F  <br/> |The recipient's email address (e.g. johndoe@contoso.com or /o=Contoso/OU=Foo/cn=Recipients/cn=johndoe)  <br/> |
|PR_ADDRTYPE_W  <br/> |0x3002001F  <br/> |The recipient's address type (e.g. SMTP or EX).  <br/> |
|PR_SEARCH_KEY  <br/> |0x300B0102  <br/> |The recipient's MAPI search key.  <br/> |
|PR_SMTP_ADDRESS_W  <br/> |0x39FE001f  <br/> |The recipient's SMTP address.  <br/> |
|PR_DROPDOWN_DISPLAY_NAME_W (not transmitted on recipients, specific to autocomplete stream only)  <br/> |0X6003001f  <br/> |The display string that appears in the autocomplete list.  <br/> |
|PR_NICK_NAME_WEIGHT (not transmitted on recipients, specific to autocomplete stream only)  <br/> |0x60040003  <br/> |The weight of this autocomplete entry. The weight is used to determine in what order autocomplete entries occur when matching the autocomplete list. Entries with higher weight will show before entries with lower weight. The complete autocomplete list is sorted by this property. The weight periodically decreases over time and increases when the user sends an email to this recipient. See the description later in this topic for more information about this property.  <br/> |
   
PR_NICK_NAME_WEIGHT
  
The set of rows in the autocomplete stream is sorted in descending order by the PR_NICK_NAME_WEIGHT property and the autocomplete stream should always preserve this sorted characteristic. Therefore, any changes to a row's weight should also ensure that the row's position maintains the sorted order of the complete set of rows. Any additions to the row-set should be inserted to the correct position to maintain the sorted order.
  
The minimum value of this weight is 0x1 and the maximum value is LONG_MAX. Any other values for the weight are considered invalid.
  
When Outlook 2007 sends a mail to or resolves a recipient, it will increase that recipient's weight by 0x2000.
  

