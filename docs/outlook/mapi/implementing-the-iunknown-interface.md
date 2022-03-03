---
title: "Implementing the IUnknown Interface"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 01bba63b-a2a1-490e-8b78-5c9ba8d9547b
 
 
---

# Implementing the IUnknown Interface

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The methods of the [IUnknown](https://msdn.microsoft.com/library/ms680509%28v=VS.85%29.aspx) interface, implemented in every MAPI object, support interobject communication and object management. 
  
 **IUnknown** has three methods: [IUnknown::AddRef](https://msdn.microsoft.com/library/ms691379%28v=VS.85%29.aspx), [IUnknown::QueryInterface](https://msdn.microsoft.com/library/ms682521%28v=VS.85%29.aspx), and [IUnknown::Release](https://msdn.microsoft.com/library/ms682317%28v=VS.85%29.aspx). **QueryInterface** enables one object to determine whether another object supports a particular interface. With **QueryInterface**, two objects with no prior knowledge of each other's functionality can interact. If the object that implements **QueryInterface** does support the interface in question, it returns a pointer to the implementation of the interface. If the object does not support the requested interface, it returns the MAPI_E_INTERFACE_NOT_SUPPORTED value. 
  
When **QueryInterface** returns a requested interface pointer, it must also increase the new object's reference count. An object's reference count is a numeric value used to manage the object's lifespan. When the reference count is greater than 1, the object's memory cannot be freed because it is actively being used. It is only when the reference count drops to 0 that the object can be released safely. 
  
The other two **IUnknown** methods, **AddRef** and **Release**, manage the reference count. **AddRef** increments the reference count, while **Release** decrements it. All methods or API functions that return interface pointers, such as **QueryInterface**, must call **AddRef** to increment the reference count. All implementations of methods that receive interface pointers must call **Release** to decrement the count when the pointer is no longer needed. **Release** checks for an existing reference count, freeing the memory associated with the interface only if the count is 0. 
  
> [!NOTE]
> Because **AddRef** and **Release** are not required to return accurate values, callers of these methods must not use the return values to determine whether an object is still valid or has been destroyed. 
  
## See also



[Implementing MAPI Objects](implementing-mapi-objects.md)

