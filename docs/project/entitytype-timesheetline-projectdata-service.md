---
title: "EntityType TimesheetLine (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 1c6c8052-117d-40bb-9df9-ced3dc362ada
description: "Contains the properties that define the reporting data for a timesheet line in the ProjectData service."
---

# EntityType: TimesheetLine (ProjectData service)

Contains the properties that define the reporting data for a timesheet line in the **ProjectData** service. 
  
## Example

The following REST query uses the [TimesheetLines](entityset-timesheetlines-projectdata-service.md) entity set and the **TimesheetLineId** key to get the **LastSavedWork** property of the specified timesheet line. The query is all on one line. 
  
```
https://<pwa_url>/_api/ProjectData/TimesheetLines
    ?$filter=TimesheetLineId eq guid'129f6ca2-0d00-0000-0985-f4a2bf47ac08'
    &amp;$select=LastSavedWork
```

## Definition

```XML
<EntityType Name="TimesheetLine">
  <Key>
    <PropertyRef Name="TimesheetLineId" />
  </Key>
  <Property Name="TimesheetLineId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="Actuals" Relationship="ReportingData.TimesheetLine_Actuals_TimesheetLineActualData_TimesheetLine" ToRole="TimesheetLineActualData_TimesheetLine" FromRole="TimesheetLine_Actuals" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of a timesheet line and navigation properties of that timesheet line. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as timesheet period status and timesheet status, that are associated with a timesheet line. A navigation property uses an **Association** element in a query for a related entity collection 
  
The **Key** element specifies the property that is the primary key for a timesheet line query. **TimesheetLineId** is the timesheet line GUID. 
  
### Property elements

The following table lists the **Property** elements for the **TimesheetLine** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of TimesheetLine**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**ActualOvertimeWorkBillable** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The actual billable overtime work that has already been performed by resources assigned to tasks.  <br/> |
|**ActualOvertimeWorkNonBillable** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The actual non-billable overtime work that has already been performed by resources assigned to tasks.  <br/> |
|**ActualWorkBillable** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The actual billable amount of regular, non-overtime work that has already been performed by resources assigned to tasks.  <br/> |
|**ActualWorkNonBillable** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The actual non-billable amount of regular, non-overtime work that has already been performed by resources assigned to tasks.  <br/> |
|**AssignmentId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID that identifies the assignment that is associated with the timesheet line.  <br/> |
|**CreatedDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The date and time that the timesheet line was created.  <br/> |
|**LastSavedWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The amount of work last saved, in 1000ths of a minute.  <br/> |
|**LCID** <br/> |**Edm.Int32** <br/> |**false** <br/> |The locale identifier.  <br/> |
|**ModifiedDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The date and time that the timesheet line was modified.  <br/> |
|**PeriodEndDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The end date and time for the timesheet line period.  <br/> |
|**PeriodStartDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The start date and time for the timesheet line period.  <br/> |
|**PlannedWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The estimated amount of work.  <br/> |
|**ProjectId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID that identifies the project that is associated with the timesheet line.  <br/> |
|**ProjectName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the project that is associated with the timesheet line.  <br/> |
|**TaskHierarchy** <br/> |**Edm.String** <br/> |**true** <br/> |The hierarchical list of tasks for a project.  <br/> |
|**TaskId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID that identifies the task.  <br/> |
|**TaskName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the task.  <br/> |
|**TimesheetApproverResourceId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of the resource that approves the timesheet.  <br/> |
|**TimesheetApproverResourceName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the resource that approves the timesheet.  <br/> |
|**TimesheetClassDescription** <br/> |**Edm.String** <br/> |**true** <br/> |The description of the timesheet class (for example, to describe its purpose as the recording of sick time or vacation time).  <br/> |
|**TimesheetClassId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID that identifies the timesheet class.  <br/> |
|**TimesheetClassName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the timesheet class.  <br/> |
|**TimesheetClassType** <br/> |**Edm.Byte** <br/> |**false** <br/> |The type of the timesheet class (for example, sick time or vacation time).  <br/> |
|**TimesheetId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID for the timesheet.  <br/> |
|**TimesheetLineComment** <br/> |**Edm.String** <br/> |**true** <br/> |The text comment for the timesheet line.  <br/> |
|**TimesheetLineId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of the timesheet line.  <br/> |
|**TimesheetLineStatus** <br/> |**Edm.String** <br/> |**true** <br/> |The status of the timesheet line.  <br/> |
|**TimesheetLineStatusId** <br/> |**Edm.Byte** <br/> |**true** <br/> |The status GUID for the timesheet line.  <br/> |
|**TimesheetName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the timesheet.  <br/> |
|**TimesheetOwner** <br/> |**Edm.String** <br/> |**true** <br/> |The timesheet owner.  <br/> |
|**TimesheetOwnerId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID of the timesheet owner.  <br/> |
|**TimesheetPeriodId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID of the timesheet period.  <br/> |
|**TimesheetPeriodName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the timesheet period.  <br/> |
|**TimesheetPeriodStatus** <br/> |**Edm.String** <br/> |**true** <br/> |The status of the timesheet period.  <br/> |
|**TimesheetPeriodStatusId** <br/> |**Edm.Byte** <br/> |**false** <br/> |The GUID of the timesheet period status.  <br/> |
|**TimesheetStatus** <br/> |**Edm.String** <br/> |**true** <br/> |The status of the timesheet (for example, Acceptable or Approved).  <br/> |
|**TimesheetStatusId** <br/> |**Edm.Byte** <br/> |**false** <br/> |The GUID of the timesheet status.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **TimesheetLine** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property. 
  
There are two types of **Relationship** attributes. One type contains two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **Actuals** navigation property, the primary type is **TimesheetLine**, and the secondary type is **TimesheetLineActualData**. For this type of navigation, the **FromRole** is **TimesheetLine_Actuals**, and the **ToRole** is **TimesheetLineActualData_TimesheetLine**.
  
The other type of **Relationship** attribute contains a single pair of names. The first name in the pair is the primary entity type in the navigation. The second name in the pair is the secondary entity type in the navigation. For example, in the **ApproverResource** navigation property relationship, **TimesheetLine** is the primary entity type and **ApproverResource** is the secondary entity type. 
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Actuals** <br/> |[TimesheetLine_Actuals_TimesheetLineActualData_TimesheetLine](association-element-timesheetline_actuals-projectserverdata-service.md) <br/> |Establishes navigation from a collection of timesheet lines to actual data and from actual data to a collection of timesheet lines.  <br/> |
|**ApproverResource** <br/> |[TimesheetLine_ApproverResource](association-timesheetline_approverresource-projectdata-service.md) <br/> |Establishes navigation from a collection of timesheet lines to the resource that approves the timesheet line.  <br/> |
|**Timesheet** <br/> |[TimesheetLine_Timesheet_Timesheet_Lines](association-timesheetline_timesheet_timesheet_lines-projectdata-service.md) <br/> |Establishes navigation from a collection of timesheet lines to a timesheet and from a timesheet to a collection of timesheet lines.  <br/> |
|**TimesheetClass** <br/> |[TimesheetLine_TimesheetClass](association-element-timesheetline_timesheetclass-projectserverdata-service.md) <br/> |Establishes navigation from a collection of timesheet lines to a timesheet class.  <br/> |
   
## See also

#### Reference

[TimesheetLines](entityset-timesheetlines-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

