---
title: "Association element Assignment_Resource (ProjectServerData service)"

 
manager: luken
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 1f19d901-b237-43b9-ad81-901ac140fb34
description: "The Assignment_Resource_Resource_Assignments association relates assignments to a resource and relates a resource to its assignments."
---

# Association element: Assignment_Resource (ProjectServerData service)

The **Assignment_Resource_Resource_Assignments** association relates assignments to a resource and relates a resource to its assignments. 
  
## Definition

```XML
<Association Name="Assignment_Resource_Resource_Assignments">
  <End Type="ReportingData.Resource" Role="Resource_Assignments" Multiplicity="0..1" />
  <End Type="ReportingData.Assignment" Role="Assignment_Resource" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Assignment_Resource_Resource_Assignments** <br/> |Identifies the entity types and the navigation properties that form the two-way association for assignments and resources. In the first half of the name, **Assignment** is the entity type and **Resource** is the navigation property. In the second half of the name, **Resource** is the entity type and **Assignments** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **Assignment_Resource_Resource_Assignments** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the Assignment_Resource_Resource_Assignment association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**Assignment_Resource** <br/> |[EntityType element: Assignment](entitytype-assignment-projectdata-service.md) <br/> |**\*** <br/> |There can be many assignments that correspond to a resource.  <br/> |
|**Resource_Assignments** <br/> |[EntityType element: Resource](entitytype-resource-projectdata-service.md) <br/> |**0..1** <br/> |There is one resource that corresponds to a collection of assignments.  <br/> |
   
## Remarks

One end of the association is the **Assignment** entity, and the other end is the **Resource** entity. The **Assignment** entity type contains the **Resource** navigation property, where the **FromRole** defines **Assignment_Resource** as the start of the association to get the collection of assignments that are associated with a resource. Similarly, the **Resource** entity type contains the **Assignments** navigation property, where the **FromRole** defines **Resource_Assignments** as the start of the association to get the resource that is associated with a collection of assignments. 
  
## See also

#### Reference

[EntityType element: Assignment](entitytype-assignment-projectdata-service.md)
  
[EntityType element: Resource](entitytype-resource-projectdata-service.md)

