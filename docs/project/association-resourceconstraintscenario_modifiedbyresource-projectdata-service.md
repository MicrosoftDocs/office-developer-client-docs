---
title: "Association ResourceConstraintScenario_ModifiedByResource (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 6c6cbe4b-44b0-4e23-9592-d9fab0cae517
description: "The ResourceConstraintScenario_ModifiedByResource association relates portfolio analysis resource constraint scenarios to a resource.."
---

# Association: ResourceConstraintScenario_ModifiedByResource (ProjectData service)

The **ResourceConstraintScenario_ModifiedByResource** association relates portfolio analysis resource constraint scenarios to a resource.. 
  
## Definition

```XML
<Association Name="ResourceConstraintScenario_ModifiedByResource">
  <End Type="ReportingData.ResourceConstraintScenario" Role="ResourceConstraintScenario" Multiplicity="*" />
  <End Type="ReportingData.Resource" Role="ModifiedByResource" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**ResourceConstraintScenario_ModifiedByResource** <br/> |Identifies the two entity types that form the **ResourceConstraintScenario_ModifiedByResource** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **ResourceConstraintScenario_ModifiedByResource** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the ResourceConstraintScenario_ModifiedByResource association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**ResourceConstraintScenario** <br/> |[EntityType element: ResourceConstraintScenario](entitytype-resourceconstraintscenario-projectdata-service.md) <br/> |**\*** <br/> |The collection of resource constraint scenarios in the reporting tables.  <br/> |
|**ModifiedByResource** <br/> |[EntityType element: Resource](entitytype-resource-projectdata-service.md) <br/> |**0..1** <br/> |The resource object that is referenced in the **ResourceConstraintScenario_ModifiedByResource** association.  <br/> |
   
## Remarks

The **ModifiedByResource** navigation property in the **ResourceConstraintScenario** entity uses the **ResourceConstraintScenario_ModifiedByResource** association to query for a resource that is associated with a collection of portfolio analysis resource constraint scenarios. 
  
## See also

#### Reference

[EntityType element: Resource](entitytype-resource-projectdata-service.md)
  
[EntityType element: ResourceConstraintScenario](entitytype-resourceconstraintscenario-projectdata-service.md)

