---
title: "New in Outlook for developers"
ms.author: soliver
author: soliver
manager: soliver
ms.date: 9/17/2015
ms.audience: Developer
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4c6d44d2-238b-42d8-896b-51d513c9e14c

description: "This document provides a top-level view of the additions and enhancements for developers in Microsoft Outlook 2013, including mail apps, third party weather data services for the Weather Bar, and inline response. The document also describes changes to the Outlook Social Connector, Office Mobile Service, support for Outlook 2013 coexisting with a previous version of Outlook, and new performance criteria for add-ins. For developers who are ready to get a jump start on the Outlook platform, this document provides you with sufficient information to begin coding against Outlook 2013."
---

# New in Outlook for developers

This document provides a top-level view of the additions and enhancements for developers in Microsoft Outlook 2013, including mail apps, third party weather data services for the Weather Bar, and inline response. The document also describes changes to the Outlook Social Connector, Office Mobile Service, support for Outlook 2013 coexisting with a previous version of Outlook, and new performance criteria for add-ins. For developers who are ready to get a jump start on the Outlook platform, this document provides you with sufficient information to begin coding against Outlook 2013.
  
## Introduction
<a name="ol15WhatsNew_Introduction"> </a>

Outlook 2013 provide programmability support for a number of new features. Office Add-ins is a new platform that allows developers to use web-based tools such as HTML and JavaScript to build apps that surface within the Outlook Reading Pane or inspector window. Unlike traditional COM Add-ins, apps don't require that you install or update a DLL on the user's computer. When a mail app is initialized by the user, the mail app uses the Office Add-ins JavaScript object model to provide contextual information about the selected message in the Outlook rich client and Outlook Web App. Your app runs on your web server and any changes you make in your web content will be immediately reflected in your app running on an Outlook client. 
  
In addition to apps, there is extensibility support for the new Weather Bar, and changes to how Outlook 2013 supports Outlook Social Connector provider extensibility and Office Mobile Services. Other features such as Outlook coexistence and add-in performance monitoring are not related directly to any object model, but they will influence the way that you architect and build your solution.
  
The following are the important changes for developers in Outlook 2013:
  
- Mail apps
    
- Custom weather service for the Weather Bar
    
- Inline response and other Outlook object model enhancements
    
- Outlook Social Connector enhancements
    
- Discontinuing support for Office Mobile Service
    
- Coexistence with previous Outlook versions
    
- Performance criteria for keeping add-ins enabled
    
> [!NOTE]
> Objects, properties, methods, and events depicted in this article might change in the RTM release of Outlook 2013. Additional object model features might also be introduced before the RTM release of Outlook 2013. Be sure to obtain the RTM version of Outlook 2013 to test your code changes before you release your solution. 
  
## Mail apps
<a name="ol15WhatsNew_MailApps"> </a>

Office Add-ins are a new feature that lets you incorporate web services directly into Outlook without having to write and deploy a traditional Outlook add-in. In Outlook 2013, mail apps provide rich and compelling experiences to users in Outlook or Outlook Web App using a single code base. A mail app displays an app pane adjacent to the Outlook Reading Pane or an inspector to provide web content appropriate for the displayed message or appointment. Apps are created using ubiquitous web technologies such as HTML and JavaScript. Mail apps do require Exchange 2013 and are not available for users with accounts on versions of Exchange previous to Exchange 2013 or with POP3 or IMAP accounts.
  
The following sections briefly describe the mail apps architecture, activation rules, and security model. These sections are not meant as a comprehensive technical reference. Please consult [Office Add-ins](http://msdn.microsoft.com/library/1e123201-6e70-45c1-a48c-d5b955896ddb%28Office.15%29.aspx) for details on the manifest schema, rule conditions, built-in entities and custom regular expressions, the JavaScript Object Model, and submitting a mail app to the Office Store. 
  
### Architecture

The architecture of the mail apps platform is beautiful in its simplicity. An Exchange client such as the Outlook rich client or Outlook Web App downloads mail app manifests from the Exchange server. The XML manifest specifies a set of rules that are run on the client and determine whether the app is activated when a user selects an email message or appointment. If the activation rules are satisfied, then the app button will appear on the app bar. For example, in Figure 1 you see that both the **Bing Maps** and **Action Item** mail apps have activated based on the content of the selected email message and appear on the app bar. 
  
**Figure 1. Mail app showing context sensitive Bing map in Outlook**

![Bing Map mail app in Outlook](media/off15appsdk_BingMapMailAppScreenshot.jpg)
  
A mail app is said to be activated when its app button appears on the app bar. Once the user selects the app button, the app pane appears and runs an [Initialize](http://msdn.microsoft.com/library/727adf79-a0b5-48d2-99c7-6642c2c334fc%28Office.15%29.aspx) event handler in the JavaScript code of your web page hosted on your web server. Figure 2 describes the process that takes place when an Outlook client starts and the user selects an item in Outlook. 
  
**Figure 2. Mail app architecture and startup process**

![Flow of events when starting Outlook mail app](media/olowawecon15_LoadingDOMAgaveRuntime.png)
  
The JavaScript code of a mail app can access properties of the selected message or appointment item. Depending on the permission requested by the app, the app can also access custom properties, enumerate entities (such as addresses or meeting suggestions) or regular expression matches, and make Exchange Web Service (EWS) calls. 
  
### Activation Rules

Activation rules control when a mail app is activated in the user interface of an Outlook client. Rules are defined in the XML manifest and are applied by the rules evaluation engine to the selected item in the Reading Pane or an inspector window. If the rules evaluate to true, the app button is visible on the app bar. Note the following about rules:
  
- Multiple rules can be combined for complex activation needs.
    
    Apply logical **And** or **Or** operators. 
    
    Rules can be defined using regular expressions. 
    
    Rules can access known entities such as phone numbers, URLs, and street addresses.
    
Rule types are as follows.
  
|**Type of rule**|**Description**|
|:-----|:-----|
|[ItemIs](http://msdn.microsoft.com/library/f7dac4a3-1574-9671-1eda-47f092390669%28Office.15%29.aspx) <br/> |A rule to check if the item is a specific type (appointment, message or custom message class). For example:  <br/> ```XML<Rule xsi:type="ItemIs" ItemType="Message" />```|
|[ItemHasKnownEntity](http://msdn.microsoft.com/library/87e10fd2-eab4-c8aa-bec3-dff92d004d39%28Office.15%29.aspx) <br/> |A rule to check if the item has a specific entity. For example:  <br/> ```XML<Rule xsi:type="ItemHasKnownEntity" EntityType="Address" />```|
|[ItemHasRegularExpressionMatch](http://msdn.microsoft.com/library/bfb726cd-81b0-a8d5-644f-2ca90a5273fc%28Office.15%29.aspx) <br/> |A rule to check if there are matches to the specified regular expression.  <br/> |
|[RuleCollection](http://msdn.microsoft.com/library/926249ab-2d2f-39f5-1d73-fab1c989966f%28Office.15%29.aspx) <br/> |Defines a rule composed of multiple rules (combined using **And** or **Or**).  <br/> |
   
Note that rules can recognize known entities or custom regular expressions that you define in the app manifest. 
  
What are known entities? Known entities are parsed by the Exchange server during message transport and stamped on the message for use by the rules evaluation engine. The following table lists some known entities that you can use to create activation rules.
  
|**Type of known entity**|**Activation condition**|
|:-----|:-----|
|**Address** <br/> |United States street addresses. For example:  <br/> 1 Microsoft Way, Redmond, WA 07722  <br/> |
|**Contact** <br/> |A personal name related to other entities. For example:  <br/> Steve Ballmer, Microsoft, 1 Microsoft Way, Redmond, WA 98052  <br/> |
|**EmailAddress** <br/> |Any SMTP email address. For example:  <br/> someone@contoso.com  <br/> |
|**MeetingSuggestion** <br/> |A reference to an event or meeting. For example:  <br/> Let's meet next Tuesday for lunch.  <br/> |
|**PhoneNumber** <br/> |United States telephone numbers. For example:  <br/> (425) 555-1212  <br/> |
|**TaskSuggestion** <br/> |Actionable sentences in an email. For example:  <br/> Please install Office 2013 on my computer.  <br/> |
|**Url** <br/> |A file name or web address. For example:  <br/> http://microsoft.com  <br/> |
   
### Security model

Your mailbox contains your private information. In a corporate setting, your mailbox contains privileged communications with your customers, suppliers, and your fellow employees. Outlook safeguards that information and ensures that mail apps keep that information secure. When a user acquires a mail app, the user must grant the permission level requested by the app in its manifest. If the user does not grant permission, the app is not installed into the user's Exchange mailbox. Mail apps use a three-tiered security model. What an app can do depends on the security grant by the end user or administrator, based on the permission requested in the app manifest. Note that apps that require the **read/write mailbox** permission cannot be installed by an end user. Apps that request the **read/write mailbox** permission must be installed by a system administrator. 
  
**Figure 3. Three-tiered security model for mail apps**

![3-tier permission model for user, developer, admin](media/olowa15wecon_Permissions.png)
  
Figure 3 and the table below describe the 3 permission levels. Note that the default permission, **restricted**, restricts an app from accessing personally identifiable information (PII) from the currently selected message. If the user grants an elevated level of permission such as **read item**, the app can obtain information such as the sender or recipients of the message. **Read/write mailbox** permission allows the app to call a subset of powerful EWS functions including the ability to create or modify items in a user's mailbox. 
  
|**Actor**|**Permission in manifest**|**Access**|
|:-----|:-----|:-----|
|End users installing low trust mail apps  <br/> |**Restricted** <br/> |Subset of known entities from message: **Address**, **PhoneNumber**, **Url** <br/> |
|End users installing low trust mail apps  <br/> |**ReadItem** <br/> | All known entities from message: **Address**, **Contact**, **EmailAddress**, **MeetingSuggestion**, **PhoneNumber**, **TaskSuggestion**, **Url** <br/>  Custom regular expression matches from message body.  <br/>  JSOM:  <br/>  Recipients/sender/attendees  <br/>  Subject/location  <br/>  Single sign on  <br/>  User profile  <br/> [GetUserIdentityTokenAsync](http://msdn.microsoft.com/library/c658518b-6867-41a0-99cf-810303e4c539%28Office.15%29.aspx) method  <br/> |
|Exchange administrators installing high trust mail apps  <br/> |**ReadWriteMailbox** <br/> |**ReadItem** access and the following:  <br/>  JSOM: [makeEWSRequestAsync](http://msdn.microsoft.com/library/2ec380e0-4a67-4146-92a6-6a39f65dc6f2%28Office.15%29.aspx) method  <br/>  EWS: subset of EWS APIs  <br/> |
   
## Custom weather data service for the Weather Bar
<a name="ol15WhatsNew_WeatherService"> </a>

The new Weather Bar in Outlook 2013 uses MSN Weather to provide weather forecasts for user-selected locations. Third party weather data services can plug into Outlook to provide similar weather forecasts. Figure 4 shows the Weather Bar displaying a weather forecast for New York.
  
**Figure 4. The Weather Bar displaying a weather forecast for New York**

![Weather Bar showing forecast for New York.](media/ol15_WeatherBar_fig1.jpg)
  
To plug into the Outlook Weather Bar, a weather data service can implement a web service that supports a simple 2-part protocol:
  
1. The weather data service supports a base URL to a web service, for example, http://service.contoso.com/data.aspx.
    
2. Part 1: The web service allows Outlook to append the following parameters to the base URL, to request a location code that corresponds to the user-selected location:
    
  - outputview=search, which indicates that the request is a location search.
    
  - weasearchstr= _city_, where  _city_ indicates the user-selected location for weather information. 
    
  - culture= _LCID_, where  _LCID_ indicates the culture of the version of Office installed for the user. The value is defined in [[RFC4646] Tags for Identifying Languages](http://www.ietf.org/rfc/rfc4646.txt)
    
  - src=outlook, which indicates that Outlook is the client application requesting the service.
    
    The web service response must conform to the [Outlook Weather Location XML Schema](outlook-weather-location-xml-schema.md).
    
    Figure 5 summarizes part 1 of the protocol to request and respond with a location code for the user-selected location.
    
   **Figure 5. Web service request and response for a location code**

     ![Weather location request and response](media/ol15_WeatherBar_Fig02.gif)
  
3. Part 2: The web service also supports Outlook to append the following parameters, to request forecast information for the location code obtained from Part 1:
    
  - wealocations= _code_, where  _code_ is the location obtained from Part 1. 
    
  - weadegreetype= _degreetype_, where  _degreetype_ can be c for metric or f for imperial units for temperature. 
    
  - culture= _LCID_, where  _LCID_ indicates the culture of the version of Office, similar to that in Part 1. 
    
  - src=outlook, which indicates that Outlook is the client application requesting the service, similar to Part 1.
    
    The web service response must conform to the [Outlook Weather Information XML Schema](outlook-weather-information-xml-schema.md).
    
    Figure 6 summarizes part 2 of the protocol to request and respond for weather data for the user-selected location.
    
   **Figure 6. Web service request and response for weather information**

     ![Weather information request and response](media/ol15_WeatherBar_Fig03.gif)
  
For more information, see [Extending the Weather Bar in Outlook](extending-the-weather-bar-in-outlook.md).
  
## Outlook Object Model changes
<a name="ol15WhatsNew_OMChanges"> </a>

New objects, properties, methods, events, and enumeration values have been added to the Outlook object model to provide programmability support for new Outlook 2013 features. Additionally, object model improvements address frequent developer requests for changes to the Outlook platform.
  
### Enhancements to existing Outlook objects

The following table lists enhancements to objects, collections, and enumerations that were available in previous versions of Outlook. Only new methods, properties, events, and enumeration values are listed in the **New members** column. 
  
 **Table 1. Outlook object model enhancements**
  
|**Object or enumeration**|**New members**|
|:-----|:-----|
|[AppointmentItem](http://msdn.microsoft.com/library/204a409d-654e-27aa-643a-8344c631b82d%28Office.15%29.aspx) <br/> |[ReadComplete](http://msdn.microsoft.com/library/749e8d58-c15c-0b63-5486-cc2aa2190638%28Office.15%29.aspx) event  <br/> |
|[ContactItem](http://msdn.microsoft.com/library/8e32093c-a678-f1fd-3f35-c2d8994d166f%28Office.15%29.aspx) <br/> |[ShowCheckAddressDialog](http://msdn.microsoft.com/library/773a1a3c-1247-fd48-399a-728766e56570%28Office.15%29.aspx) method  <br/> [ShowCheckFullNameDialog](http://msdn.microsoft.com/library/0135661c-ed4d-406d-5771-dbcaf160ffc4%28Office.15%29.aspx) method  <br/> [ReadComplete](http://msdn.microsoft.com/library/5aa9c67e-579f-5519-ed38-c80009cf506b%28Office.15%29.aspx) event  <br/> |
|[DistListItem](http://msdn.microsoft.com/library/027c3986-abff-d9b1-ecc2-26d60805e952%28Office.15%29.aspx) <br/> |[ReadComplete ](http://msdn.microsoft.com/library/5aa9c67e-579f-5519-ed38-c80009cf506b%28Office.15%29.aspx) event  <br/> |
|[DocumentItem](http://msdn.microsoft.com/library/7b0a6af0-6632-3ff6-841f-5b081d0d68d8%28Office.15%29.aspx) <br/> |[ReadComplete](http://msdn.microsoft.com/library/5a47b0f4-dfa9-9cf6-8efa-7ab45c1f90d7%28Office.15%29.aspx) event  <br/> |
|[Explorer](http://msdn.microsoft.com/library/026591e5-049f-503a-4166-34e6dbc225fb%28Office.15%29.aspx) <br/> |[ActiveInlineResponse](http://msdn.microsoft.com/library/fc38314d-7cff-44f4-9151-6129f918a721%28Office.15%29.aspx) property  <br/> [ActiveInlineResponseWordEditor](http://msdn.microsoft.com/library/b9058694-ab8f-4962-ab7d-afac1704dd29%28Office.15%29.aspx) property  <br/> [InlineResponse](http://msdn.microsoft.com/library/5dbaddbd-e6cd-4776-b417-c67f51b12812%28Office.15%29.aspx) event  <br/> [InlineResponseClose](http://msdn.microsoft.com/library/ff3f3286-995a-409c-aca5-706290e26252%28Office.15%29.aspx) event  <br/> |
|[JournalItem](http://msdn.microsoft.com/library/6e850295-39f9-47b8-e866-9622e9958c69%28Office.15%29.aspx) <br/> |[ReadComplete](http://msdn.microsoft.com/library/63f74eb2-99bc-2ce7-c412-c28eba80e75c%28Office.15%29.aspx) event  <br/> |
|[MailItem](http://msdn.microsoft.com/library/14197346-05d2-0250-fa4c-4a6b07daf25f%28Office.15%29.aspx) <br/> |[ReadComplete](http://msdn.microsoft.com/library/39bba654-0683-95a4-9092-3c0ecbbf9104%28Office.15%29.aspx) event  <br/> |
|[MeetingItem](http://msdn.microsoft.com/library/b75730f5-b395-3d66-5acd-b64fd8fcd78f%28Office.15%29.aspx) <br/> |[ReadComplete](http://msdn.microsoft.com/library/17ef8085-38ac-7e32-7704-54a2f2224e87%28Office.15%29.aspx) event  <br/> |
|[OlAccountType](http://msdn.microsoft.com/library/8aeafc50-3f97-8d28-7fd9-a9d8e1eafc4c%28Office.15%29.aspx) <br/> |**olEas** enumeration value  <br/> |
|[OlBusyStatus](http://msdn.microsoft.com/library/4391ccb4-a035-30d1-9693-61b83050b31f%28Office.15%29.aspx) <br/> |**olWorkingElsewhere** enumeration value  <br/> |
|[OlObjectClass](http://msdn.microsoft.com/library/33d724b3-df3c-2a7f-a80f-93b66d96f588%28Office.15%29.aspx) <br/> |**olClassPeopleView** enumeration value  <br/> |
|[OlSearchScope](http://msdn.microsoft.com/library/13d19f0e-88f3-07d8-b048-87fc586e2e0c%28Office.15%29.aspx) <br/> |**olSearchScopeCurrentStore** enumeration value  <br/> |
|[OlViewType](http://msdn.microsoft.com/library/f2fec9d0-55c2-0991-0e1b-4dd653fdf09d%28Office.15%29.aspx) <br/> |**olPeopleView** enumeration value  <br/> |
|[PostItem](http://msdn.microsoft.com/library/de44065d-4e93-315a-279f-7b92f09c0465%28Office.15%29.aspx) <br/> |[ReadComplete](http://msdn.microsoft.com/library/7b7a8d3d-95ef-fdaa-ae13-aae5dd33a9a4%28Office.15%29.aspx) event  <br/> |
|[RemoteItem](http://msdn.microsoft.com/library/6302aaff-cdcf-4d86-60f1-4bed15540d9f%28Office.15%29.aspx) <br/> |[ReadComplete](http://msdn.microsoft.com/library/208867c1-b6dc-4ce8-e25a-13a8f6c686ca%28Office.15%29.aspx) event  <br/> |
|[ReportItem](http://msdn.microsoft.com/library/16ebe336-72e0-42f6-99d3-edecc3ea284d%28Office.15%29.aspx) <br/> |[ReadComplete](http://msdn.microsoft.com/library/f73cb164-0c88-f439-6474-a4502b6731ea%28Office.15%29.aspx) event  <br/> |
|[SharingItem](http://msdn.microsoft.com/library/63dd3451-44f3-7cc4-c6e2-7dad5835a7d2%28Office.15%29.aspx) <br/> |[ReadComplete](http://msdn.microsoft.com/library/2ba4a409-74ab-9514-552c-c62a78457b8e%28Office.15%29.aspx) event  <br/> |
|[TaskItem](http://msdn.microsoft.com/library/5df8cfa5-5460-a5a1-a130-ba5bca1a0091%28Office.15%29.aspx) <br/> |[ReadComplete](http://msdn.microsoft.com/library/0706a4b9-1035-bdf9-a48d-8d039a2001fa%28Office.15%29.aspx) event  <br/> |
|[TaskRequestAcceptItem](http://msdn.microsoft.com/library/a2905f72-0a67-b07d-7f85-84fe4de17c25%28Office.15%29.aspx) <br/> |[ReadComplete](http://msdn.microsoft.com/library/7f161f3d-c915-8355-977b-03b1d15ac8b5%28Office.15%29.aspx) event  <br/> |
|[TaskRequestDeclineItem](http://msdn.microsoft.com/library/e842c7c0-7943-9219-329b-30b892ab99b0%28Office.15%29.aspx) <br/> |[ReadComplete](http://msdn.microsoft.com/library/7f161f3d-c915-8355-977b-03b1d15ac8b5%28Office.15%29.aspx) event  <br/> |
|[TaskRequestItem](http://msdn.microsoft.com/library/2908a28a-634c-e786-aa53-f3e32038b727%28Office.15%29.aspx) <br/> |[ReadComplete](http://msdn.microsoft.com/library/2f92c2d2-742c-42b0-47c3-b9694169d8db%28Office.15%29.aspx) event  <br/> |
|[TaskRequestUpdateItem](http://msdn.microsoft.com/library/5bc407fe-b3f6-3e46-8b91-e2ed96292cec%28Office.15%29.aspx) <br/> |[ReadComplete](http://msdn.microsoft.com/library/4cb71722-432b-7a73-02f3-965b6f8d56ad%28Office.15%29.aspx) event  <br/> |
   
### New objects

The following table lists the new objects introduced in Outlook 2013. All object members are listed in the **Properties** and **Methods** column. 
  
 **Table 2. Outlook object model additions**
  
|**Object**|**Properties**|**Methods**|
|:-----|:-----|:-----|
|[PeopleView](http://msdn.microsoft.com/library/7b569709-5da8-a950-a0fb-9d64b520a21b%28Office.15%29.aspx) <br/> |[Application](http://msdn.microsoft.com/library/3f65f994-4426-419e-a82d-1cf1d735d933%28Office.15%29.aspx) <br/> |[Apply](http://msdn.microsoft.com/library/0de7dba9-8506-880e-6f5d-7020ed954a03%28Office.15%29.aspx) <br/> |
||[Class](http://msdn.microsoft.com/library/acc63318-2ffd-2baa-f82e-2618a83cbe20%28Office.15%29.aspx) <br/> |[Copy](http://msdn.microsoft.com/library/e1e49cbb-46c3-7399-f4e8-480041c175c3%28Office.15%29.aspx) <br/> |
||[Filter](http://msdn.microsoft.com/library/2a704054-1a71-d819-2ce2-a7c9d1df47bf%28Office.15%29.aspx) <br/> |[Delete](http://msdn.microsoft.com/library/1acbfeb6-672c-899f-c02c-c7fa818af8a4%28Office.15%29.aspx) <br/> |
||[Language](http://msdn.microsoft.com/library/17c63a8e-b037-f006-68c5-851a138b9ab8%28Office.15%29.aspx) <br/> |[GoToDate](http://msdn.microsoft.com/library/a080e83b-ff37-2a3b-3ba7-75d6083417c2%28Office.15%29.aspx) <br/> |
||[LockUserChanges](http://msdn.microsoft.com/library/28249708-e88f-a95e-0618-1361630b57be%28Office.15%29.aspx) <br/> |[Reset](http://msdn.microsoft.com/library/fd3c5f34-b74a-beaa-8132-f9e3a0d517bc%28Office.15%29.aspx) <br/> |
||[Name](http://msdn.microsoft.com/library/d826eaaa-afb9-fd60-b044-6a901d08ead0%28Office.15%29.aspx) <br/> |[Save](http://msdn.microsoft.com/library/a75b144a-794e-8a7b-16d8-1afdae358680%28Office.15%29.aspx) <br/> |
||[Parent](http://msdn.microsoft.com/library/a29ed11e-24bc-471e-aee9-c910304e2c85%28Office.15%29.aspx) <br/> ||
||[SaveOption](http://msdn.microsoft.com/library/9188ae0d-ef84-1f5c-43e2-8d28cf31782d%28Office.15%29.aspx) <br/> ||
||[Session](http://msdn.microsoft.com/library/489c4789-3131-08b1-a9c3-b7faf2ad7524%28Office.15%29.aspx) <br/> ||
||[SortFields](http://msdn.microsoft.com/library/825e8a25-8fca-5159-3a90-8f4b201fae60%28Office.15%29.aspx) <br/> ||
||[Standard](http://msdn.microsoft.com/library/5e4b771f-52b2-48a9-8044-4cb7b5343645%28Office.15%29.aspx) <br/> ||
||[ViewType](http://msdn.microsoft.com/library/8063a934-fa31-f71f-ec29-812c27ac5952%28Office.15%29.aspx) <br/> ||
||[XML](http://msdn.microsoft.com/library/3a7f3263-1c23-5b08-a566-cc591aa5f983%28Office.15%29.aspx) <br/> ||
   
### Deprecated objects and members

The following are the main deprecations in the Outlook object model in this release:
  
- Support for the To-Do Bar
    
    Because the To-Do Bar is no longer supported in the Outlook 2013 user interface, attempting to use [Explorer.ShowPane(olToDoBar)](http://msdn.microsoft.com/library/3d2c9dd5-b660-e160-36db-73c23f95a7a2%28Office.15%29.aspx) to display or hide the To-Do Bar returns an error. You should modify any existing code to handle the error or avoid calling **ShowPane** with the **olToDoBar** constant for code that runs in Outlook 2013. 
    
- Support for contact linking
    
    The contact linking feature and its object model support (through the **Link** and **Links** objects) has been deprecated. The **Links** property for each item object now returns **Null** ( **Nothing** in Visual Basic), and you should modify any existing code to handle this behavior. 
    
- The **MobileItem** object. See the section [Discontinuing support for Office Mobile Service](new-in-outlook-for-developers.md#ol15WhatsNew_OMS) for more information. 
    
The following table lists the objects, members, and enumeration values deprecated in Outlook 2013. Only deprecated object members and enumeration values are listed in the **Deprecated members** column. Note that while deprecated members are hidden in the Visual Basic object browser, deprecated enumerations or enumeration values are not hidden, but nonetheless should no longer be used in your code. 
  
|**Object, collection, or enumeration**|**Deprecated member or enumeration value**|
|:-----|:-----|
|**AppointmentItem** <br/> |**Links** property  <br/> |
|[CalendarView](http://msdn.microsoft.com/library/37e078b9-9fc6-5894-b043-06d7257666a8%28Office.15%29.aspx) <br/> |**DayWeekFont** property  <br/> **DayWeekTimeFont** property  <br/> **MonthFont** property  <br/> |
|**ContactItem** <br/> |**Links** property  <br/> |
|**DistListItem** <br/> |**Links** property  <br/> |
|**DocumentItem** <br/> |**Links** property  <br/> |
|[Exception](http://msdn.microsoft.com/library/010552b0-9ba6-c81b-1e3a-fd6a681e5163%28Office.15%29.aspx) <br/> |**ItemProperties** property  <br/> |
|**JournalItem** <br/> |**Links** property  <br/> |
|**Link** <br/> |**ApplicationClass** property  <br/> **Item** property  <br/> **Name** property  <br/> **Parent** property  <br/> **Session** property  <br/> **Type** property  <br/> |
|**Links** <br/> |**ApplicationClass** property  <br/> **Count** property  <br/> **Parent** property  <br/> **Session** property  <br/> **AddItem** method  <br/> **Remove** method  <br/> |
|**MailItem** <br/> |**Links** property  <br/> |
|**MeetingItem** <br/> |**Links** property  <br/> |
|**MobileItem** <br/> |Properties  <br/> **Actions** property  <br/> **Application** property  <br/> **Attachments** property  <br/> **BillingInformation** property  <br/> **Body** property  <br/> **Categories** property  <br/> **Class** property  <br/> **Companies** property  <br/> **ConversationIndex** property  <br/> **ConversationTopic** property  <br/> **CreationTime** property  <br/> **Count** property  <br/> **EntryID** property  <br/> **FormDescription** property  <br/> **GetInspector** property  <br/> **HTMLBody** property  <br/> **Importance** property  <br/> **ItemProperties** property  <br/> **LastModificationTime** property  <br/> **MessageClass** property  <br/> **Mileage** property  <br/> **MobileFormat** property  <br/> **NoAging** property  <br/> **OutlookInternalVersion** property  <br/> **OutlookVersion** property  <br/> **Parent** property  <br/> **PropertyAccessor** property  <br/> **ReceivedByEntryID** property  <br/> **ReceivedByName** property  <br/> **ReceivedTime** property  <br/> **Recipients** property  <br/> **ReplyRecipientNames** property  <br/> **ReplyRecipients** property  <br/> **Saved** property  <br/> **SenderEmailAddress** property  <br/> **SenderEmailType** property  <br/> **SenderName** property  <br/> **SendUsingAccount** property  <br/> **Sensitivity** property  <br/> **Sent** property  <br/> **SentOn** property  <br/> **Session** property  <br/> **Size** property  <br/> **SMILBody** property  <br/> **Subject** property  <br/> **Submitted** property  <br/> **To** property  <br/> **UnRead** property  <br/> **UserProperties** property  <br/> Methods  <br/> **Close** method  <br/> **Copy** method  <br/> **Delete** method  <br/> **Display** method  <br/> **Forward** method  <br/> **Move** method  <br/> **Reply** method  <br/> **ReplyAll** method  <br/> **Save** method  <br/> **SaveAs** method  <br/> **Send** method  <br/> Events  <br/> **AttachmentAdd** event  <br/> **AttachmentReadAttachmentRemove** event  <br/> **BeforeAttachmentAdd** event  <br/> **BeforeAttachmentPreview** event  <br/> **BeforeAttachmentRead** event  <br/> **BeforeAttachmentSave** event  <br/> **BeforeAttachmentWriteToTempFile** event  <br/> **BeforeAutoSave** event  <br/> **BeforeCheckNames** event  <br/> **BeforeDelete** event  <br/> **Close** event  <br/> **CustomAction** event  <br/> **CustomPropertyChange** event event  <br/> **Forward** event  <br/> **Open** event  <br/> **PropertyChange** event  <br/> **Read** event  <br/> **ReadComplete** event  <br/> **Reply** event  <br/> **ReplyAll** event  <br/> **Send** event  <br/> **UnloadWrite** event  <br/> |
|**NoteItem** <br/> |**Links** property  <br/> |
|[OlObjectClass](http://msdn.microsoft.com/library/33d724b3-df3c-2a7f-a80f-93b66d96f588%28Office.15%29.aspx) <br/> |**olLink** enumeration value  <br/> **olLinks** enumeration value  <br/> **olMobile** enumeration value  <br/> |
|[OlPane](http://msdn.microsoft.com/library/efbdecc7-90ae-65b2-58aa-d323c19b816e%28Office.15%29.aspx) <br/> |**olToDoBar** enumeration value  <br/> |
|**PostItem** <br/> |**Links** property  <br/> |
|**RemoteItem** <br/> |**Links** property  <br/> |
|**ReportItem** <br/> |**Links** property  <br/> |
|**TaskItem** <br/> |**Links** property  <br/> |
|**TaskRequestAcceptItem** <br/> |**Links** property  <br/> |
|**TaskRequestDeclineItem** <br/> |**Links** property  <br/> |
|**TaskRequestItem** <br/> |**Links** property  <br/> |
|**TaskRequestUpdateItem** <br/> |**Links** property  <br/> |
   
### Working with an inline response

Outlook 2013 introduces the inline response feature where the user can compose a response in the Reading Pane, rather than opening a new inspector window. If your solution requires adding custom Office Fluent UI controls to the compose note ribbon, or you need to apply business logic or custom functionality to a response message before the response is sent, modify your solution to use the new [InlineResponse](http://msdn.microsoft.com/library/5dbaddbd-e6cd-4776-b417-c67f51b12812%28Office.15%29.aspx) event on the [Explorer](http://msdn.microsoft.com/library/026591e5-049f-503a-4166-34e6dbc225fb%28Office.15%29.aspx) object. 
  
> [!NOTE]
> You can use inline response only if you have selected in the **View** menu to display the Reading Pane in the explorer. 
  
The **InlineResponse** event is the inline equivalent to the [NewInspector](http://msdn.microsoft.com/library/945fb1a6-262f-da0d-16c6-bc27193505ac%28Office.15%29.aspx) event on the [Inspectors](http://msdn.microsoft.com/library/b65475d6-a212-fc96-459d-47390dfe5ee5%28Office.15%29.aspx) collection object. The **NewInspector** event fires when a new inspector window is opened. The **InlineResponse** event fires when the user performs an action that causes an inline response to appear in the Reading Pane as shown in Figure 7 below. 
  
**Figure 7. An Inline response is created when user selects a response action**

![An inline response is created](media/ol15WhatsNew_Figure1_InlineResponse.jpg)
  
#### Object model support for inline response

The following members have been added to the [Explorer](http://msdn.microsoft.com/library/026591e5-049f-503a-4166-34e6dbc225fb%28Office.15%29.aspx) object to provide programmatic support for the inline response feature: 
  
|**Member**|**Description**|
|:-----|:-----|
|[ActiveInlineResponse](http://msdn.microsoft.com/library/fc38314d-7cff-44f4-9151-6129f918a721%28Office.15%29.aspx) property  <br/> |Returns an item object representing the active inline response item in the Reading Pane. Read-only.  <br/> |
|[ActiveInlineResponseWordEditor](http://msdn.microsoft.com/library/b9058694-ab8f-4962-ab7d-afac1704dd29%28Office.15%29.aspx) property  <br/> |Returns the Word [Document](http://msdn.microsoft.com/library/8d83487a-2345-a036-a916-971c9db5b7fb%28Office.15%29.aspx) object of the active inline response that is displayed in the Reading Pane. Read-only.  <br/> |
|[InlineResponse](http://msdn.microsoft.com/library/5dbaddbd-e6cd-4776-b417-c67f51b12812%28Office.15%29.aspx) event  <br/> |Occurs when the user performs an action that causes an inline response to appear in the Reading Pane.  <br/> |
   
#### Using the InlineResponse event

Let's imagine a scenario where your code needs to insert a disclaimer for every compose message including reply, reply all, and forward messages. Since inline response is the default response mode in Outlook 2013, your code must hook up an event handler for the **InlineResponse** event on the **Explorer** object. The following C# code hooks up an event handler for the **InlineResponse** event in the  `OutlookExplorer` class. In this code sample,  `OutlookExplorer` is a wrapper class for a collection of **Explorer** objects. 
  
```cs
public OutlookExplorer(Outlook.Explorer explorer)
{
    m_Window = explorer;
    // Hook up InlineResponse event
    m_Window.InlineResponse += 
        new Outlook.ExplorerEvents_10_InlineResponseEventHandler
        (m_Window_InlineResponse);
    // Hook up other events if applicable.
}
```

Once the **InlineResponse** event fires, the sample code creates a [MailItem](http://msdn.microsoft.com/library/14197346-05d2-0250-fa4c-4a6b07daf25f%28Office.15%29.aspx) instance of  `m_Mail` and listens to the [PropertyChange](http://msdn.microsoft.com/library/768de21f-a474-4574-74f4-6d99e3ab542e%28Office.15%29.aspx) event for that **MailItem** object.  `m_Mail` is an event-aware instance variable that you can use to implement any business logic required by your add-in. 
  
The sample code compares the [MailItem.Size](http://msdn.microsoft.com/library/10bd56cc-8bdb-470d-a84f-a809c2b057c4%28Office.15%29.aspx) property to 0 to determine whether the inline response is new or an existing draft. The **ActiveInlineResponseWordEditor** property returns a **Word.Document** object,  `doc`, which represents the active inline response for the active **Explorer**. Using the Word object model, the code adds a disclaimer to the beginning of this  `doc` object. 
  
```cs
// InlineResponse fires when the user creates an inline response item
void m_Window_InlineResponse(object Item)
{
    if (Item is Outlook.MailItem)
    {
        m_Mail = Item as Outlook.MailItem;
        // Hook up event-aware instance variable.
        // Use the variable to implement any business logic 
        // required by your add-in.
        m_Mail.PropertyChange += 
            new Outlook.ItemEvents_10_PropertyChangeEventHandler(
                m_Mail_PropertyChange);
        // Implement any business logic.
        // Use mail.Size to determine if item is new 
        // or is a draft inline response.
        // Size == 0 indicates a new inline response.
        if (m_Mail.Size == 0)
        {
            {
                Word.Document doc = 
                    m_Window.ActiveInlineResponseWordEditor as Word.Document;
                Word.Application wdApp = doc.Application as Word.Application;
                Word.Range rng = wdApp.ActiveDocument.Range(Start: 1);
                rng.InsertBefore("My Disclaimer...");
            }
        }
        else
        {
            // Do nothing.
        }
    }
}
```

Note that the **ActiveInlineResponse** property returns a **MailItem** object representing the active inline response item. You can use the same properties and methods of the **MailItem** object on this item, except for the following: 
  
- [MailItem.Actions](http://msdn.microsoft.com/library/1b7bb1c0-334f-826a-fd6b-8fc3f2fe5d64%28Office.15%29.aspx) property 
    
- [MailItem.Close](http://msdn.microsoft.com/library/00a8a4e8-9bdc-d1bc-cb61-c6d925fb754f%28Office.15%29.aspx) method 
    
- [MailItem.Copy](http://msdn.microsoft.com/library/a9356844-e31e-eb0f-c0f5-a2923ad127db%28Office.15%29.aspx) method 
    
- [MailItem.Delete](http://msdn.microsoft.com/library/342c6003-e7c5-7314-453c-151fc51d5b2d%28Office.15%29.aspx) method 
    
- [MailItem.Forward](http://msdn.microsoft.com/library/5b8c2261-c5ac-fd80-8acf-dfa645a04a1e%28Office.15%29.aspx) method 
    
- [MailItem.Move](http://msdn.microsoft.com/library/08a0fa20-b891-393a-00fa-5a8fb5405cf6%28Office.15%29.aspx) method 
    
- [MailItem.Reply](http://msdn.microsoft.com/library/c03208a4-dd31-a8ff-0dcd-4ef37a36beb2%28Office.15%29.aspx) method 
    
- [MailItem.ReplyAll](http://msdn.microsoft.com/library/25a1723a-864b-1526-9897-26e40042f119%28Office.15%29.aspx) method 
    
- [MailItem.Send](http://msdn.microsoft.com/library/78c85013-523e-447b-c47d-2da0705f1fe0%28Office.15%29.aspx) method 
    
On the other hand, if no inline response is active, the **ActiveInlineResponseWordEditor** and **ActiveInlineResponse** properties return **null**.
  
#### Adding custom controls to the Compose Tools contextual tab

Another possible scenario is that you want to extend the Outlook user interface for an inline reply. To extend the Outlook user interface, you need to use Office Fluent UI extensibility which is not covered in depth in this article. See the links supplied at the end of this article for additional information on extending the Outlook user interface. When an inline response is displayed in Outlook 2013, the user sees the **Compose Tools** contextual tab displayed on the Office Fluent ribbon. To add your control to the **Compose Tools** contextual tab, add your custom controls to the <contextualTabs> </contextualTabs> section of ribbon XML that will be passed to the [GetCustomUI](http://msdn.microsoft.com/library/a0106415-999e-94da-379c-70fb7aa6119f%28Office.15%29.aspx) method of the [IRibbonExtensibility](http://msdn.microsoft.com/library/b27a7576-b6f5-031e-e307-78ef5f8507e0%28Office.15%29.aspx) interface for the  _RibbonID_ equal to "Microsoft.Outlook.Explorer". You must identify the **tabSet** element with the appropriate value for the **idMso** attribute, which in this case is "TabComposeTools". The following ribbon XML creates the  `MyButton` control shown in Figure 7. 
  
```XML
    <contextualTabs>
      <tabSet idMso="TabComposeTools">
        <tab idMso="TabMessage">
          <group label="MyGroup" id="MyComposeToolsGroup">
            <button id="MyButtonInlineResponse"
                    size="large"
                    label="MyButton"
                    imageMso="MagicEightBall"
                    onAction="OnInlineResponseButtonClick" />
          </group>
        </tab>
      </tabSet>
    </contextualTabs>

```

When the user selects the  `MyButton` control, the  `OnInlineResponseButtonClick` handler is called. The following code sample uses the **ActiveInlineResponseWordEditor** property to obtain an instance of a **Word.Document** object. You can then use all the functionality of the **Word.Document** object to insert and format text as needed by your scenario. 
  
```cs
// Callback for inline response custom button.
public void OnInlineResponseButtonClick(Office.IRibbonControl control)
{
    if (control.Context is Outlook.Explorer)
    {
        Outlook.Explorer myExplorer =
            control.Context as Outlook.Explorer;
        Word.Document doc =
        myExplorer.ActiveInlineResponseWordEditor as Word.Document;
        Word.Application wdApp = doc.Application as Word.Application;
        Word.Range rng = wdApp.ActiveDocument.Range(Start: 1,
            End: wdApp.ActiveDocument.Characters.Count);
        rng.InsertBefore("\n" + "My Disclaimer...");
    }
}

```

## Changes to Outlook Social Connector provider extensibility
<a name="ol15WhatsNew_OSC"> </a>

In Office 2013, the Outlook Social Connector (OSC) has expanded its scope. It allows not only Outlook but all Office client applications that support displaying user presence and the Contact Card to display an aggregation of social information updates applied on a professional or social network site. In addition, SharePoint Server, SharePoint Workspace, and the Lync client also support the OSC.
  
One major change in OSC provider extensibility in Outlook 2013 is that activities are no longer synchronized using the activities cache. If an OSC provider supports displaying activities, then the provider must synchronize activities on demand to display up-to-date activities.
  
In addition, providers can now use the OSC XML Schema to communicate extra metadata for a person, for example, **askmeabout**, **businessAddress**, **interests**, **skills**, **schools**, **website**.
  
For detailed information, see [What's New for Providers](what-s-new-for-providers.md).
  
## Discontinuing support for Office Mobile Service
<a name="ol15WhatsNew_OMS"> </a>

In Office 2010, developers can build web services for [Office Mobile Service](http://msdn.microsoft.com/library/3962c25d-ff3a-44af-aba3-aea17ae7655b%28Office.15%29.aspx) (OMS) to integrate the mobile capabilities of Outlook and SharePoint with mobile devices. In Office 2013, only SharePoint continues to support OMS. Outlook 2013 has also deprecated the **MobileItem** object and its members. Attempting to create a **MobileItem** using [Application.CreateItem](http://msdn.microsoft.com/library/e5fbf367-db16-5042-823e-68e6b805e612%28Office.15%29.aspx) returns E_INVALIDARG. 
  
## Coexistence with previous Outlook versions
<a name="ol15WhatsNew_Coexistence"> </a>

Coexistence refers to the ability of delivering Outlook 2013 by Click-to-Run on the same computer where Outlook 2007 or Outlook 2010 is present. Coexistence, also known as side-by-side installation, allows the user to try Outlook 2013 without having to uninstall a previous Outlook version. Click-to-Run is the default delivery mechanism for Outlook 2013. Once Outlook 2013 is delivered on a computer, the user can run Outlook 2013 or the previous version of Outlook installed on their computer. Be aware that coexistence does not mean running two versions of Outlook simultaneously. Running two versions of Outlook simultaneously is not supported and Outlook displays an error dialog if you attempt to run a previous version of Outlook while Outlook 2013 is running. 
  
> [!NOTE]
> Coexistence of Outlook 2013 is not supported with versions of Outlook prior to Outlook 2007. 
  
### Version Support Matrix

This section describes the bitness and installation modes of earlier versions of Outlook that can coexist with Outlook 2013. Note the following:
  
- MSI refers to the Microsoft Installer (MSI) installation of a previous version of Outlook.
    
- Supported Windows versions for Office 2013 are Windows 7 and Windows 8 only.
    
- Windows Server is not supported for Click-to-Run.
    
- Outlook 2013 does not support coexistence with Outlook 2003 or earlier.
    
- Outlook 2013 does not support coexistence with the same version of Outlook - that is, Outlook 2013 installed by MSI and Outlook 2013 delivered by Click-to-Run are not supported on the same computer. 
    
- Cross-bitness is not supported. The user must always install the Click-to-Run version that matches the bitness of the down-level MSI install.
    
|**Version**|**Outlook 2007 MSI**|**Outlook 2010 x86 MSI**|**Outlook 2010 x64 MSI**|
|:-----|:-----|:-----|:-----|
|Outlook 2013 C2R x86  <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|Outlook 2013 C2R x64  <br/> |No  <br/> |No  <br/> |Yes  <br/> |
   
### Version-dependent profiles

To support coexistence, Outlook 2013 stores Outlook profiles in a separate hive in the Windows registry. The profile from a previous version of Outlook is migrated to the Outlook 2013 profile hive during the first boot of Outlook 2013. Subsequent changes or additions to the profile for the previous version of Outlook are not migrated during subsequent boots of Outlook 2013.
  
#### Profiles hive in Windows Registry

Unlike previous versions of Outlook that stored profiles in a version-independent manner under HKCU\Software\Microsoft\Windows NT\Windows Messaging Subsystem\Profiles, Outlook 2013 stores profiles in a versioned hive under the following key:
  
HKEY_CURRENT_USER\Software\Microsoft\Office\\<version\>\Outlook\Profiles
  
where \<version\> is a string representing the xx.0 major version, such as 15.0 for Outlook 2013.
  
#### Calling MAPI profile APIs

There are no changes for applications to read profile data from a profile hive. After initializing MAPI (for either a down-level version or the most current MAPI version, depending on the application's requirements), an application can use common MAPI profile APIs to read values from the appropriate profile hive.
  
If an application initializes MAPI for Outlook 2013, MAPI profile APIs read or write profile data to the versioned hive. If the application initializes MAPI for a previous version of Outlook, MAPI profile APIs read or write profile data to the version-independent hive.
  
#### App Path registration

To prevent down-level applications from loading the wrong MAPI version, Outlook 2013 modifies the App Path registration in the registry. A down-level version of an application loading the wrong MAPI version can result in a crash in the application attempting to load MAPI. Typically, previous versions of Outlook have written the Outlook App Path to the following key:
  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\App Paths\OUTLOOK.EXE
  
Previous versions of Click-to-Run did not modify the App Path for Outlook. Delivering Outlook 2013 by Click-To-Run modifies the App Path as follows:
  
- Installs patches for Outlook 2007 or Outlook 2010 to remove the dependency on App Path.
    
    Modify the App Path to point to the Outlook 2013 path for Outlook.exe. 
    
    The default path for Outlook.exe for Outlook 2013 is C:\Program Files\Microsoft Office 15\root\office15.
    
#### MAPI Versioning

Applications that use MAPI calls the [MAPIInitialize](http://msdn.microsoft.com/library/b9584226-79d2-4d83-8f31-dbfbc50f16c5%28Office.15%29.aspx) function to initialize a MAPI session. By default, applications that initialize MAPI use the version of MAPI provided by Outlook 2013. If you need to use a different version of MAPI, see the following topics in the [Outlook 2013 MAPI Reference](http://msdn.microsoft.com/library/3d980b86-7001-4869-9780-121c6bfc7275%28Office.15%29.aspx).
  
- [Building MAPI Applications on 32-Bit and 64-Bit Platforms](http://msdn.microsoft.com/library/d218ba2d-7a2e-4c33-a09b-a8c7e27f9726%28Office.15%29.aspx)
    
- [How to: Link to MAPI Functions](http://msdn.microsoft.com/library/be72a893-a3bc-4dea-8234-47f3e1db4515%28Office.15%29.aspx)
    
- [How to: Choose a Specific Version of MAPI to Load](http://msdn.microsoft.com/library/85539a7f-74b6-4267-86ea-00da2c900c34%28Office.15%29.aspx)
    
#### Simple MAPI

Simple MAPI refers to the API that allows applications to send mail with attachments using [MAPISendMail](http://msdn.microsoft.com/library/mapi.mapisendmail%28Office.15%29.aspx) or the new [MAPISendMailW](http://msdn.microsoft.com/library/mapi.mapisendmailw%28Office.15%29.aspx) API introduced with Windows 8. 
  
- The only supported Simple MAPI APIs are **MAPISendMail** (Windows 7) or **MapiSendMailW** (Windows 8). 
    
    Developers should consider modifying existing Simple MAPI code to use **MAPISendMailW** (Windows 8) or [MAPISendMailHelper](http://msdn.microsoft.com/library/mapi.mapisendmailhelper%28Office.15%29.aspx) (Windows 7) with full Unicode support and the ability to display a modeless Outlook inspector. 
    
    If Outlook is not running or Outlook 2013 is running, calling **MAPISendMail** or **MAPISendMailW** displays an Outlook 2013 inspector. 
    
    If a previous version of Outlook is running, calling **MAPISendMail** or **MAPISendMailW** displays the following error: 
    
    **This action is not supported while an older version of Outlook is running.**
    
### Protocol handlers

During installation, Outlook 2013 is registered as the default protocol handler for the common protocols listed in the following table. Outlook 2013, Outlook 2010, and Outlook 2007 support these protocols.
  
|**Protocol**|**Description**|
|:-----|:-----|
|**feed:**, **feeds:** <br/> |Handler for RSS feeds  <br/> |
|**mailto:** <br/> |Handler for MailTo links that display an Outlook inspector  <br/> |
|**stssync:** <br/> |Handler for SharePoint sync  <br/> |
|**outlook:** <br/> |Outlook protocol can only be used from Outlook item body or folder home page  <br/> |
|**webcal:** <br/> |Handler for webcal protocol  <br/> |
   
Note the following if Outlook 2013 is present with an older version of Outlook on the same computer:
  
- If no previous version of Outlook is running, calling the protocol handler invokes Outlook 2013 to handle the protocol handler request.
    
If a previous version of Outlook is running, calling the protocol handler uses a command line handoff to invoke the previous version of Outlook to handle the request.
  
### File Associations

During installation, Outlook 2013 is registered as the default handler for the common file associations listed in the following table. Outlook 2013, Outlook 2010, and Outlook 2007 support all these file extensions.
  
|**File association**|**Description**|
|:-----|:-----|
|**.eml** <br/> |Email message  <br/> |
|**.fdm** <br/> |Outlook form definition  <br/> |
|**.hol** <br/> |Outlook holiday  <br/> |
|**.ics** <br/> |iCalendar file  <br/> |
|**.msg** <br/> |Outlook message item  <br/> |
|**.oft** <br/> |Outlook item template  <br/> |
|**.pst** <br/> |Outlook data file  <br/> |
|**.vcf** <br/> |vCard file  <br/> |
|**.vcs** <br/> |vCalendar file  <br/> |
   
Note the following if Outlook 2013 is present with an older version of Outlook on the same computer:
  
- If no previous version of Outlook is running, opening an item from the file system opens the item in Outlook 2013. This action starts Outlook 2013 if it is not already running.
    
- If a previous version of Outlook is running, opening an item from the file system cause Outlook 2013 to launch and hand off the request to that previous version of Outlook. 
    
### Co-creating an Outlook Application object

Add-ins should use the [Application](http://msdn.microsoft.com/library/797003e7-ecd1-eccb-eaaf-32d6ddde8348%28Office.15%29.aspx) object passed back in the **OnConnection** event (native add-ins) or  `ThisAddin_Startup` event (managed add-ins built using Visual Studio Tools for Office). If your application co-creates an **Outlook.Application** object using **CreateObject** or another function that provides the ability to co-create an instance of **Outlook.Application**, you should be aware of the following in a coexistence environment:
  
- If Outlook is not running or Outlook 2013 is running, calling  `CreateObject("Outlook.Application")` returns an **Outlook.Application** object that represents Outlook 2013. 
    
- If a previous version of Outlook is running, calling **CreateObject** returns an **Outlook.Application** object that represents the previous version of Outlook. 
    
- Examine the [Application.Version](http://msdn.microsoft.com/library/08a74ab8-7e02-3956-1827-4b6690acdec1%28Office.15%29.aspx) property to determine the version of Outlook that is running. 
    
### Detecting Click-to-Run

To detect the existence of Outlook in the Click-to-Run environment, verify that the VirtualOutlook key exists in the following registry key: 
  
HKLM\Software\Microsoft\Office\15.0\Common\InstallRoot\Virtual\VirtualOutlook
  
If the VirtualOutlook key exists, then Outlook has been delivered as a Click-to-Run application. 
  
### Ensuring your solution will run in the coexistence environment

Since coexistence is the default delivery mode, you should test your solution against Outlook 2013 and previous versions of Outlook and check for the following possible issues:
  
- Add-ins are registered in version-independent hive in the Windows registry under
    
    HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\Outlook\Addins
    
    or
    
    HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\Outlook\Addins
    
    Since the add-in registration is version-independent, your add-in should run when Outlook 2013 or a previous version of Outlook is running. Be sure to test an updated version of your add-in against Outlook 2013 and previous Outlook versions. The add-in should detect the Outlook version using **Application.Version** and adjust gracefully to the running Outlook version. 
    
- Remove dependencies on App Path from your code.
    
- Do not use the Windows registry to enumerate profiles. Instead use the MAPI profile APIs.
    
## Performance criteria for keeping add-ins enabled
<a name="ol15WhatsNew_AddinDisabling"> </a>

Extending the add-in resiliency pillar of Outlook 2010, Outlook 2013 monitors add-in performance metrics such as add-in startup, shutdown, folder switch, item open, and invoke frequency. Outlook records the elapsed time in milliseconds for each performance monitoring metric. 
  
For example, the startup metric measures the time required by each connected add-in during Outlook startup. Outlook then computes the median startup time over 5 successive iterations. If the median startup time exceeds 1000 milliseconds (1 second), then Outlook disables the add-in and displays a notification to the user that an add-in has been disabled. The user has the option of always enabling the add-in, in which case Outlook will not disable the add-in even if the add-in exceeds the 1000 millisecond performance threshold 
  
### Monitoring add-in performance for default disabling

Outlook uses the following criteria to determine if it should disable an add-in. The user has the option of always enabling an add-in and exempting the add-in from the add-in disabling criteria.
  
|**Criteria**|**Threshold (in milliseconds)**|**Description**|
|:-----|:-----|:-----|
|Startup  <br/> |1000  <br/> |Measures the time in milliseconds for the add-in to complete startup using the **IDTExtensibility2_OnConnection** event. By default, if the median time over 5 successive iterations exceeds the performance threshold, Outlook disables the add-in.  <br/> |
|Shutdown  <br/> |500  <br/> |Measures the time in milliseconds for the add-in to complete shutdown using the [IDTExtensibility2_OnDisconnection](http://msdn.microsoft.com/en-us/library/extensibility.idtextensibility2.ondisconnection%28VS.110%29.aspx) event. Only applies to add-ins that request slow shutdown. Add-ins that use fast shutdown are not subject to this criteria. If the median time over 5 successive iterations exceeds the performance threshold, Outlook disables the add-in on the next startup of Outlook.  <br/> |
|Folder switch  <br/> |500  <br/> |Measures the time in milliseconds for the add-in to complete folder switch using the [BeforeFolderSwitch](http://msdn.microsoft.com/library/ae65c073-6b4a-ac81-c4ae-691118b19df0%28Office.15%29.aspx) and [FolderSwitch](http://msdn.microsoft.com/library/5dfa1fa3-c381-8e19-0528-d70a6fd63187%28Office.15%29.aspx) events on the **Explorer** object. By default, if the median time over 5 successive iterations exceeds the performance threshold, Outlook disables the add-in.  <br/> |
|Item open  <br/> |500  <br/> |Measures the time in milliseconds for the add-in to complete opening an item using the **Open** event on an item. By default, if the median time over 5 successive iterations exceeds the performance threshold, Outlook disables the add-in.  <br/> |
|Invoke frequency  <br/> |1000  <br/> |Measures the time interval in milliseconds between the add-in making 10,000 successive invoke calls. By default, if the interval between 10,000 successive calls and the next is less than the performance threshold, Outlook disables the add-in. Unlike the other 4 criteria, this criterion does not incur taking a median value.  <br/> |
   
### System Administrator control over add-ins

The user has control over which add-ins run on their computer. For system administrators, Outlook 2013 provides an enhanced level of control over add-ins using group policy. Group policy will always override user settings and users are prevented from changing add-in settings for add-ins that have been configured by the group policy "List of Managed Add-ins". The policy key is as follows.
  
|||
|:-----|:-----|
|Key  <br/> |HKCU\Software\Policies\Microsoft\Office\15.0\Outlook\Resiliency\AddinList  <br/> |
|Name  <br/> |List of Managed Add-ins  <br/> |
|Description  <br/> |This policy setting allows you to specify which add-ins are always enabled, always disabled (blocked), or configurable by the user.  <br/> > [!NOTE]> Here, the term "managed" refers to add-ins that are handled by the group policy, and does not relate to add-ins being developed in managed programming languages.           |
   
To block add-ins that are not managed by this policy setting, you must also configure the "Block all unmanaged add-ins" policy setting.
  
To enable this policy setting, provide the following information for each add-in:
  
- In "Value name," specify the programmatic identifier (ProgID) for COM add-ins.
    
    To obtain the ProgID for an add-in, use the Registry Editor on the client computer where the add-in is installed to locate key names under
    
    HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\Outlook\Addins
    
    or
    
    HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\Outlook\Addins
    
- In "Value," specify the value as follows:
    
  - To specify that an add-in is always disabled (blocked), specify 0.
    
  - To specify that an add-in is always enabled, specify 1. 
    
  - To specify that an add-in is configurable by the user and not blocked by the "Block all unmanaged add-ins" policy setting when enabled, specify 2.
    
If you disable or do not enable this policy setting, the list of managed add-ins is deleted. If the "Block all unmanaged add-ins" policy setting is enabled, then all add-ins are blocked.
  
Add-ins that are disabled by this policy will never be disabled by the Outlook add-in disabling feature, which disables add-ins for performance, resiliency, or reliability reasons.
  
### User interface for add-in disabling feature

When an add-in exceeds the performance threshold, Outlook displays the notification bar shown in Figure 8 that informs the user that one or more add-ins has been disabled.
  
**Figure 8. Outlook displays a notification bar when an add-in is disabled automatically**

![Notification bar](media/ol15WhatsNew_Figure2_NotificationBar.png)
  
If the user clicks the **View Disabled Add-ins** button on the notification bar, the **Disabled Add-ins** dialog will be displayed as shown in Figure 9. 
  
**Figure 9. Clicking "Always enable this add-in" button enables the add-in and exempts the add-in from the add-in disabling feature**

![Always enable an add-in](media/ol15WhatsNew_Figure3_AlwaysEnable.png)
  
If the user decides that the performance timing required by the add-in is acceptable, the user has the choice of always enabling the add-in. An add-in that is always enabled will not be automatically disabled by Outlook based on performance criteria. If for some reason the user decides later that he or she no longer wants to exempt the add-in from the add-in disabling feature, the user can also disable the add-in from the **Disabled Add-ins** dialog shown in Figure 10. 
  
**Figure 10. Selecting the Disable this add-in button disables the add-in**

![Disable an add-in](media/ol15WhatsNew_Figure4_Disable.png)
  
### Preventing an add-in from being disabled

While most add-ins will not be disabled by the add-in disabling feature, you don't want your add-in to be disabled consistently. Here are suggestions for improving add-in performance:
  
- Prefer native COM add-ins over managed add-ins since managed add-ins must incur the overhead of loading the .NET Framework during Outlook startup.
    
- If you have long-running tasks such as making an expensive connection to a database, defer those tasks to occur after startup.
    
- If possible, cache data locally rather than making expensive network calls during the **FolderSwitch** and **BeforeFolderSwitch** events of an explorer, or **Open** events of an item. 
    
- Polling is an expensive operation, so always prefer an event-driven model over polling. 
    
- Be aware that all calls to the Outlook object model execute on Outlook's main foreground thread. Avoid making long-running Outlook object model calls if possible. Note that in Outlook 2013, calls to the Outlook object model return E_RPC_WRONG_THREAD when the Outlook object model is called from a background thread.
    
In particular, if you use Office developer tools in Visual Studio to create managed add-ins, be aware that the first add-in to load the CLR is likely to take a performance hit. Consider the following measures, and see the additional resources at the end of this document for details:
  
- Load a managed add-in on demand.
    
- Delay loading the CLR.
    
- Use an MSI deployment package instead of ClickOnce.
    
- If applicable, use a Fast Path to bypass schema validation, digital signatures validation in manifests, and automatic update checking. You can find more information about using the Fast Path in the blog post [Performance Improvements Coming Soon to a Service Pack Near You (Stephen Peters)](http://blogs.msdn.com/b/vsto/archive/2010/11/30/performance-improvements-coming-soon-to-a-service-pack-near-you-stephen-peters.aspx).
    
- If your add-in extends the ribbon and links in a large library, override ribbon reflection.
    
## Conclusion
<a name="ol15WhatsNew_Conclusion"> </a>

Mail apps provide an exciting opportunity for developers to bring web services and contextual web-driven UI directly into Outlook and Outlook Web App. We have delivered on our vision of "Write once, run anywhere" for Exchange and Outlook developers. We now offer two extensibility pillars, the first built on the Office COM add-in feature introduced in Office 2000 and the second built on the mail apps platform. The COM add-in model supports deep integration with only the Outlook client and requires that you touch every desktop when your solution is installed. If you have an existing add-in solution, you should consider updating the add-in to work with inline response, coexistence, and the add-in disabling feature. If you are looking for new opportunities to reach a very large audience using Outlook and Outlook Web App, create a mail app and enjoy web-simple deployment and integration of your web service directly into the Outlook UI. Whichever path you choose (and you might choose both), happy coding!
  
## Additional resources
<a name="ol15WhatsNew_AdditionalRescources"> </a>

Office Add-ins
  
- [Office Add-ins](http://msdn.microsoft.com/library/1e123201-6e70-45c1-a48c-d5b955896ddb%28Office.15%29.aspx)
    
Weather Bar
  
- [Extending the Weather Bar in Outlook](extending-the-weather-bar-in-outlook.md)
    
- [Outlook Weather Location XML Schema](outlook-weather-location-xml-schema.md)
    
- [Outlook Weather Information XML Schema](outlook-weather-information-xml-schema.md)
    
Outlook and Office object models
  
- [Outlook 2013 Developer Reference](http://msdn.microsoft.com/library/75e4ad96-62a2-49d2-bc51-48ceab50634c%28Office.15%29.aspx)
    
- [Extending the User Interface in Outlook 2010](http://msdn.microsoft.com/library/00b504b0-e897-43b9-8615-44276166823f%28Office.15%29.aspx)
    
Outlook Social Connector
  
- [Getting Started with Developing an Outlook Social Connector Provider](getting-started-with-developing-an-outlook-social-connector-provider.md)
    
Coexistence and MAPI
  
- [Outlook 2013 MAPI Reference](http://msdn.microsoft.com/library/3d980b86-7001-4869-9780-121c6bfc7275%28Office.15%29.aspx)
    
- [Outlook 2010: MAPI Header Files](http://www.microsoft.com/en-us/download/details.aspx?id=12905)
    
- [Outlook 2010 Messaging API (MAPI) Code Samples](http://ol2010mapisamples.codeplex.com/)
    
- [SGriffin's MAPI Internals](http://blogs.msdn.com/b/stephen_griffin/)
    
Performance and Office add-ins development in Visual Studio
  
- [Demand-Loading VSTO Add-ins](http://blogs.msdn.com/b/andreww/archive/2008/07/14/demand-loading-vsto-add-ins.aspx)
    
- [Delay-loading the CLR in Office Add-ins](http://blogs.msdn.com/b/andreww/archive/2008/04/19/delay-loading-the-clr-in-office-add-ins.aspx)
    
- [VSTO Performance: Delay Loading and You (Stephen Peters)](http://blogs.msdn.com/b/vsto/archive/2010/01/07/vsto-performance-delay-loading-and-you.aspx)
    
- [Performance Improvements Coming Soon to a Service Pack Near You (Stephen Peters)](http://blogs.msdn.com/b/vsto/archive/2010/11/30/performance-improvements-coming-soon-to-a-service-pack-near-you-stephen-peters.aspx)
    
- [VSTO Performance: Ribbon Reflection (Stephen Peters)](http://blogs.msdn.com/b/vsto/archive/2010/06/03/vsto-performance-ribbon-reflection.aspx)
    
- [Publishing Office Solutions by Using Windows Installer](http://msdn.microsoft.com/library/260dda48-f9d4-474c-8638-ecf5b2c2729d%28Office.15%29.aspx)
    
Miscellaneous
  
- [What's new for Office 2013 developers](http://msdn.microsoft.com/library/d76ae308-555e-4147-8900-956d3eb8ba23%28Office.15%29.aspx)
    

