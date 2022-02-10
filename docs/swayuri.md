---
title: "SwayURI"
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 11daa75b-87fc-4e63-8e02-09ab9307c8f8
ms.date: 01/28/2016
description: Use the Sway URI scheme to open the Sway application and view or edit a Sway. 
---

# Sway URI scheme

This document defines the format of Uniform Resource Identifiers (URIs) for the Sway application for Windows. You can use this URI scheme to invoke the Sway application with various commands.

## Sway URI scheme syntax

The following is the URI scheme syntax:

`<ms-sway>:<command-argument>`

- `<ms-sway>` &ndash; Indicates that Sway is the application to invoke. When Sway for Windows is installed, `ms-sway` is registered with Windows to be the Sway handler.
- `<command-argument>` &ndash; A URI might have one or more command arguments, delimited by the ampersand (`&`) character. When more than one command argument is included in a URI, an ampersand (`&`) character must separate each command argument from the following command argument. Command arguments vary according to the scenario. 

## Command arguments

Several command arguments can be included as part of the Sway URL scheme. These command arguments are not required. If you do not include the command arguments, the Sway application is invoked.

|Command argument name|Description|Type|Possible values|Required?|
|:-----|:-----|:-----|:-----|:-----|
|**id**|The unique identifier of a Sway. Used to indicate the Sway to be opened.|String|A valid unique identifier for a Sway. The id is always part of the URL to a Sway.<br/><br/>For example, for the following Sway `https://sway.com/dBheQgVZ1RQBfiQU`, the id is `dBheQgVZ1RQBfiQU`.<br/><br/>If the user account associated with the Sway application has edit permissions, the application opens the Sway in edit mode. Otherwise, the application opens the Sway in view mode.|No|
|**mode**|The mode in which a specific Sway should be opened, whether for editing or for viewing.|String|edit<br/>view<br/><br/>**NOTE**: If no **id** is specified, this command argument is ignored.|No|
|**auth_upn**|The account to use when opening Sway.|String|A valid email address.<br/><br/>If the specified email address is not associated with a Sway account, Sway asks the user to sign in as the specified user.<br/><br/>If more than one account is associated with the Sway application and the specified email address exists, the Sway application switches to using that account when invoked.|No|
|**auth\_pvr**|The type of account to use to open the Sway&mdash;either a Microsoft account or an Azure Active Directory account (Azure AD).|String|WindowsLiveId – Specifies that the **auth\_upn** account is a Microsoft account.<br/><br/>OrgId – Specifies that the **auth\_upn** account is an Azure AD account.<br/><br/>If no **auth\_upn** is specified, this command argument is ignored.|No|
|**invoking\_app**|The name of the Windows application used to invoke Sway.|String|The friendly name of the Windows application used to invoke Sway via the Sway URL scheme.<br/><br/>The purpose of this command argument is for telemetry and tracking.|No|

## URI scheme semantics

The `<ms-sway>` scheme defines a URI syntax for opening a Sway or for invoking the Sway application. The scheme defines several command arguments, which can be used to do the following: 

- Open the Sway application &ndash; No command arguments need to be specified. 

- Open a Sway for viewing in the Sway application &ndash; The **id** and **mode** set to view need to be specified. 

- Open a Sway for editing in the Sway application &ndash; The **id** and **mode** set to edit needs to be specified. We recommend that you also include **auth\_upn** and **auth\_pvr** to help ensure that the right account with editing permissions is used when Sway is opened.  

## Example

`ms-sway:id=CyrvEYLmFKi1B2_I&auth_upn=account@email.com&auth_pvr=WindowsLiveId&invoking_app=MyApp`
