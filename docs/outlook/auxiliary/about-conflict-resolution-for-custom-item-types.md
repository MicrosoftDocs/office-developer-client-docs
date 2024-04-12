---
title: "About conflict resolution for custom item types"
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: 3f0853fc-f9f2-4314-ac55-47fe1e52d019
description: "This topic describes how to resolve conflicts for custom item types that you create in Outlook."
---

# About conflict resolution for custom item types

This topic describes how to resolve conflicts for custom item types that you create in Outlook.
  
## Conflict resolution for standard Outlook item types

In Outlook, conflicts occur when two or more copies of the same item have been modified independently of each other. Outlook detects conflicts during synchronization. For example, you might update a meeting item online in Outlook Web App and then update the same meeting item in Outlook when you work offline. When Outlook goes online again and synchronizes the data between the client computer and the server, it detects that there are two different copies of the same meeting item.
  
When Outlook synchronizes items that belong to a standard Outlook item type, it takes into consideration the properties that are specific to that item type to detect possible conflicts. Outlook tries to resolve conflicts and stores the resultant copy in the appropriate folder without requesting user intervention. In cases where Outlook considers that there is a possibility that the resultant copy may not contain all essential data, Outlook stores the conflicting copies in the Conflicts folder, under the Sync Issues folder. 
  
> [!NOTE]
> Sync Issues and its subfolders are hidden until you click **Folder List** in the Navigation Pane. 
  
In such cases, users can choose to go to the Conflicts folder to verify which items were in conflict and whether to use a copy in the Conflicts folder to replace the copy that Outlook decided to retain.
  
## Conflict resolution for custom item types

### Item types and message classes
  
All items in Outlook are associated with a message class. For example, by default, a mail item is associated with the message class **IPM.Note**. The message class is primarily used to identify the form that should be used to display the item in Outlook. Outlook supports a list of message classes that are mapped to the types of items built in to Outlook. For more information about message classes, see [Item Types and Message Classes](https://msdn.microsoft.com/library/15b709cc-7486-b6c7-88a3-4a4d8e0ab292%28Office.15%29.aspx). 
  
Users can create custom item types, assign custom message classes to the custom item types, and have Outlook use a custom form to display the custom item types. For example, you may want Outlook to display a custom business contact form for your business contacts. To do that, you can create a custom message class **IPM.Contact.Business**, create a custom form for this message class, and assign business contacts with this message class. 
  
### Registering a conflict resolution scheme for custom item types
  
When you create a custom item type, other than the custom message class and custom form, you should also consider how you would like Outlook to handle conflicts between copies of an item of this item type. By default, Outlook employs a resolution scheme common to all items, does not consider properties that are specific to an item type, and presents conflicting copies for the user to make a decision. This is because custom item types may define custom fields in the custom form, and may have custom properties and custom code. If you want Outlook to consider item-specific properties and attempt to resolve the conflict with minimal user intervention, you must specify that through a setting in the Windows registry. This can be achieved in one of two ways: 
  
- By applying a Group Policy setting to the local computer that sets the registry key ConflictMsgCls. The following example specifies the version "14.0" for Outlook 2010: 
  
   `[HKCU]\Software\Policies\Microsoft\Office\14.0\Outlook\Options\ConflictMsgCls`
    
- By directly modifying the user registry key ConflictMsgCls. The following example specifies the version "14.0" for Outlook 2010: 
  
   `[HKCU]\Software\Microsoft\Office\14.0\Outlook\Options\ConflictMsgCls`
    
Setting the conflict resolution through Group Policy takes precedence over directly modifying the user registry key. The location of the key in the registry depends on the version of Outlook. You specify the name of the custom message class as a value under this key. Specify the type of the value as **DWORD**, and the data of the value as one of the values shown in the following table, depending on the resolution scheme you choose. 
  
|Data  | Description  |
|:-----|:-----|
|0  <br/> |Common item resolution that requires a user decision, as used in Outlook 2002 and earlier versions. |
|1  <br/> |Common item resolution that requires minimal user intervention, as used in Outlook since Outlook 2003. |
|2  <br/> |Resolution specific to mail items. |
|3  <br/> |Resolution specific to meeting items. |
|4  <br/> |Resolution specific to appointment items. |
|5  <br/> |Resolution specific to contact items. |
|6  <br/> |Resolution specific to task items. |
|7  <br/> |Resolution specific to sticky note items. |
|8  <br/> |Resolution specific to journal items. |
   
If you specify one of the item-specific resolution schemes (key data 2 through 8), Outlook will try to resolve conflicts in item-specific fields (for example, **Start** and **End** fields of an appointment item) automatically without user intervention. If Outlook considers that the resolution may result in the loss of essential data, Outlook will retain conflicting copies in the Conflicts folder, and users can choose to go to the Conflicts folder to manually re-resolve these items and override the automatic resolution. 
  
Using the same business contacts example above, if you want to specify the contact item-specific resolution scheme for the custom message class **IPM.Contact.Business**, you can add it as a **DWORD** value under  `[HKCU]\Software\Microsoft\Office\15.0\Outlook\Options\ConflictMsgCls`, and specify 5 as the data. 
  
> [!NOTE]
> Outlook always uses a resolution scheme that is specific to appointment items for custom message classes that are based on the appointment message class, **IPM.Appointment** (for example, **IPM.Appointment.Personal**). 
  
## See also

- [Outlook Item Objects](https://msdn.microsoft.com/library/6ea4babf-facf-4018-ef5a-4a484e55153a%28Office.15%29.aspx)

