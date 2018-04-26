---
title: "Association element PrioritizationDriverRelation_BusinessDriver1 (ProjectServerData service)"

 
manager: luken
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 1d44d647-1504-4d31-a7ec-2f9f6f284dfc
description: "The PrioritizationDriverRelation_BusinessDriver1 association relates project prioritizations in a portfolio analysis to the first business driver."
---

# Association element: PrioritizationDriverRelation_BusinessDriver1 (ProjectServerData service)

The **PrioritizationDriverRelation_BusinessDriver1** association relates project prioritizations in a portfolio analysis to the first business driver. 
  
## Definition

```XML
<Association Name="PrioritizationDriverRelation_BusinessDriver1">
  <End Type="ReportingData.PrioritizationDriverRelation" Role="PrioritizationDriverRelation" Multiplicity="*" />
  <End Type="ReportingData.BusinessDriver" Role="BusinessDriver1" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**PrioritizationDriverRelation_BusinessDriver1** <br/> |Identifies the two entity types that form the **PrioritizationDriverRelation_BusinessDriver1** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **PrioritizationDriverRelation_BusinessDriver1** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the PrioritizationDriverRelation_BusinessDriver1 association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**PrioritizationDriverRelation** <br/> |[EntityType element: PrioritizationDriverRelation](entitytype-prioritizationdriverrelation-projectdata-service.md) <br/> |**\*** <br/> |The collection of prioritization driver relations in the reporting tables.  <br/> |
|**BusinessDriver1** <br/> |[EntityType element: BusinessDriver](entitytype-businessdriver-projectdata-service.md) <br/> |**0..1** <br/> |The business driver object that is referenced in the **PrioritizationDriverRelation_BusinessDriver1** association.  <br/> |
   
## Remarks

The **BusinessDriver1** navigation property in the **PrioritizationDriverRelation** entity uses the **PrioritizationDriverRelation_BusinessDriver1** association to query for a business driver that is associated with a collection of prioritization driver relations. 
  
## See also

#### Reference

[EntityType element: BusinessDriver](entitytype-businessdriver-projectdata-service.md)
  
[EntityType element: PrioritizationDriverRelation](entitytype-prioritizationdriverrelation-projectdata-service.md)

