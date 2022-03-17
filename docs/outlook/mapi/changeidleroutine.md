---
title: "ChangeIdleRoutine"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- ChangeIdleRoutine
api_type:
- HeaderDef
ms.assetid: 0a24fe3b-a1ef-4748-b3b3-3bf747473c9d
description: "Last modified: March 09, 2015"
---

# ChangeIdleRoutine

**Applies to**: Outlook 2013 | Outlook 2016
  
Changes some or all of the characteristics of a [FNIDLE](fnidle.md) based idle routine.
  
|Key |Value |
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |

```cpp
VOID ChangeIdleRoutine(
  FTG ftg,
  PFNIDLE pfnIdle,
  LPVOID pvIdleParam,
  short priIdle,
  ULONG csecIdle,
  USHORT iroIdle,
  USHORT ircIdle
);
```

## Parameters

_ftg_
  
> [in] Function tag that identifies the idle routine.

_pfnIdle_
  
> [in] Pointer to the idle routine.

_pvIdleParam_
  
> [in] Pointer to a new block of memory that the calling implementation allocates for the idle routine.

_priIdle_
  
> [in] Value representing a new priority for the idle routine. Possible priorities for implementation-defined routines are greater than or less than zero, but not zero. A value of zero is reserved for a user event such as a mouse click or a WM_PAINT message. Values greater than zero represent priorities for background tasks that have a higher priority than user events and are dispatched as part of the standard Windows message pump loop. Values less than zero represent priorities for idle tasks that only run during message-pump idle time. Examples of priorities are: 1 for foreground submission, 1 for power-edit character insertion, and 3 for downloading new messages.

_csecIdle_
  
> [in] A new time, in hundredths of a second, to apply to the idle routine. The meaning of the initial time value varies, depending on what is passed in the _iroIdle_ parameter. It can be:

- The minimum period of user inaction that must elapse before the MAPI idle engine calls the idle routine for the first time, if the FIROWAIT flag is set in _iroIdle_. After this time passes, the idle engine can call the idle routine as often as necessary.

- The minimum interval between calls to the idle routine, if the FIROINTERVAL flag is set in _iroIdle_.

_iroIdle_
  
> [in] Bitmask of flags indicating new options for calling the idle routine. Exactly one of the following flags must be set:

- FIROINTERVAL: The time specified by the _csecIdle_ parameter is the minimum interval between successive calls to the idle routine.

- FIROONCEONLY: Obsolete. Do not use.

- FIROPERBLOCK: Obsolete. Do not use.

- FIROWAIT: The time specified by the _csecIdle_ parameter is the minimum period of user inaction that must elapse before the MAPI idle engine calls the idle routine for the first time. After this time passes, the idle engine can call the idle routine as often as necessary.

_ircIdle_
  
> [in] Bitmask of flags used to indicate the changes to be made to the idle routine. The following flags can be set in any combination:

- FIRCCSEC: A change to the time associated with the idle routine, that is, a change indicated by the value passed in the _csecIdle_ parameter.

- FIRCIRO: A change to the options for the idle routine, that is, a change indicated by the value passed in the _iroIdle_ parameter.

- FIRCPFN: A change to the idle routine pointer, that is, a change indicated by the value passed in the _pfnIdle_ parameter.

- FIRCPRI: A change to the priority of the idle routine, that is, a change indicated by the value passed in the _priIdle_ parameter.

- FIRCPV: A change to the memory block of the idle routine, that is, a change indicated by the value passed in the _pvIdleParam_ parameter.

## Return value

None.
  
## Remarks

The following functions deal with the MAPI idle engine and with idle routines based on the [FNIDLE](fnidle.md) function prototype:
  
|**Idle routine function**|**Usage**|
|:-----|:-----|
|**ChangeIdleRoutine** <br/> |Changes the characteristics of a registered idle routine. |
|[DeregisterIdleRoutine](deregisteridleroutine.md) <br/> |Removes a registered idle routine from the MAPI system. |
|[EnableIdleRoutine](enableidleroutine.md) <br/> |Disables or re-enables a registered idle routine without removing it from the MAPI system. |
|[FtgRegisterIdleRoutine](ftgregisteridleroutine.md) <br/> |Adds an idle routine to the MAPI system, with or without enabling it. |
|[MAPIDeInitIdle](mapideinitidle.md) <br/> |Shuts down the MAPI idle engine for the calling application. |
|[MAPIInitIdle](mapiinitidle.md) <br/> |Initializes the MAPI idle engine for the calling application. |

**ChangeIdleRoutine**, **DeregisterIdleRoutine**, and **EnableIdleRoutine** take as an input parameter the function tag returned by **FtgRegisterIdleRoutine**.
  
When all foreground tasks for the platform become idle, the MAPI idle engine calls the highest priority idle routine that is ready to execute. There is no guarantee of calling order among idle routines of the same priority.
  