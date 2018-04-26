---
title: "Association element ResourceScenarioProject_Project (ProjectServerData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 0cb988be-4a83-4789-90a3-690501409018
description: "The ResourceScenarioProject_Project association relates a resource scenario project to its project."
---

# Association element: ResourceScenarioProject_Project (ProjectServerData service)

The **ResourceScenarioProject_Project** association relates a resource scenario project to its project. 
  
## Definition

```XML
<Association Name="ResourceScenarioProject_Project">
  <End Type="ReportingData.ResourceScenarioProject" Role="ResourceScenarioProject" Multiplicity="*" />
  <End Type="ReportingData.Project" Role="Project" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**ResourceScenarioProject_Project** <br/> |Identifies the two entity types that form the **ResourceScenarioProject_Project** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **ResourceScenarioProject_Project** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the ResourceScenarioProject_Project association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**ResourceScenarioProject** <br/> |[EntityType element: ResourceScenarioProject](entitytype-resourcescenarioproject-projectdata-service.md) <br/> |**\*** <br/> |The collection of resource scenario projects in the reporting tables.  <br/> |
|**Project** <br/> |[EntityType element: Project](entitytype-project-projectdata-service.md) <br/> |**0..1** <br/> |The project object that is referenced in the **ResourceScenarioProject_Project** association.  <br/> |
   
## Remarks

The **Project** navigation property in the **ResourceScenarioProject** entity uses the **ResourceScenarioProject_Project** association to query for a project that is associated with a collection of resource scenario projects. 
  
## See also

#### Reference

[EntityType element: Project](entitytype-project-projectdata-service.md)
  
[EntityType element: ResourceScenarioProject](entitytype-resourcescenarioproject-projectdata-service.md)

