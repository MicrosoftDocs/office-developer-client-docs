---
title: "Types of Restrictions"
description: Outlines types of restrictions, some that focus on specific columns. This applies to Outlook 2013 and Outlook 2016.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 0d3bd58b-7100-4117-91ac-27139715c85b
 
 
---

# Types of Restrictions

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
There are many types of restrictions, some that focus on specific columns. All table implementations are expected to support restrictions on the columns in the current column set. However, to add value, table implementers can also support restrictions based on object properties that are not currently in the table view.
  
Some restrictions can be combined using a restriction that performs a logical **AND**, **OR**, or **NOT** operation. For example, most property restrictions must be joined with exist restrictions using **AND** restrictions. There are a few exceptions, such as when the property used in the property restriction is the **PR_ANR** ([PidTagAnr](pidtaganr-canonical-property.md)) property or when it is a required column in a table. A client building restrictions to limit its view should use exist restrictions with its property restrictions because MAPI does not specify how service providers should evaluate property restrictions when a property does not exist. It is reasonable and recommended that service providers fail the restriction, but there are no requirements. 
  
A restriction is defined using the [SRestriction](srestriction.md) data structure which contains a union of more specialized restriction structures and an indicator of the type of structure included in the union. 
  
Each of the specialized restriction structures in the union represents a different type of restriction. The types of restrictions and their associated data structures are:
  
|**Type of restriction**|**Associated data structure**|**Description**|
|:-----|:-----|:-----|
|Compare property |[SComparePropsRestriction](scomparepropsrestriction.md) |Compares two properties of the same type. |
|**AND** |[SAndRestriction](sandrestriction.md) |Performs a logical **AND** operation on two or more restrictions. |
|**OR** |[SOrRestriction](sorrestriction.md) |Performs a logical **OR** operation on two or more restrictions. |
|**NOT** |[SNotRestriction](snotrestriction.md) |Performs a logical **NOT** operation on two or more restrictions. |
|Content |[SContentRestriction](scontentrestriction.md) |Locates specified data. |
|Property |[SPropertyRestriction](spropertyrestriction.md) |Specifies a particular property value as criteria for matching. Can be used, for example, to search for a particular type of attachment. |
|Bitmask |[SBitMaskRestriction](sbitmaskrestriction.md) |Applies a bitmask to a PT_LONG property, typically to determine whether particular flags are set. |
|Size |[SSizeRestriction](ssizerestriction.md) |Tests the size of a property using standard relational operators. |
|Exist |[SExistRestriction](sexistrestriction.md) |Tests whether an object has a value for a property. |
|Subobject |[SSubRestriction](ssubrestriction.md) |Used for searching through subobjects, or objects that cannot be accessed with an entry identifier, such as recipients and attachments. Can be used, for example, to look for messages for a particular recipient. |
|Comment |[SCommentRestriction](scommentrestriction.md) |Associates an object with a set of named properties. |
   
Some restrictions use regular expressions, and MAPI supports a limited form of regular expression notation in the style that is used many text applications.
  
The comment restriction is used by clients that save restrictions on disk to keep application-specific information with the restriction. For example, a client saving the name of a named property used in a property restriction can do so with a comment restriction. Saving the name is not possible in a property restriction; the [SPropertyRestriction](spropertyrestriction.md) data structure holds only the property tag. Comment restrictions are ignored by [IMAPITable::Restrict](imapitable-restrict.md) in that they have no effect on the rows returned by [IMAPITable::QueryRows](imapitable-queryrows.md) after a **Restrict** call has been made. 
  
## See also



[MAPI Tables](mapi-tables.md)

