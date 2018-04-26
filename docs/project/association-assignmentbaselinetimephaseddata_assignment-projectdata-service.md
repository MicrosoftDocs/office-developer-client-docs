---
title: "Association AssignmentBaselineTimephasedData_Assignment (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 6bb8c4f0-e9ae-4142-8438-9a566eefcf42
description: "The AssignmentBaselineTimephasedData_Assignment association relates timephased data in an assignment baseline to an assignment."
---

# Association: AssignmentBaselineTimephasedData_Assignment (ProjectData service)

The **AssignmentBaselineTimephasedData_Assignment** association relates timephased data in an assignment baseline to an assignment. 
  
## Definition

```XML
<Association Name="AssignmentBaselineTimephasedData_Assignment">
  <End Type="ReportingData.AssignmentBaselineTimephasedData" Role="AssignmentBaselineTimephasedData" Multiplicity="*" />
  <End Type="ReportingData.Assignment" Role="Assignment" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**AssignmentBaselineTimephasedData_Assignment** <br/> |Identifies the two entity types that form the **AssignmentBaselineTimephasedData_Assignment** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **AssignmentBaselineTimephasedData_Assignment** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the AssignmentBaselineTimephasedData_Assignment association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**AssignmentBaselineTimephasedData** <br/> |[EntityType element: AssignmentBaselineTimephasedData](entitytype-assignmentbaselinetimephaseddata-projectdata-service.md) <br/> |**\*** <br/> |The collection of assignment baseline timephased data in the reporting tables.  <br/> |
|**Assignment** <br/> |[EntityType element: Assignment](entitytype-assignment-projectdata-service.md) <br/> |**0..1** <br/> |The assignment object that is being referenced with the **AssignmentBaseline_Task** association.  <br/> |
   
## Remarks

The **Assignment** navigation property of the **AssignmentBaselineTimephasedData** entity type uses the **AssignmentBaselineTimephasedData_Assignment** association to query for an assignment that is associated with a collection of timephased data for assignment baselines. 
  
## See also

#### Reference

[EntityType element: Assignment](entitytype-assignment-projectdata-service.md)
  
[EntityType element: AssignmentBaselineTimephasedData](entitytype-assignmentbaselinetimephaseddata-projectdata-service.md)

