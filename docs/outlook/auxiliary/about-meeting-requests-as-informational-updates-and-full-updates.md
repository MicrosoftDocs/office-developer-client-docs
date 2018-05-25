---
title: "About meeting requests as informational updates and full updates"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
localization_priority: Normal
ms.assetid: 084928ca-efc0-36da-fe4f-5cc45f226178
description: "A meeting request is an email that has IPM.Schedule.Meeting.Request as the message class. By default, an attendee receiving a meeting request responds to it directly."
---

# About meeting requests as informational updates and full updates

A meeting request is an email that has **IPM.Schedule.Meeting.Request** as the message class. By default, an attendee receiving a meeting request responds to it directly. Outlook supports setting up delegates who can respond to meeting requests on behalf of the principal recipient. Programmatically, Outlook sets the named property [PidLidMeetingType](http://msdn.microsoft.com/library/290b290c-7836-4a7e-bf1a-8d0225a07e56%28Office.15%29.aspx) of a meeting request to identify the current update status. 
  
## Recipients Without Delegates

When Outlook receives a new meeting request, Outlook sets the **PidLidMeetingType** property of the meeting request item to **mtgRequest**. Any subsequent update of that meeting is either **mtgFullUpdate** (a full update) or **mtgInfoUpdate** (an informational update) depending on the cause of the update, with Outlook setting **PidLidMeetingType** accordingly. A full update requires an attendee to explicitly respond to the meeting request, and an informational update does not. 
  
## Full Updates

There are two scenarios that result in a full update:
  
- When an organizer changes the date, time, time zones, or recurrence of a prior meeting request, the organizer must send an update to all the attendees. This update is a full update to which an attendee must explicitly respond to notify the organizer of attendance, because Outlook ignores any previous responses.
    
- If an attendee has not responded to an initial meeting request and receives a subsequent update, the initial meeting request becomes out-of-date and the update is a full update, regardless of the cause of the update.
    
## Informational Updates

There are four scenarios in which Outlook generates an informational update. In these scenarios, responding to the informational update is optional.
  
- If an organizer changes the location of a prior meeting request, the organizer must send an update to all the attendees. If an attendee already accepted the initial meeting request, the attendee receives the update as an informational update.
    
- If an organizer adds an attendee to a prior meeting request, the organizer must send the meeting request to the newly added attendee, and has the option to include existing attendees on the update. The newly added attendee receives the meeting request as a new request. If the organizer chooses to send an update to existing attendees, the attendees receive the update as an informational update.
    
- If an organizer removes an attendee from a prior meeting request, the organizer must send an update to the attendee who was removed from the meeting request and has an option to include existing attendees on the update. Attendees receive the update as an informational update.
    
- If an organizer changes the subject or body of a prior meeting request, the organizer has the option to send an update to the attendees or just save the changes to the organizer's own copy of the meeting request. If the organizer chooses to send an update, attendees receive the update as an informational update.
    
## Recipients Set Up with Delegates

Recipients who choose to set up delegates can have delegates respond to meeting requests that are not marked Private. By default, the principal receives only a copy of a meeting request or a copy of an update to a prior meeting request, and the delegates always receive the original meeting request or original full or informational update. In this default configuration, the principal always receives delegated meeting requests and updates; delegates of the principal receive meeting requests as new meeting requests, full updates, or informational updates, as described for recipients without delegates in the section "Recipients Without Delegates."
  
By default, principals can choose to respond to non-private meeting requests and updates, even though delegates are set up to do that on their behalf. However, as an alternative, administrators can set up a policy to prevent principal recipients from responding.
  

