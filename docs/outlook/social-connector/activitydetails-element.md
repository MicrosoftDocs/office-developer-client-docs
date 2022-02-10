---
title: "activityDetails Element"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: c103d48d-53ca-4b19-b16f-2862379587ef
description: "The activityDetails element stores the raw data for a single activity feed item. Each activity feed item must have its own activityDetails element. Data in the activityDetails element is referenced in activity templates by using name elements."
---

# activityDetails Element

The **activityDetails** element stores the raw data for a single activity feed item. Each activity feed item must have its own **activityDetails** element. Data in the **activityDetails** element is referenced in activity templates by using **name** elements. Every piece of data in the **activityDetails** element must have a **name** element. 
  
The following table describes the six elements that the **activityDetails** element requires. 
  
|**Element**|**Description**|
|:-----|:-----|
|**ownerID** <br/> |The ID of the user on the social network who generated this activity feed item. |
|**objectID** <br/> |A unique string for the activity feed item to detect duplicate feed items. |
|**applicationId** <br/> |One of two unique IDs that are used to match the activity feed item with its template. If you have multiple applications or other groupings, this can be used as a first-tier template organizer. |
|**templateId** <br/> |The second unique ID that is used to match the activity feed item with its template. This can be used as a second-tier template organizer. |
|**publishDate** <br/> |The date and time that the activity feed item was published. |
|**templateVariables** <br/> |The data to be used in the tokens for the activity feed item template. |
   
For an example of activity feed XML, see [Activity Feed XML Example](activity-feed-xml-example.md)
  
## See also

- [Overview of XML for an Activity Feed Item](overview-of-xml-for-an-activity-feed-item.md)  
- [activityTemplateContainer Element](activitytemplatecontainer-element.md)  
- [Template Variables](template-variables.md) 
- [Guidelines for Properly Displaying Activities](guidelines-for-properly-displaying-activities.md)  
- [XML for Activities](xml-for-activities.md)  
- [Outlook Social Connector Provider XML Schema](outlook-social-connector-provider-xml-schema.md)
- [Developing a Provider with the OSC XML Schema](developing-a-provider-with-the-osc-xml-schema.md)

