---
title: "Technical requirements"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: eff6d5d6-8855-4e54-a781-9deab8cc0aca
description: "This topic describes the supported programming languages, COM visibility and method return type requirements, and details of the Outlook Social Connector (OSC) provider extensibility DLL."
---

# Technical requirements

This topic describes the supported programming languages, COM visibility and method return type requirements, and details of the Outlook Social Connector (OSC) provider extensibility DLL. 
  
## Programming language and COM requirements

You can create an OSC provider by using managed languages such as Visual C# or Visual Basic, or unmanaged languages such as Visual C++. You can use any tool that can create a COM-visible DLL component to develop an OSC provider. The decision to use a managed or unmanaged language to develop a provider should take into account the download size and dependencies of the provider installation package.
  
An OSC provider must be COM-visible as defined by the following:
  
- After installation, an OSC provider must be registered by using COM self-registration or regsvr32.
    
- COM registration of an OSC provider DLL registers the provider under HKCU or HKLM. 
    
- A provider's ProgID is registered under  `HKCU\Software\Microsoft\Office\Outlook\SocialConnector\SocialProviders`.
    
- An OSC provider developed in a managed language is COM-visible.
    
- An OSC provider should add values to the Windows registry that indicate that the provider DLL supports both single-threaded apartment (STA) and multithreaded apartment (MTA) threading models. For more information about COM threading models, see [Descriptions and Workings of OLE Threading Models](https://support.microsoft.com/kb/150777).
    
Methods in OSC provider extensibility must return primitive types such as **string** or **bool**. Certain **string** return values must comply with the schema definition for OSC provider extensibility. Only XML is supported as a return value. 
  
## Details of the OSC provider extensibility DLL

The component that supports OSC provider extensibility is the OSC provider extensibility DLL. Third-party developers can build OSC provider DLLs by using these extensibility interfaces. The following list shows the details of the OSC provider extensibility DLL:
  
- Extensibility DLL file name: socialprovider.dll
    
- Extensibility DLL friendly name: Microsoft Outlook Social Provider Extensibility
    
- Extensibility DLL major version: 15.0
    
- Extensibiilty DLL TypeLib version: 1.1
    
## Miscellaneous technical information

JavaScript Object Notation (JSON) is not supported in the OSC provider extensibility model.
  
There are no dependencies on an XML parser. The OSC provider can use an XML parser that is included with Office, such as Microsoft XML Core Services (MSXML), use the XML parsing capabilities built into the Microsoft .NET Framework, or use a third-party XML parser. 
  
## See also

- [Best Practices for Developing a Provider](best-practices-for-developing-a-provider.md)  
- [Quick Steps for Learning to Develop a Provider](quick-steps-for-learning-to-develop-a-provider.md)
- [Deploying a Provider](deploying-a-provider.md)  
- [Getting Started with Developing an Outlook Social Connector Provider](getting-started-with-developing-an-outlook-social-connector-provider.md)

