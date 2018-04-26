---
title: "Association Prioritization_PrioritizationDrivers_PrioritizationDriver_Prioritization (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 9afade56-4b68-42c7-952b-13fa7d1e17bf
description: "The Prioritization_PrioritizationDrivers_PrioritizationDriver_Prioritization association relates a prioritization to the prioritization drivers that it contains and relates a collection of prioritization drivers to its prioritization."
---

# Association: Prioritization_PrioritizationDrivers_PrioritizationDriver_Prioritization (ProjectData service)

The **Prioritization_PrioritizationDrivers_PrioritizationDriver_Prioritization** association relates a prioritization to the prioritization drivers that it contains and relates a collection of prioritization drivers to its prioritization. 
  
## Definition

```XML
<Association Name="Prioritization_PrioritizationDrivers_PrioritizationDriver_Prioritization">
  <End Type="ReportingData.PrioritizationDriver" Role="PrioritizationDriver_Prioritization" Multiplicity="*" />
  <End Type="ReportingData.Prioritization" Role="Prioritization_PrioritizationDrivers" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Prioritization_PrioritizationDrivers_PrioritizationDriver_Prioritization** <br/> |Identifies the entity types and the navigation properties that form the two-way association for prioritizations and prioritization drivers. In the first half of the name, **Prioritization** is the entity type and **PrioritizationDrivers** is the navigation property. In the second half of the name, **PrioritizationDriver** is the entity type and **Prioritization** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **Prioritization_PrioritizationDrivers_PrioritizationDriver_Prioritization** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the Prioritization_PrioritizationDrivers_PrioritizationDriver_Prioritization association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**Prioritization_PrioritizationDrivers** <br/> |[EntityType element: Prioritization](entitytype-prioritization-projectdata-service.md) <br/> |**0..1** <br/> |There is one prioritization entity that corresponds to a collection of prioritization drivers.  <br/> |
|**PrioritizationDriver_Prioritization** <br/> |[EntityType element: PrioritizationDriver](entitytype-prioritizationdriver-projectdata-service.md) <br/> |**\*** <br/> |There can be many prioritization drivers that correspond with a prioritization.  <br/> |
   
## Remarks

One end of the association is the **Prioritization** entity, and the other end is the **PrioritizationDriver** entity. The **Prioritization** entity type contains the **PrioritizationDrivers** navigation property, where the **FromRole** defines **Prioritization_PrioritizationDrivers** as the start of the association to get the collection of prioritization drivers that are associated with a prioritization. Similarly, the **PrioritizationDriver** entity type contains the **Prioritization** navigation property, where the **FromRole** defines **PrioritizationDriver_Prioritization** as the start of the association to get the prioritization that is associated with a collection of prioritization drivers. 
  
## See also

#### Reference

[EntityType element: Prioritization](entitytype-prioritization-projectdata-service.md)
  
[EntityType element: PrioritizationDriver](entitytype-prioritizationdriver-projectdata-service.md)

