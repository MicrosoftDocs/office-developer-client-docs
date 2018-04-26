---
title: "DriverPromptEnum Enumeration (DAO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 8dda5e9f-a58f-a62d-eb49-5966d4a1e086
description: "Specifies if and when to prompt the user to establish a connection."
---

# DriverPromptEnum Enumeration (DAO)

Specifies if and when to prompt the user to establish a connection.
  
|**Name**|**Value**|**Description**|
|:-----|:-----|:-----|
|**dbDriverComplete** <br/> |0  <br/> |If the connection string provided includes the DSN keyword, the driver manager uses the string as provided in connect, otherwise it behaves as it does when **dbDriverPrompt** is specified.  <br/> |
|**dbDriverCompleteRequired** <br/> |3  <br/> |(Default) Behaves like **dbDriverComplete** except the driver disables the controls for any information not required to complete the connection.  <br/> |
|**dbDriverNoPrompt** <br/> |1  <br/> |The driver manager uses the connection string provided in connect. If sufficient information is not provided, a trappable error is returned.  <br/> |
|**dbDriverPrompt** <br/> |2  <br/> |The driver manager displays the **ODBC Data Sources** dialog box. The connection string used to establish the connection is constructed from the data source name (DSN) selected and completed by the user via the dialog boxes.  <br/> |
   

