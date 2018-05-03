---
title: "Outlook Social Connector Provider Interfaces"
ms.author: soliver
author: soliver
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8f92b2c7-9f47-4c84-874b-fec1a2a5b555
description: "The Outlook Social Connector (OSC) is an Office feature shared by Office client applications that connects to social and business networks so users can stay in touch with the people in their networks without leaving Office."
---

# Outlook Social Connector Provider Interfaces

The Outlook Social Connector (OSC) is an Office feature shared by Office client applications that connects to social and business networks so users can stay in touch with the people in their networks without leaving Office. 
  
An OSC provider is a Component Object Model (COM) DLL that allows the OSC to access social network data in a way that is independent of the APIs of each social network. The following table lists the interfaces in OSC provider extensibility. An OSC provider must implement four of the five interfaces to communicate with the OSC: [ISocialPerson](isocialpersoniunknown.md), [ISocialProfile](isocialprofileisocialperson.md), [ISocialProvider](isocialprovideriunknown.md), and [ISocialSession](isocialsessioniunknown.md). If the OSC provider supports synchronizing activities, on-demand or hybrid synchronization of friends, caching logon credentials and logging on using cached credentials, or the ability to follow a person, the provider should implement [ISocialSession2](isocialsession2iunknown.md), as well.
  
|**Name**|**Description**|
|:-----|:-----|
|[ISocialPerson](isocialpersoniunknown.md) <br/> |Represents a person on the social network.  <br/> |
|[ISocialProfile](isocialprofileisocialperson.md) <br/> |Represents the logged-on user.  <br/> |
|[ISocialProvider](isocialprovideriunknown.md) <br/> |Represents an instance of an OSC provider.  <br/> |
|[ISocialSession](isocialsessioniunknown.md) <br/> |Represents a connection to a social network site.  <br/> |
|[ISocialSession2](isocialsession2iunknown.md) <br/> |Supports synchronizing activities, adding friends, on-demand or hybrid synchronization of friends, or logging on to the social network by using cached credentials.  <br/> |
   

