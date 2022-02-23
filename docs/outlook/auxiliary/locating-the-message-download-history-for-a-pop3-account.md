---
title: "Locating the message download history for a POP3 account"
manager: soliver
ms.date: 09/17/2015
ms.audience: Developer
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: 90a51150-5c2c-4d5b-8717-5dacc8532744
description: "This topic describes how a mail client can access the PidTagAttachDataBinary property to get the message download history for a POP3 account."
---

# Locating the message download history for a POP3 account

This topic describes how a mail client can access the [PidTagAttachDataBinary](https://msdn.microsoft.com/library/3b0a8b28-863e-4b96-a4c0-fdb8f40555b9%28Office.15%29.aspx) property to get the message download history for a POP3 account.

<a name="OL15Con_AuxRef_LocatingMsgsUIDLHistory_WhyGetUIDLHistory"> </a>

## Why get the message download history?

The Post Office Protocol (POP) provider for Outlook allows users to retrieve and download new email messages on their local device, and subsequently to leave or delete these email messages on the mail server. When the mail client checks for new messages to download, it has to be able to identify and download only the new messages for that Inbox. The mail client does this by first using the UIDL (Unique ID Listing) command, which obtains a map of each message that has ever been delivered to that Inbox to a unique identifier (UID). The client also gets the message download history for messages that have been downloaded or deleted for the Inbox on that client. Using the message UID map and download history, the client can then identify those messages that are absent in the history as new and, hence, should be downloaded.
  
To get the message download history for an Inbox:
  
- Follow the steps in this topic to find the **PidTagAttachDataBinary** property, which contains the history in a binary large object (BLOB) that follows a specific format.

- Continue with [Parsing the message download history for a POP3 account](parsing-the-message-download-history-for-a-pop3-account.md), which describes how to parse this BLOB to identify messages that have been downloaded or deleted for that Inbox.

## Core concepts to know for locating the message download history

The message download history for an Inbox is stored in a binary MAPI property, **PidTagAttachDataBinary**, on an attachment of a hidden message in the Inbox. Table 1 shows resources for concepts that help you understand how to locate the message download history.
  
**Table 1. Core concepts**

|**Article title**|**Description**|
|:-----|:-----|
|[MAPI Hidden Folders](https://msdn.microsoft.com/library/8b3b9c80-f7f4-4f37-bd6b-323469d020f1%28Office.15%29.aspx) <br/> |MAPI allows mail clients to store information in hidden folders and hidden messages. Hidden folders are in the associated part of MAPI folders and typically contain information that is not visible to and not to be manipulated by users. Clients decide the format and contents to store in hidden messages in hidden folders. |
|[MAPI Messages](https://msdn.microsoft.com/library/417c113f-bd98-4515-85d1-09db7fc3a227%28Office.15%29.aspx) <br/> |MAPI stores messages in folders, either in the standard IPM subtree that is visible to users of a client, or outside of the subtree and invisible to users. Messages can have additional data stored in an attachment, which can be in the form of a file, another message, or an OLE object. In the case of the message download history, the history is stored in a property of a message that is attached to another hidden message. |
|[Message Properties Overview](https://msdn.microsoft.com/library/447f54de-9f0d-4f73-89b6-bed9cfea9c15%28Office.15%29.aspx) <br/> |When a client stores information in a message, it actually stores the information in a property of the message. MAPI supports many properties—some always exist and can be set by clients, others are optional—and clients cannot expect them to be available or set to valid values. The message download history is stored in the **PidTagAttachDataBinary** property of an attachment to a hidden message. |
|[MAPI Profiles](https://msdn.microsoft.com/library/493c87a4-317d-47ec-850b-342cac59594b%28Office.15%29.aspx) <br/> |At logon time in a session, the mail client selects a profile that describes the providers and services to be used. A profile is divided into sections that contain properties. In particular, the [PidTagSearchKey](https://msdn.microsoft.com/library/fcab369a-a1f4-4425-a272-e35046914a4d%28Office.15%29.aspx) (**PR_SEARCH_KEY**) and [PidTagProfileName](https://msdn.microsoft.com/library/13ca726d-ae7a-4da9-9c8e-3db3c479f839%28Office.15%29.aspx) (**PR_PROFILE_NAME**) properties always exist. A profile's search key is unique among all profiles, and is stored in the profile section that is identified by **MUID_PROFILE_INSTANCE** (which is defined in MAPIGUID.H). Use [IMAPISession::OpenProfileSection](https://msdn.microsoft.com/library/e2757028-27e7-4fc0-9674-e8e30737ef1d%28Office.15%29.aspx) to open the section, and use [IMAPIProp::GetProps](https://msdn.microsoft.com/library/1c7a9cd2-d765-4218-9aee-52df1a2aae6c%28Office.15%29.aspx) to get the property values. |
|[Contents Tables](https://msdn.microsoft.com/library/7b8efb4e-b5be-41b8-81bb-9aa1da421433%28Office.15%29.aspx) <br/> |Message store providers implement contents tables for their folders. For hidden messages in the associated part of a folder, message store providers support associated contents tables, and clients can use the [IMAPIContainer::GetContentsTable](https://msdn.microsoft.com/library/88c7a666-875d-473a-b126-dbbb7009f7d9%28Office.15%29.aspx) method to return a pointer to the associated contents table. |
|[About Restrictions](https://msdn.microsoft.com/library/e119fa20-08b8-4c8d-93fc-56037220890d%28Office.15%29.aspx) <br/> [Types of Restrictions](https://msdn.microsoft.com/library/0d3bd58b-7100-4117-91ac-27139715c85b%28Office.15%29.aspx) <br/> [Building a Restriction](https://msdn.microsoft.com/library/12abbd8c-f825-493e-af42-344371d9658e%28Office.15%29.aspx) <br/> [Sample Restriction Code](https://msdn.microsoft.com/library/9b82097c-dbd6-4ba0-a6cb-292301f9402b%28Office.15%29.aspx) <br/> |In MAPI, clients can use restrictions to filter contents tables, to search for rows that represent messages that have a certain property set to a specific value. Restrictions are defined by using the [SRestriction](https://msdn.microsoft.com/library/c12b4409-da6f-480b-87af-1e5baea2e8bd%28Office.15%29.aspx) data structure, which can contain a union of more specialized restriction structures. The [IMAPITable::FindRow](https://msdn.microsoft.com/library/6511368c-9777-497e-9eea-cf390c04b92e%28Office.15%29.aspx) method applies a restriction and retrieves the first row in a table that matches the restriction criteria. |
|[About Registering Stores for Indexing](https://msdn.microsoft.com/library/dd2aa06a-96e8-1291-18b5-fc3c40b74e4d%28Office.15%29.aspx) <br/> |Use the [PidTagStoreProvider](https://msdn.microsoft.com/library/6f6cc66f-a08e-4f8e-b33a-d3674319248e%28Office.15%29.aspx) (**PR_MDB_PROVIDER**) property to verify the type of store provider. For example, to verify whether a store is an Exchange store, the **PidTagStoreProvider** property should return a value represented by the constant **pbExchangeProviderPrimaryUserGuid**, which is defined in the public header file edkmdb.h. |

## Locating the appropriate hidden message and attachment

Now that we know the message download history for an Inbox is in the **PidTagAttachDataBinary** property of an attachment to a hidden message, the procedure to locate the appropriate attachment of the appropriate hidden message involves the following procedures:
  
1. [Find the appropriate hidden message](#OL15Con_AuxRef_LocatingMsgsUIDLHistory_FindHiddenMsg)

2. [Find the appropriate attachment of the hidden message](#OL15Con_AuxRef_LocatingMsgsUIDLHistory_FindAttachment)

3. [Access the PidTagAttachDataBinary property of the message attachment](#OL15Con_AuxRef_LocatingMsgsUIDLHistory_AccessProp)

<a name="OL15Con_AuxRef_LocatingMsgsUIDLHistory_FindHiddenMsg"> </a>

### Find the appropriate hidden message

1. Get the [PidTagSearchKey](https://msdn.microsoft.com/library/fcab369a-a1f4-4425-a272-e35046914a4d%28Office.15%29.aspx) (**PR_SEARCH_KEY**) property from the profile, in the profile section specified by **MUID_PROFILE_INSTANCE**.

2. Open the Associated Contents for the Inbox folder by calling **IMAPIContainer::GetContentsTable**.

3. Create a restriction based on the [PidTagConversationKey](https://msdn.microsoft.com/library/52c97d6c-7f4b-4522-aeac-0c1ed8475952%28Office.15%29.aspx) (**PR_CONVERSATION_KEY**), **PidTagSearchKey** (**PR_SEARCH_KEY**), and [PidTagMessageClass](https://msdn.microsoft.com/library/1e704023-1992-4b43-857e-0a7da7bc8e87%28Office.15%29.aspx) (**PR_MESSAGE_CLASS**) properties to get a table that contains all the hidden messages in the Associated Contents of the Inbox. The following is an example of a restriction extracted from [Locating the POP3 UIDL History](https://blogs.msdn.com/b/stephen_griffin/archive/2012/12/03/locating-the-pop3-uidl-history.aspx).

   ```cpp
      SRestriction rgRes[3]; 
      SPropValue rgProps[3]; 
      rgRes[0].rt = RES_AND; 
      rgRes[0].res.resAnd.cRes = 2; 
      rgRes[0].res.resAnd.lpRes = &amp;rgRes[1]; 
      rgRes[1].rt = RES_PROPERTY; 
      rgRes[1].res.resProperty.relop = RELOP_EQ; 
      rgRes[1].res.resProperty.ulPropTag = PR_CONVERSATION_KEY; 
      rgRes[1].res.resProperty.lpProp = &amp;rgProps[0]; 
      rgRes[2].rt = RES_PROPERTY; 
      rgRes[2].res.resProperty.relop = RELOP_EQ; 
      rgRes[2].res.resProperty.ulPropTag = PR_MESSAGE_CLASS; 
      rgRes[2].res.resProperty.lpProp = &amp;rgProps[1]; 
      rgProps[0].ulPropTag = PR_CONVERSATION_KEY; 
      rgProps[0].Value.bin = pVals[iSearchKey].Value.bin; // PR_SEARCH_KEY from the profile 
      rgProps[1].ulPropTag = PR_MESSAGE_CLASS; 
      rgProps[1].Value.LPSZ = (LPTSTR)"IPM.MessageManager";
   ```

4. From the table, find the hidden message by using **IMAPITable::FindRow**.

5. If step 4 fails to find a hidden message, change the restriction to use **PidTagSearchKey** (**PR_SEARCH_KEY**) instead of **PidTagConversationKey**, as shown below:

   ```cpp
    rgRes[1].res.resProperty.ulPropTag = rgProps[0].ulPropTag = PR_SEARCH_KEY;
   ```

6. Find the hidden message using **IMAPITable::FindRow**.

7. If Step 6 fails, change the restriction to use [PidTagSubject](https://msdn.microsoft.com/library/aa7ba4d9-c5e0-4ce7-a34e-65f675223bc9%28Office.15%29.aspx) (**PR_SUBJECT**) being equal to the following value (shown below using `printf` style substitution for brevity).

   ```cpp
    "Outlook Message Manager (%s) (KEY: %s)", PR_PROFILE_NAME, HexFromBin(PR_SEARCH_KEY)
   ```

8. Find the hidden message by using **IMAPITable::FindRow**.

9. If you are running Outlook 2010 or a later version, use the following values for **PidTagProfileName** (**PR_PROFILE_NAME**) and **PidTagSearchKey** (**PR_SEARCH_KEY**), respectively.

   ```cpp
    CHAR g_szGeneralKey[] = "General Key"; 
    const SBinary g_binGeneralKey = {sizeof(g_szGeneralKey), (LPBYTE)g_szGeneralKey};
   ```

   Run through Steps 3 through 8. If this fails to find a message, fall back to the original steps 3 through 8.

10. Open the hidden message found in Step 4, 6, or 8.

<a name="OL15Con_AuxRef_LocatingMsgsUIDLHistory_FindAttachment"> </a>

### Find the appropriate attachment of the hidden message

Because the hidden message may have more than one attachment, look for the appropriate attachment in the following order.
  
> [!NOTE]
> This procedure again uses the `printf` style substitution for brevity.

1. Look for an attachment whose [PidTagAttachLongFilename](https://msdn.microsoft.com/library/83b69e8f-0b5a-4992-b5b8-160d3bdfa22a%28Office.15%29.aspx) (**PR_ATTACH_LONG_FILENAME**) matches the following string, where `szEmailAddress` is the user's SMTP address, as specified in the user's profile. .

   ```cpp
    "BlobPOP%s", szEmailAddress
   ```

2. Look for an attachment whose [PidTagAttachFilename](https://msdn.microsoft.com/library/cbf34dd6-7733-47f6-9c41-9d82656ca9dc%28Office.15%29.aspx) (**PR_ATTACH_FILENAME**) matches "BlobPOP%s", `szEmailAddress`.

3. Look for an attachment whose [PidTagDisplayName](https://msdn.microsoft.com/library/bd094e00-5c60-4bb3-9a45-b943fab52876%28Office.15%29.aspx) (**PR_DISPLAY_NAME**) matches "BlobPOP%s", `szEmailAddress`.

4. Look for an attachment whose **PidTagAttachFilename** (**PR_ATTACH_FILENAME**) matches "Blob%.8x", `dwAcctUID`, where `dwAcctUID` comes from [PROP_ACCT_MINI_UID](prop_acct_mini_uid.md). You can use the [IOlkAccount::GetProp](iolkaccount-getprop.md) method to access the **PROP_ACCT_MINI_UID** property.

<a name="OL15Con_AuxRef_LocatingMsgsUIDLHistory_AccessProp"> </a>

### Access the PidTagAttachDataBinary property of the message attachment

After locating the appropriate message attachment of the hidden message, use **IMAPIProp::GetProps** to read the **PidTagAttachDataBinary** property of the attachment.

<a name="OL15Con_AuxRef_LocatingMsgsUIDLHistory_NextSteps"> </a>

## Next steps

You have learned from this topic how to locate the message download history for the Inbox of a POP3 mail client. See [Parsing the message download history for a POP3 account](parsing-the-message-download-history-for-a-pop3-account.md) to learn how to parse this history to identify messages that have been downloaded or deleted for the Inbox.

<a name="OL15Con_AuxRef_LocatingMsgsUIDLHistory_AdditionalRsc"> </a>

## See also

- [Managing message downloads for POP3 accounts](managing-message-downloads-for-pop3-accounts.md)
- [Parsing the message download history for a POP3 account](parsing-the-message-download-history-for-a-pop3-account.md)
- [Locating the POP3 UIDL History](https://blogs.msdn.com/b/stephen_griffin/archive/2012/12/03/locating-the-pop3-uidl-history.aspx)
