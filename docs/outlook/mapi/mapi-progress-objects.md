---
title: "MAPI Progress Objects"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: e446004e-1ef2-4e58-b764-de7b4dcefaf1
description: "Last modified: July 23, 2011"
---

# MAPI Progress Objects

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
With the methods and data of a progress object, you can control how the indicator reports progress. Although a client or MAPI implements the progress object, most of the burden of ensuring the correctness of the progress display falls on service providers. You can guarantee its accuracy by specifying a particular order and value for the parameters that are passed to progress object methods.
  
The following parameters are passed to progress objects:
  
- A bitmask of flags, set with [IMAPIProgress::SetLimits](imapiprogress-setlimits.md) and retrieved with [IMAPIProgress::GetFlags](imapiprogress-getflags.md).
    
- A minimum value (local and global), set with **SetLimits** and retrieved with [IMAPIProgress::GetMin](imapiprogress-getmin.md).
    
- A maximum value (local and global), set with **SetLimits** and retrieved with [IMAPIProgress::GetMax](imapiprogress-getmax.md).
    
- A value that indicates the current percentage of completion of the operation, passed to [IMAPIProgress::Progress](imapiprogress-progress.md).
    
- A count of the number of objects that have so far been processed, passed to **Progress**.
    
- A count of the total number of objects involved in the operation, passed to **Progress**.
    
All service providers begin their progress display processing with a call to **IMAPIProgress::GetFlags** to retrieve the present flags setting. Currently, the flags can be set only to MAPI_TOP_LEVEL. Clients and MAPI initialize the flag to MAPI_TOP_LEVEL, relying on service providers to clear it when appropriate. 
  
The flags value is set to MAPI_TOP_LEVEL while you are working with the top-level object in the operation. The top-level object is the object that is called by the client to begin an operation. In a folder copy operation, this is the folder being copied. In a folder delete operation, this is the folder being deleted. When you make a call to process a lower level object, or subobject, clear the flags value. In a folder copy operation, subobjects are the subfolders that are in the folder being copied. 
  
MAPI allows you to differentiate between top-level objects and subobjects with the MAPI_TOP_LEVEL flag so that all objects involved in an operation can use the same [IMAPIProgress](imapiprogressiunknown.md) implementation to show progress, thereby causing the indicator display to proceed smoothly in a single positive direction. Whether or not the MAPI_TOP_LEVEL flag is set affects the settings of the other parameters in subsequent calls to the progress object. 
  
Because it can be nontrivial to set appropriate parameter values for a progress display at all levels of a multilevel operation, some service providers elect not to show progress for subobjects. 
  
 **To avoid showing progress for subobjects**
  
- Pass NULL for the  _lpProgress_ parameter in the call to process a subobject. For example, if you are copying folders, this is the call to a subfolder's [IMAPIFolder::CopyFolder](imapifolder-copyfolder.md) method. 
    
- Write special code to determine how to interpret the  _lpProgress_ parameter. Because a NULL value for the  _lpProgress_ parameter can also mean that the client should display progress by using the MAPI implementation, special code is necessary to determine when to ignore the  _lpProgress_ parameter and when to call [IMAPISupport::DoProgressDialog](imapisupport-doprogressdialog.md).
    
Call **IMAPIProgress::SetLimits** to set or clear the MAPI_TOP_LEVEL flag and to set local and global minimum and maximum values. The value of the flags setting affects whether the progress object understands the minimum and maximum values to be local or global. When the MAPI_TOP_LEVEL flag is set, these values are considered global and are used to calculate progress for the entire operation. Progress objects initialize the global minimum value to 0 and the global maximum value to 1000. 
  
When MAPI_TOP_LEVEL is not set, the minimum and maximum values are considered local and are used internally by providers to display progress for lower level subobjects. Progress objects save the local minimum and maximum values only so that they can be returned to providers when **GetMin** and **GetMax** are called. 
  
The value, object count, and object total parameters are input to the **IMAPIProgress::Progress** method. The value parameter, a number that indicates the percentage of progress, is required. If the MAPI_TOP_LEVEL flag is set, you can also pass an object count and an object total. Some clients use these values to display a phrase such as "5 items completed out of 10" with the progress indicator. Progress on an operation can be reported strictly as a percentage or as a percentage and in terms of the number of items that have been processed out of the total to be processed. For example, if you are a message store provider and you are performing a copy operation that is copying 10 folders, the progress indicator can supply the user with additional information by displaying a phrase such as "1 of 10", "2 of 10", "3 of 10", and so on until the operation is complete. 
  
## See also

#### Concepts

[MAPI Progress Indicators](mapi-progress-indicators.md)

