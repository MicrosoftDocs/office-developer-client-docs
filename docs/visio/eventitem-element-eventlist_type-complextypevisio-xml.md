---
title: "EventItem element (EventList_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 6b347117-a1c1-d090-0d71-ea8528ac70c6
description: "Encapsulates an event code."
---

# EventItem element (EventList_Type complexType) (Visio XML)

Encapsulates an event code.
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[EventItem_Type](eventitem_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |document.xml  <br/> |
   
## Definition

```XML
< xs:element name="EventItem" type="EventItem_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[EventList](eventlist-element-visiodocument_type-complextypevisio-xml.md) <br/> |[EventList_Type](eventlist_type-complextypevisio-xml.md) <br/> |Contains an **EventItem** element for each event to which an object should respond. |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|Action  <br/> |xsd:unsignedShort  <br/> |required  <br/> |Specifies the action code of the parent **EventItem** element. |Values of the xsd:unsignedShort type. |
|Enabled  <br/> |xsd:boolean  <br/> |optional  <br/> |Represents a flag indicating if the event is enabled or disabled. |Values of the xsd:boolean type. |
|EventCode  <br/> |xsd:unsignedShort  <br/> |required  <br/> |A code indicating the event that triggers the add-on. |Values of the xsd:unsignedShort type. |
|ID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |The ID of the event. |Values of the xsd:unsignedInt type. |
|Target  <br/> |xsd:string  <br/> |required  <br/> |Specifies the target of an event. |Values of the xsd:string type. |
|TargetArgs  <br/> |xsd:string  <br/> |required  <br/> |Specifies a string containing arguments to be sent to the target of an event. |Values of the xsd:string type. |
   

