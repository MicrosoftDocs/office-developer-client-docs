---
title: "FORMPRINTSETUP"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.FORMPRINTSETUP
api_type:
- COM
ms.assetid: 6e82fe94-47bd-4a25-b25b-0ab6fe2db274
description: "Last modified: March 09, 2015"
---

# FORMPRINTSETUP

  
  
**Applies to**: Outlook 
  
Describes the print setup information for the form object. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
   
```cpp
typedef struct
{
  ULONG ulFlags;
  HDEVMODE hDevMode;
  HDEVNAMES hDevNames;
  ULONG ulFirstPageNumber;
  ULONG ulFPrintAttachments;
} FORMPRINTSETUP, FAR * LPFORMPRINTSETUP;

```

## Members

 **ulFlags**
  
> Bitmask of flags that controls the type of the strings. The following flag can be used:
    
MAPI_UNICODE 
  
> The strings are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format.
    
 **hDevmode**
  
> Handle to the mode of the printer.
    
 **hDevnames**
  
> Handle to the path of the printer.
    
 **ulFirstPageNumber**
  
> Page number of the first page to be printed.
    
 **ulFPrintAttachments**
  
> Flag that indicates whether there are attachments to be printed. If there are attachments to print, the **ulFPrintAttachments** member is set to 1. If there are no attachments to print, it is set to 0. 
    
## Remarks

The **FORMPRINTSETUP** structure is used to describe the print setup information for a form object. Implementations of [IMAPIViewContext::GetPrintSetup](imapiviewcontext-getprintsetup.md) fill in the **FORMPRINTSETUP** structure and return it in the contents of the  _lppFormPrintSetup_ output parameter of **GetPrintSetup**.
  
If the MAPI_UNICODE flag is passed in the  _ulFlags_ parameter of **GetPrintSetup**, the strings referenced by the **hDevmode** and **hDevnames** members should be in Unicode format. Otherwise, the strings should be in ANSI format. 
  
Form viewers implementing **IMAPIViewContext** must allocate the **FORMPRINTSETUP** structure using the MAPI allocator function [MAPIAllocateBuffer](mapiallocatebuffer.md), but allocate the individual members, **hDevMode** and **hDevNames**, with the Windows function [GlobalAlloc](http://go.microsoft.com/fwlink/?LinkId=132110). The release of memory is handled similarly. The **hDevMode** and **hDevNames** members must be freed using the Windows function [GlobalFree](http://go.microsoft.com/fwlink/?LinkId=132108) whereas the **FORMPRINTSETUP** structure must be freed with the [MAPIFreeBuffer](mapifreebuffer.md) function. 
  
## See also

#### Reference

[IMAPIViewContext::GetPrintSetup](imapiviewcontext-getprintsetup.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[MAPIAllocateBuffer](mapiallocatebuffer.md)
#### Concepts

[MAPI Structures](mapi-structures.md)

