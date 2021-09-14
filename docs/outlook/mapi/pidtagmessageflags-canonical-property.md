---
title: "PidTagMessageFlags Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagMessageFlags
api_type:
- HeaderDef
ms.assetid: 7561112b-ca72-4c49-a8a0-cc1879a4e151
description: "Last modified: March 09, 2015"
---

# PidTagMessageFlags Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a bitmask of flags that indicate the origin and current state of a message. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_MESSAGE_FLAGS  <br/> |
|Identifier:  <br/> |0x0E07  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

This property is a nontransmittable message property exposed at both the sending and receiving ends of a transmission, with different values depending upon the client application or store provider involved. This property is initialized by the client or message store provider when a message is created and saved for the first time and then updated periodically by the message store provider, a transport provider, and the MAPI spooler as the message is processed and its state changes. 
  
This property exists on a message both before and after submission, and on all copies of the received message. Although it is not a recipient property, it is exposed differently to each recipient according to whether it has been read or modified by that recipient. 
  
One or more of the following flags can be set for this property:
  
MSGFLAG_ASSOCIATED 
  
> The message is an associated message of a folder. The client or provider has read-only access to this flag. The MSGFLAG_READ flag is ignored for associated messages, which do not retain a read/unread state. 
    
MSGFLAG_FROMME 
  
> The messaging user sending was the messaging user receiving the message. The client or provider has read/write access to this flag until the first [IMAPIProp::SaveChanges](imapiprop-savechanges.md) call and read-only thereafter. This flag is meant to be set by the transport provider. 
    
MSGFLAG_HASATTACH 
  
> The message has at least one attachment. This flag corresponds to the message's **PR_HASATTACH** ([PidTagHasAttachments](pidtaghasattachments-canonical-property.md)) property. The client has read-only access to this flag. 
    
MSGFLAG_NRN_PENDING 
  
> A nonread report needs to be sent for the message. The client or provider has read-only access to this flag. 
    
MSGFLAG_ORIGIN_INTERNET 
  
> The incoming message arrived over the Internet. It originated either outside the organization or from a source the gateway cannot consider trusted. The client should display an appropriate message to the user. Transport providers set this flag; the client has read-only access. 
    
MSGFLAG_ORIGIN_MISC_EXT 
  
> The incoming message arrived over an external link other than X.400 or the Internet. It originated either outside the organization or from a source the gateway cannot consider trusted. The client should display an appropriate message to the user. Transport providers set this flag; the client has read-only access. 
    
MSGFLAG_ORIGIN_X400 
  
> The incoming message arrived over an X.400 link. It originated either outside the organization or from a source the gateway cannot consider trusted. The client should display an appropriate message to the user. Transport providers set this flag; the client has read-only access. 
    
MSGFLAG_READ 
  
> The message is marked as having been read. This can occur as the result of a call at any time to [IMessage::SetReadFlag](imessage-setreadflag.md) or [IMAPIFolder::SetReadFlags](imapifolder-setreadflags.md). Clients can also set this flag by calling a message's **IMAPIProp::SetProps** method before the message has been saved for the first time. This flag is ignored if the **MSGFLAG_ASSOCIATED** flag is set. 
    
MSGFLAG_RESEND 
  
> The message includes a request for a resend operation with a nondelivery report. The client or provider has read/write access to this flag until the first [IMAPIProp::SaveChanges](imapiprop-savechanges.md) call and read-only thereafter. 
    
MSGFLAG_RN_PENDING 
  
> A read report needs to be sent for the message. The client or provider has read-only access to this flag. 
    
MSGFLAG_SUBMIT 
  
> The message is marked for sending as a result of a call to [IMessage::SubmitMessage](imessage-submitmessage.md). Message store providers set this flag; the client has read-only access. 
    
MSGFLAG_UNMODIFIED 
  
> The outgoing message has not been modified since the first time that it was saved; the incoming message has not been modified since it was delivered. 
    
MSGFLAG_UNSENT 
  
> The message is still being composed. It is saved, but has not been sent. The client or provider has read/write access to this flag until the first [IMAPIProp::SaveChanges](imapiprop-savechanges.md) call and read-only thereafter. If a client doesn't set this flag by the time the message is sent, the message store provider sets it when **IMessage::SubmitMessage** is called. Typically, this flag is cleared after the message is sent. 
    
A client or message store provider can check the current state of the message at any time by calling the [IMAPIProp::GetProps](imapiprop-getprops.md) method to read the flag values. The client or provider can also call the [IMAPIProp::SetProps](imapiprop-setprops.md) method to change any flags that currently have read/write access. 
  
Several of the flags are always read-only. Some are read/write until the first call to the [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method and thereafter become read-only as far as **IMAPIProp::SetProps** is concerned. One of these, MSGFLAG_READ, can be changed later through [IMessage::SetReadFlag](imessage-setreadflag.md) or [IMAPIFolder::SetReadFlags](imapifolder-setreadflags.md). 
  
The initial values for this property are typically MSGFLAG_UNSENT and MSGFLAG_UNMODIFIED to indicate a message that has not yet been sent or changed. When a message is saved for the second time, the message store provider clears the MSGFLAG_UNMODIFIED flag. Another value that a message store provider can set when a message is saved is the MSGFLAG_HASATTACH flag, indicating that the message has one or more attachments. The **PR_HASATTACH** property is computed from this setting. 
  
When a client calls the [IMessage::SubmitMessage](imessage-submitmessage.md) method to send the message, the message store provider makes a copy of it for the MAPI spooler and updates this property by setting the MSGFLAG_SUBMIT flag. The message store provider also sets MSGFLAG_UNSENT if it is not yet set. MSGFLAG_SUBMIT indicates that **SubmitMessage** has been called, beginning the send process, and that the message is now read-only to the client. MSGFLAG_UNSENT indicates that the MAPI spooler is handling the message. If the send process is canceled, the message store provider resets this flag. 
  
When the message is given to a transport provider for delivery, the transport provider sets the MSGFLAG_FROMME flag if the sender had the same account on the messaging server as the message was received on. Transport providers set MSGFLAG_FROMME for an incoming message that was sent by the currently logged on user. A client can use this value to determine that it is more appropriate to show recipient names in the contents table of the Sent Items folder than sender names. Messages that have been saved during the composition process and not yet sent should also be displayed with recipient names rather than sender names. 
  
For an incoming message, a message store provider clears the MSGFLAG_READ flag to reset its read status. A client can set or clear the MSGFLAG_READ flag when it is necessary to change the read status and control the sending of read and nonread reports, by calling either the message's [IMessage::SetReadFlag](imessage-setreadflag.md) method or its folder's [IMAPIFolder::SetReadFlags](imapifolder-setreadflags.md) method. The main difference between these methods, other than the object implementing them, is that the folder method can affect one, several, or all of the messages in the folder. The message method affects a single message. 
  
A client should also test an incoming message for the MSGFLAG_ORIGIN_X400, MSGFLAG_ORIGIN_INTERNET, and MSGFLAG_ORIGIN_MISC_EXT flags. These flags are set by the inbound transport provider and indicate that the message arrived from a source that the gateway cannot consider trusted. This means the message originated either outside the organization, or internally but from a workstation not known to the gateway. In any case, the identity of the sender may not be confirmed, and there is a risk of introducing a computer virus into the organization. The client should display a warning message to the user and offer an option of deleting the message without opening it. 
  
Message store providers set the MSGFLAG_UNMODIFIED flag for incoming messages. MSGFLAG_UNMODIFIED indicates that a message has not been changed since delivery. A client cannot clear this value after it has been set by a message store provider. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCMSG]](https://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[IMsgStore::AbortSubmit](imsgstore-abortsubmit.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

