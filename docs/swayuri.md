---
title: "SwayURI"
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 11daa75b-87fc-4e63-8e02-09ab9307c8f8

---
# Sway URI scheme

Use the Sway URI scheme to open the Sway application and view or edit a Sway.

**Last modified:** January 28, 2016

***Applies to:*** *Sway for Windows*

This document defines the format of Uniform Resource Identifiers (URIs) for the Sway application for Windows. You can use this URI scheme to invoke the Sway application with various commands.

##Sway URI scheme syntax

The following is the URI scheme syntax:

    <ms-sway>:<command-argument>

- `<ms-sway>` - Indicates that Sway is the application to invoke. When Sway for Windows is installed, *ms-sway* is registered with Windows to be the Sway handler.
- `<command-argument>` - A URI might have one or more command arguments, delimited by the ampersand (&) character. When more than one command argument is included in a URI, an ampersand (&) character must separate each command argument from the following command argument. Command arguments vary according to the scenario. 

##Command arguments

Several command arguments can be included as part of the Sway URL scheme. These command arguments are not required. If you do not include the command arguments, the Sway application will be invoked.

|**Command argument name**|**Description**|**Type**|**Possible values**|**Required?**|
|:-----|:-----|:-----|:-----|:-----|
|*id*|The unique identifier of a Sway. Used to indicate the Sway to be opened.|String|A valid unique identifier for a Sway. The id is always part of the URL to a Sway. For example, for the following Sway: https://sway.com/dBheQgVZ1RQBfiQU, the id is dBheQgVZ1RQBfiQU. If the user account associated with the Sway application has edit permissions, the application will open the Sway in edit mode. Otherwise, the application will open the Sway in view mode.|No|
|*mode*|The mode in which a specific Sway should be opened, whether for editing or for viewing.|String|edit<br/>view<br/>**Note:** If no *id* is specified, this command argument is ignored.|No|
|*auth_upn*|The account to use when opening Sway.|String|A valid email address.<br/>If the specified email address is not associated with a Sway account, Sway will ask the user to sign in as the specified user. If more than one account is associated with the Sway application and the specified email address exists, the Sway application will switch to using that account when invoked.|No|
|*auth_pvr*|The type of account to use to open the Sway - either a Microsoft Account (MSA) or an Azure Active Directory Account (AAD).|String|WindowsLiveId – Specifies that the auth_upn account is an MSA.<br/>OrgId – Specifies the auth_upn account is an AAD account.<br/>If no *auth_upn* is specified, this command argument is ignored.|No|
|*invoking_app*|The name of the Windows application used to invoke Sway.|String|The friendly name of the Windows application used to invoke Sway via the Sway URL scheme.<br/>The purpose of this command argument is for telemetry and tracking.|No|

##URI scheme semantics

The `<ms-sway>` scheme defines a URI syntax for opening a Sway or for invoking the Sway application. The scheme defines several command arguments, which can be used to do the following: 

- Open the Sway application – No command arguments need to be specified.  
- Open a Sway for viewing in Sway application – The *id* and *mode* set to view need to be specified.  
- Open a Sway for editing in Sway application – The *id* and *mode* set to edit needs to be specified. We recommend that you also include *auth_upn* and *auth_pvr* to help ensure that the right account with editing permissions is used when Sway is opened.  

**Example**

ms-sway:id=CyrvEYLmFKi1B2_I&auth_upn=account@email.com&auth_pvr=WindowsLiveId&invoking_app=MyApp 

