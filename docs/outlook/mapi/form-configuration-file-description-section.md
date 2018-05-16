---
title: "Form Configuration File [Description] Section"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 4ce91a65-17db-4ee2-ad59-01fd5b1f1ea7
description: "Last modified: July 23, 2011"
 
 
---

# Form Configuration File [Description] Section

  
  
**Applies to**: Outlook 
  
The **[Description]** section lists all properties of the form that are associated with controls in the form's user interface, plus attributes that are used in locating the form. The **MessageClass**, **Clsid**, and **DisplayName** entries, which identify the name of the form's message class, its GUID, and the message class's display name, respectively, are required entries used to locate the form within the form library. The remaining entries are optional. The format of the **[Description]** section is: 
  
The **[Description]** section lists all properties of the form that are associated with controls in the form's user interface, plus attributes that are used in locating the form. The **MessageClass**, **Clsid**, and **DisplayName** entries, which identify the name of the form's message class, its GUID, and the message class's display name, respectively, are required entries used to locate the form within the form library. The remaining entries are optional. The format of the **[Description]** section is: 
  
 **[Description] MessageClass** =  _string_
  
 **Clsid** =  _guid_
  
 **DisplayName** =  _displayedstring_
  
 **SmallIcon** =  _path_
  
 **LargeIcon** =  _path_
  
Optional entries are:
  
 **Category** =  _displayed string_
  
 **Subcategory** =  _displayed string_
  
 **Comment** =  _displayed string_
  
 **Owner** =  _displayed string_
  
 **Number** =  _displayed string_
  
 **Version** =  _integer_
  
 **Locale** =  _string_
  
 **Hidden** =  _integer_
  
 **DesignerToolName** =  _string_
  
 **DesignerToolGuid** =  _clsid_
  
 **DesignerRuntimeGuid** =  _clsid_
  
 **ComposeInFolder** =  _0|1_
  
 **ComposeCommand** =  _string_
  
The **Category** and **Subcategory** entries are used by form installers to set up the default categorization of forms within client application's user interface. For example a hierarchy could be set up where "Help Desk" is the category and "Software" and "Hardware" were the subcategories. This categorization can then be used by viewer applications to display messages in a more organized way. The **Comment**, **Owner**, and **Number** entries are all comment strings that appear in client application's user interface. These are form specific properties that can be used at the discretion of the form developer. For example, the **Comment** entry can be used to indicate the purpose of the form, the **Owner** entry used to indicate the person or organization responsible for maintaining the form, and the number used to track different version of the form. For the **Comment** entry, up to ten lines of comments can be included. The first line of comments uses the word "Comment" as the key, the second line of comments uses "Comment1" as the key, and so on through "Comment9." 
  
The **LargeIcon** and **SmallIcon** entries are used to specify the path for the icon resources used to display icons in the client application's user interface, typically this is for table rows that include the **PR_ICON** ( [PidTagIcon](pidtagicon-canonical-property.md)) or **PR_MINI_ICON** ( [PidTagMiniIcon](pidtagminiicon-canonical-property.md)) property columns. Icon file names can be specified as pathnames relative to the directory where the form configuration file is installed. The **Version** entry is used to indicate the version number of the form. **Locale** is the three-letter language identifier of the destination form library. A list of these identifiers can be found in the  _Win32 Programmer's Reference_.
  
The **Hidden** entry indicates whether the form should be displayed in a form library provider's user interface: 1 indicates that the file is hidden and 0 indicates that the form is visible. An example form configuration file is shown following. 
  
The **ComposeInFolder** entry controls whether the form is designed to be placed in the current folder or in the user's Inbox when the user saves the message while composing it: 1 indicates that the form should go in the current folder and 0 indicates that it should go in the Inbox. 
  
The **ComposeCommand** entry is the string to be placed in the client application's compose menu. If this is not specified, the **DisplayName** entry will be used. 
  
```
[Description]
MessageClass = IPM.Help
Clsid = {00020D31-0000-0000-C000-000000000046}
DisplayName = Help Desk Request Form
;optional entries
Category = Help Desk Requests
Subcategory = New Requests
Comment = Use this form to request network assistance
Owner = Help Desk
Number = 1
SmallIcon = C:\WINDOWS|EFORMS\HELPDESK\HDSMALL.ICO
LargeIcon = C:\WINDOWS|EFORMS\HELPDESK\HDLARGE.ICO
Version = 1.00
Locale = enu
Hidden = 0
ComposeInFolder = 0
ComposeCommand = &amp;Help Desk Request
 
```


