---
title: "Association RiskTaskAssociation_Task (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 782243d9-e2e9-4351-bee3-5ea41d953eaa
description: "The RiskTaskAssociation_Task association relates a task to a risk task association."
---

# Association: RiskTaskAssociation_Task (ProjectData service)

The **RiskTaskAssociation_Task** association relates a task to a risk task association. 
  
## Definition

```XML
<Association Name="RiskTaskAssociation_Task">
  <End Type="ReportingData.Task" Role="Task" Multiplicity="0..1" />
  <End Type="ReportingData.RiskTaskAssociation" Role="RiskTaskAssociation" Multiplicity="*" />
</Association>

```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**RiskTaskAssociation_Task** <br/> |Identifies the two entity types that form the **RiskTaskAssociation_Task** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **RiskTaskAssociation_Task** association element contains two **End** elements that represent opposite ends of an association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the RiskTaskAssociation_Task association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**RiskTaskAssociation** <br/> |[EntityType element: RiskTaskAssociation](entitytype-risktaskassociation-projectdata-service.md) <br/> |**\*** <br/> |The collection of risk task associations in the reporting tables.  <br/> |
|**Task** <br/> |[EntityType element: Task](entitytype-task-projectdata-service.md) <br/> |**0..1** <br/> |The task that is referenced in the **RiskTaskAssociation_Task** association.  <br/> |
   
## Remarks

The **Task** navigation property in the **RiskTaskAssociation** entity uses the **RiskTaskAssociation_Task** association to query tasks that are associated with a collection of risk task assocations. 
  
## See also

#### Reference

[EntityType element: RiskTaskAssociation](entitytype-risktaskassociation-projectdata-service.md)
  
[EntityType element: Task](entitytype-task-projectdata-service.md)

