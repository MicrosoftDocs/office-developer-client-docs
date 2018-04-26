---
title: "EntityType PrioritizationDriverRelation (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 69526adc-2c16-45dd-a86b-e298fb376b22
description: "Contains the properties that define the reporting data for a prioritization driver relation in the ProjectData service."
---

# EntityType: PrioritizationDriverRelation (ProjectData service)

Contains the properties that define the reporting data for a prioritization driver relation in the **ProjectData** service. 
  
## Example

The following REST query uses the [PrioritizationDriverRelations](entityset-prioritizationdriverrelations-projectdata-service.md) entity set and the **PrioritizationId** key to get the specified prioritization driver relation information. The query is all on one line. 
  
```
http://<pwa_url>/_api/ProjectData/PrioritizationDriverRelations
    ?$filter=PrioritizationId eq guid'755af49e-4b96-e211-a1ea-00155da03113'
```

## Definition

```XML
<EntityType Name="PrioritizationDriverRelation">
  <Key>
    <PropertyRef Name="PrioritizationId" />
    <PropertyRef Name="BusinessDriver1Id" />
    <PropertyRef Name="BusinessDriver2Id" />
  </Key>
  <Property Name="PrioritizationId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="Prioritization" Relationship="ReportingData.Prioritization_PrioritizationDriverRelations_PrioritizationDriverRelation_Prioritization" ToRole="Prioritization_PrioritizationDriverRelations" FromRole="PrioritizationDriverRelation_Prioritization" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of a prioritization driver relation and navigation properties of that prioritization driver relation. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as prioritization, that are associated with a prioritization driver relation. A navigation property uses an **Association** element in a query for a related entity or collection 
  
The **Key** elements specify the properties that are the primary keys for a prioritization driver query. **PrioritizationId** is the GUID of the prioritization, **BusinessDriver1Id** is the GUID of the first business driver, and **BusinessDriver2Id** is the GUID of the second business driver. 
  
### Property elements

The following table lists the values of the **Property** elements for the **PrioritizationDriverRelation** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of PrioritizationDriverRelation**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**BusinessDriver1Id** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of the first business driver.  <br/> |
|**BusinessDriver2Id** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of the second business driver.  <br/> |
|**BusinessDriver1Name** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the first business driver.  <br/> |
|**BusinessDriver2Name** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the second business driver.  <br/> |
|**PrioritizationId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of a Portfolio Analysis prioritization.  <br/> |
|**PrioritizationName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a Portfolio Analysis prioritization.  <br/> |
|**RelationValue** <br/> |**Edm.String** <br/> |**true** <br/> |The importance of the business driver relationship.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **PrioritizationDriverRelation** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property.There are two types of **Relationship** attributes. One type contains two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **Prioritization** navigation property, the primary type is **Prioritization**, and the secondary type is **PrioritizationDriverRelation**. For this type of navigation, the **FromRole** is **Prioritization_PrioritizationDriverRelations**, and the **ToRole** is **PrioritizationDriverRelation_Prioritization**.
  
The other type of **Relationship** attribute contains a single pair of names. The first name in the pair is the primary entity type in the navigation. The second name in the pair is the secondary entity type in the navigation. For example, in the **BusinessDriver1** navigation property relationship, **PrioritizationDriverRelation** is the primary entity type and **BusinessDriver1** is the secondary entity type. 
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Prioritization** <br/> |[Prioritization_PrioritizationDriverRelations_PrioritizationDriverRelation_Prioritization](association-prioritization_prioritizationdriverrelations_prioritizationdriverrel.md) <br/> |Establishes navigation from a prioritization to a collection of prioritization driver relations and from a prioritization river relations entity to a prioritization.  <br/> |
|**BusinessDriver1** <br/> |[PrioritizationDriverRelation_BusinessDriver1](association-element-prioritizationdriverrelation_businessdriver1-projectserverda.md) <br/> |Establishes navigation from a collection of prioritization driver relations to the first business driver.  <br/> |
|**BusinessDriver2** <br/> |[PrioritizationDriverRelation_BusinessDriver2](association-prioritizationdriverrelation_businessdriver2-projectdata-service.md) <br/> |Establishes navigation from a collection of prioritization driver relations to the second business driver.  <br/> |
   
## See also

#### Reference

[PrioritizationDriverRelations](entityset-prioritizationdriverrelations-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

