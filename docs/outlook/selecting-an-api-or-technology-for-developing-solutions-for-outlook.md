---
title: "Selecting an API or technology for developing solutions for Outlook"
manager: lindalu
ms.date: 09/15/2021
ms.audience: Developer
ms.assetid: 01a46083-03d0-4333-920c-01a9f17f68cb
description: "This article describes the APIs and technologies you can use to extend Outlook 2013 and Outlook 2016, and helps you decide the appropriate API or technology for your scenario."
ms.localizationpriority: high
---

# Selecting an API or technology for developing solutions for Outlook

This article describes the APIs and technologies that you can use to extend Outlook 2013 and Outlook 2016, and helps you decide the appropriate API or technology for your scenario.
  
Microsoft supports various APIs and technologies that extend Outlook:
  
- Starting in Office 2013, the apps for Office platform opens up opportunities to extend Outlook functionality across Outlook clients on the desktop, tablet and smart phone. The platform includes a JavaScript API for Office and a schema for app manifests.

- The object model, the corresponding Outlook Primary Interop Assembly (PIA), and the Messaging API (MAPI) have been the most commonly used APIs in Outlook solutions.

- The auxiliary APIs complement MAPI in a few scenarios.

- Outlook Social Connector (OSC) provider extensibility and the Weather Bar extensibility serve specific scenarios of their niche markets.

This article explains the selection criteria for the Office Add-ins platform, the object model, PIA, and MAPI. Note that Office Add-ins use the JavaScript API for Office and do not call into the object model, and vice versa. Solutions that use the other APIs can use one or more APIs. For example, a COM add-in written in C++ can use the object model, MAPI, and auxiliary APIs in the same solution.
  
To get the most benefit from this article, you should be familiar with Outlook at the user level and have general software development knowledge. However, you do not need to have a comprehensive understanding of the features that these APIs or technologies support. The article helps answer the following questions:
  
- If you have only an idea about the goals of your solution, the target market, and available resources, what other criteria should you consider to select an API?

- Why would you consider Office Add-ins, and when would you choose to create apps as opposed to add-ins?

- If your solution has to run on earlier versions of Outlook, including Outlook 2003, how does that affect your API choice?

- If your solution has to iterate through Outlook folders that contain thousands of items, and you need to be able to modify those items, which API would work best?

- If your solution relies heavily on Outlook business logic and interacts with other Office applications, is the Outlook object model the best choice?

- What do the object model and MAPI allow you to extend in Outlook?

- If you can use either the object model or MAPI to achieve your task, how should you decide which API to use?

<a name="OLSelectAPI_ObjectiveChar"> </a>

## Objective evaluation criteria

This section describes criteria that you can use to compare the Office Add-ins platform, object model, PIA, and MAPI to determine which better meets your needs. Different criteria can be more or less important, depending on your projects and available resources.
  
The tables in this section define evaluation criteria in the following categories:
  
- Functional criteria—Describes the things you can and cannot do with the technology.

- Development criteria—Describes the development tools or information you need to use the technology

- Security criteria—Describes the security and permissions issues related to the technology.

- Deployment criteria—Describes the recommended deployment and distribution methods for the technology.

<a name="OLSelectAPI_ObjectiveEvalCritApps"> </a>

### Objective evaluation criteria for the apps for Office platform

Starting in Office 2013, developers can use the Office Add-ins platform to extend web services and content into the context of Office rich and web clients. An Office Add-in is a web page that is developed using common web technologies, hosted inside an Office client application (such as Outlook), and can run on-premises or in the cloud. Of the few types of Office Add-ins, the type that Outlook supports is called mail apps. While the object model, PIA, and MAPI are often used to automate Outlook at an application level, you can use the JavaScript API for Office to interact at an item level with the content and properties of an email message, meeting request, or appointment. You can publish mail apps to the Office Store or an internal Exchange catalog.
  
End users and administrators can install mail apps on an Exchange mailbox, and use mail apps in the Outlook rich client as well as Outlook Web App. As a developer, you can choose to make your mail app available on only the desktop, or also on the tablet or smart phone. Figure 1 shows an example of a YouTube mail app, which is described in detail in [Sample: Create a mail add-in to view YouTube videos in Outlook](/samples/officedev/outlook-add-in-javascript-viewyoutubevideos/outlook-add-in-view-youtube-videos/). The YouTube mail app allows end users select a URL for a YouTube video and watch the video within Outlook or Outlook Web App, on the desktop or tablet.
  
**Figure 1. YouTube mail app is active for the selected message, which contains a URL to a video on YouTube.com**

![YouTube mail app in Outlook](media/off15appsdk_YouTubeMailAppScreenshot.png)
  
After a user installs a mail app, the app is available for use in the app bar when the current context matches the activation conditions that the app specifies. A mail apps allows you to specify rules about the currently selected item that activate a mail app only if certain conditions are met. For example, the YouTube mail app that lets you play a YouTube video within Outlook is relevant only when the selected Outlook item contains a URL to a video on YouTube.com. In this case, you would specify that the app should be active only when the selected message contains such a URL.
  
The following tables show the evaluation criteria for the Office Add-ins platform.
  
#### Functional criteria

|**Criteria**|**Mail apps support in apps for Office platform**|
|:-----|:-----|
|Application domain |The scope of activity of a mail app is virtually any supported message or appointment item in the user's Exchange mailbox that the user has selected and that satisfies the activation conditions. The permissions of a mail app determine its access to the properties and specific entities (such as an email address or telephone number) that exist for that item. For example, a mail app requesting the **read/write mailbox** permission can read and write all the properties of any item in the user's mailbox; create, read, and write to any folder or item; and send an item from that mailbox. |
|Major objects |The JavaScript API for Office provides a few objects at the top level that are shared by all the types of Office Add-ins: [Office](https://msdn.microsoft.com/library/c490b13d-ee52-4291-af5d-f4a5a11d3af0%28Office.15%29.aspx), [Context](https://msdn.microsoft.com/library/662883d5-b86f-4bdc-99f0-9ee9129ed16c%28Office.15%29.aspx), and [AysncResult](https://msdn.microsoft.com/library/540c114f-0398-425c-baf3-7363f2f6bc47%28Office.15%29.aspx). The next level in the API that is applicable and specific to mail apps includes the [Mailbox](https://msdn.microsoft.com/library/a3880d3b-8a09-4cf9-9274-f2682cb3b769%28Office.15%29.aspx), [Item](https://msdn.microsoft.com/library/ad288df1-3ca2-474c-bea4-c51f46e6fc43%28Office.15%29.aspx), and [UserProfile](https://msdn.microsoft.com/library/6d0a36ec-0d5c-40e3-9f6f-9a7fcf0ac3d8%28Office.15%29.aspx) objects, which support accessing information about the user and the item currently selected in the user's mailbox. At the data level, the [CustomProperties](https://msdn.microsoft.com/library/95a69bd6-c4dc-429a-8b27-e2b68f74f3e3%28Office.15%29.aspx) and [RoamingSettings](https://msdn.microsoft.com/library/cf21bb08-7274-4ad6-ae9e-b2c12f92abc9%28Office.15%29.aspx) objects support persisting properties set up by the mail app for the selected item and for the user's mailbox, respectively. Item-level objects include the [Appointment](https://msdn.microsoft.com/library/08ebffff-eb52-4e21-9d4e-8f79e426f992%28Office.15%29.aspx) and [Message](https://msdn.microsoft.com/library/909ad9eb-a1bc-4caa-b51e-fd59a02b9569%28Office.15%29.aspx) objects that inherit from **Item**, and the [MeetingRequest](https://msdn.microsoft.com/library/c658fa3d-1138-4a67-9a4b-c9edd11f8385%28Office.15%29.aspx) object that inherits from **Message**. These represent the types of Outlook items that support mail apps: calendar items of appointments and meetings, and message items such as email messages, meeting requests, responses, and cancellations. Beyond this level in the API are item-level properties (such as [Appointment.subject](https://msdn.microsoft.com/library/ffa6812c-34b8-4b0a-8f92-22c3580c8379%28Office.15%29.aspx)) as well as objects and properties that support certain known [Entities](https://msdn.microsoft.com/library/1a06c8d1-dafe-46f4-967e-dd9b1d5b20e9%28Office.15%29.aspx) objects (for example [Contact](https://msdn.microsoft.com/library/2604b44c-7b79-47f0-ac3e-7d99bc9e6751%28Office.15%29.aspx), [MeetingSuggestion](https://msdn.microsoft.com/library/9726fbff-0f4f-4b70-8deb-effc14607d4e%28Office.15%29.aspx), [PhoneNumber](https://msdn.microsoft.com/library/cc86426a-2730-4774-9067-0611e5c8e9c1%28Office.15%29.aspx), and [TaskSuggestion](https://msdn.microsoft.com/library/16b0c3d6-adf4-4a88-ad09-4bb5565816b1%28Office.15%29.aspx)). See [Overview of Outlook add-ins architecture and features](https://msdn.microsoft.com/library/2cd5641b-492b-4431-8388-7fc589163e9c%28Office.15%29.aspx) for a summary of the features supported for mail apps. |
|Data-access model |The JavaScript API for Office represents the following features as a hierarchical set of objects: the app's runtime environment, user's mailbox and profile, and data about an item. |
|Threading models |Each mail app executes in its own process separate from the Outlook process. |
|Application architectures |In Outlook, a mail app is a set of HTML and JavaScript web pages hosted as a separate process inside a web browser control which, in turn, is hosted inside an app runtime process that provides security and performance isolation. |
|Remote usage |Mail apps use the JavaScript API for Office to access data about the current user, mailbox, and selected item stored on the corresponding Exchange Server. Provided that they have the appropriate permissions and use the appropriate technique for cross-domain access, mail apps can also call Exchange Web Services and other third-party web services to extend their functionality. |
|Transactions |The JavaScript API for Office does not support transactions. |
|Availability |The JavaScript API for Office is available for mailboxes on Exchange Server 2013, starting in Outlook 2013. |

#### Development criteria

|**Criteria**|**Mail apps support in apps for Office platform**|
|:-----|:-----|
|Languages and tools |You can implement mail apps using any common web technology, including HTML5, JavaScript, CSS3, XML, and REST APIs. You can use your preferred web development tool. Alternatively, using Napa, Visual Studio 2012, or a later version of these tools provides conveniences that save you time in development. |
|Managed implementation |Where appropriate in your scenario, you can use managed .aspx pages to implement server-side code for your mail apps. |
|Scriptable |The JavaScript API for Office is directly used in scripts. |
|Test and debug tools |You can use any web development tools you prefer. Napa and Visual Studio provide an integrated development environment that facilitates app testing and debugging. [Troubleshoot Outlook add-in activation](https://msdn.microsoft.com/library/da5b56c9-7fd1-4556-8c0e-f489c4c9e9b6%28Office.15%29.aspx) and [Sample: Debug properties of Outlook items](https://code.msdn.microsoft.com/office/Mail-apps-for-Outlook-faca78cd) provide further help in troubleshooting and debugging mail apps. |
|Expert availability |Programmers who have the required level of web development expertise for Office Add-ins are relatively easy to find. The platform is intended for both professional and non-professional developers. |
|Available information |Information about developing and posting Office Add-ins is available at [Build apps for Office and SharePoint](https://msdn.microsoft.com/office/apps/fp160950.aspx). Specific documentation for mail apps is available at [Outlook add-ins](https://msdn.microsoft.com/library/71e64bc9-e347-4f5d-8948-0a47b5dd93e6%28Office.15%29.aspx). |
|Developer and deployment licensing |Refer to [License your Office and SharePoint Add-ins](https://msdn.microsoft.com/library/3e0e8ff6-66d6-44ff-b0c2-59108ebd9181%28Office.15%29.aspx) for information about the app license framework for Office Add-ins. |

#### Security criteria

|**Criteria**|**Mail apps support in apps for Office platform**|
|:-----|:-----|
|Design-time permissions |No special permissions are required to develop mail apps. |
|Setup permissions |By default, end users and administrators can install low-trust mail apps that require **restricted** or **read item** permission, and administrators can install high-trust mail apps that require **read/write mailbox** permission. |
|Run-time permissions |Mail apps request a specific level of permission that is based on a three-tier permissions model: **restricted**, **read item**, and **read/write mailbox**. |
|Built-in security features | The Office Add-ins runtime provides the following benefits to prevent an app from damaging the end user's environment:  Isolates the process that the app runs in.  Doesn't involve .dll or .exe replacement or ActiveX components.  Makes apps easy to install or uninstall by the end user.  The administrator and end users have control over the mail apps that are made available and whether to grant the requested permission before installing a mail app.  In the case of rich clients, governs the use of memory and CPU to prevent denial of service malicious attacks. |
|Security monitoring features | For mail apps, the following resources are monitored:  CPU core usage.  Memory usage.  Number of crashes.  Length of time blocking an application.  Regular expression response time.  Number of times re-evaluating regular expressions.  Administrators can override default settings that govern the resource usage. |

#### Deployment criteria

|**Criteria**|**Mail apps support in apps for Office platform**|
|:-----|:-----|
|Server platform requirements |The user's mailbox for which a mail app is installed must be on Exchange Server 2013 or a later version. |
|Client platform requirements |For a mail app to run on the Outlook rich client, Outlook 2013 and Internet Explorer 9, or a later version of these applications, must be installed on the local computer. |
|Deployment methods |You can publish mail apps to the Office Store or to an Exchange catalog that makes the app available to users on that Exchange Server. Administrators or users can then choose to install a mail app from the Office Store or Exchange catalog, by using either the Exchange Admin Center (EAC) or by running remote Windows PowerShell cmdlets. You can access the EAC from the Outlook Backstage view or Outlook Web App, or by directly signing into the EAC for your mailbox. For more information, see [Deploy and install Outlook add-ins for testing](https://msdn.microsoft.com/library/d6eea4c4-bb21-4f24-bcba-1eccbb4e12dd%28Office.15%29.aspx). |
|Deployment notes |Once you install a mail app on Outlook or Outlook Web App, the mail app is available for that mailbox on both Outlook clients. |

<a name="OLSelectAPI_ObjectiveEvalCritApps"> </a>

### Objective evaluation criteria for the object model and PIA

Solutions that run on the client computer can use the Outlook object model or PIA to programmatically access Outlook items, such as contacts, messages, calendar items, meeting requests, and tasks. Unlike MAPI, the Outlook object model and PIA can provide event notifications for Outlook user-interface changes, such as changing the current folder or displaying an Outlook inspector.
  
> [!NOTE]
> For a solution to access data that is stored in a Microsoft Exchange mailbox or a personal folders (.pst) file, Outlook must be installed and configured on the client computer on which the application is running. > The Outlook object model and PIA support the same functionality to extend Outlook. The PIA defines managed interfaces that map to the COM-based object model and that a managed solution can interact with. In the remaining discussions in this section, most of the functional, security, and deployment criteria apply to the object model and the PIA in the same way. For more information about how the PIA facilitates interoperability between COM and the .NET Framework, see [Introduction to interoperability between COM and .NET](https://msdn.microsoft.com/library/6b2d099a-ec6f-4099-aaf6-e61003fe5a32%28Office.15%29.aspx) and [Architecture of the Outlook PIA](https://msdn.microsoft.com/library/89577d14-e6e2-4270-8e72-b0adba378667%28Office.15%29.aspx).
  
The following tables show evaluation criteria for the Outlook object model and PIA.
  
#### Functional criteria

|**Criteria**|**Outlook object model or PIA**|
|:-----|:-----|
|Application domain |Add-ins or standalone applications that use the Outlook object model or PIA typically handle user-specific messages, customize the Outlook user interface, or create custom item types for specialized solutions such as customer relationship management (CRM) solutions that integrate with Outlook. The Outlook object model or PIA is sometimes used for message processing in an informal workflow process, especially where application development on the Microsoft Exchange Server is not permitted. Unlike browser-based clients, cached-mode operation allows Outlook solutions to work when the user is offline or disconnected from the corporate network. |
|Major objects |The top-level object in the Outlook object model and PIA is the Outlook [Application](https://msdn.microsoft.com/library/797003e7-ecd1-eccb-eaaf-32d6ddde8348%28Office.15%29.aspx) object. [Explorers](https://msdn.microsoft.com/library/8398532a-1fad-7390-6778-109ac5e6c67c%28Office.15%29.aspx), [Conversation](https://msdn.microsoft.com/library/2705d38a-ebc0-e5a7-208b-ffe1f5446b1b%28Office.15%29.aspx), [Inspectors](https://msdn.microsoft.com/library/b65475d6-a212-fc96-459d-47390dfe5ee5%28Office.15%29.aspx), [Views](https://msdn.microsoft.com/library/5dd7edc2-12a2-f4c2-d158-8053d80e8dc9%28Office.15%29.aspx), [NavigationPane](https://msdn.microsoft.com/library/b6538c72-6115-99fc-c926-e0532a747823%28Office.15%29.aspx), [SolutionsModule](https://msdn.microsoft.com/library/4597765e-a95d-bf07-2ac4-103218ebc696%28Office.15%29.aspx), [FormRegion](https://msdn.microsoft.com/library/3a0b83eb-4076-9cb3-86a9-68f9e44df89f%28Office.15%29.aspx), and related objects represent elements of the Outlook user interface. The [NameSpace](https://msdn.microsoft.com/library/f0dcaa19-07f5-5d42-a3bf-2e42b7885644%28Office.15%29.aspx), [Stores](https://msdn.microsoft.com/library/8915a8e4-9c22-21d5-c492-051d393ce5f7%28Office.15%29.aspx), [Folders](https://msdn.microsoft.com/library/0c814c3c-74fc-414c-982d-a0097fcb35c2%28Office.15%29.aspx), [Accounts](https://msdn.microsoft.com/library/2510b7d7-5062-8ea3-dda4-b544d2882a2b%28Office.15%29.aspx), [AccountSelector](https://msdn.microsoft.com/library/846f176e-5680-a214-7624-75f3a524c989%28Office.15%29.aspx), [AddressEntries](https://msdn.microsoft.com/library/db91b717-07c6-d1f2-c545-b766ee1f0c6b%28Office.15%29.aspx), [ExchangeUser](https://msdn.microsoft.com/library/6ec117d1-7fdb-aa36-b567-1242f8238df0%28Office.15%29.aspx), and related objects support extending Outlook sessions, profiles, user accounts, message stores, and folders. At the data level, a number of item-level objects, such as [MailItem](https://msdn.microsoft.com/library/14197346-05d2-0250-fa4c-4a6b07daf25f%28Office.15%29.aspx), [AppointmentItem](https://msdn.microsoft.com/library/204a409d-654e-27aa-643a-8344c631b82d%28Office.15%29.aspx), [ContactItem](https://msdn.microsoft.com/library/8e32093c-a678-f1fd-3f35-c2d8994d166f%28Office.15%29.aspx), and [TaskItem](https://msdn.microsoft.com/library/5df8cfa5-5460-a5a1-a130-ba5bca1a0091%28Office.15%29.aspx), represent the built-in Outlook item types. The [PropertyAccessor](https://msdn.microsoft.com/library/2fc91e13-703c-3ec9-9066-ffee7144306c%28Office.15%29.aspx), [Table](https://msdn.microsoft.com/library/0affaafd-93fe-227a-acee-e09a86cadc20%28Office.15%29.aspx), [Search](https://msdn.microsoft.com/library/226a5d49-3caf-90dd-725c-265404d1939f%28Office.15%29.aspx), [ItemProperties](https://msdn.microsoft.com/library/34a110ed-6617-72da-1e98-a9773c705b40%28Office.15%29.aspx), [UserDefinedProperties](https://msdn.microsoft.com/library/196e5d4c-22be-02d3-95e0-3ea7594c2e4b%28Office.15%29.aspx), [Attachments](https://msdn.microsoft.com/library/4cc96a5f-a822-8ad5-6f61-e996bee8ba22%28Office.15%29.aspx), [Categories](https://msdn.microsoft.com/library/319efa26-269d-9f2f-c8ec-33082e80a9e2%28Office.15%29.aspx), [Recipients](https://msdn.microsoft.com/library/774f56b7-4de8-9584-60cd-4fbf361f4c85%28Office.15%29.aspx), [RecurrencePattern](https://msdn.microsoft.com/library/36c098f7-59fb-879a-5173-ed0260d13fa4%28Office.15%29.aspx), [Reminders](https://msdn.microsoft.com/library/66b94251-7fe4-886b-7c29-7feac4440dee%28Office.15%29.aspx), [Rules](https://msdn.microsoft.com/library/dd41b4de-bf5f-5532-46c9-394a5d078bec%28Office.15%29.aspx), and related objects support customizing and manipulating item-level objects. |
|Data-access model |The Outlook object model and PIA represent all data as a hierarchical set of objects and collections. |
|Threading models |All calls to the Outlook object model and PIA execute on Outlook's main foreground thread. The only threading model that the Outlook object model supports is single-threaded apartment (STA). Calling the Outlook object model or PIA from a background thread is not supported and can lead to errors and unexpected results in your solution. |
|Application architectures |Typically, COM add-ins and other Office applications use the Outlook object model to extend Outlook. Managed solutions can use the Outlook PIA and the COM interoperability layer of Visual Studio and the .NET Framework to access the Outlook object model. Visual Studio provides templates and additional class libraries and manifests to facilitate Office document and application customizations. For more information about using Visual Studio to develop managed add-ins for Outlook, see [Architecture of Application-Level Add-Ins](https://msdn.microsoft.com/library/978f102f-15c6-44e4-84e8-80b161408324.aspx) and [Outlook Solutions](https://msdn.microsoft.com/library/2ae3cd9c-bf31-4efa-8b18-b6b1c34a8d93.aspx). The Outlook object model also supports Visual Basic for Applications (VBA) macros and Windows Scripting Host (WSH), but does not support Windows Service applications. |
|Remote usage |The Outlook object model and PIA can be used only on a computer on which Outlook is installed. The Outlook object model can be used to access information stored in Exchange that is available in the Outlook application. |
|Transactions |The Outlook object model and PIA do not support transactions. |
|Availability |The Outlook object model is currently available in all versions of Outlook. The PIA is available in versions of Outlook since Outlook 2003. There have been extensions and improvements with each new version of Outlook. |

#### Development criteria

|**Criteria**|**Outlook object model or PIA**|
|:-----|:-----|
|Languages and tools |You can implement Outlook object model applications by using any COM or automation-compatible language, such as Visual Basic or C#, as well as non-COM languages, such as native C or C++. Microsoft Office development tools in Microsoft Visual Studio 2010 are the preferred tools for development of managed add-ins for Outlook 2010 and Outlook 2007. Microsoft Visual Studio 2005 Tools for the Microsoft Office System are the preferred tools for Outlook 2003. You can also use Office development tools in Visual Studio 2010 to create solutions for 32-bit and 64-bit versions of Outlook. When you build a solution in Office development tools in Visual Studio 2010 or Microsoft Visual Studio Tools for the Microsoft Office System, specifying the **Any CPU** option for the target platform results in managed solutions that work for both 32-bit and 64-bit versions of Outlook 2010. |
|Managed implementation |The Outlook PIA enables the Outlook object model to be used in a managed-code environment, which is supported by a rich set of class libraries and support technologies that address many limitations of VBA and COM add-ins. The PIA is a COM wrapper that acts as a bridge between the managed and COM environments. For more information, see [Why Use the Outlook PIA](https://msdn.microsoft.com/library/5cc9085e-7c97-4698-8cb9-e33e427c02e7%28Office.15%29.aspx). |
|Scriptable |The Outlook object model can be used in scripts. |
|Test and debug tools |No special debugging tools are needed to use the Outlook object model or PIA. On the other hand, you can use Visual Studio to provide an integrated development environment that facilitates application testing and debugging. |
|Expert availability |Developers who can successfully develop applications by using the Outlook object model or PIA are relatively easy to find. The Outlook object model and PIA are intended for add-ins created by using widely available development tools, such as Visual Studio. These tools provide design-time environments that simplify the development process. |
|Available information |Information about programming by using the Outlook object model is available in both Microsoft and third-party resources. For more information about the Outlook object model, see the [Outlook 2010 Developer Reference](https://msdn.microsoft.com/library/75e4ad96-62a2-49d2-bc51-48ceab50634c%28Office.15%29.aspx). For more information about the Outlook PIA, see the [Outlook 2010 Primary Interop Assembly Reference](https://msdn.microsoft.com/library/54bdde85-8dc9-4498-a1ac-f72eaf8f0cd3%28Office.15%29.aspx). For examples of managed Outlook solutions developed by using Office development tools in Visual Studio, see [Outlook Solutions with Visual Studio](https://msdn.microsoft.com/vsto/dd162450.aspx). |
|Developer and deployment licensing |Refer to your Exchange and Microsoft Developer Network (MSDN) subscription licensing agreements to determine whether additional licenses are required for Outlook and Outlook object model use in your applications. |

#### Security criteria

|**Criteria**|**Outlook object model or PIA**|
|:-----|:-----|
|Design-time permissions |No special permissions are required to develop applications by using the Outlook object model or PIA. |
|Setup permissions |No special permissions are required to install applications that use the Outlook object model or PIA. However, local administrator rights are required to install Office and Outlook. |
|Run-time permissions |No special permissions are required to run applications that use the Outlook object model or PIA. |
|Built-in security features |The Outlook object model and PIA communicate with Exchange by using MAPI and with Active Directory by using Active Directory Service Interfaces (ADSI). The current security context of the user who is running the application is used to determine what resources that code can access. By default, add-ins are trusted for full access to all objects, properties, and methods in the Outlook object model or PIA. IT administrators can exercise control over which add-ins and objects can access the Outlook object model or PIA. The Outlook object model and PIA prevent code that is run outside the Outlook process from accessing secure objects and methods. |
|Security monitoring features | Outlook monitors the following metrics of an add-in to determine whether it should disable the add-in:  Startup  Shutdown  Folder switch  Item open **Invoke** frequency  Administrators can use group policy to override user settings and control the add-ins that run on the user's computers.  For more information, see [Performance criteria for keeping add-ins enabled](https://msdn.microsoft.com/library/office/4c6d44d2-238b-42d8-896b-51d513c9e14c#ol15WhatsNew_AddinDisabling). |

#### Deployment criteria

|**Criteria**|**Outlook object model or PIA**|
|:-----|:-----|
|Server platform requirements |The Outlook object model and PIA are client-side technologies. |
|Client platform requirements |Applications that use the Outlook object model or PIA to access Exchange data require that Outlook be installed on the local computer. |
|Deployment methods |Applications that use the Outlook object model or PIA are distributed by using standard application installation software. |
|Deployment notes |Because Outlook should not be installed on the Exchange Server, applications that use the Outlook object model or PIA cannot be run on the Exchange Server. |

<a name="OLSelectAPI_ObjectiveEvalCritApps"> </a>

### Objective evaluation criteria for MAPI

You can use MAPI to access items and folders in public and private stores, as well as to access the properties stored with each item. All versions of Outlook use MAPI. You can create clients that use MAPI, and can create MAPI servers and MAPI forms handlers, as well. The information in this section applies only to MAPI client applications.
  
> [!NOTE]
> MAPI is a mature mechanism used to access information in Exchange or in a personal folders (.pst) file, and MAPI provides some capabilities that are not available in any other API. However, MAPI does not work well outside an intranet, maintains an open connection for the duration of the MAPI session, and can be difficult to learn. MAPI does not enforce Outlook business logic, so you must take special care to ensure that Outlook business logic is maintained.
  
The following tables show evaluation criteria for MAPI.
  
#### Functional criteria

|**Criteria**|**MAPI**|
|:-----|:-----|
|Application domain |Client applications that use MAPI access a user mailbox or public folder information stored in Exchange, and user directory information stored in Active Directory. Client applications that use MAPI are typically email clients, such as Outlook, and applications that require complex email processing. |
|Major objects |MAPI objects are all obtained through the [IMAPISession : IUnknown](https://msdn.microsoft.com/library/5650fa2a-6e62-451c-964e-363f7bee2344%28Office.15%29.aspx) interface. The session object provides the client access to objects for working with MAPI profiles, status, message service provider administration, message store tables, and address books. The message store table contains objects for the message store, folders, messages, attachments, and recipients. The address book tables contain objects for messaging users and distribution lists. |
|Data-access model |MAPI represents messages and users as a hierarchical set of objects. |
|Threading models |There are no specific threading prohibitions. However, applications that use free-threading should avoid sharing MAPI objects among threads due to the high costs of marshaling the object. MAPI and MAPI service providers use free-threading. |
|Application architectures |MAPI client applications are typically Windows Forms-based client applications. However, you can use MAPI to write N-tier applications. |
|Remote usage |MAPI uses remote procedure calls (RPCs) to communicate with the Exchange Server. Typically RPCs are intentionally blocked from passing through Internet firewalls. |
|Transactions |MAPI does not support transactions. |
|Availability |A MAPI stub currently ships with all versions of Windows. Office installs its own MAPI subsystem when it installs Outlook. No changes to MAPI are anticipated at this time. |

#### Development criteria

|**Criteria**|**MAPI**|
|:-----|:-----|
|Languages and tools |You can directly access MAPI by using C or C++. Other languages that can access the C/C++ calling convention may be able to access MAPI. The use of managed languages, such as Visual Basic or C#, is not supported. You must compile separate MAPI solutions for 32-bit and 64-bit versions of Outlook. |
|Managed implementation |MAPI is an unmanaged component. Use of MAPI is not supported under the COM interoperability layer of Visual Studio and the .NET Framework.  |
|Scriptable |MAPI cannot be directly used in scripts. |
|Test and debug Tools |No special debugging tools are needed to debug applications that use MAPI. On the other hand, you can use [MFCMAPI](https://stephenegriffin.github.io/mfcmapi/). MFCMAPI uses MAPI to provide access to MAPI stores through a graphical user interface, and facilitates investigation of issues when you extend Outlook by using MAPI. |
|Expert availability |Expert MAPI programmers can be difficult to find, and learning the technology can take a significant amount of time. In addition to the Microsoft communities, there are only a small number of high-quality third-party websites that provide helpful MAPI development information. |
|Available information |Both Microsoft and third-party books that describe MAPI programming are available. |
|Developer and deployment licensing |No special licensing is required for developing applications that use MAPI. |

#### Security criteria

|**Criteria**|**MAPI**|
|:-----|:-----|
|Design-time permissions |The developer must have permissions to access the data in the Exchange store. Exchange stores user and distribution list information in Active Directory, so developers who create MAPI client applications that access that information must have the ability to retrieve and set that information. |
|Setup permissions |Setting up MAPI-based applications typically requires the user to be a local administrator, or to have rights to install software. |
|Run-time permissions |Running a MAPI-based application usually requires only that the user has sufficient permissions to access the data on an Exchange store or personal folders (.pst) file. |
|Built-in security features |MAPI profiles can be password protected on most platforms. |

#### Deployment criteria

|**Criteria**|**MAPI**|
|:-----|:-----|
|Server platform requirements |The Exchange Server on which user data is stored for users of the MAPI client application must be properly configured to allow access by MAPI clients. |
|Client platform requirements |The client application installer should verify that the proper version of MAPI is available on the computer, and that it is properly configured by using the Mapisvc.inf file. |
|Deployment methods |Applications that use MAPI can be deployed to client computers by using standard software distribution technologies. |
|Deployment notes |The installer should verify that the correct version of MAPI is available. |

<a name="OLSelectAPI_FactorsApps"> </a>

## Decision factors for the apps for Office platform

Because Office Add-ins use web technologies, they are best for connecting to services in the cloud or on-premises, and bringing the services into the context of the rich client and web client. By requesting appropriate permissions, mail apps also allow reading, writing, or sending items in a mailbox.
  
The following are common reasons why mail apps are a better choice for developers than add-ins:
  
- You can use existing knowledge of and the benefits of web technologies such as HTML, JavaScript, and CSS. For power users and new developers, XML, HTML, and JavaScript require less significant ramp-up time than COM-based APIs, including the object model and MAPI.

- You can use a simple web deployment model to update your mail app (including the web services that the app uses) on your web server without any complex installation on the Outlook client. In fact, any updates to the mail app, with the exception of the app manifest, do not require any updating on the Office client. You can update the code or user interface of the mail app conveniently just on the web server. This presents a significant advantage over the administrative overhead involved in updating add-ins.

- You can use a common web development platform for mail apps that can roam across the Outlook rich client and Outlook Web App on the desktop, tablet, and smartphone. On the other hand, add-ins use the object model for the Outlook rich client and, hence, can run on only that rich client on a desktop form factor.

- You can enjoy rapid turnaround of building and releasing apps via the Office Store.

- Because of the three-tier permissions model, users and administrators perceive better security and privacy in mail apps than add-ins, which have full access to the content of each account in the user's profile. This, in turn, encourages user consumption of apps.

- Depending on your scenarios, there are features unique to mail apps that you can take advantage of and that are not supported by add-ins:

  - You can specify a mail app to activate only for certain contexts (for example, Outlook displays the app in the app bar only if the message class of the user-selected appointment is IPM.Appointment.Contoso, or if the body of an email contains a package tracking number or a customer identifier).

  - You can activate a mail app if the selected message contains some known entities, such as an address, contact, email address, meeting suggestion, or task suggestion.

  - You can take advantage of authentication by identity tokens, and of Exchange Web Services.

However, the following features are unique to add-ins and may make them a more appropriate choice than mail apps in some circumstances:
  
- You can use add-ins to extend or automate Outlook at an application-level, because the object model and PIA have extensive integration with Outlook features (such as all Outlook item types, user interface, sessions, and rules). At the item-level, add-ins can interact with an item in read or compose mode. With mail apps, you cannot automate Outlook at the application level, and you can extend Outlook's functionality in the context of only the read-mode of the supported items (messages and appointments) in the user's mailbox.

- You can specify custom business logic for a new item type.

- You can modify and add custom commands in the ribbon and Backstage view.

- You can display a custom form page or form region.

- You can detect events such as sending an item or modifying properties of an item.

- You can use add-ins on Outlook 2013 and Exchange Server 2013, as well as earlier versions of Outlook and Exchange. On the other hand, mail apps work with Outlook and Exchange starting in Outlook 2013 and Exchange Server 2013, but not earlier versions.

For more information about scenarios that the object model and PIA support, see the next section, [Decision factors for the object model or PIA](#OLSelectAPI_FactorsOM). For a comparison of the Office Add-ins platform with other extensibility technologies for Office, see [The background on apps for Office and SharePoint](https://blogs.msdn.com/b/officeapps/archive/2012/07/23/introducing-apps-for-the-new-office-and-sharepoint.aspx).

<a name="OLSelectAPI_FactorsOM"> </a>

## Decision factors for the object model or PIA

### Major baseline scenarios supported by the Outlook object model or PIA

In general, use the object model or the PIA if your solution customizes the Outlook user interface or relies on Outlook's business logic. Following are the major baseline scenarios for which Outlook solutions use the object model or the PIA.
  
- [Customize the Outlook user interface](#OLSelectAPI_CustomizeTheOutlookInterface)
- [Add, remove, read, write, filter, search, or sort Outlook items](/office/vba/outlook/how-to/items-folders-and-stores/outlook-item-objects)
- [Customize item properties, fields, and forms](#OLSelectAPI_ItemPropFieldsForms)
- [Process Outlook events such as switching folders or opening an item](#OLSelectAPI_Events)
- [Automate Outlook and integrate with other Office applications](#OLSelectAPI_AutomateOutlook)

<!--Images removed because we can't add a link to the images. If someone figures out a way to do this, you can add them back in but they're not really needed; I replaced them with a bulleted list here and after the next paragraph: 
![Customize the Outlook UI](media/odc_ol15_ta_SelectingTech_Fig2-1.gif)
![Use Outlook items](media/odc_ol15_ta_SelectingTech_Fig2-2.gif)
![Customize item properties, fields, and forms](media/odc_ol15_ta_SelectingTech_Fig2-3.gif)
![Process Outlook events](media/odc_ol15_ta_SelectingTech_Fig2-4.gif)
![Automate Outlook](media/odc_ol15_ta_SelectingTech_Fig2-5.gif)-->

### Scenarios supported by the object model or PIA since Outlook 2007

In addition to the baseline scenarios, if your Outlook solution supports any of the scenarios shown in the following list, and your solution is intended to run on Outlook 2007 or a later version but not earlier versions, you can use the object model or the PIA as well. This section specifies the main objects or members that you can use in the Outlook object model to extend each scenario (with the exception of the [IDTExtensibility2](/dotnet/api/extensibility.idtextensibility2?view=visualstudiosdk-2017.md&preserve-view=true) interface in the Visual Studio automation object model, and the [IRibbonExtensibility](/office/vba/api/Office.IRibbonExtensibility) interface in the Office object model, which you can integrate with the Outlook object model).

- [Customize the Outlook UI: Office Fluent Ribbon, Navigation pane, Task pane](#OLSelectAPI_CustomizeTheOutlookInterface)
- [Customize forms as form regions and deploy them by add-ins](#OLSelectAPI_CustomFormRegions)
- [Set and get built-in, item-level properties that are not exposed in the object model](#OLSelectAPI_CustomizingProperties)
- [Enumerate and view many items in a folder](#OLSelectAPI_Enumerating)
- [Flag items as tasks](#OLSelectAPI_ItemsFlag)
- [Share calendars, RSS feeds, and folders](#OLSelectAPI_Sharing)
- [Add, remove, save, and get block level, path, size, and type of an attachment](#OLSelectAPI_Attachments)
- [Manage rules, time zones, and views](#OLSelectAPI_Misc)
- [Add or remove a category to the master category list for the current profile](#OLSelectAPI_Categories)
- [Obtain detailed information for an account in the current profile](#OLSelectAPI_PrimaryAccount)
- [Obtain detailed information of an Exchange distribution list or user as an address entry](#OLSelectAPI_AddressBook)
- [Store private data for solutions](#OLSelectAPI_StoringData)

<!--More removed images
![Customize the Outlook UI](media/odc_ol15_ta_SelectingAPI_Fig3-1.gif)
![Customize form regions](media/odc_ol15_ta_SelectingTech_Fig3-2.gif)
![Use PropertyAccessor to access properties](media/odc_ol15_ta_SelectingAPI_Fig3-3.gif)
![Enumerate and view items in a folder](media/odc_ol15_ta_SelectingAPI_Fig3-4.gif)
![Flag items as tasks](media/odc_ol15_ta_SelectingAPI_Fig3-5.gif)
![Share calendars, RSS feeds, and folders](media/odc_ol15_ta_SelectingAPI_Fig3-6.gif)
![Manage attachments](media/odc_ol15_ta_SelectingAPI_Fig3-7.gif)
![Manage rules, time zones, and views](media/odc_ol15_ta_SelectingAPI_Fig3-8.gif)
![Add or remove a category](media/odc_ol15_ta_SelectingAPI_Fig3-9.gif)
![Get detailed information for an account](media/odc_ol15_ta_SelectingAPI_Fig3-10.gif)
![Manage Exchange distribution lists and users](media/odc_ol15_ta_SelectingAPI_Fig3-11.gif)
![Store private data for solutions](media/odc_ol15_ta_SelectingAPI_Fig3-12.gif)
-->

### Scenarios supported by the object model or PIA since Outlook 2010

If your Outlook solution is intended to run on Outlook 2010 and not earlier versions, you can choose to use the object model or the PIA to support the scenarios shown in this next section. This section specifies the main objects or members that you can use in the Outlook object model to extend each scenario (with the exception of the [IRibbonControl](/office/vba/api/Office.IRibbonControl), [IRibbonExtensibility](/office/vba/api/Office.IRibbonExtensibility), and [IRibbonUI](/office/vba/api/Office.IRibbonUI) interfaces that are in the Office object model, which you can integrate with the Outlook object model).

- [Customize the Outlook 2010 UI such as the Office Backstage view and context menus](#OLSelectAPI_CustomizingUIOutlook2010)
- [Manage and access heterogeneous items in a conversation](#OLSelectAPI_Conversations)
- [Manage selection of items in an explorer or locate a selection](#OLSelectAPI_ItemSelection)
- [Manage selection of attachments in an inspector](#OLSelectAPI_AttachmentSelection)
- [Support multiple Exchange accounts in one profile](#OLSelectAPI_MultipleAccounts)
- [Create a contact card for an address entry](/office/vba/api/Outlook.NameSpace.CreateContactCard)
- [Organize solution-specific folders in the Solutions module](#OLSelectAPI_Folders)

<!--more removed images:
![Customize the Outlook 2010 UI](media/odc_ol15_ta_SelectingAPI_Fig4-1.gif)
![Manage items in a conversation](media/odc_ol15_ta_SelectingAPI_Fig4-2.gif)
![Manage selection of items in an explorer](media/odc_ol15_ta_SelectingAPI_Fig4-3.gif)
![Manage selection of attachments in an inspector](media/odc_ol15_ta_SelectingAPI_Fig4-4.gif)
![Support multiple Exchange accounts in one profile](media/odc_ol15_ta_SelectingAPI_Fig4-5.gif)
![Create a contact card for an address entry](media/odc_ol15_ta_SelectingAPI_Fig4-6.gif)
![Organize solution-specific folders](media/odc_ol15_ta_SelectingAPI_Fig4-7.gif)
-->

### Scenarios supported by the object model or PIA since Outlook 2013

If your solution is intended to run on Outlook 2013 and not any earlier version, you can use the object model or the PIA to support the scenarios shown in the following resources.

- [Display a view for all contacts in the current folder](/office/vba/api/Outlook.peopleview)
- [Select inline response in reading pane](#OLSelectAPI_InlineResponse)
- [Show check address or full name dialog for contact](#OLSelectAPI_ContactCheckDialogs)
- [Detecting reading item properties is complete](/office/vba/outlook/How-to/Items-Folders-and-Stores/outlook-item-objects)

<!--more removed images:
![Display view for all contacts in current folder](media/odc_ol15_ta_SelectingAPI_Fig5-1.gif)
![Inline response in reading pane](media/odc_ol15_ta_SelectingAPI_Fig5-2.gif)
![Show check address or full name dialog for contact](media/odc_ol15_ta_SelectingAPI_Fig5-3.gif)
![Detecting reading item properties is complete](media/odc_ol15_ta_SelectingAPI_Fig5-4.gif)
-->

<a name="OLSelectAPI_FactorsMAPI"> </a>

## Decision factors for MAPI

In general, you use MAPI to access data on a MAPI-based server such as the Microsoft Exchange server, and to do tasks such as the following:
  
- Create a custom service provider such as an address book provider, transport provider, or store provider.
- Create a sink process.

- Create or manipulate a profile.

- Run an application as a Windows NT service.

- Run tasks on a background thread. For example, enumerating numerous items in a folder and modifying the items' properties in a background thread can optimize performance.

For more information and code samples, see the [Outlook MAPI Reference](/office/client-developer/outlook/mapi/outlook-mapi-reference) and [MFCMAPI](https://stephenegriffin.github.io/mfcmapi/).
  
In addition, if your solution runs on a version of Outlook earlier than Outlook 2007, and scenarios such as the following apply to your solution, you should use MAPI to extend those scenarios.
  
- Set and get built-in item-level properties that are not exposed in the object model.
- Manage accounts, attachments, Exchange distribution lists, Exchange users, or stores.
- Store private data for solutions.
- Manage a message store for an account.

Since Outlook 2007, the object model has supported a range of features that, prior to Outlook 2007, developers had to resort to MAPI or other APIs such as Microsoft Collaboration Data Objects (CDO) 1.2.1 and Microsoft Exchange Client Extensions. So if any of the scenarios in the previous list applies to your solution, but your solution runs on Outlook 2007 or Outlook 2010, you can and should use the Outlook object model or PIA to support these scenarios. For more information about Outlook 2007 enhancements that unify Outlook development technologies, see [What's New for Developers in Outlook 2007 (Part 1 of 2)](https://msdn.microsoft.com/library/76e3f0b7-ef2b-4e9f-8515-3002d75d7721%28Office.15%29.aspx).

<a name="OLSelectAPI_FactorsAux"> </a>

## Decision factors for the Auxiliary APIs

The Outlook auxiliary APIs can integrate with Outlook business logic or MAPI in some scenarios where the object model or MAPI does not provide a solution. Use the Outlook auxiliary APIs in the following scenarios:
  
- Account management: Manage account information, manipulate accounts, provide notification on account changes, and protect accounts from spam.
- Data degradation: Wrap an object in a preferred character format rather than exposing the object in its native format.
- Rebasing calendars and time zone support: Rebase Outlook calendars to support daylight saving time.
- Free/busy status: Provide free/busy information on calendars.
- Contact pictures: Determine the display of a contact's picture in Outlook.
- Item currency: Determine whether an Outlook item has unsaved changes.
- Categorizing an item: Categorize an Outlook item after sending the item.

For more information about the auxiliary APIs, see the [Additional resources—Auxiliary APIs](#OLSelectAPI_AdditionalResourcesAuxAPIs) section.

<a name="OLSelectAPI_InOrOut"> </a>

## Automating Outlook by in-process vs. out-of-process Solutions

> [!NOTE]
> The discussion of automating Outlook in this section and the next is outside the scope of Office Add-ins, which are intended to extend the functionality of the Office client or web application but not to automate it.
  
Outlook supports automation by using add-ins that run in the same foreground process as the Outlook process, and by standalone solutions that run in their own separate process outside of the Outlook process. Generally, to automate Outlook, use an add-in to interact with Outlook through the object model, PIA, or MAPI, and in less common scenarios, through an auxiliary API (such as [HrProcessConvActionForSentItem](auxiliary/hrprocessconvactionforsentitem.md)). Use an out-of-process solution only when it's necessary (for example, when you're writing a MAPI client application that uses the Tzmovelib.dll file to rebase Outlook calendars for customers, or enumerating numerous items in a folder and modifying the items' properties in a background thread to optimize performance).
  
Add-ins are the preferred solution to automate Outlook, because Outlook trusts only the [Application](/office/vba/api/Outlook.Application) object passed to the add-in during the [OnConnection(Object, ext_ConnectMode, Object, Array)](/dotnet/api/extensibility.idtextensibility2.onconnection?&view=visualstudiosdk-2022#Extensibility_IDTExtensibility2_OnConnection_System_Object_Extensibility_ext_ConnectMode_System_Object_System_Array__) event of the add-in. You can avoid the display of security warnings of the Object Model Guard by deriving all objects, properties, and methods from this **Application** object. If the add-in creates a new instance of the **Application** object, Outlook does not trust that object, even if the add-in is on the list of trusted add-ins. Any objects, properties, and methods derived from such an **Application** object will not be trusted and the blocked properties and methods will invoke security warnings. For more information about the Outlook Object Model Guard, see [Security Behavior of the Outlook Object Model](/office/vba/outlook/How-to/Security/security-behavior-of-the-outlook-object-model).

<a name="OLSelectAPI_ManOrUnman"> </a>

## Automating Outlook by managed vs. unmanaged solutions

Outlook supports automation by add-ins and standalone applications, written in managed or unmanaged languages. The more commonly used managed languages are C# and Visual Basic. C++ and Delphi tools are more common in unmanaged development. Available expertise is one consideration when choosing between managed and unmanaged development.
  
If your solution uses only the object model, you can consider developing a managed solution by using the PIA, or Office development tools in Visual Studio. The Office development tools in Visual Studio provide project templates and visual designers that simplify creating custom user interfaces and developing Office solutions.

On the other hand, because MAPI was developed years before the .NET Framework, and Microsoft does not provide managed wrappers for MAPI, Microsoft does not support using MAPI in managed code. If you are using MAPI, you must develop an unmanaged solution. For more information, see [The support guidelines for client-side messaging development](https://support.office.com/article/Best-practices-for-Outlook-f90e5f69-8832-4d89-95b3-bfdf76c82ef8).
  
## Niche APIs and technologies

The Outlook Social Connector (OSC) and Weather Bar support extending very specific scenarios in Outlook.
  
### Outlook Social Connector (OSC) provider extensibility

The Outlook Social Connector (OSC) provider extensibility supports developing a provider for a social network to allow users to view, in Outlook and other Office client applications, friends and activities updates on that social network. Figure 6 shows the OSC displaying in the People Pane the activities of a person in social network sites.
  
**Figure 6. The OSC displaying social network data in the People Pane**

![Outlook Social Connector pane](media/2d6b867f-73d8-4a3b-b8bd-3844bc34bf4e.jpg)
  
The OSC in Outlook allows users to view, in the People Pane, an aggregation of emails, attachments, and meeting requests from a person in Outlook. In an organizational environment, users who collaborate on a SharePoint site can see document updates and other site activities of this person on the SharePoint site. Outlook Social Connector provider extensibility supports developing a provider for the OSC to synchronize and surface social network updates in Outlook. Common OSC providers (such as Facebook and LinkedIn) are installed by default with Outlook. Depending on the social network sites that an Outlook user has signed into, the user can see, in the People Pane, updates such as photos, status, and activities on the corresponding social networks.
  
### Weather Bar extensibility

Starting in Outlook 2013, the Weather Bar allows developers to plug in a third-party weather web service for the Weather Bar, to provide weather conditions data for a user-chosen location. The Weather Bar in Outlook displays weather conditions and forecast for a geographic location. A user can choose one or multiple locations, and conveniently see weather data in the Weather Bar in the calendar module. Figure 7 shows the Weather Bar displaying a three-day forecast for New York, NY.
  
**Figure 7. Weather Bar in Outlook**

![Weather Bar showing forecast for New York.](media/ol15_WeatherBar_fig1.jpg)
  
By default, Outlook uses weather data provided by MSN Weather. The Weather Bar supports third-party weather data web services which follow a defined protocol to communicate with Outlook. As long as a third-party weather data service supports this protocol, users can choose that weather data service to provide weather data in the Weather Bar.
  
See the [Additional resources—primary references, resources, and code samples](#OLSelectAPI_AdditionalResourcesRefCode) section for more information about using OSC provider extensibility and the Weather Bar extensibility.

## Conclusion

To determine the best API or technology for your solution, you must first define the goals of your solution:
  
- The versions of Outlook you intend your solution to support.

- The high-priority scenarios of your solution. Does your solution mainly interact with the content and properties of a message or appointment item? Or does your solution automate Outlook at an application level? If so, do these scenarios involve enumerating, filtering, or modifying folders that contain many Outlook items?

First, verify whether the mail app support in the Office Add-ins platform meets your needs. See the Functional Criteria section of [Objective evaluation criteria for the apps for Office platform](#OLSelectAPI_ObjectiveEvalCritApps) to determine whether the major objects and features support your scenarios. See the section [Decision factors for the apps for Office platform](#OLSelectAPI_FactorsApps) to verify whether mail apps are a better choice than add-ins for your scenarios. In general, develop your solution as an app, if possible, to take advantage of the platform's support across Outlook clients over different form factors.
  
If your scenarios require you to extend beyond message and appointment items, or require you to automate Outlook at an application level, try to match your scenarios with those outlined in the section [Decision factors for the object model or PIA](#OLSelectAPI_FactorsOM). If the object model (or PIA) of your target Outlook versions supports your scenarios, and your solution does not manipulate folders with many items, you should implement your solution as an add-in, in either a managed or unmanaged language.
  
If the object model (or PIA) of a target Outlook version does not support some of your scenarios, verify whether the scenarios in the [Decision factors for MAPI](#OLSelectAPI_FactorsMAPI) or [Decision factors for the Auxiliary APIs](#OLSelectAPI_FactorsAux) section meet your needs. If MAPI meets your needs, you should implement your solution in unmanaged code. If an auxiliary API solves one of your scenarios, you can use managed or unmanaged code.
  
If your solution uses MAPI, you must implement it in unmanaged code, such as C++. Otherwise, the decision to use managed or unmanaged code to create the solution generally depends on your available resources and their expertise. As for deciding whether to implement the solution as an add-in or standalone application, choose an add-in to avoid the user constantly invoking the Outlook Object Model Guard, unless your scenario requires manipulation of folders that contain numerous items. In the latter scenario, implementing the solution to run as a background thread can optimize Outlook performance.
  
If your scenarios include showing social network information or updates in Outlook, you should use the OSC provider extensibility to create a COM-visible DLL. You can do this in either a managed or unmanaged language.
  
If you are interested in plugging in a third-party weather data service to the Weather Bar, you can follow the protocol defined by Weather Bar extensibility and provide the appropriate web services. You can create these web services in a managed language.
  
Once you have decided on the APIs or technologies to use in your solution, you can refer to additional documentation and code samples in the [Additional resources—primary references, resources, and code samples](#OLSelectAPI_AdditionalResourcesRefCode) section for more information.

<a name="OLSelectAPI_AdditionalResourcesApps"> </a>

[Office Add-ins platform overview](/office/dev/add-ins/overview/office-add-ins) provides a good introduction of Office Add-ins, including the architecture and development life cycle.
  
See [Outlook add-ins](/office/dev/add-ins/outlook/outlook-add-ins-overview) for a detailed roadmap of resources about developing mail apps.
  
## See also: Object model and PIA

The following resources provide more information about using the object model and PIA.

<a name="OLSelectAPI_PrimaryAccount"> </a>

- [Account](/office/vba/api/Outlook.Account) object

- [NameSpace.Accounts](/office/vba/api/Outlook.NameSpace.Accounts) property

<a name="OLSelectAPI_MultipleAccounts"> </a>

### Accounts—multiple accounts in profile

- [Account](/office/vba/api/Outlook.Account) object

- [Using Multiple Accounts for the Same Profile on Outlook](/office/vba/outlook/Concepts/Accounts/using-multiple-accounts-for-the-same-profile-on-outlook)

- [Obtain Information for Multiple Accounts](https://msdn.microsoft.com/library/af587ee2-429a-252f-ecb6-2f058b9a37a8%28Office.15%29.aspx)

- [Manipulating Multiple Exchange Accounts in Outlook 2010](https://msdn.microsoft.com/library/b5a80da9-102d-4617-8a06-49ded01a237a%28Office.15%29.aspx)

<a name="OLSelectAPI_AddressBook"> </a>

### Address book and Exchange users

- [Display Names from the Address Book](https://msdn.microsoft.com/library/32e7179c-8133-ee20-ecf6-52c9275f205f%28Office.15%29.aspx)

- [Access Exchange User or Distribution List Information from the Address Book](https://msdn.microsoft.com/library/077a8666-09c5-e641-0b9b-7d83133d931f%28Office.15%29.aspx)

- [List the Groups that My Manager Belongs to](https://msdn.microsoft.com/library/2f0ff92c-e026-4f62-c039-fbda9aaf1546%28Office.15%29.aspx)

- [List the Name and Office Location of Each Manager Belonging to an Exchange Distribution List](https://msdn.microsoft.com/library/abc26854-62db-be7f-4025-46acbcb42541%28Office.15%29.aspx)

- [AddressEntries](https://msdn.microsoft.com/library/db91b717-07c6-d1f2-c545-b766ee1f0c6b%28Office.15%29.aspx) object

- [AddressLists](https://msdn.microsoft.com/library/b8c5ce75-3030-0179-45bb-f44fe6628074%28Office.15%29.aspx) object

- [ExchangeDistributionList](https://msdn.microsoft.com/library/2830dfba-6c0a-a81f-6b98-92ac2aafb59d%28Office.15%29.aspx) object

- [ExchangeUser](https://msdn.microsoft.com/library/6ec117d1-7fdb-aa36-b567-1242f8238df0%28Office.15%29.aspx) object

- [SelectNamesDialog](https://msdn.microsoft.com/library/1522736a-3cad-9f1c-4da9-b52a3a01731c%28Office.15%29.aspx) object

<a name="OLSelectAPI_Attachments"> </a>

### Attachments

- [Attach a File to a Mail Item](https://msdn.microsoft.com/library/1d94629b-e713-92cb-32de-c8910612e861%28Office.15%29.aspx)

- [Attachment file types restricted by Outlook 2010](https://technet.microsoft.com/library/cc179163.aspx)

- [Attachment](https://msdn.microsoft.com/library/3e11582b-ac90-0948-bc37-506570bb287b%28Office.15%29.aspx) object

- [AttachmentSelection](https://msdn.microsoft.com/library/398cf106-a904-9048-e627-e47aaadf1105%28Office.15%29.aspx) object

- **AttachmentAdd** event per item object

- **AttachmentRead** event per item object

- **AttachmentRemove** event per item object

- **BeforeAttachmentAdd** event per item object

- **BeforeAttachmentPreview** event per item object

- **BeforeAttachmentRead** event per item object

- **BeforeAttachmentSave** event per item object

- **BeforeAttachmentWrite** event per item object

<a name="OLSelectAPI_AttachmentSelection"> </a>

### Attachments: selection in inspector

- [Inspector.AttachmentSelection](https://msdn.microsoft.com/library/19466ce7-def8-4cce-1776-dcea1df9f15d%28Office.15%29.aspx) property

- [Inspector.AttachmentSelectionChange](https://msdn.microsoft.com/library/1250045d-bcb3-b823-31d5-ec31c64ad59e%28Office.15%29.aspx) event

<a name="OLSelectAPI_AutomateOutlook"> </a>

### Automating Outlook

- [Customizing Outlook using COM add-ins](https://msdn.microsoft.com/library/84a4f616-3ace-0139-57d5-f0c070064ab2%28Office.15%29.aspx)

- [Building a C++ Add-in for Outlook 2010](https://msdn.microsoft.com/library/70b308e7-d713-4a26-9892-5021f7320674%28Office.15%29.aspx)

- [Introduction to interoperability between COM and .NET](https://msdn.microsoft.com/library/6b2d099a-ec6f-4099-aaf6-e61003fe5a32%28Office.15%29.aspx)

- [Why Use the Outlook PIA](https://msdn.microsoft.com/library/5cc9085e-7c97-4698-8cb9-e33e427c02e7%28Office.15%29.aspx)

- [Best practices in developing managed Outlook add-ins](https://msdn.microsoft.com/library/a03246f6-2ca5-4fcb-8e63-a11cfbc8d9a0%28Office.15%29.aspx)

- [Obtain and Log On to an Instance of Outlook](https://msdn.microsoft.com/library/ef369364-6500-2759-3ef4-ed4411112e96%28Office.15%29.aspx)

- [Automating Outlook from a Visual Basic Application](https://msdn.microsoft.com/library/623f91af-cd50-1ff0-9519-5a39cbcf5d18%28Office.15%29.aspx)

- [Automating Outlook from Other Office Applications](https://msdn.microsoft.com/library/d3e44f80-df67-2d28-94dc-14d7a8c8c26c%28Office.15%29.aspx)

<a name="OLSelectAPI_Categories"> </a>

### Categories

- [Categorize Your Outlook Items](https://msdn.microsoft.com/library/e8cfb450-b8b0-bee6-fdf0-d0a92bf9af56%28Office.15%29.aspx)

- [Category](https://msdn.microsoft.com/library/143ef095-54b0-cbe2-e356-632029061ac2%28Office.15%29.aspx) object

- [NameSpace.Categories](https://msdn.microsoft.com/library/3963afca-3a7e-38d7-1347-7e1467be3a10%28Office.15%29.aspx) property

<a name="OLSelectAPI_ContactCheckDialogs"> </a>

### Contacts: check address and full name

- [ContactItem.ShowCheckAddressDialog](https://msdn.microsoft.com/library/773a1a3c-1247-fd48-399a-728766e56570%28Office.15%29.aspx) method

- [ContactItem.ShowCheckFullNameDialog](https://msdn.microsoft.com/library/d42632e3-6f50-cce7-80c6-cf846be1f925%28Office.15%29.aspx) method

<a name="OLSelectAPI_Conversations"> </a>

### Conversations

- [Managing Outlook Items as Conversations](https://msdn.microsoft.com/library/d91959d7-07b2-7952-8e6d-a39422d355e0%28Office.15%29.aspx)

- [Obtain and Enumerate Selected Conversations](https://msdn.microsoft.com/library/3bba1e98-b2eb-c53d-354a-bdd899b65a59%28Office.15%29.aspx)

- [Conversation](https://msdn.microsoft.com/library/2705d38a-ebc0-e5a7-208b-ffe1f5446b1b%28Office.15%29.aspx) object

- [ConversationHeader](https://msdn.microsoft.com/library/5142d5f7-55c1-4d9d-3a11-d25c8763fcb7%28Office.15%29.aspx) object

- [SimpleItems](https://msdn.microsoft.com/library/b929ae28-fe5f-607e-37b5-ed6a304d4896%28Office.15%29.aspx) object

- **ConversationID** property per item object

<a name="OLSelectAPI_Events"> </a>

### Events

- [Working with Outlook Events](https://msdn.microsoft.com/library/514f8f31-8047-2a9f-cbac-d0a23218f49c%28Office.15%29.aspx)

- [Implement a Wrapper for Inspectors and Track Item-Level Events in Each Inspector](https://msdn.microsoft.com/library/8021dd2b-c36c-492b-b281-783e85140ad8%28Office.15%29.aspx)

<a name="OLSelectAPI_InlineResponse"> </a>

### Explorer: inline response

- [Explorer.ActiveInlineResponse](https://msdn.microsoft.com/library/fc38314d-7cff-44f4-9151-6129f918a721%28Office.15%29.aspx) property

- [Explorer.ActiveInlineResponseWordEditor](https://msdn.microsoft.com/library/b9058694-ab8f-4962-ab7d-afac1704dd29%28Office.15%29.aspx) property

- [Explorer.InlineResponse](https://msdn.microsoft.com/library/5dbaddbd-e6cd-4776-b417-c67f51b12812%28Office.15%29.aspx) event

<a name="OLSelectAPI_ItemPropFieldsForms"> </a>

### Items: basic properties, fields, and forms

- [Outlook Item Objects](https://msdn.microsoft.com/library/6ea4babf-facf-4018-ef5a-4a484e55153a%28Office.15%29.aspx)

- [ItemProperties](https://msdn.microsoft.com/library/34a110ed-6617-72da-1e98-a9773c705b40%28Office.15%29.aspx) object

- [UserProperties](https://msdn.microsoft.com/library/20b49c86-d74f-9bda-382c-559af278c148%28Office.15%29.aspx) object

- [Standard Fields Overview](https://msdn.microsoft.com/library/f0d903a3-f404-8511-af3d-d4f3e30f0779%28Office.15%29.aspx)

- [Outlook Fields and Equivalent Properties](https://msdn.microsoft.com/library/acc5d2c5-f579-0a60-5676-3faa63f26c0e%28Office.15%29.aspx)

- [Custom Fields and Data Types Overview](https://msdn.microsoft.com/library/a85a7bc2-2b85-1782-04a3-0104e0df32aa%28Office.15%29.aspx)

- [Customizing Form Pages and Form Regions](https://msdn.microsoft.com/library/c8c2d080-66a8-b761-bdc0-527b209e0bd1%28Office.15%29.aspx)

<a name="OLSelectAPI_CustomizingProperties"> </a>

### Items: customizing properties

- [Properties Overview](https://msdn.microsoft.com/library/242c9e89-a0c5-ff89-0d2a-410bd42a3461%28Office.15%29.aspx)

- [Efficiently Getting and Setting Custom Properties in a Contact Folder in Outlook 2010](https://msdn.microsoft.com/library/bb49f7a6-ec0a-483a-a27e-e843c6af781b%28Office.15%29.aspx)

- [PropertyAccessor](https://msdn.microsoft.com/library/2fc91e13-703c-3ec9-9066-ffee7144306c%28Office.15%29.aspx) object

<a name="OLSelectAPI_Enumerating"> </a>

### Items: enumerating, filtering, and sorting

- [Storing Outlook Items](https://msdn.microsoft.com/library/e4a639a4-10b2-7665-9261-19d6e7707e48%28Office.15%29.aspx)

- [Default Properties Displayed in a Table Object](https://msdn.microsoft.com/library/649c64f3-2d1e-23f1-bf13-3368da79e62b%28Office.15%29.aspx)

- [Efficiently Filtering Contact Items in a Contact Folder in Outlook 2010](https://msdn.microsoft.com/library/b8dd39e7-d716-4acd-873b-d2b0faaff30d%28Office.15%29.aspx)

- [Enumerating, Searching, and Filtering Items in a Folder](https://msdn.microsoft.com/library/d786d292-7a0e-0e1a-e132-affbfde37744%28Office.15%29.aspx)

- [Sorting Items in a Folder](https://msdn.microsoft.com/library/bc3651da-cfdb-4301-4034-bb848f371e55%28Office.15%29.aspx)

- [Table](https://msdn.microsoft.com/library/0affaafd-93fe-227a-acee-e09a86cadc20%28Office.15%29.aspx) object

<a name="OLSelectAPI_ItemsFlag"> </a>

### Items: flag as tasks

See the following task-related properties in some item objects such as the [MailItem](https://msdn.microsoft.com/library/14197346-05d2-0250-fa4c-4a6b07daf25f%28Office.15%29.aspx) object:
  
- [TaskCompleteDate](https://msdn.microsoft.com/library/4bee35d4-1f1e-0b77-2021-84d4916bef8e%28Office.15%29.aspx) property

- [TaskDueDate](https://msdn.microsoft.com/library/161ed0ed-0e3f-2e4c-7e63-daad4e918dd6%28Office.15%29.aspx) property

- [TaskStartDate](https://msdn.microsoft.com/library/76b7109f-55fc-b7e2-63dc-bf7804a709f5%28Office.15%29.aspx) property

- [TaskSubject](https://msdn.microsoft.com/library/f7e4629f-ad47-b455-9fee-b5e537602a34%28Office.15%29.aspx) property

- [ToDoTaskOrdinal](https://msdn.microsoft.com/library/d1ccb01a-0792-3779-3f94-eb5195a39bb0%28Office.15%29.aspx) property

<a name="OLSelectAPI_ItemSelection"> </a>

### Items: selection in explorer

- [Selection.GetSelection](https://msdn.microsoft.com/library/c6af6665-d97d-3833-1014-5b43282bafc2%28Office.15%29.aspx) method

- [Selection.Location](https://msdn.microsoft.com/library/8a2db72a-8db0-840e-349e-5d9d22f3affb%28Office.15%29.aspx) property

<a name="OLSelectAPI_Misc"> </a>

### Miscellaneous: business cards, rules, and views

- [Customize and Share Business Cards](https://msdn.microsoft.com/library/d29fd962-ea5f-040d-e9af-e8ab70595832%28Office.15%29.aspx)

- [Managing Rules in the Outlook Object Model](https://msdn.microsoft.com/library/05ddd643-e9bd-a37d-b680-b8519960a5f6%28Office.15%29.aspx)

- [Create a Rule to Move Specific E-mails to a Folder](https://msdn.microsoft.com/library/e72fa307-8224-c2d2-1318-a18cd8e9f22f%28Office.15%29.aspx)

- [Rules](https://msdn.microsoft.com/library/dd41b4de-bf5f-5532-46c9-394a5d078bec%28Office.15%29.aspx) object

- [RuleActions](https://msdn.microsoft.com/library/82ba76cd-86a4-3372-cb51-2df1d58c8b71%28Office.15%29.aspx) object

- [RuleConditions](https://msdn.microsoft.com/library/b2af6ebf-f9f8-8106-20a3-1725c3b78174%28Office.15%29.aspx) object

- [TimeZones](https://msdn.microsoft.com/library/c68f8589-44e9-3c12-45c1-96943fa9bcb7%28Office.15%29.aspx) object

- [Outlook Views](https://msdn.microsoft.com/library/cbaa3192-6c27-26c0-ebd6-f6489c2e812e%28Office.15%29.aspx)

- [Views](https://msdn.microsoft.com/library/5dd7edc2-12a2-f4c2-d158-8053d80e8dc9%28Office.15%29.aspx) object

<a name="OLSelectAPI_Misc"> </a>

### Security

- [Security Behavior of the Outlook Object Model](https://msdn.microsoft.com/library/4aa3b7c7-5f3f-41ce-bbf3-75d8ecbd6d4f%28Office.15%29.aspx)

- [Shutdown Changes for Outlook 2010](https://msdn.microsoft.com/library/1b154d46-8d13-4c65-91e3-180b22603d03%28Office.15%29.aspx)

- [Attachment file types restricted by Outlook 2010](https://technet.microsoft.com/library/cc179163.aspx)

- [Application Shutdown Changes in Outlook 2007 SP2](https://msdn.microsoft.com/library/795a8237-7804-4da4-9d04-2bb663d300d9%28Office.15%29.aspx)

- [Code Security Changes in Outlook 2007](https://msdn.microsoft.com/library/26a9fd8f-6277-48ac-a92f-3ff46e1d883a%28Office.15%29.aspx)

<a name="OLSelectAPI_Sharing"> </a>

### Sharing

- [Sharing Calendars](https://msdn.microsoft.com/library/03e0b693-5446-ca62-f868-69a583087966%28Office.15%29.aspx)

- [Sharing Online Calendars, RSS Feeds, Microsoft SharePoint Foundation Folders, and Exchange Folders](https://msdn.microsoft.com/library/e579e026-bd10-37bb-eb3e-5c9f042fa0fa%28Office.15%29.aspx)

- [SharingItem](https://msdn.microsoft.com/library/63dd3451-44f3-7cc4-c6e2-7dad5835a7d2%28Office.15%29.aspx) object

<a name="OLSelectAPI_Folders"> </a>

### Solutions: solution-specific folders

- [Programming the Outlook 2010 Solutions Module](https://msdn.microsoft.com/library/5989a3da-2f2a-4abd-87b0-cc0e1560dd59%28Office.15%29.aspx)

- [SolutionsModule](https://msdn.microsoft.com/library/4597765e-a95d-bf07-2ac4-103218ebc696%28Office.15%29.aspx) object

<a name="OLSelectAPI_StoringData"> </a>

### Solutions: storing data

- [Storing Data for Solutions](https://msdn.microsoft.com/library/58e69983-5718-4dde-64fc-858abd80c9e5%28Office.15%29.aspx)

- [StorageItem](https://msdn.microsoft.com/library/41776bc3-b838-2755-fd6b-3b5012fb9ae5%28Office.15%29.aspx) object

<a name="OLSelectAPI_CustomFormRegions"> </a>

### User interface: customizing form regions

- [Customizing Form Pages and Form Regions](https://msdn.microsoft.com/library/c8c2d080-66a8-b761-bdc0-527b209e0bd1%28Office.15%29.aspx)

- [Form Regions](https://msdn.microsoft.com/library/66e80f83-60db-e3b1-47e9-097f855f6512%28Office.15%29.aspx)

- [Create a Form Region](https://msdn.microsoft.com/library/695b95a5-c795-cb4a-8d35-ba12b0007b1f%28Office.15%29.aspx)

- [Walkthrough: Add a Form Region to an Existing Page on a Form](https://msdn.microsoft.com/library/3c988dac-f171-966d-cf9a-17139353d604%28Office.15%29.aspx)

- [Building an Outlook 2007 Form Region with a Managed Add-In](https://msdn.microsoft.com/library/cc8503c2-9e17-4718-a757-9f0b7d42f0ee%28Office.15%29.aspx)

- [Implementing a Form Region to Display Email Headers in Outlook 2010](https://msdn.microsoft.com/library/243a4e64-d4ea-4cfc-871e-af19d622fb1b%28Office.15%29.aspx)

- [FormRegion](https://msdn.microsoft.com/library/3a0b83eb-4076-9cb3-86a9-68f9e44df89f%28Office.15%29.aspx) object

- [FormRegionStartup](https://msdn.microsoft.com/library/948ea6b7-2962-57e7-618d-fa0977b65651%28Office.15%29.aspx) object

<a name="OLSelectAPI_CustomizeTheOutlookInterface"> </a>

### User interface: customizing since Outlook 2007

- [Overview of Customizing the Ribbon](https://msdn.microsoft.com/library/ee49751d-9eae-357c-5fa9-0b2dd4ff0890%28Office.15%29.aspx)

- [Customizing the Ribbon in Outlook 2007](https://msdn.microsoft.com/library/946e97ea-f556-4e84-8fac-01cd9214e170%28Office.15%29.aspx)

- [Developing Interfaces in Outlook 2007](https://msdn.microsoft.com/library/e50257a3-98dd-498f-b9ff-dbfb6705a95a%28Office.15%29.aspx)

- [Custom Task Panes Overview](https://msdn.microsoft.com/library/9a415109-5333-433e-95c6-3d59ce9c4d02.aspx)

- [Targeting User Interface Solutions to the 2007 and 2010 Releases of Microsoft Office](https://msdn.microsoft.com/library/98726fb2-5d5c-44be-80c3-cfef926471f9%28Office.15%29.aspx)

- [Customizing the Navigation Pane](https://msdn.microsoft.com/library/426c3d1c-13b5-cac5-702d-87dfe71f2478%28Office.15%29.aspx)

- [Outlook View Control Object Model Reference](https://msdn.microsoft.com/library/36fa9303-2135-6fcc-b93c-05eef37af3ec%28Office.15%29.aspx)

- [IDTExtensibility2](https://msdn.microsoft.com/library/Extensibility.IDTExtensibility2.aspx) interface

- [IRibbonExtensibility](https://msdn.microsoft.com/library/b27a7576-b6f5-031e-e307-78ef5f8507e0%28Office.15%29.aspx) object

- [NavigationPane](https://msdn.microsoft.com/library/b6538c72-6115-99fc-c926-e0532a747823%28Office.15%29.aspx) object

<a name="OLSelectAPI_CustomizingUIOutlook2010"> </a>

### User interface: customizing since Outlook 2010

- [Extending the User Interface in Outlook 2010](https://msdn.microsoft.com/library/00b504b0-e897-43b9-8615-44276166823f%28Office.15%29.aspx)

- [Office Fluent User Interface Extensibility for Outlook](https://msdn.microsoft.com/library/8496c52e-1f9d-16ef-2fd8-c1bca1a96816%28Office.15%29.aspx)

- [Programming the Outlook 2010 Solutions Module](https://msdn.microsoft.com/library/5989a3da-2f2a-4abd-87b0-cc0e1560dd59%28Office.15%29.aspx)

- [Customizing the Context Menu of a Contact Card in Outlook 2010](https://msdn.microsoft.com/library/8513c8de-15d7-4396-8ced-f5f56f4cd9b3%28Office.15%29.aspx)

- [IRibbonControl](https://msdn.microsoft.com/library/63aef709-e1d3-b1a6-76af-b568ad0e69ae%28Office.15%29.aspx) object

- [IRibbonExtensibility](https://msdn.microsoft.com/library/b27a7576-b6f5-031e-e307-78ef5f8507e0%28Office.15%29.aspx) object

- [IRibbonUI](https://msdn.microsoft.com/library/d323aa21-de74-e821-c914-db71ef3b9c5e%28Office.15%29.aspx) object

<a name="OLSelectAPI_CustomizingUIOutlook2010"> </a>

### User interface: solutions-specific folders

- [Programming the Outlook 2010 Solutions Module](https://msdn.microsoft.com/library/5989a3da-2f2a-4abd-87b0-cc0e1560dd59%28Office.15%29.aspx)

- [Adding Solution-Specific Folders to the Solutions Module in Outlook 2010](https://msdn.microsoft.com/library/9709af57-1577-4497-8c9c-3d239353e2ed%28Office.15%29.aspx)

- [SolutionsModule](https://msdn.microsoft.com/library/4597765e-a95d-bf07-2ac4-103218ebc696%28Office.15%29.aspx) object

<a name="OLSelectAPI_AdditionalResourcesAuxAPIs"> </a>

## See also: Auxiliary APIs

The following resources provide more information about the Outlook auxiliary APIs.
  
### Account management

- [About the Account Management API](auxiliary/about-the-account-management-api.md)

- [Account management API reference](auxiliary/account-management-api-reference.md)

- [About anti-spam settings](auxiliary/about-anti-spam-settings.md)

### Categorizing items

- [HrProcessConvActionForSentItem](auxiliary/hrprocessconvactionforsentitem.md)

### Contact pictures

- [Specify whether to display a contact's picture in Outlook (Outlook Auxiliary Reference)](https://msdn.microsoft.com/library/office/gg262879.aspx)

### Data degradation

- [About the Data Degradation Layer API](auxiliary/about-the-data-degradation-layer-api.md)

- [Data degradation layer API reference](auxiliary/data-degradation-layer-api-reference.md)

### Free/busy status

- [About the Free/Busy API](auxiliary/about-the-free-busy-api.md)

- [Use relative time to access free/busy data](auxiliary/how-to-use-relative-time-to-access-free-busy-data.md)

- [Free/busy API reference](auxiliary/free-busy-api-reference.md)

### Item currency

- [Determine whether an Outlook item has been modified but not saved (Outlook Auxiliary Reference)](auxiliary/how-to-determine-if-outlook-item-has-been-modified-but-not-saved.md)

### Rebase calendars

- [About rebasing calendars programmatically for Daylight Saving Time](auxiliary/about-rebasing-calendars-programmatically-for-daylight-saving-time.md)

- [About persisting TZDEFINITION to a stream to commit to a binary property](auxiliary/about-persisting-tzdefinition-to-a-stream-to-commit-to-a-binary-property.md)

- [Parse a stream from a binary property to read the TZDEFINITION structure](auxiliary/how-to-parse-stream-from-binary-property-to-read-tzdefinition-structure.md)

- [Parse a stream from a binary property to read the TZREG structure](auxiliary/how-to-parse-a-stream-from-a-binary-property-to-read-the-tzreg-structure.md)

- [Read time zone properties from an appointment](auxiliary/how-to-read-time-zone-properties-from-an-appointment.md)

<a name="OLSelectAPI_AdditionalResourcesRefCode"> </a>

## See also: Primary references, resources, and code samples

The following resources provide more information about the primary Outlook references, resources, and code samples.
  
### Major references and resources

- [Office Add-ins](/office/dev/add-ins/overview/office-add-ins)
- [Outlook 2013 developer reference](/office/vba/api/overview/outlook)
- [Outlook 2010 Primary Interop Assembly Reference](./pia/welcome-to-the-outlook-primary-interop-assembly-reference.md)
- [Outlook MAPI Reference](./mapi/outlook-mapi-reference.md)
- [Outlook 2013 Auxiliary Reference](auxiliary/welcome-to-the-outlook-auxiliary-reference.md)
- [Outlook Social Connector provider reference](social-connector/outlook-social-connector-provider-reference.md)
- [Extending the Weather Bar in Outlook](weather/extending-the-weather-bar-in-outlook.md)
- [Outlook Weather Information XML Schema](weather/outlook-weather-information-xml-schema.md)
- [Outlook Weather Location XML Schema](weather/outlook-weather-location-xml-schema.md)
- [What's New in XML Schemas for Outlook 2010](/previous-versions/office/developer/office-2010/ff697175(v=office.14))
- [Outlook 2010: XML Schema Reference](/office/client-developer/outlook/social-connector/outlook-social-connector-provider-xml-schema)
- [Developing Outlook 2010 Solutions for 32-Bit and 64-Bit Systems](/previous-versions/office/developer/office-2010/gg549122(v=office.14))

### Code samples

- [Mail apps samples](https://developer.microsoft.com/microsoft-365/gallery/?filterBy=Outlook,Samples)
- Object model code samples: [How Do I ... in Outlook](/office/vba/outlook/concepts/miscellaneous/how-do-i-outlook-vba-reference)  
- PIA code samples: [How Do I... (Outlook Reference)](./pia/how-do-i-outlook-2013-pia-reference.md)  
- [MAPI Samples](./mapi/mapi-samples.md)
- Auxiliary API code samples: [Sample tasks](auxiliary/sample-tasks.md)
