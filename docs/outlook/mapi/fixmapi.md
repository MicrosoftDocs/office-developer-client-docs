---
title: "FixMAPI"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 32676003-ba32-886f-1185-4760cb0e30e3
description: "Last modified: March 09, 2015"
---

# FixMAPI

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Makes a backup copy of the current copy of mapi32.dll on the client computer, and restores mapi32.dll with the MAPI stub library, mapistub.dll.
  
## Quick info

|||
|:-----|:-----|
|Exported by:  <br/> |mapistub.dll  <br/> |
|Called by:  <br/> |Client  <br/> |
|Implemented by:  <br/> |Windows  <br/> |
   
```cpp
DWORD STDAPICALLTYPE FixMAPI(void); 
```

## Return values

If the function succeeds, the return value is a non-zero value.
  
If the function fails, the return value is zero. To get extended error information, call the Microsoft Windows Software Development Kit (SDK) function, **[GetLastError](https://msdn.microsoft.com/library/ms679360.aspx)**. 
  
## Remarks

 **FixMAPI** does not replace the current mapi32.dll file if the file is marked as read-only. 
  
 **FixMAPI** does not replace the current mapi32.dll if Microsoft Exchange Server is installed on the computer. 
  
When **FixMAPI** makes a backup copy of the current copy of mapi32.dll on the computer, it assigns the backup copy a name different from "mapi32.dll". It then directs subsequent calls intended for that assembly to the backup copy. 
  
## See also



[KB 256946: You receive a program conflict error message when you start Outlook 2000](https://support.microsoft.com/kb/256946)
  
[KB 228457: Description of the Fixmapi.exe Tool Included with Internet Explorer 5](https://support.microsoft.com/kb/228457)

