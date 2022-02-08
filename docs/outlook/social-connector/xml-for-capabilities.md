---
title: "XML for capabilities" 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: edad1223-a55f-4e4a-8e90-3471f2f559ac
description: "The capabilities element in the (OSC) provider XML schema allows an OSC provider to specify its functionality. Such functionality includes the following:"
---

# XML for capabilities

The **capabilities** element in the (OSC) provider XML schema allows an OSC provider to specify its functionality. Such functionality includes the following: 
  
- Whether the provider supports getting, caching, or dynamically looking up friends and activities from the social network.
    
- How the OSC should display certain logon user interfaces.
    
- Whether the OSC should use forms-based authentication or automatically configure the social network and logs on the user on the social network.
    
The XML schema for **capabilities** is critical because it identifies to the OSC the functionality supported by the provider. An OSC provider must implement the [ISocialProvider::GetCapabilities](isocialprovider-getcapabilities.md) method that returns a  _result_ string. The OSC calls **ISocialProvider::GetCapabilities** to obtain information about the capabilities of the OSC provider in the _result_ string, which complies with the XML schema definition for the **capabilities** element. This information enables subsequent calls from the OSC to the OSC provider to operate correctly. 
  
To specify capabilities of an OSC provider as an output parameter of the **ISocialProvider::GetCapabilities** method, you must conform to the OSC provider extensibility XML schema. The following figure shows the **capabilities** XML structure. 
  
**Figure 1. \<capabilities\> XML structure**

![capabilities XML structure](media/ol14oscref_Specifyingxmlforcapabilities_image1.gif)
  
For detailed descriptions of child elements of the **capabilities** element, see [Capabilities XML Elements](capabilities-xml-elements.md). For an example of **capabilities** XML, see [Capabilities XML Example](capabilities-xml-example.md). For a complete definition of the OSC provider XML schema, including which elements are required or optional, see [Outlook Social Connector Provider XML Schema](outlook-social-connector-provider-xml-schema.md).
  
## See also

- [Capabilities XML Example](capabilities-xml-example.md)  
- [Synchronizing Friends and Activities](synchronizing-friends-and-activities.md)  
- [XML for Friends](xml-for-friends.md)  
- [XML for Activities](xml-for-activities.md)
- [Developing a Provider with the OSC XML Schema](developing-a-provider-with-the-osc-xml-schema.md)

