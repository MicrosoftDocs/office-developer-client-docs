---
title: "EntityType BusinessDriverDepartment (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 5943d206-e23a-405f-8bcd-42fcd1e8adaf
description: "Contains the properties that define the reporting data for a business driver department in the ProjectData service."
---

# EntityType: BusinessDriverDepartment (ProjectData service)

Contains the properties that define the reporting data for a business driver department in the **ProjectData** service. 
  
## Example

The following REST query uses the [BusinessDriverDepartments](entityset-businessdriverdepartments-projectdata-service.md) entity set and the **DepartmentId** key to get the specified business driver departments in **ProjectData**. The query is all on one line.
  
```
https://<pwa_url>/_api/ProjectData/BusinessDriverDepartments
    ?$filter=DepartmentId eq guid'64a32ef6-7849-e211-9c40-00155da03b0b'
```

## Definition

```XML
<EntityType Name="BusinessDriverDepartment">
  <Key>
    <PropertyRef Name="BusinessDriverId" />
    <PropertyRef Name="DepartmentId" />
  </Key>
  <Property Name="BusinessDriverId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="BusinessDriver" Relationship="ReportingData.BusinessDriver_Departments_BusinessDriverDepartment_BusinessDriver" ToRole="BusinessDriver_Departments" FromRole="BusinessDriverDepartment_BusinessDriver" />
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of a business driver department and navigation properties of that business driver department. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as tasks and assignments, that are associated with a business driver department. A navigation property uses an **Association** element in a query for a related entity or collection 
  
The **Key** elements specify the properties that are the primary keys for a query for a business driver department. **BusinessDriverId** is the GUID of the business driver department and **DepartmentId** is the GUID of the department of the business driver. 
  
### Property elements

The following table lists the values of the **Property** elements for the **BusinessDriverDepartment** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of BusinessDriverDepartment**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**BusinessDriverId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of the business driver.  <br/> |
|**BusinessDriverName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the business driver.  <br/> |
|**DepartmentId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of the business driver department.  <br/> |
|**DepartmentName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the business driver department.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **BusinessDriveDepartment** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property. 
  
Each **Relationship** attribute has two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **BusinessDriver** navigation property, the primary type is **BusinessDriver**, and the secondary type is **BusinessDriverDepartment**. For this type of navigation, the **FromRole** is **BusinessDriver_Departments**, and the **ToRole** is **BusinessDriverDepartment_BusinessDriver**.
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**BusinessDriver** <br/> |[BusinessDriver_Departments_BusinessDriverDepartment_BusinessDriver](association-element-businessdriver_departments-projectserverdata-service.md) <br/> |Establishes navigation from a business driver to a collection of business driver departments and from a business driver department to a business driver.  <br/> |
   
## See also

#### Reference

[BusinessDriverDepartments](entityset-businessdriverdepartments-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

