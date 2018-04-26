---
title: "Open Method (ADO Stream)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: fa2e6aaa-e9f5-009c-f3a0-050a00abf9b0

---

# Open Method (ADO Stream)

Opens a [Stream](stream-object-ado.md) object to manipulate streams of binary or text data. 
  
## Syntax

 *Stream*  . **Open** * Source *  ,  *Mode*  ,  *OpenOptions*  ,  *UserName*  ,  *Password* 
  
## Parameters

-  *Source* 
    
- Optional. A **Variant** value that specifies the source of data for the **Stream**.  *Source*  may contain an absolute URL string that points to an existing node in a well-known tree structure, like an e-mail or file system. A URL should be specified using the URL keyword ("URL=  *scheme*  ://  *server*  /  *folder*  "). Alternately,  *Source*  may contain a reference to an already open [Record](record-object-ado.md) object, which opens the default stream associated with the **Record**. If  *Source*  is not specified, a **Stream** is instantiated and opened, associated with no underlying source by default. For more information about URL schemes and their associated providers, see [Absolute and Relative URLs](absolute-and-relative-urls.md).
    
-  *Mode* 
    
- Optional. A [ConnectModeEnum](connectmodeenum.md) value that specifies the access mode for the resultant **Stream** (for example, read/write or read-only). Default value is **adModeUnknown**. See the [Mode](mode-property-ado.md) property for more information about access modes. If  *Mode*  is not specified, it is inherited by the source object. For example, if the source **Record** is opened in read-only mode, the **Stream** will also be opened in read-only mode by default. 
    
-  *OpenOptions* 
    
- Optional. A [StreamOpenOptionsEnum](streamopenoptionsenum.md) value. Default value is **adOpenStreamUnspecified**. 
    
-  *UserName* 
    
- Optional. A **String** value that contains the user identification that, if needed, accesses the **Stream** object. 
    
-  *Password* 
    
- Optional. A **String** value that contains the password that, if needed, accesses the **Stream** object. 
    
## Remarks

When a **Record** object is passed in as the source parameter, the  *UserID*  and  *Password*  parameters are not used because access to the **Record** object is already available. Similarly, the [Mode](mode-property-ado.md) of the **Record** object is transferred to the **Stream** object.When  *Source*  is not specified, the **Stream** opened contains no data and has a [Size](http://msdn.microsoft.com/library/deb84313-36d1-fa49-e4cd-daecab96f343%28Office.15%29.aspx) of zero (0). To avoid losing any data that is written to this **Stream** when the **Stream** is closed, save the **Stream** with the [CopyTo](copyto-method-ado.md) or [SaveToFile](savetofile-method-ado.md) methods, or save it to another memory location. 
  
An  *OpenOptions*  value of **adOpenStreamFromRecord** identifies the contents of the  *Source*  parameter to be an already open **Record** object. The default behavior is to treat  *Source*  as a URL that points directly to a node in a tree structure, such as a file. The default stream associated with that node is opened. 
  
While the **Stream** is not open, it is possible to read all the read-only properties of the **Stream**. If a **Stream** is opened asynchronously, all subsequent operations (other than checking the [State](state-property-ado.md) and other read-only properties) are blocked until the **Open** operation is completed. 
  
In addition to the options discussed above, by not specifying  *Source*  , you can simply instantiate a **Stream** object in memory without associating it with an underlying source. You can dynamically add data to the stream simply by writing binary or text data to the **Stream** with [Write](write-method-ado.md) or [WriteText](writetext-method-ado.md), or by loading data from a file with [LoadFromFile](loadfromfile-method-ado.md).
  

