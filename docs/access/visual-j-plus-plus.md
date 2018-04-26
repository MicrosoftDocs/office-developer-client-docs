---
title: "Visual J++"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 5c05db85-cdf2-9a73-fbc5-3dbfa6752376
description: "This short Microsoft Visual J++ example shows how you can associate your own function with a particular event."
---

# Visual J++

This short Microsoft Visual J++ example shows how you can associate your own function with a particular event.
  
```
 
// BeginEventExampleVJ 
import com.ms.wfc.data.*; 
 
public class EventExampleVJ 
{ 
 ConnectionEventHandler handler = new ConnectionEventHandler(this,"onConnectComplete"); 
 
 public void onConnectComplete(Object sender,ConnectionEvent e) 
 { 
 if (e.adStatus == AdoEnums.EventStatus.ERRORSOCCURRED) 
 System.out.println("Connection failed"); 
 else 
 System.out.println("Connection completed"); 
 return; 
 } 
 
 public static void main (String[] args) 
 { 
 EventExampleVJ Class1 = new EventExampleVJ(); 
 Connection conn = new Connection(); 
 
 conn.addOnConnectComplete(Class1.handler); // Enable event support. 
 conn.open("DSN=Pubs"); 
 conn.close(); 
 conn.removeOnConnectComplete(Class1.handler); // Disable event support. 
 } 
} 
// EndEventExampleVJ 

```

First, the class method  *onConnectionComplete*  is associated with the **ConnectionComplete** event by creating a new **ConnectionEventHandler** object and assigning the  *onConnectComplete*  function to the object. 
  
The  *main*  function then creates a **Connection** object and enables event handling by calling the **addOnConnectComplete** method and passing it the address of the  *handler*  function. 
  

