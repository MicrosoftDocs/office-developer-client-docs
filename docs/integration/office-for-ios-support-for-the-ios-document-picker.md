---
title: "Office for iOS support for the iOS Document Picker"
 
 
manager: soliver
ms.date: 02/09/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 802224ef-6eea-4929-824c-507da1c073a5
description: "Office for iOS integrates with the iOS Document Picker by means of the Document Provider extension, which enables Office to open files stored by another document provider."
---

# Office for iOS support for the iOS Document Picker

Office for iOS integrates with the iOS Document Picker by means of the Document Provider extension, which enables Office to open files stored by another document provider.
  
Versions of the Apple iOS starting with iOS 8.0 include [app extension support](https://developer.apple.com/library/prerelease/ios/documentation/General/Conceptual/ExtensibilityPG/index.html#//apple_ref/doc/uid/TP40014214-CH20-SW1). You can use these extensions to expand the functionality of your application into other apps or contexts on the user's device. To integrate Office for iOS with the iOS Document Picker, you use the [Document Provider extension](https://developer.apple.com/library/prerelease/ios/documentation/General/Conceptual/ExtensibilityPG/FileProvider.html).
  
The Document Provider extension supports four operations:
  
- Import
    
- Export
    
- Open
    
- Move
    
Office for iOS integrates with the open operation. When you create a Document Provider extension, your users can use the Document Picker to open and edit documents directly in Office without creating a duplicate copy of the file.
  
## Learn more about app extensions and the Document Picker
<a name="bk_addresources"> </a>

- [App extensions](https://developer.apple.com/library/prerelease/ios/documentation/General/Conceptual/ExtensibilityPG/index.html#//apple_ref/doc/uid/TP40014214-CH20-SW1)
    
- [Document Picker Programming Guide](https://developer.apple.com/library/prerelease/ios/documentation/FileManagement/Conceptual/DocumentPickerProgrammingGuide/Introduction/Introduction.html)
    
- [Document Provider Programming Guide](https://developer.apple.com/library/prerelease/ios/documentation/General/Conceptual/ExtensibilityPG/FileProvider.html)
    

