---
title: "Association element TaskBaseline_Project (ProjectServerData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: e2c4c02d-ee36-4aad-95fe-657fdaae49f1
description: "The TaskBaseline_Project association relates task baselines to a project."
---

# Association element: TaskBaseline_Project (ProjectServerData service)

The **TaskBaseline_Project** association relates task baselines to a project. 
  
## Definition

```XML
<Association Name="TaskBaseline_Project">
  <End Type="ReportingData.TaskBaseline" Role="TaskBaseline" Multiplicity="*" />
  <End Type="ReportingData.Project" Role="Project" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**TaskBaseline_Project** <br/> |Identifies the two entity types that form the **TaskBaseline_Project** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **TaskBaseline_Project** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the TaskBaseline_Project association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**TaskBaseline** <br/> |[EntityType element: TaskBaseline](entitytype-taskbaseline-projectdata-service.md) <br/> |**\*** <br/> |The collection of task baselines in the reporting tables.  <br/> |
|**Project** <br/> |[EntityType element: Project](entitytype-project-projectdata-service.md) <br/> |**0..1** <br/> |The project object being referenced in the **TaskBaseline_Project** association.  <br/> |
   
## Remarks

The **Project** navigation property in the **TaskBaseline** entity uses the **TaskBaseline_Project** association to query for a project that is associated with a collection of task baselines. 
  
## See also

#### Reference

[EntityType element: Project](entitytype-project-projectdata-service.md)
  
[EntityType element: TaskBaseline](entitytype-taskbaseline-projectdata-service.md)

