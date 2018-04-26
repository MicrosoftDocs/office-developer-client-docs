---
title: "EntityType Prioritization (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 09fe7989-e444-455f-b408-7dd69e1d8af5
description: "Contains the properties that define the reporting data for a prioritization in the ProjectData service."
---

# EntityType: Prioritization (ProjectData service)

Contains the properties that define the reporting data for a prioritization in the **ProjectData** service. 
  
## Example

The following REST query uses the [Prioritizations](entityset-prioritizations-projectdata-service.md) entity set and the **PrioritizationId** key to get the specified prioritization in **ProjectData**. The query is all on one line.
  
```
http://<pwa_url>/_api/ProjectData/Prioritizations
    ?$filter=PrioritizationId eq guid'5a4b039e-ab5a-e211-beb6-00155da2200e'
```

## Definition

```XML
<EntityType Name="Prioritization">
  <Key>
    <PropertyRef Name="PrioritizationId" />
  </Key>
  <Property Name="PrioritizationId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="CreatedByResource" Relationship="ReportingData.Prioritization_CreatedByResource" ToRole="CreatedByResource" FromRole="Prioritization" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of a prioritization and navigation properties of that prioritization. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as prioritization drivers and prioritization driver relations, that are associated with a prioritization. A navigation property uses an **Association** element in a query for a related entity or collection 
  
The **Key** element specifies the property that is the primary key for a prioritization query. **PrioritizationId** is the GUID of the prioritization. 
  
### Property elements

The following table lists the values of the **Property** elements for the **Prioritization** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of Prioritization**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**ConsistencyRatio** <br/> |**Edm.Double** <br/> |**true** <br/> |The prioritization consistency ratio.  <br/> |
|**CreatedByResourceId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of the resource that created the prioritization.  <br/> |
|**CreatedByResourceName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the resource that created the prioritization.  <br/> |
|**DepartmentId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of a department.  <br/> |
|**DepartmentName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a department.  <br/> |
|**ModifiedByResourceId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of the resource that last updated the prioritization.  <br/> |
|**ModifiedByResourceName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the resource that last updated the prioritization.  <br/> |
|**PrioritizationCreatedDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The date and time that a portfolio analysis prioritization was created.  <br/> |
|**PrioritizationDescription** <br/> |**Edm.String** <br/> |**true** <br/> |The description for a portfolio analysis prioritization.  <br/> |
|**PrioritizationId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID for a portfolio analysis prioritization.  <br/> |
|**PrioritizationIsManual** <br/> |**Edm.Boolean** <br/> |**false** <br/> |**True** if a portfolio analysis prioritization is manual.  <br/> |
|**PrioritizationModifiedDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The date and time that a portfolio analysis prioritization was modified.  <br/> |
|**PrioritizationName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a portfolio analysis prioritization.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **Prioritization** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property.There are two types of **Relationship** attributes. One type contains two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **PrioritizationDrivers** navigation property, the primary type is **Prioritization**, and the secondary type is **PrioritizationDriver**. For this type of navigation, the **FromRole** is **Prioritization_PrioritizationDrivers**, and the **ToRole** is **PrioritizationDriver_Prioritization**.
  
The other type of **Relationship** attribute contains a single pair of names. The first name in the pair is the primary entity type in the navigation. The second name in the pair is the secondary entity type in the navigation. For example, in the **CreatedByResource** navigation property relationship, **Prioritization** is the primary entity type and **CreatedByResource** is the secondary entity type. 
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**CreatedByResource** <br/> |[Prioritization_CreatedByResource](association-element-prioritization_createdbyresource-projectserverdata-service.md) <br/> |Establishes navigation from a collection of prioritizations to the resource that created a prioritization.  <br/> |
|**Modified ByResource** <br/> |[Prioritization_ModifiedByResource](association-element-prioritization_modifiedbyresource-projectserverdata-service.md) <br/> |Establishes navigation from a collection of prioritizations to the resource that modified a prioritization.  <br/> |
|**PrioritizationDrivers** <br/> |[Prioritization_PrioritizationDrivers_PrioritizationDriver_Prioritization](association-prioritization_prioritizationdriverrelations_prioritizationdriverrel.md) <br/> |Establishes navigation from a prioritization to a collection of prioritization drivers and from a prioritization driver to a prioritization.  <br/> |
|**PrioritizationDriverRelations** <br/> |[Prioritization_PrioritizationDriverRelations_PrioritizationDriverRelation_Prioritization](association-prioritization_prioritizationdrivers_prioritizationdriver_prioritiza.md) <br/> |Establishes navigation from a prioritization to a collection of prioritization driver relations and from a prioritization driver relations entity to a prioritization.  <br/> |
   
## See also

#### Reference

[Prioritizations](entityset-prioritizations-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

