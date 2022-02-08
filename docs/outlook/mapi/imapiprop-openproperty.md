---
title: "IMAPIPropOpenProperty"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIProp.OpenProperty
api_type:
- COM
ms.assetid: e400e6cc-4e36-43fc-9304-b688a0a7fd77
description: "Last modified: March 09, 2015"
---

# IMAPIProp::OpenProperty

**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns a pointer to an interface that can be used to access a property.
  
```cpp
HRESULT OpenProperty(
  ULONG ulPropTag,
  LPCIID lpiid,
  ULONG ulInterfaceOptions,
  ULONG ulFlags,
  LPUNKNOWN FAR * lppUnk
);
```

## Parameters

 _ulPropTag_
  
> [in] The property tag for the property to be accessed. Both the identifier and the type must be included in the property tag.
    
 _lpiid_
  
> [in] A pointer to the identifier for the interface to be used to access the property. The  _lpiid_ parameter must not be **null**.
    
 _ulInterfaceOptions_
  
> [in] Data that relates to the interface identified by the  _lpiid_ parameter. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls access to the property. The following flags can be set:
    
MAPI_CREATE 
  
> If the property does not exist, it should be created. If the property does exist, the current value of the property should be discarded. When a caller sets the MAPI_CREATE flag, it should also set the MAPI_MODIFY flag.
    
MAPI_DEFERRED_ERRORS 
  
> Allows **OpenProperty** to return successfully, possibly before the object is fully available to the caller. If the object is not available, making a subsequent object call can raise an error. 
    
MAPI_MODIFY 
  
> MAPI_MODIFY is required in these situations:
    
  - When opening a stream property, such as **IID_IStream**, to modify it.
    
  - When opening an embedded message attachment, such as [PR_ATTACH_DATA_OBJ](pidtagattachdataobject-canonical-property.md) opened with **IID_IMessage**, to modify it.
    
 _lppUnk_
  
> [out] A pointer to the requested interface to be used for property access.
    
## Return value

S_OK 
  
> The requested interface pointer was successfully returned.
    
MAPI_E_INTERFACE_NOT_SUPPORTED 
  
> The requested interface is not supported for this property.
    
MAPI_E_NO_ACCESS 
  
> The caller has insufficient permissions to access the property.
    
MAPI_E_NO_SUPPORT 
  
> The object cannot provide access to this property through the requested interface.
    
MAPI_E_NOT_FOUND 
  
> The requested property does not exist and MAPI_CREATE was not set in the  _ulFlags_ parameter. 
    
MAPI_E_INVALID_PARAMETER 
  
> The property type in the tag is set to PT_UNSPECIFIED.
    
## Remarks

The **IMAPIProp::OpenProperty** method provides access to a property through a particular interface. **OpenProperty** is an alternative to the [IMAPIProp::GetProps](imapiprop-getprops.md) and [IMAPIProp::SetProps](imapiprop-setprops.md) methods. When either **GetProps** or **SetProps** fails because the property is too large or too complex, call **OpenProperty**. **OpenProperty** is typically used to access properties of type PT_OBJECT. 
  
## Notes to callers

To access message attachments, open the **PR_ATTACH_DATA_OBJ** ([PidTagAttachDataObject](pidtagattachdataobject-canonical-property.md)) property with a different interface identifier, depending on the type of attachment. The following table describes how to call **OpenProperty** for the different types of attachments: 
  
|**Type of attachment**|**Interface identifier to use**|
|:-----|:-----|
|Binary  <br/> |IID_IStream  <br/> |
|String  <br/> |IID_IStream  <br/> |
|Message  <br/> |IID_IMessage  <br/> |
|OLE 2.0  <br/> |IID_IStreamDocfile  <br/> |
   
**IStreamDocfile** is a derivative of the [IStream](https://msdn.microsoft.com/library/aa380034%28VS.85%29.aspx) interface that is based on an OLE 2.0 compound file. **IStreamDocfile** is the best choice for accessing OLE 2.0 attachments because it involves the least amount of overhead. You can use IID_IStreamDocFile for those properties that contain data stored in structured storage available through the [IStorage](https://msdn.microsoft.com/library/aa380015%28VS.85%29.aspx) interface. 
  
For more information about how to use **OpenProperty** with attachments, see the **PR_ATTACH_DATA_OBJ** property and [Opening an Attachment](opening-an-attachment.md).
  
Do not use the **IStream** pointer that you receive to call either its [Seek](https://msdn.microsoft.com/library/aa380043%28v=VS.85%29.aspx) or [SetSize](https://msdn.microsoft.com/library/aa380044%28v=VS.85%29.aspx) method unless you use a zero position or size variable. Also, do not rely on the value of the  _plibNewPosition_ output parameter returned from the **Seek** call. 
  
If you call **OpenProperty** to access a property with the **IStream** interface, use only that interface to make changes to it. Do not attempt to update the property with any of the other [IMAPIProp : IUnknown](imapipropiunknown.md) methods, such as **SetProps** or [IMAPIProp::DeleteProps](imapiprop-deleteprops.md). 
  
Do not try to open a property with **OpenProperty** more than once. The results are undefined because they can vary from provider to provider. 
  
If you need to modify the property to be opened, set the MAPI_MODIFY flag. If you are not sure whether the object supports the property but you think it should, set the MAPI_CREATE and MAPI_MODIFY flags. Whenever MAPI_CREATE is set, MAPI_MODIFY must also be set.
  
You are responsible for recasting the interface pointer returned in the _lppUnk_ parameter to one that is appropriate for the interface specified in the  _lpiid_ parameter. You must also use the returned pointer to call its [IUnknown::Release](https://msdn.microsoft.com/library/ms682317%28v=VS.85%29.aspx) method when you are finished with it. 
  
Sometimes setting the flags in the  _ulFlags_ parameter is not enough to indicate the type of access to the property that is required. You can put additional data, such as flags, in the  _ulInterfaceOptions_ parameter. This data is interface dependent. Some interfaces (such as **IStream**) use it, and others do not. For example, when you open a property to be modified with **IStream**, set the STGM_WRITE flag in the  _ulInterfaceOptions_ parameter in addition to MAPI_MODIFY. When you open a table by using the [IMAPITable](imapitableiunknown.md) interface, you can set  _ulInterfaceOptions_ to MAPI_UNICODE to indicate whether the columns in the table that hold string properties should be in Unicode format. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|StreamEditor.cpp  <br/> |CStreamEditor::ReadTextStreamFromProperty  <br/> |MFCMAPI uses the **IMAPIProp::OpenProperty** method to retrieve a stream interface for large text and binary properties.  <br/> |
   
## See also

- [HrIStorageFromStream](hristoragefromstream.md) 
- [IMAPIProp::DeleteProps](imapiprop-deleteprops.md) 
- [IMAPIProp::GetProps](imapiprop-getprops.md)
- [IMAPIProp::SetProps](imapiprop-setprops.md)
- [IMAPISupport::IStorageFromStream](imapisupport-istoragefromstream.md)
- [IMAPITable : IUnknown](imapitableiunknown.md)
- [IMAPIProp : IUnknown](imapipropiunknown.md)
- [MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
- [Opening an Attachment](opening-an-attachment.md)

