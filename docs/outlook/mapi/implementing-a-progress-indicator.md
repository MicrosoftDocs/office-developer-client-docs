---
title: "Implementing a Progress Indicator"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 3a062a88-e87e-4c0c-944e-544a8f080930
 
 
---

# Implementing a Progress Indicator

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Many of the operations initiated by clients take a significant amount of time. One of the input parameters to these potentially lengthy operations is a pointer to a progress object — an object that implements the [IMAPIProgress : IUnknown](imapiprogressiunknown.md) interface. Progress objects control the appearance and display of progress indicators and are implemented by clients and by MAPI. You can choose whether or not to implement a progress object. The MAPI implementation is available for service providers to use if you elect not to supply an implementation. 
  
Progress objects work with the following pieces of data:
  
- A global minimum value which, when your [IMAPIProgress::Progress](imapiprogress-progress.md) method is called, should be less than or equal to the value of the  _ulValue_ parameter. At the beginning of the operation,  _ulValue_ will be equal to this minimum value. 
    
- A global maximum value which, when your **IMAPIProgress::Progress** method is called, should be greater than or equal to the  _ulValue_ parameter. At the end of the operation,  _ulValue_ will be equal to this maximum value. 
    
- A flags value which indicates whether the progress corresponds to a top or lower level item.
    
- A value that indicates the current level of progress for the operation.
    
- The number of the currently processed items relative to the total.
    
- The total number of items to be processed during the operation.
    
The minimum and maximum values represent the beginning and end of the operation in numeric form. Use 1 for the initial minimum value and 1000 for the initial maximum value, passing these values to service providers in the [IMAPIProgress::GetMin](imapiprogress-getmin.md) and [IMAPIProgress::GetMax](imapiprogress-getmax.md) methods. Service providers reset these values when they call [IMAPIProgress::SetLimits](imapiprogress-setlimits.md). 
  
The flags value is used by service providers to determine how they should set the other values. Initialize the flags value to MAPI_TOP_LEVEL and return this value in your implementation of **GetFlags** until the service provider resets it by calling **SetLimits**. 
  
In your implementation of the **SetLimits** method, save local copies of each of the parameters:  _lpulMin_,  _lpulMax_, and  _lpulFlags_. These values should be readily available when a service provider calls your **GetMin**, **GetMax**, or **GetFlags** methods. 
  
To update the display of the progress indicator, service providers call your **IMAPIProgress::Progress** method. There are three parameters to this method: a value, a count, and a total. Use the first parameter,  _ulValue_, to display the progress indicator. The  _ulValue_ parameter is the progress indicator and will be equal to global  _ulMin_ only at the very beginning of the operation and equal to global  _ulMax_ only at the completion of the operation. 
  
Use the second and third parameters,  _ulCount_ and  _ulTotal_, if available, to display an optional message such as "5 items completed out of 10." If the second and third parameters are set to 0, you can choose whether or not to visually change the progress indicator. Some service providers set these parameters to zeroes to indicate that they are processing a subobject whose progress is monitored relative to a parent object. In this situation, it makes sense to change the display only when the parent object reports progress. Some service providers pass zeroes for these parameters every time. 
  

