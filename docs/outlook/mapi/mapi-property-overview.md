---
title: "MAPI Property Overview"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 02e5b23f-1bdb-4fbf-a27d-e3301a359573
description: "Last modified: July 23, 2011"
 
 
---

# MAPI Property Overview

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
A property is an attribute of a MAPI object. Properties describe something about the object, such as the subject line of a message or the address type of a messaging user. MAPI defines many properties, some to describe many objects and some that are appropriate only for an object of a particular type. Clients and service providers can extend MAPI's set of predefined properties by creating new, custom properties. Clients can define properties to describe new message classes, and service providers can define properties to expose the unique features of their messaging system.
  
Properties can be persistent or temporary. Properties that persist from session to session can be stored with their objects' data or in the profile. Temporary properties exist only for the duration of the current session. 
  
Clients and service providers can show properties to users with either a table or a property sheet. Tables provide users with a read-only view of some of the properties belonging to multiple objects. The data is displayed in row and column format, with each row representing an object and each column a property. Property sheets are tabbed dialog boxes that display related properties for a single object. Property sheets can provide read-only or read/write access to the data. Whether or not a user is allowed to make changes is up to the implementer of the property sheet.
  
The [IMAPIProp](imapipropiunknown.md) interface is the primary interface for working with properties. All objects that support properties implement **IMAPIProp**. **IMAPIProp** includes methods for retrieving property values, copying properties, making changes and saving those changes, mapping between property names and their identifiers, and retrieving information about a prior error. 
  
There are several data structures for describing properties and information about properties. The most commonly used structures are the [SPropValue](spropvalue.md) structure and the [SPropTagArray](sproptagarray.md) structure. The **SPropValue** structure contains the three pieces of information that describe a property: 
  
- Data, or value, of the property.
    
- Data type of the property's value, such as integer or Boolean. 
    
- Numeric value within a particular range that uniquely identify the property and component responsible for maintaining it. For example, there is a range to hold message content properties defined by MAPI and another range to hold message content properties defined by a client for a custom message class. 
    
The property type and identifier are combined into a single component called the property tag. Property tags are constants that can be used to easily refer to the property. Property tags for properties defined by MAPI are included in the MAPITAGS.H header file and in the **ulPropTag** member of an **SPropValue** structure. Clients and service providers use property tags to identify, retrieve, and update the corresponding properties. 
  
The **SPropTagArray** structure is a counted array of property tags. Many of the methods in **IMAPIProp** and other interfaces use an **SPropTagArray** structure for describing properties. 
  
## See also

#### Other resources

[MAPI Concepts](mapi-concepts.md)

