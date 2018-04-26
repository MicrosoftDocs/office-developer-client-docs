---
title: "EntityType PrioritizationDriver (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: fc2bd0b8-8c53-480e-b43a-b6b6593beb8c
description: "Contains the properties that define the reporting data for a prioritization driver in the ProjectData service."
---

# EntityType: PrioritizationDriver (ProjectData service)

Contains the properties that define the reporting data for a prioritization driver in the **ProjectData** service. 
  
## Example

The following REST query uses the [PrioritizationDrivers](entityset-prioritizationdrivers-projectdata-service.md) entity set and the **BusinessDriverId** key to get the specified business driver properties, ordered by priority. The query is all in one line. 
  
```
http://<pwa_url>/_api/ProjectData/PrioritizationDrivers
    ?$filter=BusinessDriverId eq guid'9b63f657-9a48-e211-9c40-00155da03b0b'
    &amp;$orderby=BusinessDriverPriority
```

## Definition

```XML
<EntityType Name="PrioritizationDriver">
  <Key>
    <PropertyRef Name="PrioritizationId" />
    <PropertyRef Name="BusinessDriverId" />
  </Key>
  <Property Name="PrioritizationId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="Prioritization" Relationship="ReportingData.Prioritization_PrioritizationDrivers_PrioritizationDriver_Prioritization" ToRole="Prioritization_PrioritizationDrivers" FromRole="PrioritizationDriver_Prioritization" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of a prioritization driver and navigation properties of that prioritization driver. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as business driver id and business driver name, that are associated with a prioritization driver. A navigation property uses an **Association** element in a query for a related entity or collection 
  
The **Key** elements specify the properties that are the primary keys for a prioritization driver query. **PrioritizationId** is the GUID of the prioritization and **BusinessDriverId** is the GUID of the business driver. 
  
### Property elements

The following table lists the values of the **Property** elements for the **PrioritizationDriver** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of PrioritizationDriver**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**BusinessDriverId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies a business driver.  <br/> |
|**BusinessDriveName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a business driver.  <br/> |
|**BusinessDriverPriority** <br/> |**Edm.Double** <br/> |**false** <br/> |The level of importance of a business driver.  <br/> |
|**PrioritizationId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID for a Portfolio Analysis prioritization.  <br/> |
|**PrioritizationName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a Portfolio Analysis prioritization.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **PrioritizationDriver** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property.There are two types of **Relationship** attributes. One type contains two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **Prioritization** navigation property, the primary type is **Prioritization**, and the secondary type is **PrioritizationDriver**. For this type of navigation, the **FromRole** is **Prioritization_PrioritizationDrivers**, and the **ToRole** is **PrioritizationDriver_Prioritization**.
  
The other type of **Relationship** attribute contains a single pair of names. The first name in the pair is the primary entity type in the navigation. The second name in the pair is the secondary entity type in the navigation. For example, in the **BusinessDriver** navigation property relationship, **PrioritizationDriver** is the primary entity type and **BusinessDriver** is the secondary entity type. 
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**BusinessDriver** <br/> |[PrioritizationDriver_BusinessDriver](association-prioritizationdriver_businessdriver-projectdata-service.md) <br/> |Establishes navigation from a collection of prioritization drivers to a business driver.  <br/> |
|**Prioritization** <br/> |[Prioritization_PrioritizationDrivers_PrioritizationDriver_Prioritization](association-prioritization_prioritizationdrivers_prioritizationdriver_prioritiza.md) <br/> |Establishes navigation from a prioritization to a collection of prioritization drivers and from a prioritization driver to a prioritization.  <br/> |
   
## See also

#### Reference

[PrioritizationDrivers](entityset-prioritizationdrivers-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

