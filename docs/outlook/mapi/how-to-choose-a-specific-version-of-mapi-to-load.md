---
title: "How to Choose a Specific Version of MAPI to Load"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 85539a7f-74b6-4267-86ea-00da2c900c34
description: "Last modified: March 09, 2015"
 
 
---

# How to: Choose a Specific Version of MAPI to Load

  
  
**Applies to**: Outlook 
  
When linking explicitly to an implementation of MAPI, you must carefully select which implementation to load. 
  
There are two methods to link explicitly to an implementation of MAPI. 
  
1. You can load the MAPI stub library, and specify in the registry a custom DLL to load and dispatch MAPI calls to.
    
2. You can implement the MAPI client lookup algorithm to look up the version of MAPI used by the default mail client and load it.
    
Because you can change the [Mapi32.dll Stub Registry Settings](http://msdn.microsoft.com/en-us/library/ms531218%28EXCHG.10%29.aspx) to direct your application to use any implementation of MAPI, we recommend that you direct your application to use an implementation of MAPI that you have tested with. The following describes both methods of linking explicitly. 
  
## Reading from the Registry

### To Read MAPI Implementation Information from the Registry

1. The registry keys that indicate a custom DLL for a mail client are located under the  `HKLM\Software\Clients\Mail` key of the mail client. 
    
    The following table describes these keys:
    
|**Key**|**Description**|
|:-----|:-----|
|MSIComponentID  <br/> |A Windows Installer PublishComponent category ID (GUID) that identifies the DLL that exports simple MAPI or MAPI calls. If set, this key takes precedence over the **DLLPath** or **DLLPathEx** key.  <br/> |
|MSIApplicationLCID  <br/> |Locale identifier (LCID) for your application. The first string value identifies a sub-key from  `HKLM\Software` and subsequent string values identify registry values underneath this key that contain locale information.  <br/> |
|MSIOfficeLCID  <br/> |LCIDs for Microsoft Office. The first string value identifies a sub-key from  `HKLM\Software` and subsequent string values identify registry values underneath this key.  <br/> |
   
    Obtain the information from these keys.
    
2. Pass the values that you obtained from the previous step to the [FGetComponentPath](fgetcomponentpath.md) function. **FGetComponentPath** is a function that is exported by the MAPI stub library Mapistub.dll. It returns the path of the custom version of MAPI. 
    
### 

### To Load the Implementation of MAPI Marked as Default

1. Read the  `HKLM\Software\Clients\Mail::(default)` registry value. 
    
2. Look up the information for the indicated client as described earlier.
    
> [!NOTE]
> Note that the default mail client might not implement Extended MAPI. 
  
### Example

To load MAPI as implemented by Outlook, look up the registry keys under  `HKLM\Software\Clients\Mail\Microsoft Outlook` and pass them to **FGetComponentPath**. **FGetComponentPath** will return the path for Outlook's implementation of MAPI. 
  
If the keys **MSIComponentID**, **MSIApplicationLCID**, and **MSIOfficeLCID** are not set, check the **DLLPathEx** registry value. If the keys are set, **FGetComponentPath** gives the path of the client's implementation of MAPI. 
  
## Implementing the MAPI Client Lookup Algorithm

The following table lists the four functions from MFCMAPI that are used to look up the path for a custom implementation of MAPI:
  
|**Function**|**Description**|
|:-----|:-----|
| `GetMAPIPath` <br/> |Gets the MAPI library path.  <br/> |
| `GetMailKey` <br/> |Gets the MAPI mail registry key.  <br/> |
| `GetMapiMsiIds` <br/> |Gets the Windows Installer identifier.  <br/> |
| `GetComponentPath` <br/> |Gets the component path using [FGetComponentPath](fgetcomponentpath.md).  <br/> |
   
Because MFCMAPI loads the default implementation of MAPI by default, if you want to use a different implementation of MAPI, you must explicitly direct it to do so. This is performed by using the **Session\Load MAPI** routine. 
  
### The following steps describe how these functions work:

1. MFCMAPI calls  `GetMAPIPath`, passing NULL for the client parameter, to load the default MAPI implementation.
    
2.  `GetMAPIPath` calls  `GetMapiMsiIds` to read the values for **MSIComponentID**, **MSIApplicationLCID**, and **MSIOfficeLCID**.
    
3.  `GetMapiMsiIds` calls  `GetMailKey` to open the registry key for the default mail client. 
    
4.  `GetMapiMsiIds` uses the registry handle returned by  `GetMailKey` to look up values for **MSIComponentID**, **MSIApplicationLCID**, and **MSIOfficeLCID**.
    
5. The values for **MSIComponentID**, **MSIApplicationLCID**, and **MSIOfficeLCID**, are returned to  `GetMAPIPath`.  `GetMAPIPath` then passes them to  `GetComponentPath`.
    
6.  `GetComponentPath` loads the MAPI stub library, Mapi32.dll, from the system directory. 
    
7.  `GetComponentPath` then retrieves the address of the **FGetComponentPath** function from Mapi32.dll, assuming that Mapi32.dll exports **FGetComponentPath**.
    
8. If getting the address of **FGetComponentPath** from Mapi32.dll fails,  `GetComponentPath` retrieves the address from Mapistub.dll. 
    
9.  `GetComponentPath` then calls **FGetComponentPath**, obtaining the path of the default version of MAPI.
    
10.  `GetMAPIPath` then returns this path to the caller, which then loads MAPI and explicitly links to it as described in [How to: Link to MAPI Functions](how-to-link-to-mapi-functions.md).
    
## Notes

- To support localized copies of MAPI for English and non-English locales,  `GetMAPIPath` reads the values for the **MSIApplicationLCID** and **MSIOfficeLCID** subkeys.  `GetMAPIPath` then calls **FGetComponentPath**, first specifying **MSIApplicationLCID** as **szQualifier**, and again specifying **MSIOfficeLCID** as **szQualifier**. 
    
    For more information about registry keys for mail clients that support non-English languages, see [Setting Up the MSI Keys for Your MAPI DLL](http://msdn.microsoft.com/en-us/library/ee909494%28VS.85%29.aspx).
    
- If MFCMAPI does not receive a path for MAPI using  `GetMAPIPath`, it loads the MAPI stub library from the system directory.
    
- The **MSMapiApps** registry value discussed in [Explicitly Mapping MAPI Calls to MAPI DLLs](http://msdn.microsoft.com/en-us/library/ee909490%28VS.85%29.aspx) only applies when the MAPI Stub library is used. Applications that load a specific implementation of MAPI or load the default implementation do not have to set the **MSMapiApps** registry key. 
    
## See also

#### Reference

[FGetComponentPath](fgetcomponentpath.md)
#### Concepts

[MAPI Programming Overview](mapi-programming-overview.md)
  
[How to: Link to MAPI Functions](how-to-link-to-mapi-functions.md)
#### Other resources

[Mapi32.dll Stub Registry Settings](http://msdn.microsoft.com/en-us/library/ms531218%28EXCHG.10%29.aspx)
  
[Setting Up the MSI Keys for Your MAPI DLL](http://msdn.microsoft.com/en-us/library/ee909494%28VS.85%29.aspx)
  
[Explicitly Mapping MAPI Calls to MAPI DLLs](http://msdn.microsoft.com/en-us/library/ee909490%28VS.85%29.aspx)

