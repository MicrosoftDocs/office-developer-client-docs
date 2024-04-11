---
title: "Multithreading and Memory Management"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 6f7e052a-4270-4b83-b1ed-feabf6dbeaa2

---

# Multithreading and Memory Management

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Proper handling of memory is vital to creating reliable XLL add-ins for Microsoft Excel. Failure to allocate appropriate memory buffers and free them when they are no longer needed reduces performance, creates resource contention, and destabilizes Excel.
  
Beginning with Microsoft Office Excel 2007, you can configure Excel to use up to 1,024 concurrent threads when recalculating. In some cases, especially when multiple processors are available or with user-defined functions running on clustered servers, multithreading can improve performance.
  
The following topics describe how to manage memory and threads in XLLs:
  
- [Memory Management in Excel](memory-management-in-excel.md)
    
- [Multithreading and Memory Contention in Excel](multithreading-and-memory-contention-in-excel.md)
    
- [Multithreaded Recalculation in Excel](multithreaded-recalculation-in-excel.md)
    
## See also



[Developing Excel XLLs](developing-excel-xlls.md)

