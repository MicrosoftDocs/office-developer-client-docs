---
title: Systematically releasing objects
TOCTitle: Systematically releasing objects
ms:assetid: d4cd1d8e-aae6-483b-a4d8-1656171e838d
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb623945(v=office.15)
ms:contentKeyID: 55119785
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Systematically releasing objects

This topic summarizes add-in shutdown recommendations for add-in developers and IT administrators that use Outlook. For more information, see [Shutdown Changes for Outlook 2010](https://msdn.microsoft.com/en-us/library/ee720183\(v=office.15\)).

## Add-in shutdown changes in Outlook

Starting in Outlook 2010, Outlook, by default, does not signal add-ins that it is shutting down. Specifically, Outlook no longer calls the **OnBeginShutdown(Array)** and **OnDisconnection(ext\_DisconnectMode, Array)** methods of the **IDTExtensibility2** interface during fast shutdown. Similarly, an Outlook add-in, written with Office development tools in Visual Studio 2010 or a later version, no longer calls the ThisAddin\_Shutdown method when Outlook is shutting down. 

The reason to stop calling these methods is that while a majority of add-ins perform simple tasks like releasing references, some add-ins make Web service calls or other long-running operations synchronously during these events, significantly delaying Outlook from shutting down. As a result of this change, Outlook works better than it has in the past when shutting down.

## Recommendations for add-in shutdown for developers

It is important that developers observe the following recommendations for add-in shutdown to ensure that end users continue to benefit from a fast and responsive Outlook shutdown experience.

- Add-ins should continue to implement the OnBeginShutdown and OnDisconnection methods or ThisAddin\_Shutdown to release references and allocated memory, because there are scenarios in which administrators might revert to slow shutdown through group policy, or the user might manually disconnect your add-in through the **COM Add-ins** dialog box.

- Add-in developers should only perform tasks that absolutely must take place during shutdown.

- Add-in developers should evaluate the performance of their add-ins in various scenarios and under different Windows registry settings that control Outlook shutdown, and proactively modify their add-ins to work with Outlook.

## Recommendations for add-in shutdown for IT administrators

For IT administrators, if there are add-ins that are already deployed in an enterprise and cannot be upgraded to become compatible with the new shutdown Outlook mechanism, IT administrators can resort to a couple of Windows registry settings to revert to the slow shutdown behavior.

### Individual add-in setting

IT administrators can enable shutdown notifications to individual Outlook add-ins as part of the add-in deployment. Although you cannot do this through group policy, it is useful if you have backward-compatibility requirements for specific add-ins.

Configure this setting for each add-in through the add-in registration in the HKCU or the HKLM registry hives, by adding an additional value to the add-in registration. Type the following text as a single line:

`HKCU\Software\Microsoft\Office\Outlook\Add-ins\<ProgID>[RequireShutdownNotification]=dword:0x1`

Setting this value to 0x1 enables the add-in to receive blocked callbacks during Outlook shutdown. This has an impact on the performance of Outlook shutdown and should be evaluated as part of a deployment. This setting should be used only if an add-in has significant compatibility issues with the new shutdown mechanism. Setting the value to 0x0 uses the default behavior of Outlook.

### Global setting

IT administrators can enable shutdown notifications globally for all add-ins through group policy. This is recommended for organizations that have a large number of internal solutions or desktops that need to deploy this setting to ensure compatibility during a rollout of Outlook.

Use this setting to change the shutdown mechanism to match that used by Outlook 2007. You can deploy the setting through group policy, either per user or per computer. Type the following text as a single line:

`HKCU\Policies\Microsoft\Office\Outlook\15.0\Options\Shutdown[AddinFastShutdownBehavior]=dword:0x1`

Setting AddinFastShutdownBehavior to 0x1 enables shutdown notifications for all add-ins. Setting the value to 0x0 uses the default behavior of Outlook.

