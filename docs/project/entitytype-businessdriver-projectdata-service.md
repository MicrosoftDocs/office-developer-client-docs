---
title: "EntityType BusinessDriver (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 0107a5dd-6224-4680-bb62-c5c9efee3a1b
description: "Contains the properties that define the reporting data for a business driver in the ProjectData service."
---

# EntityType: BusinessDriver (ProjectData service)

Contains the properties that define the reporting data for a business driver in the **ProjectData** service. 
  
## Example

The following REST query uses the [BusinessDrivers](entityset-businessdrivers-projectdata-service.md) entity set and the **BusinessDriverIsActive** property to get the specified properties for active business drivers in **ProjectData**. The query is all on one line.
  
```
https://<pwa_url>/_api/ProjectData/BusinessDrivers
    ?$filter=BusinessDriverIsActive eq true
    &amp;$select=BusinessDriverName,BusinessDriverDescription
```

## Definition

```XML
<EntityType Name="BusinessDriver">
  <Key>
    <PropertyRef Name="BusinessDriverId" />
  </Key>
  <Property Name="BusinessDriverId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="CreatedByResource" Relationship="ReportingData.BusinessDriver_CreatedByResource" ToRole="CreatedByResource" FromRole="BusinessDriver" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of a business driver and navigation properties of that business driver. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as departments, that are associated with a business driver. A navigation property uses an **Association** element in a query for a related entity or collection 
  
The **Key** element specifies the property that is the primary key for a business driver query. **BusinessDriverId** is the business driver GUID. 
  
### Property elements

The following table lists the values of the **Property** elements for the **BusinessDriver** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of BusinessDriver**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**BusinessDriverCreatedDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The date and time of the creation of a business goal, also known as a business driver.  <br/> |
|**BusinessDriverDescription** <br/> |**Edm.String** <br/> |**true** <br/> |The description of a business driver.  <br/> |
|**BusinessDriverId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies a business driver.  <br/> |
|**BusinessDriverIsActive** <br/> |**Edm.Boolean** <br/> |**false** <br/> |**True** if a business driver is active.  <br/> |
|**BusinessDriverModifiedDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The date and time that a business driver was last modified.  <br/> |
|**BusinessDriverName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a business driver.  <br/> |
|**CreatedByResourceId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of the resource that created the business driver.  <br/> |
|**CreatedByResourceName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the resource that created the driver.  <br/> |
|**ImpactDescriptionExtreme** <br/> |**Edm.String** <br/> |**true** <br/> |The description of risk occurrence impact when the magnitude of the impact is extreme.  <br/> |
|**ImpactDescriptionLow** <br/> |**Edm.String** <br/> |**true** <br/> |The description of risk occurrence impact when the magnitude of the impact is low.  <br/> |
|**ImpactDescriptionModerate** <br/> |**Edm.String** <br/> |**true** <br/> |The description of risk occurrence impact when the magnitude of the impact is moderate.  <br/> |
|**ImpactDescriptionNone** <br/> |**Edm.String** <br/> |**true** <br/> |The description of risk occurrence impact when the magnitude of the impact is nonexistent.  <br/> |
|**ImpactDescriptionStrong** <br/> |**Edm.String** <br/> |**true** <br/> |The description of risk occurrence impact when the magnitude of the impact is strong.  <br/> |
|**ModifiedByResourceId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of the resource that last updated the business driver.  <br/> |
|**ModifiedByResourceName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the resource that last modified the driver.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **BusinessDriver** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property.There are two types of **Relationship** attributes. One type contains two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **Departments** navigation property, the primary type is **BusinessDriver**, and the secondary type is **BusinessDriverDepartment**. For this type of navigation, the **FromRole** is **BusinessDriver_Departments**, and the **ToRole** is **BusinessDriverDepartment_BusinessDriver**.
  
The other type of **Relationship** attribute contains a single pair of names. The first name in the pair is the primary entity type in the navigation. The second name in the pair is the secondary entity type in the navigation. For example, in the **CreatedByResource** navigation property relationship, **BusinessDriver** is the primary entity type and **CreatedByResource** is the secondary entity type. 
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**CreatedByResource** <br/> |[BusinessDriver_CreatedByResource](association-businessdriver_createdbyresource-projectdata-service.md) <br/> |Establishes navigation from a collection of business drivers to the resource that created the business driver.  <br/> |
|**Departments** <br/> |[BusinessDriver_Departments_BusinessDriverDepartment_BusinessDriver](association-element-businessdriver_departments-projectserverdata-service.md) <br/> |Establishes navigation from a business driver to a collection of business driver departments and from a business driver department to a business driver.  <br/> |
|**ModifiedByResource** <br/> |[BusinessDriver_ModifiedByResource](association-businessdriver_modifiedbyresource-projectdata-service.md) <br/> |Establishes navigation from a collection of business drivers to the resource that modified the business driver.  <br/> |
   
## See also

#### Reference

[BusinessDrivers](entityset-businessdrivers-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

