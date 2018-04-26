---
title: "Association element Prioritization_CreatedByResource (ProjectServerData service)"

 
manager: luken
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: a04098a2-91e4-43a1-b364-3eb293c0bed2
description: "The Prioritization_CreatedByResource association relates prioritizations to a resource."
---

# Association element: Prioritization_CreatedByResource (ProjectServerData service)

The **Prioritization_CreatedByResource** association relates prioritizations to a resource. 
  
## Definition

```XML
<Association Name="Prioritization_CreatedByResource">
  <End Type="ReportingData.Resource" Role="CreatedByResource" Multiplicity="0..1" />
  <End Type="ReportingData.Prioritization" Role="Prioritization" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Prioritization_CreatedByResource** <br/> |Identifies the two entity types that form the **Prioritization_CreatedByResource** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **Prioritization_CreatedByResource** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the Prioritization_CreatedByResource association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**Prioritization** <br/> |[EntityType element: Prioritization](entitytype-prioritization-projectdata-service.md) <br/> |**\*** <br/> |The collection of prioritizations in the reporting tables.  <br/> |
|**CreatedByResource** <br/> |[EntityType element: Resource](entitytype-resource-projectdata-service.md) <br/> |**0..1** <br/> |The resource object that is referenced in the **Prioritization_CreatedByResource** association.  <br/> |
   
## Remarks

The **CreatedByResource** navigation property in the **Prioritization** entity uses the **Prioritization_CreatedByResource** association to query for a resource that is associated with a collection of project prioritizations in a portfolio analysis. 
  
## See also

#### Reference

[EntityType element: Prioritization](entitytype-prioritization-projectdata-service.md)
  
[EntityType element: Resource](entitytype-resource-projectdata-service.md)

