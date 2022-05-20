---
title: "SPropertyRestriction"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SPropertyRestriction
api_type:
- COM
ms.assetid: 2bbf13e9-05b3-4498-8e08-d9e07505190d
description: "Describes a property restriction that is used to match a constant with the value of a property."
---

# SPropertyRestriction

**Applies to**: Outlook 2013 | Outlook 2016
  
Describes a property restriction that is used to match a constant with the value of a property.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |

```cpp
typedef struct _SPropertyRestriction
{
  ULONG relop;
  ULONG ulPropTag;
  LPSPropValue lpProp;
} SPropertyRestriction;

```

## Members

**relop**
  
> Relational operator that will be used in the search. Possible values are as follows:

- RELOP_GE: The comparison is made based on a greater or equal first value.

- RELOP_GT: The comparison is made based on a greater first value.

- RELOP_LE: The comparison is made based on a lesser or equal first value.

- RELOP_LT: The comparison is made based on a lesser first value.

- RELOP_NE: The comparison is made based on unequal values.

- RELOP_RE: The comparison is made based on LIKE (regular expression) values.

- RELOP_EQ: The comparison is made based on equal values.

**ulPropTag**
  
> Property tag identifying the property to be compared.

**lpProp**
  
> Pointer to an [SPropValue](spropvalue.md) structure that contains the constant value that will be used in the comparison.

## Remarks

There are two property tags in an **SPropertyRestriction** structure. One is in the **ulPropTag** member and the other is in the **ulPropTag** member of the **SPropValue** structure pointed to by **lpProp**. MAPI requires both the property identifier field and the property type field. The **ulPropTag** in **SPropertyRestriction** is the property to be matched, and the **lpProp** pointer of the **SPropertyRestriction** to the **ulPropTag**'s type of the **SPropValue** indicates how the members value of the **lpProp** union are interpreted. The two property types must match, or else the error value MAPI_E_TOO_COMPLEX is returned when the restriction is used in a call to [IMAPITable::Restrict](imapitable-restrict.md) or [IMAPITable::FindRow](imapitable-findrow.md).
  
The comparison order is  _(property value) (relational operator) (constant value)_.
  
When a property restriction is passed to **IMAPITable::Restrict** or **IMAPITable::FindRow** and the target property does not exist, the results of the restriction are undefined. By creating an **AND** restriction that joins the property restriction with an **EXIST** restriction, a caller can be guaranteed accurate results. Use an [SExistRestriction](sexistrestriction.md) structure to define the **EXIST** restriction and an [SAndRestriction](sandrestriction.md) structure to define the **AND** restriction.
  
Multi-valued property tags can be used in property restrictions if the service provider implementing the table supports them. If supported, multi-valued property tags can be used anywhere single-valued property tags can be used.
  
Multi-valued property tags can be used in the following methods:
  
- [IMAPIProp::SetProps](imapiprop-setprops.md)

- [IMAPIProp::GetProps](imapiprop-getprops.md)

- [IMAPITable::SetColumns](imapitable-setcolumns.md)

- [IMAPITable::SortTable](imapitable-sorttable.md)

- [IMAPITable::Restrict](imapitable-restrict.md)

> [!IMPORTANT]
> A notable case when the two property tags won't match is if restricting on a multi-value property. In this case the following must be true.
> If the property type of the **ulPropTag** of **SPropertyRestriction** contains the multi-value property type bit flag MV_FLAG (0x1000), the property type of the **ulPropTag** of **SPropValue** should match the former minus the MV_FLAG bit flag, that is, its inverse. > For example, to restrict using a multi-value custom string property such as a category with a property tag for the property 0x8012101f, that is, PROP_TAG(MV_FLAG|PT_UNICODE, 0x8012)), the corresponding **SPropertyRestriction** would appear as follows.
> `SPropertyRestriction.ulPropTag = 0x8012101f; // attempt to restrict a MultiValue property`
> `SPropertyRestriction.lpProp->ulPropTag = 0x8012001f; // the lpszW member of the Value property is valid`> `SPropertyRestriction.lpProp.Value->lpszW = L"My Category";`> Note that if the property type of the **ulPropTag** of **SPropValue** contains the MV_FLAG bit flag, the likely return is MAPI_E_TOO_COMPLEX.
  
For more information about the **SPropertyRestriction** structure, see [About Restrictions](about-restrictions.md).
  
## See also

- [SExistRestriction](sexistrestriction.md)
- [SAndRestriction](sandrestriction.md)
- [SPropValue](spropvalue.md)
- [SRestriction](srestriction.md)
- [IMAPITable::FindRow](imapitable-findrow.md)
- [IMAPITable::Restrict](imapitable-restrict.md)
- [MAPI Structures](mapi-structures.md)
