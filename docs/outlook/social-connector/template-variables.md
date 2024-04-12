---
title: "Template variables"
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: overview
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: 6f8f6af2-c7fa-4135-9532-7af5fc643b0d
description: "Instances of template variables (represented by a templateVariable element) specify the data of an activity feed item in an activity template."
---

# Template variables

Instances of template variables (represented by a **templateVariable** element) specify the data of an activity feed item in an activity template. 
  
For an example of activity feed XML, see [Activity Feed XML Example](activity-feed-xml-example.md).

The following table shows the types of supported template variables, each represented by the corresponding XML enumeration value.
  
|**Type of template variable**|**Description**|
|:-----|:-----|
|**entityVariable** <br/> |A person, group, or thing. |
|**linkVariable** <br/> |A link. |
|**listVariable** <br/> |A group of objects. |
|**pictureVariable** <br/> |A picture. |
|**publisherVariable** <br/> |The publisher of the activity feed item. |
|**textVariable** <br/> |A block of text. |
   
Each type of template variable has required elements to specify the data about that variable. Template variables are specified as follows:
  
`<templateVariable type="variable type">`
  
## List template variable

You can specify template variables that are contained within a list (delimited by the **listVariable** and **listItems** elements) as follows: 
  
`<simpleTemplateVariable type="variable type of text, link, or picture">`
  
A template variable of the **listVariable** type is a container for objects. It can contain comma-delimited items (of the **linkVariable** or **textVariable** type) or pictures (of the **pictureVariable** type). Lists can contain up to five link items, five text items, or five pictures. 
  
The Outlook Social Connector (OSC) localizes link or text list items according to the Windows system locale.
  
To correctly parse and display pictures in an activity feed item, you must include pictures in a list. All pictures are resized to be 52 pixels high. The width of the picture is not resized.
  
## Template variable elements

This section covers the required and optional elements supported for each type of template variable.
  
### entityVariable

|**Element**|**Description**|
|:-----|:-----|
|**name** <br/> |The name of the variable. Required. |
|**id** <br/> |The unique ID of the user. Required. |
|**nameHint** <br/> |The name to be displayed in the feed item. Optional. |
|**profileUrl** <br/> |The URL of the person's profile that will be used as the hyperlink for the person's name in the feed item, if the person's name is present. Optional. |
|**emailAddress** <br/> |The email address that is used to update this person's contact information in Outlook. Optional. |
   
### linkVariable

|**Element**|**Description**|
|:-----|:-----|
|**name** <br/> |The name of the variable. Required. |
|**value** <br/> |The URL for this link. Required. |
|**text** <br/> |The link text to display instead of the URL itself. Optional. |
   
### listVariable

|**Element**|**Description**|
|:-----|:-----|
|**name** <br/> |The name of the variable. Required. |
|**listItems** <br/> |A container for items in the list. Required. |
   
### pictureVariable

|**Element**|**Description**|
|:-----|:-----|
|**name** <br/> |The name of the variable. Required. |
|**value** <br/> |The URL for the picture. Required. |
|**altText** <br/> |The alternate text to display for accessibility and when the user moves the mouse pointer over the picture. Optional. |
|**href** <br/> |The hyperlink to use when the user clicks the picture, if the desired target is not the picture URL specified by the **value** element. Optional. |
   
### publisherVariable

|**Element**|**Description**|
|:-----|:-----|
|**name** <br/> |The name of the variable. Required. |
|**id** <br/> |The unique ID of the user. Required. |
|**nameHint** <br/> |The name to be displayed in the feed item. Optional. |
|**profileUrl** <br/> |The URL of the person's profile that will be used as the hyperlink for the person's name in the feed item, if the person's name is present. Optional. |
|**emailAddress** <br/> |The email address that is used to update this person's contact information in Outlook. Optional. |
   
### textVariable

|**Element**|**Description**|
|:-----|:-----|
|**name** <br/> |The name of the variable. Required. |
|**value** <br/> |The text to display. Optional. |
   
## See also

- [Overview of XML for an Activity Feed Item](overview-of-xml-for-an-activity-feed-item.md)  
- [activityDetails Element](activitydetails-element.md)  
- [activityTemplateContainer Element](activitytemplatecontainer-element.md)  
- [Guidelines for Properly Displaying Activities](guidelines-for-properly-displaying-activities.md)  
- [XML for Activities](xml-for-activities.md)  
- [Outlook Social Connector Provider XML Schema](outlook-social-connector-provider-xml-schema.md)
- [Developing a Provider with the OSC XML Schema](developing-a-provider-with-the-osc-xml-schema.md)

