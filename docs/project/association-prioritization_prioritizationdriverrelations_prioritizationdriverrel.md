---
title: "Association Prioritization_PrioritizationDriverRelations_PrioritizationDriverRelation_Prioritization (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: ab90b6e7-aa17-4bee-b2f4-aa0742ed017c
description: "The Prioritization_PrioritizationDriverRelations_PrioritizationDriverRelation_Prioritization association relates a prioritization to prioritization driver relations and relates prioritization driver relations to a prioritization."
---

# Association: Prioritization_PrioritizationDriverRelations_PrioritizationDriverRelation_Prioritization (ProjectData service)

The **Prioritization_PrioritizationDriverRelations_PrioritizationDriverRelation_Prioritization** association relates a prioritization to prioritization driver relations and relates prioritization driver relations to a prioritization. 
  
## Definition

```XML
<Association Name="Prioritization_PrioritizationDriverRelations_PrioritizationDriverRelation_Prioritization">
  <End Type="ReportingData.PrioritizationDriverRelation" Role="PrioritizationDriverRelation_Prioritization" Multiplicity="*" />
  <End Type="ReportingData.Prioritization" Role="Prioritization_PrioritizationDriverRelations" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Prioritization_PrioritizationDriverRelations_PrioritizationDriverRelation_Prioritization** <br/> |Identifies the entity types and the navigation properties that form the two-way association for prioritizations and prioritization driver relations. In the first half of the name, **Project** is the entity type and **PrioritizationDriverRelations** is the navigation property. In the second half of the name, **PrioritizationDriverRelation** is the entity type and **Prioritization** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **Prioritization_PrioritizationDriverRelations_PrioritizationDriverRelation_Prioritization** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the Prioritization_PrioritizationDriverRelations_PrioritizationDriverRelation_Prioritization association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**Prioritization_PrioritizationDriverRelations** <br/> |[EntityType element: Prioritization](entitytype-prioritization-projectdata-service.md) <br/> |**0..1** <br/> |There is one prioritization entity that corresponds to a collection of prioritization driver relations.  <br/> |
|**PrioritizationDriverRelation_Prioritization** <br/> |[EntityType element: PrioritizationDriverRelation](entitytype-prioritizationdriverrelation-projectdata-service.md) <br/> |**\*** <br/> |There can be many prioritization driver relations entities in a prioritization.  <br/> |
   
## Remarks

One end of the association is the **Prioritization** entity, and the other end is the **PrioritizationDriverRelation** entity. The **Prioritization** entity type contains the **PrioritizationDriverRelations** navigation property, where the **FromRole** defines **Prioritization_PrioritizationDriverRelations** as the start of the association to get the collection of prioritization driver relations in a prioritization. Similarly, the **PrioritizationDriverRelation** entity type contains the **Prioritization** navigation property, where the **FromRole** defines **PrioritizationDriverRelation_Prioritization** as the start of the association to get the prioritization that is associated with a collection of prioritization driver relations. 
  
## See also

#### Reference

[EntityType element: Prioritization](entitytype-prioritization-projectdata-service.md)
  
[EntityType element: PrioritizationDriverRelation](entitytype-prioritizationdriverrelation-projectdata-service.md)

