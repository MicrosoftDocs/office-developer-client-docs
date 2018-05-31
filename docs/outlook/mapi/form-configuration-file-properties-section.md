---
title: "Form Configuration File [Properties] Section"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: f31a08ce-3a56-4c90-9502-5bcb09d8d80f
description: "Last modified: July 23, 2011"
 
 
---

# Form Configuration File [Properties] Section

  
  
**Applies to**: Outlook 
  
The **[Properties]** section lists the complete set of properties that the form uses and publishes; that is, the properties it creates in its custom messages that MAPI client applications can use when displaying columns, filtering contents tables, setting up search-results folders, and so on. Each entry in this property list references a subsequent **[Property.** _string_ **]** section as shown following. 
  
 **[Properties]**
  
 **Property.** _string_ =  _string_
  
The format of a [ **Property.** _string_] section is: 
  
 **[Property.** _string_ **]**
  
 **Type** =  _integer_
  
 **NmidPropset** =  _guid_
  
 **NmidString** =  _string_
  
 **NmidInteger** =  _integer_
  
 **DisplayName** =  _string_
  
 **Flags** =  _integer_
  
 **SpecialType** = 0|1 
  
 **Enum1** =  _string_
  
Each **[Property.** _string_ **]** section describes a single property. The **Type** entry specifies the MAPI property type, for example 3 (PT_I4), of the property. The **NmidPropset** entry is optional; together with either the **NmidString** entry or the **NmidInteger** entry, the **NmidPropset** entry gives the name of the property. **NmidString** gives the name of the property, while **NmidInteger** gives the identifier of the property. **NmidString** and **NmidInteger** are mutually exclusive. 
  
If set, **NmidPropset** should contain the name of the property set; if absent, **NmidPropset** is set to a default based on the following rule: If **NmidInteger** is present and its value is less than 0x8000, **NmidPropset** is set to PS_MAPI. If the value of **NmidInteger** is set to an integer greater than 0x8000, or if it is absent, **NmidPropset** is set to PS_PUBLIC_STRINGS. 
  
The **DisplayName** entry contains the label for the property. The **SpecialType** entry, if present and nonzero indicates that this property is a special property. At present, the only special property type defined is **SpecialType** = 1, which indicates string enumerated properties. If **SpecialType** is set to 1, the **Enum1** entry references the **[Enum1.** _string_ **]** section. 
  
Following is an example of a **[Properties]** section and a **[Properties.** _string_ **]** section. 
  
```cpp
[Properties]
Property.1 = Fire Hazard
Property.2 = Safe
[Property.Fire Hazard]
Type = 1
NmidPropSet = {E47F4480-8400-101B-934D-04021C007002]
NmidString = FireHazard
DisplayName = Fire Hazard
SpecialType = 1
Enum1 = HazardEnum

```

The **Enum1** entry in the preceeding example references to a subsequent **[Enum1.** _string_ **]** section describing an enumeration of a particular type. Such an enumeration associates the first property in the **[Property.** _string_ **]** section with an integer property, called the index. Such an enumeration also contains a list of the possible values that the display-index pair can assume. Specifying a property type for the enumeration is unnecessary because by definition an **Enum1** entry always has the PT_I4 type. The format for the **[Enum1.** _string_ **]** section is: 
  
 **[Enum1.** _string_ **]**
  
 **NmidPropset** =  _guid_
  
 **NmidString** =  _string_
  
 **NmidInteger** =  _integer_
  
 **EnumCount** =  _integer_
  
 **Val.** _integer_ **.Display** =  _string_
  
 **Val.** _integer_ **.Index** =  _integer_
  
The following is an example property definition for an enumerated property named Fire Hazard with possible values of Low, Medium, and High.
  
```cpp
[Properties]
Property1 = Fire Hazard
[Enum1.HazardEnum]
IdxNmidPropset={E47F4480-8400-101B-934D-04021C007002]
IdxNmidString=FireHazardEnum
EnumCount = 3
Val.1.Display = Low
Val.1.Index = 1
Val.2.Display = Medium
Val.2.Index = 2
Val.3.Display = High
Val.3.Index = 3

```

 **[Enum1.** _string_ **]** sections can be used by applications for two purposes: to speed up the filtering of properties by using the index instead of the string and to sort by a different order than the alphanumeric order of the string values. For example, sorting could be done based on Low-Medium-High order instead of High-Medium-Low order. 
  

