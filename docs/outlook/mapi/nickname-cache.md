---
title: "Nickname cache"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
ms.assetid: 2813c102-6778-4443-ab4b-b573f3568705
description: "Last modified: January 30, 2013"
 
 
---

# Nickname cache

 
  
**Applies to**: Outlook 
  
Microsoft Office Outlook 2007, Microsoft Outlook 2010, and Microsoft Outlook 2013 interact with the nickname cache, also known as the "autocomplete stream." The autocomplete stream is where Outlook persists the autocomplete list, which is the list of names that displays in the **To**, **Cc**, and **Bcc** edit boxes while a user is composing an email. This topic describes how Outlook 2007, Outlook 2010, and Outlook 2013 interact with the autocomplete stream and also discusses the binary format of the file and the recommended ways for interacting with the autocomplete stream. 
  
For applications that interact with Outlook 2010 or Outlook 2013, the autocomplete stream is stored as a MAPI property and can be modified using the MAPI or the **PropertyAccessor** object of the message. The **PropertyAccessor** object is exposed in the Outlook 2010 or Outlook 2013 object models. 
  
There are no dependencies on the Outlook 2007 object model or MAPI APIs. Therefore, applications that make changes to the autocomplete stream within Outlook 2007 can be written using any programming language.
  
## Interacting with the Autocomplete Stream

When the **To**, **Cc**, or **Bcc** edit boxes are accessed on a message, the autocomplete stream is loaded and the list of user names is displayed. Outlook interacts with the autocomplete stream in two ways: 
  
1. Loading the autocomplete stream 
    
2. Saving changes to the data in the autocomplete stream
    
The means of storing the autocomplete data differs between Outlook 2007 and Outlook 2010 or Outlook 2013 as follows: 
  
 **Outlook 2007**
  
For Outlook 2007, the autocomplete stream is stored in a file with the same name as the profile and an extension of .nk2. For example, if the default profile of "outlook" is used, the file will be called "outlook.nk2". The .nk2 file is stored in %APPDATA%\Microsoft\Outlook. For more information about the nickname cache binary file format, see [Outlook 2003/2007 NK2 File Format and Developer Guidelines](http://portalvhds6gyn3khqwmgzd.blob.core.windows.net/files/NK2/NK2WithBinaryExample.pdf).
  
 **Outlook 2010 and Outlook 2013**
  
Outlook 2010 or Outlook 2013 reads the autocomplete stream from a message in the Associated Contents table of the Inbox of the mail account's delivery store. This hidden message has a message class and subject of IPM.Configuration.Autocomplete. The autocomplete stream is stored on this message in the PR_ROAMING_BINARYSTREAM property ([PidTagRoamingBinary Canonical Property](pidtagroamingbinary-canonical-property.md)). The autocomplete data may be temporarily cached in an autocomplete .dat file located in %USERPROFILE%\AppData\Local\Microsoft\Outlook\RoamCache. However, the .dat file is only a cache and is not used to write back to the delivery store when the user exits Outlook 2010 or Outlook 2013.
  
## Loading the Autocomplete Stream

Outlook loads the autocomplete stream whenever an item with addressing functionality is initialized. For example, email addresses are used in a new mail, a mail reply, a contact item, a meeting request, and so on. To load the data, Outlook reads all of the contents of the stream into memory.
  
For autocomplete operations, Outlook interacts exclusively with this in-memory structure for the duration of the outlook.exe process lifetime. Outlook only saves the structure on shutdown. See the following section "Saving the Autocomplete Stream" for more information on this process.
  
## Saving the Autocomplete Stream

Outlook saves the autocomplete stream on shutdown if the autocomplete list has changed in any of the following ways:
  
- A new nickname entry is added through resolving a name, picking a recipient from the address book dialog, or sending mail to a recipient that was not already in the list.
    
- An entry is modified by sending mail to an existing recipient in the list.
    
- An entry is removed by the user through the UI.
    
- Other minor scenarios not relevant to this topic.
    
Saving changes to the autocomplete data involves writing the in-memory structure back to an [Autocomplete Stream](autocomplete-stream.md). When interacting with Outlook 2007, the stream is saved to a local .nk2 file. For Outlook 2010 or Outlook 2013, the autocomplete stream writes back to the Associated Contents table of the Inbox of the mail account's delivery store.
  
## Recommendations

- Never partially modify the autocomplete stream. The supported interaction is to 1) read the entire autocomplete stream into memory, 2) modify the memory structure, and 3) write the entire stream back to either the Associated Contents table of the Inbox of the mail account's delivery store (for Outlook 2010 or Outlook 2013) or to the local .nk2 file (Outlook 2007).
    
- Do not interact with the autocomplete stream while Outlook is running. If Outlook is running while you modify the stream, it will likely overwrite your changes when it shuts down.
    
- Do not write properties of type PT_MV_UNICODE and PR_MV_STRING8 into an autocomplete stream to be consumed by Microsoft Outlook 2003. These properties are only understood by Outlook 2007, Outlook 2010, and Outlook 2013.
    
- When developing code that interacts with Outlook 2007, we recommend that you lock the .nk2 file from modification by other processes while you are reading and writing it using standard file locking APIs (for example, **LockFile** in C/C++ and **FileStream.Lock** in C#). 
    
- Only modify the properties of types that are from the row-set of the autocomplete stream. For more information about the autocomplete stream properties and property types, see [Autocomplete Stream](autocomplete-stream.md).
    
## See also



[Autocomplete Stream](autocomplete-stream.md)
  
[MAPI Profiles](mapi-profiles.md)


[Outlook 2003/2007 NK2 File Format and Developer Guidelines](http://portalvhds6gyn3khqwmgzd.blob.core.windows.net/files/NK2/NK2WithBinaryExample.pdf)

