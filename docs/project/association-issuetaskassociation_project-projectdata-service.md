---
title: "Association IssueTaskAssociation_Project (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 1a270f25-89fa-4cfd-bae1-992ce52113e3
description: "The IssueTaskAssociation_Project association relates an issue task assocation to a project."
---

# Association: IssueTaskAssociation_Project (ProjectData service)

The **IssueTaskAssociation_Project** association relates an issue task assocation to a project. 
  
## Definition

```XML
<Association Name="IssueTaskAssociation_Project">
  <End Type="ReportingData.Project" Role="Project" Multiplicity="0..1" />
  <End Type="ReportingData.IssueTaskAssociation" Role="IssueTaskAssociation" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**IssueTaskAssociation_Project** <br/> |Identifies the two entity types that form the **IssueTaskAssociation_Project** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **IssueTaskAssociation_Project** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the IssueTaskAssociation_Project association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**IssueTaskAssociation** <br/> |[EntityType element: IssueTaskAssociation](entitytype-issuetaskassociation-projectdata-service.md) <br/> |**\*** <br/> |The collection of issue task associations in the reporting tables.  <br/> |
|**Project** <br/> |[EntityType element: Project](entitytype-project-projectdata-service.md) <br/> |**0..1** <br/> |The related project that is referenced in the **IssueTaskAssociation_Project** association.  <br/> |
   
## Remarks

The **Project** navigation property in the **IssueTaskAssociation** entity uses the **IssueTaskAssociation_Project** association to query for a project that is associated with a collection of issue task associations. 
  
## See also

#### Reference

[EntityType element: IssueTaskAssociation](entitytype-issuetaskassociation-projectdata-service.md)
  
[EntityType element: Project](entitytype-project-projectdata-service.md)

