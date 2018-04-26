---
title: "Association IssueTaskAssociation_Task (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 79faed72-9b86-43ff-b4a5-00c6f980296b
description: "The IssueTaskAssociation_Task association relates an issue task assocation to a task."
---

# Association: IssueTaskAssociation_Task (ProjectData service)

The **IssueTaskAssociation_Task** association relates an issue task assocation to a task. 
  
## Definition

```XML
<Association Name="IssueTaskAssociation_Task">
  <End Type="ReportingData.Task" Role="Task" Multiplicity="0..1" />
  <End Type="ReportingData.IssueTaskAssociation" Role="IssueTaskAssociation" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**IssueTaskAssociation_Task** <br/> |Identifies the two entity types that form the **IssueTaskAssociation_Task** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **IssueTaskAssociation_Task** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the IssueTaskAssociation_Task association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**IssueTaskAssociation** <br/> |[EntityType element: IssueTaskAssociation](entitytype-issuetaskassociation-projectdata-service.md) <br/> |**\*** <br/> |The collection issue task associations in the reporting tables.  <br/> |
|**Task** <br/> |[EntityType element: Task](entitytype-task-projectdata-service.md) <br/> |**0..1** <br/> |There is one task that corresponds to a collection of issue task associations.  <br/> |
   
## Remarks

The **Task** navigation property in the **IssueTaskAssociation** entity uses the **IssueTaskAssociation_Task** association to query for a task that is associated with a collection of issue task associations. 
  
## See also

#### Reference

[EntityType element: IssueTaskAssociation](entitytype-issuetaskassociation-projectdata-service.md)
  
[EntityType element: Task](entitytype-task-projectdata-service.md)

