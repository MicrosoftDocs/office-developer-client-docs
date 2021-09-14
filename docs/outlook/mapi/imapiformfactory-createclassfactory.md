---
title: "IMAPIFormFactoryCreateClassFactory"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIFormFactory.CreateClassFactory
api_type:
- COM
ms.assetid: dceb21b1-be5e-418d-b0c9-db39195fc82e
description: "Last modified: July 23, 2011"
---

# IMAPIFormFactory::CreateClassFactory

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns a class factory object for the form.
  
```cpp
HRESULT CreateClassFactory(
  REFCLSID clsidForm,
  ULONG ulFlags,
  LPCLASSFACTORY FAR * lppClassFactory
);
```

## Parameters

 _clsidForm_
  
> [in] A class identifier for the form to be created by the class factory.
    
 _ulFlags_
  
> [in] Reserved; must be zero.
    
 _lppClassFactory_
  
> [out] A pointer to the class factory object.
    
## Return value

S_OK 
  
> The class factory object was returned.
    
## Remarks

Form viewers call the **IMAPIFormFactory::CreateClassFactory** method to obtain a class factory for a specific form. The class factory is used to create instances of a form that handles messages of a specific class and to control the access to these instances. 
  
The **CreateClassFactory** method is called by form viewers to obtain a class factory object for form servers that implement multiple message classes. This method receives a class identifier (CLSID) as a parameter. Based on that parameter, this method can determine the specific kind of class factory object to return. 
  
## Notes to implementers

You can return from your **CreateClassFactory** implementation the same class factory object on multiple calls for the same class identifier. Creating a new class factory instance is not required. 
  
You can have a single class factory implementation that creates appropriate class factory instances on demand, or multiple class factory implementations, one for each message class.
  
## See also



[IMAPIFormFactory : IUnknown](imapiformfactoryiunknown.md)

