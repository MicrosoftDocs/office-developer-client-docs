---
title: "EntityType TimesheetClass (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 54283282-1a59-4c0e-988b-3a494b81bbd3
description: "Contains the properties that define the reporting data for a timesheet class in the ProjectData service."
---

# EntityType: TimesheetClass (ProjectData service)

Contains the properties that define the reporting data for a timesheet class in the **ProjectData** service. 
  
## Example

The following REST query uses the [TimesheetLineClasses](entityset-timesheetclasses-projectdata-service.md) entity set and the **TimesheetClassType** property to get the specified timesheet class properties. The query is all on one line. 
  
```
https://<pwa_url>/_api/ProjectData/TimesheetClasses
    ?$filter=TimesheetClassType eq 1
    &amp;$select=TimesheetClassName,TimesheetClassId

```

## Definition

```XML
<EntityType Name="TimesheetClass">
  <Key>
    <PropertyRef Name="TimesheetClassId" />
    <PropertyRef Name="DepartmentId" />
  </Key>
  <Property Name="TimesheetClassId" Type="Edm.Guid" Nullable="false" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of a timesheet class. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. Unlike most entity types, there are no **NavigationProperty** child elements for the **TimesheetClass** entity type. 
  
The **Key** elements specify the properties that are the primary keys for a timesheet class query. **TimesheetClassId** is the timesheet class GUID and **DepartmentId** is the department GUID. 
  
### Property elements

The following table lists the **Property** elements for the **TimesheetClass** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**DepartmentId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of the timesheet department.  <br/> |
|**DepartmentName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the timesheet class department.  <br/> |
|**Description** <br/> |**Edm.String** <br/> |**true** <br/> |The description of the timesheet class. (For example, a description that states that the timesheet class records vacation time.)  <br/> |
|**LCID** <br/> |**Edm.Int32** <br/> |**true** <br/> |The locale identifier.  <br/> |
|**TimesheetClassId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of the timesheet class.  <br/> |
|**TimesheetClassName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the timesheet class.  <br/> |
|**TimesheetClassType** <br/> |**Edm.Byte** <br/> |**false** <br/> |A numerical value that represents the type of the timesheet class (for example, sick time).  <br/> |
   
### NavigationProperty elements

There are no **NavigationProperty** child elements associated with a timesheet class. 
  
## See also

#### Reference

[TimesheetLineClasses](entityset-timesheetclasses-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

