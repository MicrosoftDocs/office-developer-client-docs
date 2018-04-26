---
title: "Granting Guest Privileges to a Web Server Computer; RDS guest privileges [ADO]"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 4ec9c05b-36f6-de22-b848-0cb8573f9dd1
description: "The anonymous Web server account (IUSR_ComputerName ) must be added to the Guests local group on the Web server computer to use RDS."
---

# Granting Guest Privileges to a Web Server Computer; RDS guest privileges [ADO]

The anonymous Web server account (IUSR_ *ComputerName*  ) must be added to the Guests local group on the Web server computer to use RDS. 
  
 **To grant guest privileges to a Web server computer**
  
1. On your Microsoft Windows® 2000 Server computer, click **Start**, point to **Programs**, point to **Administrative Tools**, and then click **Computer Management**. 
    
2. In the console tree, in **Local Users and Groups**, click **Groups**. 
    
3. Select the **Guests** local group. From the **Action** menu, choose **Properties**. 
    
4. In the **Guests Properties** dialog box, click **Add**. 
    
5. If the anonymous Web server account does not appear in the list in the **Select Users or Groups** dialog box, type its name (IUSR_  *ComputerName*  ) into the bottom blank box, and then click **Add**. 
    
6. Click **OK**. 
    

