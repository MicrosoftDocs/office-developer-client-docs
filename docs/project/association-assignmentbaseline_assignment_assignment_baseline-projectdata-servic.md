---
title: "Association AssignmentBaseline_Assignment_Assignment_Baseline (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: e41be1c3-6678-455f-9ed7-cb75b4e1e206
description: "The AssignmentBaseline_Assignment_Assignment_Baseline association relates an assignment baseline to the assignments that it contains and relates an assignment to its baseline."
---

# Association: AssignmentBaseline_Assignment_Assignment_Baseline (ProjectData service)

The **AssignmentBaseline_Assignment_Assignment_Baseline** association relates an assignment baseline to the assignments that it contains and relates an assignment to its baseline. 
  
## Definition

```XML
<Association Name="AssignmentBaseline_Assignment_Assignment_Baseline">
  <End Type="ReportingData.Assignment" Role="Assignment_Baseline" Multiplicity="0..1" />
  <End Type="ReportingData.AssignmentBaseline" Role="AssignmentBaseline_Assignment" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**AssignmentBaseline_Assignment_Assignment_Baseline** <br/> |Identifies the entity types and the navigation properties that form the two-way association for assignment baselines and assignments. In the first half of the name, **AssignmentBaseline** is the entity type and **Assignment** is the navigation property. In the second half of the name, **Assignment** is the entity type and **Baseline** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **AssignmentBaseline_Assignment_Assignment_Baseline** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the AssignmentBaseline_Assignment_Assignment_Baseline association End element attributes**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**AssignmentBaseline_Assignment** <br/> |[EntityType element: AssignmentBaseline](entitytype-assignmentbaseline-projectdata-service.md) <br/> |**\*** <br/> |There can be multiple assignment baseline entities that correspond to an assignment.  <br/> |
|**Assignment_Baseline** <br/> |[EntityType element: Assignment](entitytype-assignment-projectdata-service.md) <br/> |**0..1** <br/> |There is one assignment for a baseline.  <br/> |
   
## Remarks

One end of the association is the **AssignmentBaseline** entity, and the other end is the **Assignment** entity. The **AssignmentBaseline** entity type contains the **Assignment** navigation property, where the **FromRole** defines **AssignmentBaseline_Assignment** as the start of the association to get the collection of assignments in an assignment baseline. Similarly, the **Assignment** entity type contains the **Baseline** navigation property, where the **FromRole** defines **Assignment_Baseline** as the start of the association to get the baseline that is associated with an assignment. 
  
## Example

Microsoft.Win32.RegistryKey#4
  
## See also

#### Reference

[EntityType element: Assignment](entitytype-assignment-projectdata-service.md)
  
[EntityType element: AssignmentBaseline](entitytype-assignmentbaseline-projectdata-service.md)

