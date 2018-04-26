---
title: "Association element Project_Risks (ProjectServerData service)"

 
manager: luken
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 48692756-c492-482c-bf34-7d396dbc44c7
description: "The Project_Risks_Risk_Project association relates a project to the risks that it contains and relates a risk to its project."
---

# Association element: Project_Risks (ProjectServerData service)

The **Project_Risks_Risk_Project** association relates a project to the risks that it contains and relates a risk to its project. 
  
## Definition

```XML
<Association Name="Project_Risks_Risk_Project">
  <End Type="ReportingData.Risk" Role="Risk_Project" Multiplicity="*" />
  <End Type="ReportingData.Project" Role="Project_Risks" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Project_Risks_Risk_Project** <br/> |Identifies the entity types and the navigation properties that form the two-way association for projects and risks. In the first half of the name, **Project** is the entity type and **Risks** is the navigation property. In the second half of the name, **Risk** is the entity type and **Project** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **Project_Risks_Risk_Project** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the Project_Risks association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**Project_Risks** <br/> |[EntityType element: Project](entitytype-project-projectdata-service.md) <br/> |**0..1** <br/> |There is one project entity that corresponds to a collection of risks.  <br/> |
|**Risk_Project** <br/> |[EntityType element: Risk](entitytype-risk-projectdata-service.md) <br/> |**\*** <br/> |There can be many risk entities in a project.  <br/> |
   
## Remarks

One end of the association is the **Project** entity, and the other end is the **Risk** entity. The **Project** entity type contains the **Risks** navigation property, where the **FromRole** defines **Project_Risks** as the start of the association to get the collection of risks in a project. Similarly, the **Risk** entity type contains the **Project** navigation property, where the **FromRole** defines **Risk_Project** as the start of the association to get the project that is associate with the collection of rsks. 
  
## See also

#### Reference

[EntityType element: Project](entitytype-project-projectdata-service.md)
  
[EntityType element: Risk](entitytype-risk-projectdata-service.md)

