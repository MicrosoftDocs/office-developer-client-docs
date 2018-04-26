---
title: "CreateObject Method (RDS)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 130debe5-31cf-4ab0-5f78-9adaec7d7126
---

# CreateObject Method (RDS)

Creates the proxy for the target business object and returns a pointer to it. The proxy packages and marshals data to the server-side stub for communications with the business object to send requests and data over the Internet. For in-process component objects, no proxies are used, just a pointer to the object is provided.
  
## Syntax

Remote Data Service supports the following protocols: HTTP, HTTPS (HTTP over Secure Socket Layer), DCOM, and in-process.
  
|**Protocol**|**Syntax**|
|:-----|:-----|
|HTTP  <br/> |**Set** *object*  =  *DataSpace*  . **CreateObject**(" *ProgId*  ", "  *http://awebsrvr*  ")  <br/> |
|HTTPS  <br/> |**Set** *object*  =  *DataSpace*  . **CreateObject**(" *ProgId*  ", "  *https://awebsrvr*  ")  <br/> |
|DCOM  <br/> |**Set** *object*  =  *DataSpace*  . **CreateObject**(" *ProgId*  ", "  *computername*  ")  <br/> |
|In-process  <br/> |**Set** *object*  =  *DataSpace*  . **CreateObject**(" *ProgId*  ", " ")  <br/> |
   
## Parameters

-  *Object* 
    
- An object variable that evaluates to an object that is the type specified in  *ProgID*  . 
    
-  *DataSpace* 
    
- An object variable that represents an [RDS.DataSpace](dataspace-object-rds.md) object used to create an instance of the new object. 
    
-  *ProgID* 
    
- A **String** value that contains the programmatic identifier specifying a server-side business object that implements your application's business rules. 
    
-  *awebsrvr*  or  *computername* 
    
- A **String** value that represents a URL identifying the Internet Information Services (IIS) Web server where an instance of the server business object is created. 
    
## Remarks

The  *HTTP protocol*  is the standard Web protocol;  *HTTPS*  is a secure Web protocol. Use the  *DCOM protocol*  when running a local-area network without HTTP. The  *in-process*  protocol is a local dynamic-link library (DLL); it does not use a network. 
  

