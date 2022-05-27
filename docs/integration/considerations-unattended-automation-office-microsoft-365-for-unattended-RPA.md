---
title: "Considerations for unattended automation of Office in the Microsoft 365 for unattended RPA environment"

ms.date: 03/30/2020
ms.audience: Developer
 
ms.localizationpriority: medium
description: "Considerations for unattended automation of Office in the Microsoft 365 for unattended RPA environment."
---

# Considerations for unattended automation of Office in the Microsoft 365 for unattended RPA environment

Although Microsoft 365 for unattended RPA provides a license that enables the automation of Office with no user present, all current versions of Office were designed and tested to run as end-user products on a client workstation with a user present to interact with the application’s interface. Unexpected behaviors resulting from the use of applications without a user present are not defects. If you want to run Office in this configuration, you must be prepared to account for these unexpected behaviors in your application logic.

This article outlines some of the considerations for unattended automation of Office to help you if you use this approach. However, note that usage of Office in this configuration is strictly “AS IS” and must account for these unexpected behaviors. The information provided here is not exhaustive and is not guaranteed to resolve all issues for all clients. We encourage you to test your solution thoroughly before you deploy.

## Common problems in unattended automation

If you want to use Office without a user present, be aware of the following areas in which Office can behave differently than expected. For your solution to run successfully, it must address these issues and minimize their effects as much as possible. Consider these issues carefully when you build your application.

### Interactive UI elements

Office applications assume that they are being run interactively. If an unexpected error occurs, or if an unspecified parameter is needed to complete a function, Office is designed to prompt the user with a dialog box that asks the user how they want to proceed. In unattended automation, this might result in the application appearing to “hang” as the application stops until it receives this input. If you’re automating Office via its public APIs, you can suppress many of these alerts by configuring properties like [Application.DisplayAlerts](https://docs.microsoft.com/office/vba/api/word.application.displayalerts) and [Application.AutomationSecurity](https://docs.microsoft.com/office/vba/api/word.application.automationsecurity) appropriately. Your code should be designed to identify and process blocking alerts at any time.

### User identity

Office applications require a user identity when the applications are run, even when the application is started via automation. This user identity can cause any or all of the following:

- The presence of additional sign-in UI that must be handled.
- Files that cannot be opened and/or edited based on per-user access permissions.
- Unexpected changes to the metadata of the file (for example, certain file properties will be updated based on the identity of the user identity of the automated application instance).

Various approaches can help to mitigate these issues; for example, running the [Document Inspector](https://docs.microsoft.com/office/vba/library-reference/concepts/using-the-document-inspector) to remove metadata. Consider whether these approaches are appropriate based on your scenario.

### Server-side security

When running Office unattended and processing arbitrary file content, no additional protections specific in that environment are available to prevent macros stored in those files from loading and running. Office does not protect you from unintentionally running macros from your code, or from starting another server that might run macros. You can use properties like [Application.AutomationSecurity](https://docs.microsoft.com/office/vba/api/word.application.automationsecurity) to mitigate this risk, but you should ensure that you are only loading trusted content.

Additionally, Office uses many components (such as Simple MAPI, WinInet, and MSDAIPP) that can cache client authentication information to speed processing. When Office is being automated server-side and processing multiple files, if authentication information has been cached for that session, one client can use the cached credentials of another client. Therefore, the client can gain non-granted access permissions by impersonating other users.

### UI changes

The UI elements in Office are largely stable, but the specific location of any UI element is not guaranteed and might change as the product design evolves to incorporate user feedback and meet customer needs. The logic of any automation must account for this. These changes might result in button or group tab naming changes, movement of commands between tabs, the addition of new tabs, or the removal of commands in alignment with our feature deprecation policies. These changes can take place in the UI as well as within the accessibility information provided by the application, as that information is modified to improve usability and account for ongoing customer feedback, and might be rolled out for different users at different times.

Even without product changes, differences between system environments (such as screen size/resolution/DPI) can result in changes in the location of items on screen. Any approach that relies on screen coordinates to simulate user input must consider these changes and adapt accordingly.

### Single-threading

Office applications are non-reentrant, STA-based applications that are designed to provide diverse but resource-intensive functionality for a single client. The applications use global resources such as memory mapped files, global add-ins or templates, and shared automation servers. This can limit the number of instances that can run concurrently and can lead to race conditions if the applications are configured in a multiclient environment. If you plan to run more than one instance of any Office application, you should plan to isolate them at the virtual machine level to ensure the stability of the resulting solution.

### Resiliency and stability

Even with the considerations above, if the applications are automated in ways that simulate user input or for session lengths that dramatically exceed interactive usage, they might encounter issues that are not present when run interactively. Solutions that utilize Office in this context should proactively build mechanisms to monitor the state of the application and restart them (and/or the virtual machine on which they are running) if/as needed.

## Suggested Alternatives

Microsoft strongly recommends a few alternatives that do not require Office to be installed and run server-side, and that can perform common tasks more efficiently and more quickly than automation in this configuration. Before you involve Office as a server-side component in your project, consider alternatives.

### Microsoft Graph

The Microsoft Graph API provides access to the services, data, and intelligence that are available to users and solutions as part of the Microsoft cloud, including many services supporting the needs of unattended automation: access to users’ mail / calendar / contacts / files, document conversion, Excel workbook calculation, and more. These services are designed for unattended use and high-scale access, and utilize a standard RESTful API syntax. For more information on Microsoft Graph and how to use it to work with users’ data, visit the following:

- [Overview of Microsoft Graph](https://docs.microsoft.com/graph/overview) 
- [Get started with Microsoft Graph](https://developer.microsoft.com/graph/get-started)
- [Download a file in another format](/graph/api/driveitem-get-content-format?view=graph-rest-1.0&tabs=http) (file conversion)
- [Working with Excel in Microsoft Graph](/graph/api/resources/excel?view=graph-rest-1.0) (workbook details)

### Open XML file formats

Many automation tasks involve document creation or editing. Office supports Open XML file formats that let developers create, edit, read, and transform file content using standard XML and ZIP technologies, defined in the ISO 29500 International Standard. These file formats can be manipulated via any ZIP/XML tools, including the System.IO.Package.IO namespace in the Microsoft .NET 3.x Framework. Direct editing of the file formats is the recommended and supported method for handling changes to Office files from a service.

Microsoft provides an SDK for manipulating Open XML file formats from the .NET 3.x Framework. For more information about the SDK and how to use the SDK to create or edit Open XML files, visit the following:

- [Understanding the Open XML file formats](https://docs.microsoft.com/office/open-xml/understanding-the-open-xml-file-formats)
- [Welcome to the Open XML SDK 2.5 for Office](https://docs.microsoft.com/office/open-xml/open-xml-sdk)
