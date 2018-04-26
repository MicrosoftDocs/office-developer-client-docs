---
title: "Association element Assignment_TimephasedData (ProjectServerData service)"

 
manager: luken
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 25dffad6-5825-4bd0-9815-671b642da8ff
description: "The AssignmentTimephasedData_Assignment_Assignment_TimephasedData association relates assignment timephased data to its assignment and relates an assignment to its timephased data."
---

# Association element: Assignment_TimephasedData (ProjectServerData service)

The **AssignmentTimephasedData_Assignment_Assignment_TimephasedData** association relates assignment timephased data to its assignment and relates an assignment to its timephased data. 
  
## Definition

```XML
<Association Name="AssignmentTimephasedData_Assignment_Assignment_TimephasedData">
  <End Type="ReportingData.Assignment" Role="Assignment_TimephasedData" Multiplicity="0..1" />
  <End Type="ReportingData.AssignmentTimephasedData" Role="AssignmentTimephasedData_Assignment" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**AssignmentTimephasedData_Assignment_Assignment_TimephasedData** <br/> |Identifies the entity types and the navigation properties that form the two-way association for assignment timephased data and assignments. In the first half of the name, **AssignmentTimephasedData** is the entity type and **Assignment** is the navigation property. In the second half of the name, **Assignment** is the entity type and **TimephasedData** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **AssignmentTimephasedData_Assignment_Assignment_TimephasedData** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the AssignmentTimephasedData_Assignment_Assignment_TimephasedData association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**AssignmentTimephasedData_Assignment** <br/> |[EntityType element: AssignmentTimephasedData](entitytype-assignmenttimephaseddata-projectdata-service.md) <br/> |**\*** <br/> |There can be many assignment timephased data entities that correspond with an assignment.  <br/> |
|**Assignment_TimephasedData** <br/> |[EntityType element: Assignment](entitytype-assignment-projectdata-service.md) <br/> |**0..1** <br/> |There is one assignment that corresponds to a collection of timephased data.  <br/> |
   
## Remarks

One end of the association is the **AssignmentTimephasedData** entity, and the other end is the **Assignment** entity. The **AssignmentTimephasedData** entity type contains the **Assignment** navigation property, where the **FromRole** defines **AssignmentTimephasedData_Assignment** as the start of the association to get the assignment that is associated with the timephased data. Similarly, the **Assignment** entity type contains the **TimephasedData** navigation property, where the **FromRole** defines **Assignment_TimephasedData** as the start of the association to get the timephased data that is associated with an assignment. 
  
## See also

#### Reference

[EntityType element: Assignment](entitytype-assignment-projectdata-service.md)
  
[EntityType element: AssignmentTimephasedData](entitytype-assignmenttimephaseddata-projectdata-service.md)

