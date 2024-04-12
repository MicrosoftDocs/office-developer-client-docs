---
title: "Display a progress indicator"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 20f5ad5a-b700-4fb5-9658-f71da5a06a12
---

# Display a progress indicator
 
**Applies to**: Outlook 2013 | Outlook 2016 
  
To display a progress indicator, call [IMAPIProgress::GetFlags](imapiprogress-getflags.md) to retrieve the current flags setting. 
  
If the MAPI_TOP_LEVEL flag is set, complete the following steps:
  
1. Set a variable equal to the total number of items to process in the operation. For example, if you are copying the contents of a folder, this value will be equal to the number of the subfolders in the folder plus the number of messages. 
    
2. Set a variable equal to 1000 divided by the number of items. 
    
3. If you are showing progress for subobjects, call the progress object's [IMAPIProgress::SetLimits](imapiprogress-setlimits.md) method and pass the following values for the three parameters: 
    
   - Set the  _lpulMin_ parameter to 0. 
    
   - Set the  _lpulMax_ parameter to 1000. 
    
   - Set the  _lpulFlags_ parameter to MAPI_TOP_LEVEL. 
    
4. For each object to be processed, complete the following steps:
    
   1. Call **IMAPIProgress::SetLimits** and pass the following values for the three parameters: 
      
     - Set the  _lpulMin_ parameter to the variable set in step 2 multiplied by the current item minus 1. 
      
     - Set the  _lpulMax_ parameter to the variable set in step 2 multiplied by the current object. 
      
     - Set the  _lpulFlags_ parameter to 0. 
      
   2. Perform whatever processing should be done on this object. If this is a subobject and you want to display progress on subobjects, pass a pointer to the progress object in the _lpProgress_ parameter to the method. 
      
   3. Call [IMAPIProgress::Progress](imapiprogress-progress.md) and pass the following values for the three parameters: 
      
     - Set the  _ulValue_ parameter to the variable set in step 2 multiplied by the current object. 
      
     - Set the  _ulCount_ parameter to the current object. 
      
     - Set the  _ulTotal_ parameter to the variable set in step 1, the total number of objects. 
    
If the MAPI_TOP_LEVEL flag is not set, complete the following steps:
  
1. Call the progress object's [IMAPIProgress::GetMin](imapiprogress-getmin.md) method to retrieve the minimum value for the display. 
    
2. Call [IMAPIProgress::GetMax](imapiprogress-getmax.md) to retrieve the maximum value for the display. 
    
3. Set a variable equal to the total number of objects to be processed. 
    
4. Set a variable equal to the result of subtracting the minimum value from the maximum value and then dividing by the total number of objects.
    
5. For each object to be processed, complete the following steps:
    
   1. If your provider is showing progress for subobjects, call **IMAPIProgress::SetLimits** and pass the following values for the three parameters: 
      
     - Set the  _lpulMin_ parameter to the minimum value plus the current item minus 1 multiplied by the variable set in step 4. 
      
     - Set the  _lpulMax_ parameter to the minimum value plus the current unit multiplied by the variable set in step 4. 
      
     - Set the  _lpulFlags_ parameter to 0. 
      
   2. Perform whatever processing should be done on this object. If the object is a subobject, and your provider displays progress for subobjects, pass a pointer to the progress object in the _lpProgress_ parameter to the method. 
      
   3. Call [IMAPIProgress::Progress](imapiprogress-progress.md) and pass the following values for the three parameters: 
      
     - Set the  _ulValue_ parameter to variable set in step 2 multiplied by the current object. 
      
     - Set the  _ulCount_ parameter to 0. 
      
     - Set the  _ulTotal_ parameter to 0.
    
The following code example illustrates the logic required to show progress at all levels of an operation that copies the contents of a folder that contains five subfolders. 
  
```cpp
lpProgress->GetFlags (lpulFlags);
ulFlags = *lpulFlags;
/* The folder in charge of the display. It contains 5 subfolders. */
if (ulFlags & MAPI_TOP_LEVEL)
{
    ulItems = 5                         // 5 subfolders in this folder
    ulScale = (ulMax / ulItems)         // 200 because ulMax = 1000
    lpProgress->SetLimits(0, ulMax, MAPI_TOP_LEVEL)
    for (i = 1; i <= ulItems; i++)      // for each subfolder to copy
    {
        lpProgress->SetLimits( (i - 1) * ulScale, i * ulScale, 0)
        CopyOneFolder(lpFolder(i), lpProgress)
        lpProgress->Progress( i * ulScale, i, ulItems)
    }
}
else
/* One of the subfolders to be copied. It contains 3 messages. */
{
    lpProgress->GetMin(&ulMin);
    lpProgress->GetMax(&ulMax);
    ulItems = 3;
    ulDelta = (ulMax - ulMin) / ulItems;
    for (i = 1; i <= ulItems; i++)
    {
        lpProgress->SetLimits(ulMin + (i - 1) * ulDelta,
                              ulMin + i * ulDelta, 0)
        CopyOneFolder(lpFolder(i), lpProgress)
        /* Pass 0 for ulCount and ulTotal because this is not the */
        /* top-level display, and that information is unavailable */
        lpProgress->Progress( i * ulDelta, 0, 0)
    }
}
 
```

## See also

- [MAPI Progress Indicators](mapi-progress-indicators.md)
