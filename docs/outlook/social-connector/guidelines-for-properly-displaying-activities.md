---
title: "Guidelines for Properly Displaying Activities"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 55268188-8432-4145-9527-f5888949fc24
description: "Outlook Social Connector (OSC) providers can set the getActivities and dynamicActivitiesLookupEx elements to have the OSC store activity items in memory. This topic describes the OSC provider extensibility APIs that the OSC calls to get or refresh activities and activity owner details, if the OSC provider supports synchronizing activity feeds from the social network. The topic also lists a few child elements of the activityFeed element that the OSC provider should set for the OSC to display activities properly in the Office Contact Card or Outlook People Pane."
---

# Guidelines for Properly Displaying Activities

Outlook Social Connector (OSC) providers can set the **getActivities** and **dynamicActivitiesLookupEx** elements to have the OSC store activity items in memory. This topic describes the OSC provider extensibility APIs that the OSC calls to get or refresh activities and activity owner details, if the OSC provider supports synchronizing activity feeds from the social network. The topic also lists a few child elements of the **activityFeed** element that the OSC provider should set for the OSC to display activities properly in the Office Contact Card or Outlook People Pane. 
  
- The OSC calls the [ISocialSession2::GetActivitiesEx](isocialsession2-getactivitiesex.md) method to get and store activities in the News Feed folder for the logged-on user. The OSC provider must implement **GetActivitiesEx** to return an  _activities_ XML string that complies with the OSC provider XML schema definition of the **activityFeed** element. 
    
- The OSC provider must set the **ownerID** element, which is a child element of the **activityDetails** element. **ownerID** is an opaque string that identifies the owner of the activity on the social network. 
    
- The OSC provider should set the **nameHint** and **emailAddress** elements in the **publisherVariable** node of the **templateVariables** element. 
    
    Note that per the OSC provider XML schema, the **nameHint** element is an optional element. The OSC uses it to match the display name of the user selected in the Contact Card or People Pane. Similarly, the **emailAddress** element is an optional element in the XML schema. The OSC uses it to match the SMTP address of the user selected in the Contact Card or People Pane. 
    
    If only the **ownerID** element is specified, but one or both of **nameHint** and **emailAddress** are not specified, the OSC calls the [ISocialSession2::GetPeopleDetails](isocialsession2-getpeopledetails.md) method and then the [ISocialPerson::GetDetails](isocialperson-getdetails.md) method to get more information about the person identified by the **ownerID**. When the OSC calls **ISocialPerson::GetDetails**, the provider must return **person** XML that specifies the **fullName** and **emailAddress** elements. 
    
## See also

#### Concepts

[XML for Activities](xml-for-activities.md)
  
[XML for Friends](xml-for-friends.md)
  
[XML for Capabilities](xml-for-capabilities.md)

