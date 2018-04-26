---
title: "EntityType ResourceTimephasedData (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: cfc58a05-d526-4f72-b36b-6d42d7c22d9c
description: "Contains the properties that define the reporting data for resource timephased data in the ProjectData service."
---

# EntityType: ResourceTimephasedData (ProjectData service)

Contains the properties that define the reporting data for resource timephased data in the **ProjectData** service. 
  
## Example

The following REST query uses the [ResourceTimephasedDataSet](entityset-resourcetimephaseddataset-projectdata-service.md) entity set and the **ResourceId** and **TimeByDay** keys to get the resource timephased data for the specified resource and time range. The query is all on one line. 
  
```
http://<pwa_url>/_api/ProjectData/ResourceTimephasedDataSet
    ?$filter=ResourceId eq guid'95b91da5-d01e-e211-b6af-00155d344024'
    and TimeByDay ge datetime'2013-11-16'
    and TimeByDay le datetime'2013-11-20'
```

## Definition

```XML
<EntityType Name="ResourceTimephasedData">
  <Key>
    <PropertyRef Name="ResourceId" />
    <PropertyRef Name="TimeByDay" />
  </Key>
  <Property Name="ResourceId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="Resource" Relationship="ReportingData.ResourceTimephasedData_Resource_Resource_TimephasedInfoDataSet" ToRole="Resource_TimephasedInfoDataSet" FromRole="ResourceTimephasedData_Resource" />
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of resource timephased data and navigation properties of resource timephased data. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** element specifies the resource entity as associated with resource timephased data. A navigation property uses an **Association** element in a query for a related entity collection 
  
The **Key** elements specify the properties that are the primary keys for resource timephased data queries. **ResourceId** is the resource GUID and **TimeByDay** is a day along a timeline. 
  
### Property elements

The following table lists the **Property** elements for the **ResourceTimephasedData** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of ResourceTimephasedData**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**BaseCapacity** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The maximum work capacity that is determined by the resource calendar. Also known as baseline capacity.  <br/> |
|**Capacity** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The amount of work that can be done by a resource (for example, hours per day).  <br/> |
|**ResourceId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies the resource.  <br/> |
|**ResourceName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the resource.  <br/> |
|**TimeByDay** <br/> |**Edm.DateLine** <br/> |**false** <br/> |**Key**         A primary key that identifies the day along a timeline. The granularity is in days only.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **ResourceTimephasedData** entity. The **Name** and **Relationship** columns contain attribute values for this navigation property. 
  
The **Relationship** attribute has two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For the **Resource** navigation property, the primary type is **ResourceTimephasedData**, and the secondary type is **Resource**. For this type of navigation, the **FromRole** is **ResourceTimephasedData_Resource**, and the **ToRole** is **Resource_TimephasedInfoDataSet**.
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Resource** <br/> |[ResourceTimephasedData_Resource_Resource_TimephasedInfoDataSet](association-resourcetimephaseddata_resource_resource_timephasedinfodataset-proje.md) <br/> |Establishes navigation from a collection of resource timephased data to a resource and from a resource to a collection timephased information data set.  <br/> |
   
## See also

#### Reference

[ResourceTimephasedDataSet](entityset-resourcetimephaseddataset-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

