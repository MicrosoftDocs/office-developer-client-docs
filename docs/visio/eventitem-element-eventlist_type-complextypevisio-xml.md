---
title: "EventItem element (EventList_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 6b347117-a1c1-d090-0d71-ea8528ac70c6
description: "Encapsulates an event code."
---

# EventItem element (EventList_Type complexType) (Visio XML)

Encapsulates an event code.
  
## Element information

|||
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
|[EventList](eventlist-element-visiodocument_type-complextypevisio-xml.md) <br/> |[EventList_Type](eventlist_type-complextypevisio-xml.md) <br/> |Contains an **EventItem** element for each event to which an object should respond.  <br/> |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|Action  <br/> |xsd:unsignedShort  <br/> |required  <br/> |Specifies the action code of the parent **EventItem** element.  <br/> |Values of the xsd:unsignedShort type.  <br/> |
|Enabled  <br/> |xsd:boolean  <br/> |optional  <br/> |Represents a flag indicating if the event is enabled or disabled.  <br/> |Values of the xsd:boolean type.  <br/> |
|EventCode  <br/> |xsd:unsignedShort  <br/> |required  <br/> |A code indicating the event that triggers the add-on.  <br/> |Values of the xsd:unsignedShort type.  <br/> |
|ID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |The ID of the event.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|Target  <br/> |xsd:string  <br/> |required  <br/> |Specifies the target of an event.  <br/> |Values of the xsd:string type.  <br/> |
|TargetArgs  <br/> |xsd:string  <br/> |required  <br/> |Specifies a string containing arguments to be sent to the target of an event.  <br/> |Values of the xsd:string type.  <br/> |
   

