---
title: "Outlook Social Connector provider error codes"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: overview
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 0799243e-ba92-44c4-b687-182e50b57cb7
description: "Providers should return errors to the caller by using one of the error codes shown in the following table."
---

# Outlook Social Connector provider error codes

Providers should return errors to the caller by using one of the error codes shown in the following table. 
  
|**Error**|**Error code (hexadecimal)**|**Description**|
|:-----|:-----|:-----|
|OSC_E_AUTH_ERROR  <br/> |0x80041404  <br/> |Authentication failed on the network of the social network site.  <br/> |
|OSC_E_COULDNOTCONNECT  <br/> |0x80041402  <br/> |No connection is available to connect to the social network site.  <br/> |
|OSC_E_FAIL  <br/> |0x80004005  <br/> |General failure error.  <br/> |
|OSC_E_INTERNAL_ERROR  <br/> |0x80041400  <br/> |An internal error occurred because of an invalid operation.  <br/> |
|OSC_E_INVALIDARG (E_INVALIDARG)  <br/> |0x80070057  <br/> |An invalid argument was passed to a function.  <br/> |
|OSC_E_NO_CHANGES  <br/> |0x80041406  <br/> |No changes have occurred since the last synchronization.  <br/> |
|OSC_E_NOT_FOUND  <br/> |0x80041405  <br/> |A resource cannot be found.  <br/> |
|OSC_E_NOT_IMPLEMENTED (E_NOTIMPL)  <br/> |0x80004001  <br/> |The request to the social network site is valid but has not been implemented by the social network site.  <br/> |
|OSC_E_OUT_OF_MEMORY (E_OUTOFMEMORY)  <br/> |0x8007000E  <br/> |An out-of-memory error occurred.  <br/> |
|OSC_E_PERMISSION_DENIED  <br/> |0x80041403  <br/> |The OSC provider denied permission for the resource.  <br/> |
|OSC_E_SERVER_VERSION_NOT_SUPPORTED  <br/> |0x80041406  <br/> |The version of the server to configure the social network account is not supported.  <br/> |
|OSC_E_VERSION  <br/> |0x80041401  <br/> |The provider does not support this version of OSC provider extensibility.  <br/> |
   
## Remarks

Success, warning, and error values are returned by using a 32-bit number that is called a result handle, or **HRESULT**. An **HRESULT** is not a handle to anything; it is merely a 32-bit value that has several fields encoded in the value. A positive result indicates success with status, a zero result indicates success without status (S_OK), and a negative result indicates failure. 
  

