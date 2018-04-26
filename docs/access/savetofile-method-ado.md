---
title: "SaveToFile Method (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: db0fd95e-8ef3-af87-5346-8f8713153ca7

---

# SaveToFile Method (ADO)

Saves the binary contents of a [Stream](stream-object-ado.md) to a file. 
  
## Syntax

 *Stream*  . **SaveToFile** *FileName*  ,  *SaveOptions* 
  
## Parameters

-  *FileName* 
    
- A **String** value that contains the fully-qualified name of the file to which the contents of the **Stream** will be saved. You can save to any valid local location, or any location you have access to via a UNC value. 
    
-  *SaveOptions* 
    
- A [SaveOptionsEnum](saveoptionsenum.md) value that specifies whether a new file should be created by **SaveToFile**, if it does not already exist. Default value is **adSaveCreateNotExists**. With these options you can specify that an error occurs if the specified file does not exist. You can also specify that **SaveToFile** overwrites the current contents of an existing file. 
    
> [!NOTE]
> If you overwrite an existing file (when **adSaveCreateOverwrite** is set), **SaveToFile** truncates any bytes from the original existing file that follow the new [EOS](eos-property-ado.md). 
  
## Remarks

 **SaveToFile** may be used to copy the contents of a **Stream** object to a local file. There is no change in the contents or properties of the **Stream** object. The **Stream** object must be open before calling **SaveToFile**. 
  
This method does not change the association of the **Stream** object to its underlying source. The **Stream** object will still be associated with the original URL or **Record** that was its source when opened. 
  
After a **SaveToFile** operation, the current position ( [Position](position-property-ado.md)) in the stream is set to the beginning of the stream (0).
  

