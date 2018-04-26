---
title: "Association CostConstraintScenario_CreatedByResource (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 8b907357-c323-4d1c-b9d3-b24b39e8f26e
description: "The CostConstraintScenario_CreatedByResource association relates cost constraint scenarios to a resource."
---

# Association: CostConstraintScenario_CreatedByResource (ProjectData service)

The **CostConstraintScenario_CreatedByResource** association relates cost constraint scenarios to a resource. 
  
## Definition

```XML
<Association Name="CostConstraintScenario_CreatedByResource">
  <End Type="ReportingData.Resource" Role="CreatedByResource" Multiplicity="0..1" />
  <End Type="ReportingData.CostConstraintScenario" Role="CostConstraintScenario" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**CostConstraintScenario_CreatedByResource** <br/> |Identifies the two entity types that form the **CostConstraintScenario_CreatedByResource** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **CostConstraintScenario_CreatedByResource** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the CostConstraintScenario_CreatedByResource association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**CostConstraintScenario** <br/> |[EntityType element: CostConstraintScenario](entitytype-costconstraintscenario-projectdata-service.md) <br/> |**\*** <br/> |The collection of cost constraint scenarios in the reporting tables.  <br/> |
|**CreatedByResource** <br/> |[EntityType element: Resource](entitytype-resource-projectdata-service.md) <br/> |**0..1** <br/> |The resource object that is referenced in the **CostConstraintScenario_CreatedByResource** association.  <br/> |
   
## Remarks

The **CreatedByResource** navigation property of the **CostConstraintScenario** entity type uses the **CostConstraintScenario_CreatedByResource** association to query for a resource that is associated with a collection of cost constraint scenarios. 
  
## See also

#### Reference

[EntityType element: CostConstraintScenario](entitytype-costconstraintscenario-projectdata-service.md)
  
[EntityType element: Resource](entitytype-resource-projectdata-service.md)

