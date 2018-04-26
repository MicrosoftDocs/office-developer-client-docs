---
title: "Editing Existing Records"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 86b961e0-e0a5-85a2-1138-7ab2e696ec11
description: "To edit existing records, move to the row you want to edit and change the Value property of the fields you want to change. For more information about the Field object's Value property, see Chapter 3: Examining Data. Depending on your cursor type, you will use Update or UpdateBatch to send changes back to the data source. For more information, see Chapter 5: Updating and Persisting Data."
---

# Editing Existing Records

To edit existing records, move to the row you want to edit and change the **Value** property of the fields you want to change. For more information about the **Field** object's **Value** property, see [Chapter 3: Examining Data](chapter-3-examining-data.md). Depending on your cursor type, you will use **Update** or **UpdateBatch** to send changes back to the data source. For more information, see [Chapter 5: Updating and Persisting Data](chapter-5-updating-and-persisting-data.md).
  
It is usually more efficient to use a stored procedure with a command object to perform updates, as well as to perform other operations, because a stored procedure does not require the creation of a cursor. For more information about cursors, see [Chapter 8: Understanding Cursors and Locks](chapter-8-understanding-cursors-and-locks.md).
  

