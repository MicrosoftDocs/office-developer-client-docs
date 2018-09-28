---
title: Determine whether Outlook is a Click-to-Run application on a computer
TOCTitle: Determine whether Outlook is a Click-to-Run application on a computer
ms:assetid: 1b8573be-8ea8-4973-869d-87fda57ce525
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff522355(v=office.15)
ms:contentKeyID: 55119804
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Determine whether Outlook is a Click-to-Run application on a computer

Click-to-Run is a software delivery and updating mechanism available to Office 2010 and later versions. Products delivered via Click-to-Run execute in a virtual application environment on the local operating system. This means that they have private copies of their files and settings, and that any changes they make are captured in the virtual environment.

Click-to-Run is fast—users can start running an application within a short time without waiting for the complete product to finish installing. Updates are run automatically in the background, without requiring a user to first remove an installation or manually install updates. Click-to-Run products are virtualized and do not conflict with other installed software. However, because a product delivered by Click-to-Run has private copies of all its files and registration, an add-in developer cannot determine the product’s existence in the same manner as a product that was installed on a client computer’s hard disk. Starting with Outlook 2010, add-in developers should verify whether Outlook has been installed, and whether Outlook has been delivered as a Click-to-Run product.


> [!NOTE]
> Only 32-bit Office 2013 is supported in the Click-to-Run virtual application environment, even if the client computer runs a 64-bit operating system.



### To check whether Outlook 2013 was delivered by Click-to-Run on a client computer

- Verify whether the VirtualOutlook key exists in the following location in the Windows registry:
    
  `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\15.0\Common\InstallRoot\Virtual\VirtualOutlook`
    
  The VirtualOutlook key is a REG\_SZ value that contains the culture tag of the installed product language, such as "en-us".

## See also

- [Add-in administration](add-in-administration.md)

