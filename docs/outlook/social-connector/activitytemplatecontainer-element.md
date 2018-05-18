---
title: "activityTemplateContainer Element"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 74662f25-5e18-4d0b-999c-a144427ad9e3
description: "An activityTemplateContainer element is a template that allows you to format your activity feed items and reuse XML that specifies a layout. Use IDs (applicationID and templateID) to match a feed item (activityDetails) to a template (activityTemplateContainer). Store the layout data as part of the activityTemplate element. To reference data that is pulled from the individual activity feed item, use template variables as placeholders for information such as people, links, and text."
---

# activityTemplateContainer Element

An **activityTemplateContainer** element is a template that allows you to format your activity feed items and reuse XML that specifies a layout. Use IDs ( **applicationID** and **templateID**) to match a feed item ( **activityDetails**) to a template ( **activityTemplateContainer**). Store the layout data as part of the **activityTemplate** element. To reference data that is pulled from the individual activity feed item, use template variables as placeholders for information such as people, links, and text. 
  
The following table describes the three elements that the **activityTemplateContainer** element requires. 
  
|**Element**|**Description**|
|:-----|:-----|
|**applicationID** <br/> |One of two unique IDs that are used to match the feed item with its template. If you have multiple applications or other groupings, this can be used as a first-tier template organizer.  <br/> |
|**templateID** <br/> |The second unique ID that is used to match the feed item with its template. This can be used as a second-tier template organizer.  <br/> |
|**activityTemplate** <br/> |The layout of the template ( **icon**, **title**, and **data** elements), and the type of activity ( **type** element).  <br/> |
   
The following table describes the child elements of **activityTemplate**, which describe the layout and the type of a template.
  
|**Element**|**Description**|
|:-----|:-----|
|**icon** <br/> |A link token, which references the URL for the icon for that feed item.  <br/> |
|**title** <br/> |The required information for the feed item.  <br/> |
|**type** <br/> |The type of activity, such as an update of status, photo, or document.  <br/> |
|**data** <br/> |Any additional information for the feed item, such as pictures, text, or links.  <br/> |
   
For an example of activity feed XML, see [Activity Feed XML Example](activity-feed-xml-example.md)
  
## See also



[Overview of XML for an Activity Feed Item](overview-of-xml-for-an-activity-feed-item.md)
  
[activityDetails Element](activitydetails-element.md)
  
[Template Variables](template-variables.md)
  
[Guidelines for Properly Displaying Activities](guidelines-for-properly-displaying-activities.md)
  
[XML for Activities](xml-for-activities.md)
  
[Outlook Social Connector Provider XML Schema](outlook-social-connector-provider-xml-schema.md)


[Developing a Provider with the OSC XML Schema](developing-a-provider-with-the-osc-xml-schema.md)

