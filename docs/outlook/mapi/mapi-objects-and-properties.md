---
title: "MAPI Objects and Properties"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 0aebf536-dcfb-406d-86ac-65db98c78139
description: "Last modified: July 23, 2011"
 
 
---

# MAPI Objects and Properties

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Some properties are supported by many different types of objects. The following properties are examples of properties that are used by multiple objects:
  
- **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) is a binary identifier used to open objects.
    
- **PR_OBJECT_TYPE** ([PidTagObjectType](pidtagobjecttype-canonical-property.md)) is a constant used to identify the kind of object.
    
- **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)) is a character string used to describe an object to the user.
    
Other properties make sense for a single type of object. The following properties are examples of properties that apply to one type of object:
  
- **PR_MESSAGE_CLASS** ([PidTagMessageClass](pidtagmessageclass-canonical-property.md)) is a character string used to describe the type of a message.
    
- **PR_ROWID** ([PidTagRowid](pidtagrowid-canonical-property.md)) is an integer used to identify a row in a table.
    
- **PR_ATTACH_SIZE** ([PidTagAttachSize](pidtagattachsize-canonical-property.md)) is an integer used to store the number of bytes in an attachment.
    
Still other properties are applicable only for a single type of object in a particular state. Properties of this type are typically message properties. When a message is first created, its set of properties is very small. As it is sent by a client to a recipient through the messaging system, the number of properties needed to describe the message increases. Some of these added properties appear only on the message as it is being delivered while others appear only on the message as it is being sent. Messages also have properties that are associated with the class to which they belong. Report messages, for example, have properties that are not supported by messages of other classes, such as note messages. 
  
Every object has some required properties and may or may not have other optional properties. Required properties are properties that must exist on an object before the object can be successfully saved with its [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method. Clients or service providers using an object can depend on the availability of required properties after the **SaveChanges** call. That is, they can be sure that a call to the object's [IMAPIProp::GetProps](imapiprop-getprops.md) method or [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method to retrieve these properties will succeed. 
  
Optional properties are properties that, depending on the object's implementer, may or may not be supported by an object. A client or service provider using the object cannot expect optional properties to be available through the **GetProps** or **OpenProperty** methods and to be set to valid values. 
  
For a list or properties in the this Reference, see [MAPI Properties](mapi-properties.md). Descriptions of properties belonging to each of the message store and address book objects can be found in the discussion of the object's standard interface. For example, folder properties are discussed with **IMAPIFolder** and messaging user properties are discussed with **IMailUser**. Message properties, including report message properties, are described with **IMessage** and in [Message Properties Overview](message-properties-overview.md). Properties belonging to each of the different types of tables are described in the appropriate [MAPI Tables](mapi-tables.md) topic. For example, hierarchy table properties are described in [Hierarchy Tables](hierarchy-tables.md). Properties belonging to form servers are describing in [Choosing a Form's Property Set](choosing-a-form-s-property-set.md).
  
When a client or service provider calls an object's **GetProps** method to retrieve several of its properties and one of these properties is unavailable, **GetProps** returns the warning MAPI_W_ERRORS_RETURNED. The call is considered to be successful because some of the properties were returned. When a client or service provider calls **OpenProperty** and the target property is unavailable, the method fails with the error MAPI_E_NOT_FOUND. It is important to check that a requested property is returned before attempting to work with it. 
  
Depending on the object, the service provider supplying the implementation, and the property, a property can have read/write or read-only permission. Read/write permission allows a client or service provider using the property to change its value; read-only permission allows only the service provider owning the object to make changes. 
  
To find out exactly which properties are currently set for an object, call [IMAPIProp::GetPropList](imapiprop-getproplist.md). The **GetPropList** method lets a caller find out what is available before an attempt to open a potentially nonexistent property is made. Because there is no standard set of properties that all objects of a specific type support, it is impossible to guess whether or not an object supports a particular property. Calling **GetPropList** eliminates the guess work. 
  
## See also



[MAPI Objects and Properties](mapi-objects-and-properties.md)

