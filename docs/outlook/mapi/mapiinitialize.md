---
title: "MAPIInitialize"
description: Describes the MAPIInitialize function and provides syntax, parameters, remarks, and MFCMAPI references.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPIInitialize
api_type:
- HeaderDef
ms.assetid: b9584226-79d2-4d83-8f31-dbfbc50f16c5
---

# MAPIInitialize

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Increments the MAPI subsystem reference count and initializes global data for the MAPI DLL. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapix.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications  <br/> |
   
```cpp
HRESULT MAPIInitialize(
  LPVOID lpMapiInit
);
```

## Parameters

 _lpMapiInit_
  
> [in] Pointer to a [MAPIINIT_0](mapiinit_0.md) structure. The  _lpMapiInit_ parameter can be set to NULL. 
    
## Return value

S_OK 
  
> The MAPI subsystem was initialized successfully.
    
## Remarks

The **MAPIInitialize** function increments the MAPI reference count for the MAPI subsystem, and the [MAPIUninitialize](mapiuninitialize.md) function decrements the internal reference count. Thus, the number of calls to one function must equal the number of calls to the other. **MAPIInitialize** returns S_OK if MAPI has not been previously initialized. 
  
A client or service provider must call **MAPIInitialize** before making any other MAPI call. Failure to do so causes client or service provider calls to return the MAPI_E_NOT_INITIALIZED value. 
  
When calling **MAPIInitialize** from a multithreaded application, set the  _lpMapiInit_ parameter to a [MAPIINIT_0](mapiinit_0.md) structure that is declared as follows: 
  
 **MAPIINIT_0** MAPIINIT= { 0, MAPI_MULTITHREAD_NOTIFICATIONS} 
  
and call: 
  
 **MAPIInitialize** (&amp;MAPIINIT); 
  
When this structure is declared, MAPI creates a separate thread to handle the notification window, which continues until the initialize reference count falls to zero. A Windows service must set the **ulflags** member of the **MAPIINIT_0** structure pointed to by  _lpMapiInit_ to MAPI_NT_SERVICE. 
  
> [!NOTE]
> You cannot call **MAPIInitialize** or **MAPIUninitialize** from within a Win32 **DllMain** function or any other function that creates or terminates threads. For more information, see [Using Thread-Safe Objects](using-thread-safe-objects.md). 
  
 **MAPIInitialize** does not return any extended error information. Unlike most other MAPI calls, the meanings of its return values are strictly defined to correspond to the particular step of the initialization that failed: 
  
1. Checks parameters and flags.
    
    MAPI_E_INVALID_PARAMETER or MAPI_E_UNKNOWN_FLAGS. Caller passed invalid parameter or flag.
    
2. Initializes registry keys required by MAPI and confirms the type of operating system. This step only happens if the client process is running as a service under Windows and sets the MAPI_NT SERVICE flag in the **MAPIINIT_0** structure. 
    
    MAPI_E_TOO_COMPLEX. The calling process is a Windows service and registry keys required by MAPI could not be initialized. 
    
    Additional information may be available in the application event log.
    
3. Check for the compatibility of MAPI with OLE, then initialize OLE.
    
1. Checks for compatibility between the current versions of OLE and MAPI. 
    
    MAPI_E_VERSION. The version of OLE installed on the workstation is not compatible with this version of MAPI.
    
2. Initializes OLE. 
    
    During this step only, this function can return an error code not listed here. Any error  _not_ listed here should be assumed to come from the OLE function **CoInitialize**.
    
4. Initializes per-process global variables.
    
    MAPI_E_SESSION_LIMIT. MAPI sets up context specific to the current process. Failures may occur on Win16 if the number of processes exceeds a certain number, or on any system if available memory is exhausted.
    
5. Initializes shared global variables of all processes.
    
    MAPI_E_NOT_ENOUGH_RESOURCES. Not enough system resources were available to complete the operation.
    
6. Initializes the notification engine, creates its window and its thread if requested by the MAPI_MULTITHREAD_NOTIFICATIONS flag. 
    
    MAPI_E_INVALID_OBJECT. May fail if system resources are exhausted. 
    
7. Loads and initializes the profile provider. Verifies that **MAPIInitialize** can access the registry key where profile data are stored. 
    
    MAPI_E_NOT_INITIALIZED. The profile provider has encountered an error. 
    
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|ContentsTableListCtrl.cpp  <br/> ||MFCMAPI uses the **MAPIInitialize** method to initialize MAPI on a background thread to do some table processing. |
   
## See also



[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

