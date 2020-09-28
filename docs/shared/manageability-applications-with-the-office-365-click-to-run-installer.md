---
title: "Integrating manageability applications with Microsoft 365 Apps click-to-run installer"
manager: lindalu
ms.date: 10/22/2017
ms.audience: ITPro
localization_priority: Normal
ms.assetid: c0fa8fed-1585-4566-a9be-ef6d6d1b4ce8
description: "Learn how to integrate the Microsoft 365 Apps Click-to-Run installer with a software management solution."
---

# Integrating manageability applications with Microsoft 365 Apps click-to-run installer

Learn how to integrate the Microsoft 365 Apps Click-to-Run installer with a software management solution.
  
The Microsoft 365 Apps Click-to-Run installer provides a COM interface that allows IT Professionals and software management solutions programmatic control over update management. This interface provides additional management capabilities beyond what is provided by the Office Deployment Tool.
  
> [!NOTE]
> This article applies to Office 2016 and later, Office 365. 
  
## Integrating with the Click-to-Run

To use this interface, a manageability application invokes the COM interface and calls exposed APIs that communicate directly with the Click-to-Run installation service. 
  
> [!NOTE]
> The Office Click-to-Run installer can be run from the command-line with parameters that can control the behavior, as documented in [Office Deployment Tool for Click-to-Run](https://www.microsoft.com/download/details.aspx?id=49117). 
  
**Following is a conceptual diagram of the COM interface**

![A diagram of using the COM interface on  the Office Click-To-Run installer.](media/e7ac2523-e67b-4a44-ae67-c048709f872a.png "A diagram of using the COM interface on  the Office Click-To-Run installer")
  
The Microsoft 365 Apps Click-to-Run installer implements a COM-based interface, **IUpdateNotify** registered to CLSID **CLSID_UpdateNotifyObject**.
  
This interface can be invoked as follows:
  
```cpp
hr = CoCreateInstance(CLSID_UpdateNotifyObject, NULL, CLSCTX_ALL,
       IID_IUpdateNotify, 
      (void **)&p); 
```

The call will only succeed if the caller is running under elevated privileges, as the Click-to-Run installation program must be run with elevated privileges.
  
The **IUpdateNotify** COM interface exposes three asynchronous functions responsible for validating the commands and parameters and scheduling execution with the Click-to-Run installation service. 
  
```cpp
HRESULT Download([in] LPWSTR pcwszParameters) // Download update content.
HRESULT Apply([in] LPWSTR pcwszParameters) // Apply update content.
HRESULT Cancel() // Cancel the download action.

```

A forth method, **Status**, can be used to get information about the status of the last executed command or the status of the currently executing command (i.e. success, failure, detailed error codes).
  
```cpp
HRESULT status([out] _UPDATE_STATUS_REPORT* pUpdateStatusReport) // Get status of current action. 
typedef struct _UPDATE_STATUS_REPORT  
{  
UPDATE_STATUS status;  
UINT error; 
BSTR contentid;  
} UPDATE_STATUS_REPORT;

```

There are four states that the Click-to-Run installation service may be in during its lifecycle, during which **IUpdateNotify** methods may be called; Rebooting, Idle, Downloading and Applying. 
  
**Following is the COM Interface State Machine diagram**

![A state diagram for the COM interface.](media/a409003e-6876-4ab3-bb4c-cd0c0fed5cbb.png "A state diagram for the COM interface")
  
> [!NOTE]
> **Rebooting**: When the machine is booting there is a period of time when the Click-to-Run installer service is not available. A successful call to the Status method after a reboot will return eUPDATE_UNKNOWN. 
  
**Idle:** When the Click-to-Run installer is in the idle state, you can call: 
  
- **Apply**: Install previously downloaded content.
    
- **Cancel**: Returns  `0x800000e`, "A method was called at an unexpected time."
    
- **Download**: Downloads new content to the client for later installation.
    
- **Status**: Returns the result of the last completed action, or an error message if the action ended in failure. If there is no previous action, **Status** returns  `eUPDATE_UNKNOWN`.
    
**Downloading:** When the Click-to-Run installer is in the downloading state, you can call: 
  
- **Apply**: Returns an **HRESULT** with the value  `0x800000e`, "A method was called at an unexpected time."
    
- **Cancel**: Stops the download and removes the partially downloaded content.
    
- **Download**: Returns an **HRESULT** with the value  `0x800000e`, "A method was called at an unexpected time." 
    
- **Status**: Returns **DOWNLOAD_WIP** to indicate that download work is in progress. 
    
**Applying:** When the Click-to-Run installer is in the process of installing previously download content: 
  
- **Apply**: Returns an **HRESULT** with the value  `0x800000e`, "A method was called at an unexpected time."
    
- **Cancel**: Returns  `0x800000e`, the Apply action cannot be canceled.
    
- **Download**: Returns an **HRESULT** with the value  `0x800000e`, "A method was called at an unexpected time." 
    
- **Status**: Returns **APPLY_WIP** to indicate that apply work is in progress. 
    
> [!NOTE]
> Since OfficeC2RCOM is a COM+ service and is dynamically loaded, you need to call **CoCreateInstance** every time you call a method on this class to ensure that you get the expected result. The COM+ service will handle creating a new instance if necessary. When one of the methods is called for the first time, COM+ will load the **IUpdateNotify** object and run it within one of the dllhost.exe instances. The new object will stay active for about 3 minutes in idle. If a subsequent call is made within three minutes of the last call, the **IUpdateNotify** object will remain loaded and a new instance is not created. If no call is made within three minutes, the IUpdateNotify object will be unloaded and a new **IUpdateNotify** object will be created when the next call is made. 
  
## Click-to-Run installer COM API reference guide

In the following API reference documentation:
  
- Parameters are in a key/value pair format separated by a space.
    
- The parameters are not case-sensitive.
    
- There is a [list of parameters](https://blogs.technet.microsoft.com/odsupport/2014/03/03/the-new-update-now-feature-for-office-2013-click-to-run-for-office365-and-its-associated-command-line-and-switches/) with documentation available. 
    
- Summary of IUpdateNotify2 interface is now included.
    
### Apply

```cpp
HRESULT Apply([in] LPWSTR pcwszParameters) // Apply update content.
```

#### Parameters

-  _displaylevel_: **true** to show the installation status, including errors, during the update process; **false** to hide the installation status, including errors, during the update process. The default is **false**.
    
-  _forceappshutdown_: **true** to force Office applications to shut down immediately when the **Apply** action is triggered; **false** to fail if any Office applications are running. The default is **false**. See [Remarks](#bk_ApplyRemark) for more information. 
    
  If any Office application is running when the **Apply** action is triggered, the **Apply** action will usually fail. Passing  `forceappshutdown=true` to the **Apply** method will cause the **OfficeClickToRun** service to immediately shut down the applications and apply the update. The user may experience data loss in this case. 
    
#### Return results

|||
|:-----|:-----|
|**S_OK** <br/> |Action was successfully submitted to the Click-To-Run service for execution.  <br/> |
|**E_ACCESSDENIED** <br/> |The caller is not running with elevated privileges.  <br/> |
|**E_INVALIDARG** <br/> |Invalid parameters were passed.  <br/> |
|**E_ILLEGAL_METHOD_CALL** <br/> |Action is not allowed at this time. See [Remarks](#bk_ApplyRemark) for more information.  <br/> |

<a name="bk_ApplyRemark"></a>

#### Remarks

- If any Office application is running when the **Apply** action is triggered, the **Apply** action will fail. Passing  `forceappshutdown=true` to the **Apply** method will cause the **OfficeClickToRun** service to immediately shut down any Office applications that are running and apply the update. The user may experience data as they are not prompted to save changes to open documents.. 
    
- This action can only be triggered when the COM status is one of the following: 
    
  - **eUPDATE_UNKNOWN**
    
  - **eDOWNLOAD_CANCELLED**
    
  - **eDOWNLOAD_FAILED**
    
  - **eDOWNLOAD_SUCCEEDED**
    
  - **eAPPLY_SUCCEEDED**
    
  - **eAPPLY_FAILED**
    
- If you call the **Apply** method without previously downloading content, the **Apply** method will report **Succeeded** as it detected nothing to apply and completed the **Apply** process successfully. 
    
### Cancel

```cpp
HRESULT Cancel() // Cancel the download action.
```

#### Return results

|||
|:-----|:-----|
|S_OK  <br/> |Action was successfully submitted to the Click-to-Run service for execution.  <br/> |
|E_ILLEGAL_METHOD_CALL  <br/> |Action is not allowed at this time. See the [Remarks](#bk_CancelRemarks) section for more information  <br/> |

<a name="bk_CancelRemarks"></a>

#### Remarks

- This method can only be triggered when the COM status id **eDOWNLOAD_WIP**. It will attempt to cancel the current download action. The COM status will change to **eDOWNLOAD_CANCELLING** and eventually change to **eDOWNLOAD_CANCELED**. The COM status will return **E_ILLEGAL_METHOD_CALL** if triggered at any other time. 
    
### Download

```cpp
HRESULT Download([in] LPWSTR pcwszParameters) // Download update content.
```

#### Parameters

-  _displaylevel_: **true** to show the installation status, including errors, during the update process; **false** to hide the installation status, including errors, during the update process. The default is **false**.
    
-  _updatebaseurl_: URL to the alternate download source.
    
-  _updatetoversion_: The version to update Office to. Define this parameter if you want to update to an older version than the version that is currently installed.
    
-  _downloadsource_: CLSID of the customized **IBackgroundCopyManager** implementation (BITS manager). 
    
-  _contentid_: Identifies the content to download from the content server through the customized BITS manager. This value is passed through the BITS interface for interpretation.
    
#### Return results

|||
|:-----|:-----|
|**S_OK** <br/> |Action was successfully submitted to the Click-To-Run service for execution.  <br/> |
|**E_ACCESSDENIED** <br/> |The caller is not running with elevated privileges.  <br/> |
|**E_INVALIDARG** <br/> |Invalid parameters were passed.  <br/> |
|**E_ILLEGAL_METHOD_CALL** <br/> |Action is not allowed at this time. See [Remarks](#bk_DownloadRemark) for more information.  <br/> |

<a name="bk_DownloadRemark"></a>

#### Remarks

- You must specify  _downloadsource_ and  _contentid_ as a pair. If not, the **Download** method will return an **E_INVALIDARG** error. 
    
- If  _downloadsource_,  _contentid_, and  _updatebaseurl_ are provided,  _updatebaseurl_ will be ignored. 
    
- This action can only be triggered when the COM status is one of the following: 
    
  - **eUPDATE_UNKNOWN**
    
  - **eDOWNLOAD_CANCELLED**
    
  - **eDOWNLOAD_FAILED**
    
  - **eDOWNLOAD_SUCCEEDED**
    
  - **eAPPLY_SUCCEEDED**
    
  - **eAPPLY_FAILED**
    
- If you call the **Apply** method without previously downloaded content, the **Apply** method will report **Succeeded** as it detected nothing to apply and completed the **Apply** process successfully. 
    
#### Examples

- To download the content from the customized BITS manager: Call the **download()** function passing the following parameters: 
    
  ```cpp
  "downloadsource=CLSIDofBITSInterface contentid=BITSServerContentIdentifier"
  ```

- To download the content from the Microsoft CDN: Call the **download()** function without specifying the  _downloadsource_,  _contentid_, or  _updatebaseurl_ parameters. 
    
- To download the content from a customized location: Call the **download()** function passing the following parameter: 
    
  ```cpp
  "updatebaseurl=yourcontentserverurl"
  ```

### Status

```cpp
typdef struct _UPDATE_STATUS_REPORT
{
    UPDATE_STATUS status;
    UINT error;
    LPCWSTR contentid;
}UPDATE_STATUS_REPORT;
HRESULT status([out] _UPDATE_STATUS_REPORT& pUpdateStatusReport) // Get status of current action
```

#### Parameters

|||
|:-----|:-----|
| _pUpdateStatusReport_ <br/> |Pointer to an UPDATE_STATUS_REPORT structure.  <br/> |
   
#### Return results

|||
|:-----|:-----|
|**S_OK** <br/> |The **Status** method always returns this result. Inspect the  `UPDATE_STATUS_RESULT` structure for the status of the current action.  <br/> |
   
#### Remarks

- The status field of the  `UPDATE_STATUS_REPORT` contains the status of the current action. One of the following status values is returned: 
    
  ```cpp
  typedef enum _UPDATE_STATUS
  {
  eUPDATE_UNKNOWN = 0,
  eDOWNLOAD_PENDING,
  eDOWNLOAD_WIP,
  eDOWNLOAD_CANCELLING,
  eDOWNLOAD_CANCELLED,
  eDOWNLOAD_FAILED,
  eDOWNLOAD_SUCCEEDED,
  eAPPLY_PENDING,
  eAPPLY_WIP,
  eAPPLY_SUCCEEDED,
  eAPPLY_FAILED,
  } UPDATE_STATUS;
  
  ```

- If the last command resulted in an error, the error field of the  `UPDATE_STATUS_REPORT` contains detailed information about the error. Two types of error codes are returned from the **Status** method. 
    
- If the error less than  `UPDATE_ERROR_CODE::eUNKNOWN`, the error is one of the following pre-defined error codes:
    
  ```cpp
  typedef enum _UPDATE_ERROR_CODE
  {
  eOK = 0,
  eFAILED_UNEXPECTED,
  eTRIGGER_DISABLED,
  ePIPELINE_IN_USE,
  eFAILED_STOP_C2RSERVICE,
  eFAILED_GET_CLIENTUPDATEFOLDER,
  eFAILED_LOCK_PACKAGE_TO_UPDATE,
  eFAILED_CREATE_STREAM_SESSION,
  eFAILED_PUBLISH_WORKING_CONFIGURATION,
  eFAILED_DOWNLOAD_UPGRADE_PACKAGE,
  eFAILED_APPLY_UPGRADE_PACKAGE,
  eFAILED_INITIALIZE_RSOD,
  eFAILED_PUBLISH_RSOD,
  // Keep this one as the last
  eUNKNOWN
  } UPDATE_ERROR_CODE;
  
  ```

  If the return error code is larger than  `UPDATE_ERROR_CODE::eUNKNOWN` it is the **HRESULT** of a failed function call. To extract the HRESULT subtract  `UPDATE_ERROR_CODE::eUNKNOWN` from the value returned in the error field of the  `UPDATE_STATUS_REPORT`.
    
  The complete list of status and error values can be viewed by inspecting the **IUpdateNotify** type library embedded in OfficeC2RCom.dll. 
    
- The contentid field is used for calls to **Status** after **Download** has initiated and returns the contentid that was passed in to the **Download** call. It is a best practice to initialize this field to **null** before you call the **Status** method and then check the value after **Status** has been returned. If the value is still **null**, that means there is no contentid to return. If the value is not **null**, you need to free it with a call to **SysFreeString()**. Here is a code snippet of how to call **Status** after **Download**.
    
  ```cpp
  std::wstring contentID;
  UPDATE_STATUS_REPORT statusReport;
  statusReport.status = eUPDATE_UNKNOWN;
  statusReport.error = eOK;
  statusReport.contentid = NULL;
  hr = p->Status(&statusReport);
  if (statusReport.contentid != NULL)
  {
  contentID = statusReport.contentid;
  SysFreeString(statusReport.contentid);
  }
  wprintf(L"ContentID: %s, Status: %d, LastError: %d", contentID.c_str(), statusReport.status, statusReport.error);
  
  ```

### Summary of IUpdateNotify2 interface

> [!NOTE]
> This summary is provided as a compliment info to [Integrating manageability applications with the Office 365 click-to-run installer](https://docs.microsoft.com/office/client-developer/shared/manageability-applications-with-the-office-365-click-to-run-installer). Once the public doc is updated, this doc can be considered as obsolete. 
  
From C2RTenant [16.0.8208.6352](https://oloop/BuildGroup/Details/tenantc2rclient#3519/1255278) (First publicly available build should be June fork build -- 8326.*) we have added a new **IUpdateNotify2** interface. Here is some basic info about this interface: 
  
- CLSID_UpdateNotifyObject2, {52C2F9C2-F1AC-4021-BF50-756A5FA8DDFE}
    
- This interface also hosted the original IUpdateNotify interface to provide backward compatibility. Which means if you use this interface, you have access to all the methods provided in **UpdateNotifyObject** interface. 
    
- New methods added to IUpdateNotify2:
    
  - **HRESULT** GetBlockingApps([out] BSTR \* AppsList). Get updates blocking apps list. This call will return running Office apps which will block the update process from proceeding. 
    
  - **HRESULT** GetOfficeDeploymentData([in] int dataType, [in] **LPCWSTR** pcwszName, [out] BSTR * OfficeData). Get Office deployment Data. 
    
- If you want to use the new methods, you need to make sure:
    
  - Your C2R version is newer than the above build (\>= June fork build).
    
  - Use UpdateNotifyObject2, instead of **UpdateNotifyObject** to call **CoCreateInstance**.
    
If you don't use any of the new methods, you don't need to change anything. All the existing methods will work as exact the same way as before.
  
## Implementing the BITS interface

The [Background Intelligent Transfer Service](https://docs.microsoft.com/windows/win32/bits/background-intelligent-transfer-service-portal) (BITS) is a service provided by Microsoft to transfer files between a client and server. BITS is one of the channels that Office Click-To-Run installer can use to download content. By default, the Microsoft 365 Apps Click-To-Run installer uses the Windows' built in implementation of BITS to download the content from the CDN. 
  
By providing a customized BITS implementation to the **download()** method of the **IUpdateNotify** interface, your manageability software can control where and how the client downloads the content. A customized BITS interface is useful when providing a custom content distribution channel other than the Click-to-Run built-in channels, such as the Office CDN, IIS servers, or file shares. 
  
The minimum requirement for a customized BITS interface to work with Office C2R service is:
  
- For **IBackgroundCopyManager**:
    
  ```cpp
  HRESULT _stdcall CreateJob(
                      [in] LPWSTR DisplayName, 
                      [in] BG_JOB_TYPE Type, 
                      [out] GUID* pJobId, 
                      [out] IBackgroundCopyJob** ppJob)
  HRESULT _stdcall GetJob(
                      [in] GUID* jobID, 
                      [out] IBackgroundCopyJob** ppJob)
  HRESULT _stdcall EnumJobs(
                      [in] unsigned long dwFlags, 
                      [out] IEnumBackgroundCopyJobs** ppenum)
  
  ```

- For **IBackgroundCopyJob**:
    
  ```cpp
  HRESULT _stdcall AddFile(
                      [in] LPWSTR RemoteUrl, 
                      [in] LPWSTR LocalName)
  HRESULT _stdcall Resume()
  HRESULT _stdcall Complete()
  HRESULT _stdcall Cancel();
  HRESULT _stdcall GetState([out] BG_JOB_STATE* pVal);
  HRESULT GetProgress( [out] BG_JOB_PROGRESS *pProgress);
  
  ```

- For **IBackgroundCopyJob3**:
    
  ```cpp
  HRESULT _stdcall AddFileWithRanges(
                      [in] LPWSTR RemoteUrl, 
                      [in] LPWSTR LocalName,
                      [in] DWORD RangeCount,
                      [in] BG_FILE_RANGE Ranges[])
  
  ```

- For the  `Addfile` and  `AddFileWithRanges` functions, the remote URL is in the following format: 
    
  ```cpp
  cmbits://<contentid>/<relative path to target file>
  ```

  - cmbits is hard coded, and stands for customized BITS.
    
  -  _\<contentid\>_ is the  _contentid_ parameter for the **Download()** method. 
    
  -  _\<relative path to target file\>_ provides the location and file name of the file to download. 
    
    For example, if you have provided a  _contentid_ of  `f732af58-5d86-4299-abe9-7595c35136ef` to the **Download()** method, and Office C2R wants to download the version cab file, such as  `v32.cab` file, it will call **AddFile()** with the following  `RemoteUrl`:
    
  ```cpp
  cmbits://f732af58-5d86-4299-abe9-7595c35136ef/Office/Data/V32.cab
  ```

- For **IBackgroundCopyError**:
    
  ```cpp
  HRESULT _stdcall GetErrorDescription(
        [in]  DWORD  LanguageId,
        [out] LPWSTR *ppErrorDescription);
  
  ```

- For **IBackgroundCopyFile**:
    
  ```cpp
  HRESULT _stdcall GetLocalName([out] LPWSTR *ppName); 
  HRESULT _stdcall GetRemoteName([out] LPWSTR *ppName);
  
  ```
## Automating content staging

IT administrators can choose to have desktop clients enabled to automatically receive updates when they are available directly from the Microsoft Content Delivery Network (CDN) or they can choose to control the deployment of updates available from the update channels using the Office Deployment Tool or System Center Configuration Manager.
  
The service supports the ability for management tools to recognize and automate the download of the content when updates are made available.
  
**The following image is an overview of downloading a custom image**

![A diagram of using the COM interface on  the Office Click-To-Run installer.](media/e7ac2523-e67b-4a44-ae67-c048709f872a.png "A diagram of using the COM interface on  the Office Click-To-Run installer")
  
### Overview of downloading a custom image
  
In the previous diagram, you see that a new Microsoft 365 Apps image is available on the Office Content Distribution Network (CDN). Along with the Microsoft 365 Apps image, an API is available which has the information needed to enable manageability software to directly create customized images replacing the need for using the Office Deployment Tool.

An enterprise configures their WSUS to sync the Microsoft 365 Apps updates. These updates do not contain the actual image payload but does allow the manageability software to recognize when new content is available. The manageability software can then read the Microsoft 365 Apps Update metadata to understand what version of Office the update applies to.

If the update is applicable, the manageability software can use the CDN content and the file list to create the custom image and store it onto the file share location that it is configured to use.
  
### Using the Microsoft 365 Apps file list API

The Microsoft 365 Apps file list API is used to retrieve the names of the files needed for a particular Microsoft 365 Apps update.

HTTP Request

GET https://config.office.com/api/filelist

Do not supply a request body for this method.

No permissions are required to call this API.

Optional query parameters

| Name       | Description|
|:-----------|:----------|
| channel | Specifies the channel name |
| | Optional – default to ‘SemiAnnual’ |
| | Supported values https://docs.microsoft.com/en-us/DeployOffice/office-deployment-tool-configuration-options#channel-attribute-part-of-add-element |
| version | Specifies the update version |
| | Optional – defaults to the latest version available for the specified channel |
| arch | Specifies client architecture |
| | Optional – defaults to ‘x64’ |
| | Supported values: x64, x86 |
| lid | Specifies the language files to include |
| | Optional – defaults to none |
| | To specify multiple languages, include an lid query parameter for each language |
| | Use the language identifier format, ex. ‘en-us’, ‘fr-fr’ |
| alllanguages | Specifies to include all language files |
| | Optional – defaults to false |

HTTP Response

If successful, this method returns a 200 OK response code and collection of file objects in the response body.

To create an image, follow these steps:
1.	Call the API, providing the appropriate query parameters for the channel, version and architecture of the update you are interested in.
Note: File objects with the attribute "lcid": "0" are language neutral files and must be included in the image.
2.	Construct a local image of the CDN by iterating through the file objects and copying the CDN files, while creating the folder structure as specified by the “relativePath” attribute defined for each of the file objects.

The following example retrieves the file list for the Current Channel and version 16.0.4229.1004 for 64bit and includes the French and English language files:

```http
Get https://config.office.com/api/filelist?Channel=Current&Version=16.0.4229.1004&Arch=x64&Lid=fr-fr&Lid=en-US
```

### Hash verification of .dat files

Image creation tools may verify the integrity of the downloaded .dat files by comparing a computed hash value with the supplied hash value associated with each of the .dat files. Following is an example of a file object that specifies hashLocation and hashAlgorithm values:
  
```xml
{
  "url": "http://officecdn.microsoft.com/pr/7ffbc6bf-bc32-4f92-8982-f9dd17fd3114/office/data/16.0.1234.1001/stream.x64.x-none.dat",
  "name": "stream.x64.x-none.dat",
  "relativePath": "/office/data/16.0.1234.1001/",
  "hashLocation": "s640.cab/stream.x64.x-none.hash",
  "hashAlgorithm": "Sha256",
  "lcid": "0"
},
```

- The **hashLocation** attribute specifies the relative path location of .cab file that contains the hash value. Construct the hash file location by concatenating URL + relativePath + hashLocation. In the following example, the stream.x64.bg-bg.hash location would be: 
    
  ```http
  https://officecdn.microsoft.com/pr/492350f6-3a01-4f97-b9c0-c7c6ddf67d60/office/data/16.0.4229.1004/s641026.cab/stream.x64.bg-bg.hash 
  ```

- The **hashAlgorithm** attribute specifies what hashing algorithm was used. 
    
  To validate the integrity of the stream.x64.bg-bg.dat file, open the stream.x64.bg-bg.hash and read the HASH value which is the first line of text in the hash file. Compare this to the computed hash value (using the specified hashing algorithm) to verify the integrity of the downloaded .dat file.
    
  The following example shows the C# code to read the hash.
    
  ```cs
    string[] readHashes = System.IO.File.ReadAllLines(tmpFile, Encoding.Unicode);
    string readHash = readHashes.First();
  ```

### Microsoft 365 Apps Updates

All Microsoft 365 Apps Updates are published to the [Microsoft Update Catalog](https://www.catalog.update.microsoft.com/Search.aspx?q=office+365+client).
  
Microsoft 365 Apps Updates enable manageability software to treat Microsoft 365 Apps Updates in a manner very similar to any other WU update with one exception; the client updates do not contain an actual payload. The Microsoft 365 Apps Updates should not be installed on any clients but rather used to trigger the workflows with the manageability software replacing the installation command with the COM based installation mechanism shown above.

**The following figure shows a diagram of the Office 365 Client Update workflow.**

![Workflow diagram for O365PP client updates.](media/bc8092b0-62b8-402c-a5c0-04d55cca01d4.png "Workflow diagram for O365PP client updates")
  
Each Microsoft 365 Apps Update that is published includes metadata about the update. This metadata includes a parameter called MoreInfoUrl which can be used to derive the API call to the file list API for that specific update.

In the following example, the file list API is embedded in the MoreInfoURL and starts with “ServicePath=”

http://go.microsoft.com/fwlink/?LinkId=626090&Ver=16.0.12527.21104&Branch=Insiders&Arch=64&XMLVer=1.6&xmlPath=http://officecdn.microsoft.com/pr/wsus/ofl.cab&xmlFile=O365Client_64bit.xml& ServicePath=https://config.office.com/api/filelist?Channel=Insiders&Version=16.0.12527.21104&Arch=64&AllLanguages=True
  
### Additional metadata for automating content staging

**Release History API**
  
The Microsoft 365 Apps release history API is used to retrieve details for each of the updates published to the Microsoft Office CDN along with the channel names and other channel attributes.

HTTP Request

```http
GET https://config.office.com/api/filelist/channels 
```

Do not supply a request body for this method.

No permissions are required to call this API.

HTTP Response

If successful, this method returns a 200 OK response code and collection of file objects in the response body.

**SKUs API**
  
The SKUs API returns information that is useful for determining which products are available for deployment and servicing from the Office CDN along with various options for each.

HTTP Request

```http
GET https://config.office.com/api/filelist/skus 
```

Do not supply a request body for this method.

No permissions are required to call this API.

HTTP Response

If successful, this method returns a 200 OK response code and collection of file objects in the response body.
