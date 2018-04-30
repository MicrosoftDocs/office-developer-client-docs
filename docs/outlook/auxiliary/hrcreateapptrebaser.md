---
title: "HrCreateApptRebaser"
ms.author: soliver
author: soliver
manager: soliver
ms.date: 12/7/2015
ms.audience: Developer
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 265028b7-a583-f6ba-0214-5a4322f98f35
description: "Initializes an IOlkApptRebaser object for use in rebasing appointments in Outlook calendars."
---

# HrCreateApptRebaser

Initializes an [IOlkApptRebaser](iolkapptrebaser.md) object for use in rebasing appointments in Outlook calendars. 
  
## Quick Info

|||
|:-----|:-----|
|Header file:  <br/> |tzmovelib.h  <br/> |
|Implemented by:  <br/> |tzmovelib.dll  <br/> |
|Called by:  <br/> |MAPI client applications  <br/> |
|Pointer type:  <br/> |**LPHRCREATEAPPTREBASER** <br/> |
|DLL entry point:  <br/> |**HrCreateApptRebaser@44** <br/> |
   
```
HRESULT HrCreateApptRebaser(  
    ULONG ulFlags, 
    IMAPISession *pSession, 
    IMsgStore *pCalendarMsgStore, 
    IMAPIFolder *pCalendarFolder, 
    LPCWSTR pwszUpdatePrefix, 
    const FILETIME *pftInstallDateUTC, 
    LONG lExpansionDepth, 
    const TZDEFINITION *pTZTo, 
    const TZDEFINITION *pTZMissing, 
    MAPIERROR **ppError, 
    IOlkApptRebaser **ppApptRebase); 

```

## Parameters

 _ulFlags_
  
> [in] Required. A bitmask of flags used to control how rebasing is performed. The following flags can be set and are defined in tzmovelib.h:
    
    - **REBASE_FLAG_UPDATE_ORGANIZED_MEETINGS** —Appointment items in which the user is the meeting organizer are rebased. Note that by default, this causes Outlook to send meeting updates to all attendees of any meeting being rebased. You can combine this flag with either **REBASE_FLAG_FORCE_NO_EX_UPDATES** or **REBASE_FLAG_FORCE_NO_UPDATES** to change how meeting updates are handled. 
    
    - **REBASE_FLAG_UPDATE_UNMARKED** —Update appointment items that have not been marked with a time zone. If this flag is specified, the  *pTZMissing*  value is used as the time zone that an item is created in for all items that do not have time zone data. 
    
    - **REBASE_FLAG_UPDATE_ONLYRECURRING** —Update only recurring appointment items. 
    
    - **REBASE_FLAG_NO_UI** —Do not show any user interface (UI), including logon dialog boxes generally displayed when opening a message store. 
    
    - **REBASE_FLAG_UPDATE_MINIMIZEAPPTS** —Do not rebase appointment items that occur in the past. 
    
    - **REBASE_FLAG_FORCE_REBASE** —Do not check the organizer for rebasing decisions, but rebase appointment items in which the user is an attendee. 
    
    - **REBASE_FLAG_FORCE_NO_EX_UPDATES** —Send updates only if the user is the organizer and recipient is not connected to an Exchange Server. 
    
    - **REBASE_FLAG_FORCE_NO_UPDATES** —Never send updates. 
    
    - **REBASE_FLAG_ONLY_CREATED_PRE_PATCH** —Rebase only single-instance appointment items created before the patch was applied. 
    
    - **REBASE_FLAG_REPORTING_MODE** —Do not actually rebase, just report appointment items that would be rebased. 
    
    - **REBASE_FLAG_SEND_RESOURCE_UPDATES** —Send meeting updates to resources. 
    
 _pSession_
  
> [in] Required. A pointer to a MAPI session interface.
    
 _pCalendarMsgStore_
  
> [in] Required. A pointer to a message store containing appointment items to be rebased.
    
 _pCalendarFolder_
  
> [in] Required. A pointer to a calendar folder containing appointment items to be rebased.
    
 _pwszUpdatePrefix_
  
> [in] Optional. A pointer to a string containing the prefix to be prepended on meeting requests. May be NULL.
    
 _pftInstallDateUTC_
  
> [in] Optional. The time zone patch install date. Used only if the **REBASE_FLAG_ONLY_CREATED_PRE_PATCH** flag is set. 
    
 _IExpansionDepth_
  
> [in] Optional. The expansion depth when expanding distribution lists to exclude recipients connected to Exchange Server. Only used if the **REBASE_FLAG_FORCE_NO_EX_UPDATES** flag is set. 
    
 _pTZTo_
  
> [in] Required. A pointer to a **TZDEFINITION** structure describing the time zone to be rebased to. **TZDEFINITION** is defined in tzmovelib. 
    
pTZMissing
  
> [in] Required. A pointer to a **TZDEFINITION** structure describing the time zone to be assumed if time zone information is not stamped on an item. Must not be NULL, but only used if the **REBASE_FLAG_UPDATE_UNMARKED** flag is set. 
    
 _ppError_
  
> [out] A pointer to a pointer to a **MAPIERROR** structure containing version, component, and context information for the error. Can be NULL if no extended error information is desired. Free with [MAPIFreeBuffer](http://msdn.microsoft.com/library/9412594f-8acc-4c7e-a668-4ec1da0ad9cf%28Office.15%29.aspx). 
    
 _ppApptRebase_
  
> [out] A pointer to a pointer to the returned **IOlkApptRebaser** interface. 
    
## Return Values

S_OK if the call succeeded; otherwise, an error code.
  
## Remarks

When using [GetProcAddress](http://msdn.microsoft.com/library/a0d7fc09-f888-4f46-a571-d3719a627597%28Office.15%29.aspx) to look for the address of this function in tzmovelib.dll, specify **HrCreateApptRebaser@44** as the procedure name. Not all of the flags are valid in combination with each other. 
  
For more information about the various options, see the section "Glossary of command-line options for the Outlook Time Zone Data Update tool" in [KB 931667: How to address time zone changes by using the Time Zone Data Update Tool for Microsoft Office Outlook](http://support.microsoft.com/kb/931667/en-us).
  
## See also

#### Concepts

[About rebasing calendars programmatically for Daylight Saving Time](about-rebasing-calendars-programmatically-for-daylight-saving-time.md)

