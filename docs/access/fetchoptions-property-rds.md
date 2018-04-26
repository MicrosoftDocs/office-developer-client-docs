---
title: "FetchOptions Property (RDS)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 0d86c5e4-9abc-5c0e-dc04-4183f4c278cc

---

# FetchOptions Property (RDS)

Indicates the type of asynchronous fetching.
  
## Setting and Return Values

Sets or returns one of the following values.
  
|**Constant**|**Description**|
|:-----|:-----|
|**adcFetchUpFront** <br/> |All the records of the [Recordset](recordset-object-ado.md) are fetched before control is returned to the application. The complete **Recordset** is fetched before the application is allowed to do anything with it.  <br/> |
|**adcFetchBackground** <br/> |Control can return to the application as soon as the first batch of records has been fetched. A subsequent read of the **Recordset** that attempts to access a record not fetched in the first batch will be delayed until the sought record is actually fetched, at which time control returns to the application.  <br/> |
|**adcFetchAsync** <br/> |Default. Control returns immediately to the application while records are fetched in the background. If the application attempts to read a record that hasn't yet been fetched, the record closest to the sought record will be read and control will return immediately, indicating that the current end of the **Recordset** has been reached. For example, a call to [MoveLast](movefirst-movelast-movenext-and-moveprevious-methods-rds.md) will move the current record position to the last record actually fetched, even though more records will continue to populate the **Recordset**.  <br/> |
   
> [!NOTE]
> Each client-side executable file that uses these constants must provide declarations for them. You can cut and paste the constant declarations you want from the file Adcvbs.inc, located in the C:\Program Files\Common Files\System\MSADC folder. 
  
## Remarks

In a Web application, you will usually want to use **adcFetchAsync** (the default value), because it provides better performance. In a compiled client application, you will usually want to use **adcFetchBackground**. 
  

