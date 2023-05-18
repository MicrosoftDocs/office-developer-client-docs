---
title: "XML for activities"
manager: lindalu
ms.date: 03/09/2022
ms.audience: Developer
ms.topic: overview
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: acc4a555-a3bf-4a79-86dc-aba6477733b8
description: "This topic contains an example scenario that shows the Outlook Social Connector (OSC) provider extensibility API calls that an OSC provider implements and the OSC makes to obtain activities information. Information is expressed in XML strings that conform to the OSC provider XML schema."
---

# XML for activities

This topic contains an example scenario that shows the Outlook Social Connector (OSC) provider extensibility API calls that an OSC provider implements and the OSC makes to obtain activities information. Information is expressed in XML strings that conform to the OSC provider XML schema.
  
The OSC provider XML schema allows an OSC provider to define activities. Activity information can include the social network where the activity feed items originated, details of each activity feed item (such as owner, type, and publish date of the activity), and the template to display the activity. To support showing activities on the People Pane or Contact Card, a social network's OSC provider must implement and return the correct activities XML. For an example of activity feed XML, see [Activity Feed XML Example](activity-feed-xml-example.md). For more information about synchronizing friends' activities, see [Synchronizing Friends and Activities](synchronizing-friends-and-activities.md). For a complete definition of the OSC provider XML schema, including which elements are required or optional, see [Outlook Social Connector Provider XML Schema](outlook-social-connector-provider-xml-schema.md).
  
In the following scenario, the OSC dynamically synchronizes activities for a person selected in the People Pane, and gets details about that person:
  
1. An OSC provider that supports on-demand synchronization of activities indicates that to the OSC by using the **getActivities** and **dynamicActivitiesLookupEx** elements. The OSC provider also sets the **hashFunction** element. All three elements are child elements of **capabilities**.

2. The OSC provider implements the **ISocialProvider::GetCapabilities** and [ISocialSession2::GetActivitiesEx](isocialsession2-getactivitiesex.md) methods.

3. The OSC calls **ISocialProvider::GetCapabilities** to check the value of **getActivities** and **dynamicActivitiesLookupEx** to verify that the OSC provider supports on-demand synchronization of activities. The OSC also notes the value of the **hashFunction** element supported by the OSC provider.

4. The OSC refreshes the People Pane or Contact Card to let the user see the latest activities of the selected person. The OSC encrypts the person's SMTP address by using the hash function specified in the **hashFunction** element, forming an XML string that conforms to the XML schema definition for the **hashedAddresses** element.

5. The OSC calls **ISocialSession2::GetActivitiesEx**, providing this XML string of the hashed address as the _hashedAddresses_ parameter, to get a current collection of activities for that person in the _activities_ parameter. The _activities_ parameter string complies with the XML schema definition of the **activityFeed** element.

6. Based on the XML schema definition for **activityFeed**, the OSC further parses the _activities_ string to find out the type, publish date, and other information about each activity, and how to display the activity.

7. To get details about the selected person, the OSC calls [ISocialSession2::GetPeopleDetails](isocialsession2-getpeopledetails.md), providing the same XML string of hashed addresses as the argument for the _personsAddresses_ parameter. The details about the person are returned in the _personsCollection_ parameter. These details can include **firstName**, **lastName**, and **emailAddress**. The _personsCollection_ parameter conforms to the XML schema definition for the **person** element.

You can find more information about specifying XML for activities in the following topics of this section:
  
- [Overview of XML for an Activity Feed Item](overview-of-xml-for-an-activity-feed-item.md)
- [activityDetails Element](activitydetails-element.md)
- [activityTemplateContainer Element](activitytemplatecontainer-element.md)
- [Template Variables](template-variables.md)
- [Guidelines for Properly Displaying Activities](guidelines-for-properly-displaying-activities.md)

## See also

- [Activity Feed XML Example](activity-feed-xml-example.md)  
- [Synchronizing Friends and Activities](synchronizing-friends-and-activities.md)
- [XML for Capabilities](xml-for-capabilities.md)  
- [XML for Friends](xml-for-friends.md)
- [Developing a Provider with the OSC XML Schema](developing-a-provider-with-the-osc-xml-schema.md)
