---
title: "EntityType Assignment (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 957e6e40-7e33-4512-a9c0-bb1140c5a68b
description: "Contains properties that define the reporting data for an assignment in the ProjectData service."
---

# EntityType: Assignment (ProjectData service)

Contains properties that define the reporting data for an assignment in the **ProjectData** service. 
  
## Example

The following REST query uses the [Assignments](entityset-assignments-projectdata-service.md) entity set and the **ResourceName** property to get the IDs of all assignments that have unassigned resources. The query is all on one line. 
  
```
https://<pwa_url>/_api/ProjectData/Assignments
    ?$filter=ResourceName eq 'Unassigned Resource'
    &amp;$select=AssignmentId
```

The following statement uses LINQ query syntax to retrieve **Assignment** entity data from the OData interface of the Project Server reporting tables. To use the statement in an application, set a service reference to the **ProjectDataService**, and initialize the **ReportingData** context. The **Assignments** entity set can then be accessed as  `context.Assignments`. For more information, see [Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md).
  
```cs
var query =
    from a in Assignments
    orderby a.ProjectName, a.ResourceName
    select new
    {
        Project = a.ProjectName,
        Resource = a.ResourceName,
        AssignmentBookingType = a.AssignmentBookingName,
        AssignmentStartDate = a.AssignmentStartDate,
        Task = a.TaskName,
        AssignmentWork = a.AssignmentWork,
        AssignmentCost = a.AssignmentCost,
        AssisgnmentCostVariance = a.AssignmentCostVariance,
        AssignmentFinishVariance = a.AssignmentFinishVariance
    };
```

The preceding statement can be written by using Lambda expression syntax, as follows:
  
```cs
var query = Assignments
    .OrderBy(a => a.ProjectName)
    .ThenBy(a => a.ResourceName)
    .Select(a => new
    {
        Project = a.ProjectName,
        Resource = a.ResourceName,
        AssignmentBookingType = a.AssignmentBookingName,
        AssignmentStartDate = a.AssignmentStartDate,
        Task = a.TaskName,
        AssignmentWork = a.AssignmentWork,
        AssignmentCost = a.AssignmentCost,
        AssisgnmentCostVariance = a.AssignmentCostVariance,
        AssignmentFinishVariance = a.AssignmentFinishVariance
    });
```

Either statement creates the following REST URL (all on one line).
  
```
http://<pwa_url>/_vti_bin/client.svc/ProjectData/Assignments
    ?$orderby=ProjectName,ResourceName
    &amp;$select=ProjectName,ResourceName,AssignmentBookingName,AssignmentStartDate,TaskName,
    AssignmentWork,AssignmentCost,AssignmentCostVariance,AssignmentFinishVariance
```

All three of the sample queries get the same data.
  
**Sample results of the Task query**

|**Project**|**Resource**|**AssignmentBookingType**|**AssignmentStartDate**|**Task**|**AssignmentWork**|**AssignmentCost**|**AssignmentCostVariance**|**AssignmentFinishVariance**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|ProjectA  <br/> |Res2  <br/> |Committed  <br/> |3/12/2012 8:00:00 AM  <br/> |T1  <br/> |24.0 hrs  <br/> |$404.00  <br/> |$0.00  <br/> |0.0 hrs  <br/> |
|ProjectA  <br/> |Res7  <br/> |Committed  <br/> |3/12/2012 8:00:00 AM  <br/> |T3  <br/> |32.0 hrs  <br/> |$564.00  <br/> |$136.00  <br/> |8.0 hrs  <br/> |
|ProjectA  <br/> |Res8  <br/> |Committed  <br/> |3/12/2012 8:00:00 AM  <br/> |T2  <br/> |8.0 hrs  <br/> |$156.00  <br/> |-$272.00  <br/> |-16.0 hrs  <br/> |
|ProjectB  <br/> |Res3  <br/> |Committed  <br/> |3/19/2012 8:00:00 AM  <br/> |T3  <br/> |40.0 hrs  <br/> |$740.00  <br/> |$0.00  <br/> |0.0 hrs  <br/> |
|ProjectB  <br/> |Res4  <br/> |Proposed  <br/> |3/19/2012 8:00:00 AM  <br/> |T4  <br/> |8.0 hrs  <br/> |$168.00  <br/> |-$168.00  <br/> |-8.0 hrs  <br/> |
|ProjectB  <br/> |Res7  <br/> |Committed  <br/> |3/19/2012 8:00:00 AM  <br/> |T1  <br/> |48.0 hrs  <br/> |$836.00  <br/> |$272.00  <br/> |16.0 hrs  <br/> |
|ProjectB  <br/> |Res8  <br/> |Committed  <br/> |3/19/2012 8:00:00 AM  <br/> |T2  <br/> |24.0 hrs  <br/> |$428.00  <br/> |$0.00  <br/> |0.00  <br/> |
   
## Definition

```XML
<EntityType Name="Assignment">
  <Key>
    <PropertyRef Name="AssignmentId" />
    <PropertyRef Name="ProjectId" />
  </Key>
  <Property Name="ProjectId" Type="Edm.Guid" Nullable="false" />
. . .
  <NavigationProperty Name="Baseline" Relationship="ReportingData.AssignmentBaseline_Assignment_Assignment_Baseline" ToRole="AssignmentBaseline_Assignment" FromRole="Assignment_Baseline" />
 . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of an assignment and navigation properties of that assignment. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as baselines and resources, that are associated with an assignment. A navigation property uses an **Association** element in a query for a related entity or collection 
  
The **Key** elements specify the properties that are the primary keys for an assignment query. **ProjectId** is the project GUID and **AssignmentId** is the GUID of the assignment. 
  
### Property elements

The following table lists the values of the **Property** elements for the **Assignment** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of Assignment**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**AssignmentActualCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The costs incurred for work already performed on an assignment, along with any other associated costs.  <br/> |
|**AssignmentActualFinishDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The date and time when an assignment was actually completed.  <br/> |
|**AssignmentActualOvertimeCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The costs incurred for overtime work already performed on an assignment.  <br/> |
|**AssignmentActualOvertimeWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The actual amount of overtime work already performed on an assignment.  <br/> |
|**AssignmentActualRegularCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The cost of the total non-overtime work already performed on an assignment.  <br/> |
|**AssignmentActualRegularWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The total amount of non-overtime work already performed on an assignment.  <br/> |
|**AssignmentActualStartDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The date and time that the assignment actually began.  <br/> |
|**AssignmentActualWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The amount of work that has already been performed on an assignment.  <br/> |
|**AssignmentACWP** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The costs incurred for work already performed on an assignment, up to the project status date or today's date.\</td\>  <br/> |
|**AssignmentBCWP** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The budgeted cost of work performed on an assignment that is scheduled, up to the status date or today's date.  <br/> |
|**AssignmentBCWS** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The budgeted cost of work scheduled, up to the status date or today's date.  <br/> |
|**AssignmentBookingDescription** <br/> |**Edm.String** <br/> |**true** <br/> |The text description of the booking type.  <br/> |
|**AssignmentBookingId** <br/> |**Edm.Int32** <br/> |**false** <br/> |The integer constant that represents the assignment booking type. For more information, see the [Microsoft.Office.Project.Server.Library.Resource.BookingType](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Library.Resource.BookingType.aspx) enumeration.  <br/> |
|**AssignmentBookingName** <br/> |**Edm.String** <br/> |**true** <br/> |The assignment booking name (committed or proposed).  <br/> |
|**AssignmentBudgetCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The total scheduled or projected cost for an assignment.  <br/> |
|**AssignmentBudgetMaterialWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The total scheduled or projected use of equipment, supplies, or other consumable items for an assignment.  <br/> |
|**AssignmentBudgetWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The total amount of work originally planned for an assignment.  <br/> |
|**AssignmentCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The total cost for an assignment, based on costs already incurred, in addition to costs planned for the remaining work.  <br/> |
|**AssignmentCostVariance** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The difference between the baseline cost of an assignment and the total cost for work already performed, in addition to work remaining.  <br/> |
|**AssignmentCreatedDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The date and time that the assignment was created.  <br/> |
|**AssignmentCreatedRevisionCounter** <br/> |**Edm.Int32** <br/> |**false** <br/> |The number of times that the assignment has been revised. When the assignment is created, the **AssignmentCreatedRevisionCounter** = **1**.  <br/> |
|**AssignmentCV** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The difference between how much it should have cost to achieve the current level of completion on the assignment and how much it has actually cost to achieve the current level of completion, up to the status date or today's date.  <br/> |
|**AssignmentDelay** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The amount of time beyond the start date that an assignment is allowed to start.  <br/> |
|**AssignmentFinishDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The date and time that the assignment is completed.  <br/> |
|**AssignmentFinishVariance** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The difference between an assignment's baseline finish date and its scheduled finish date.  <br/> |
|**AssignmentId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies the assignment.  <br/> |
|**AssignmentIsOverallocated** <br/> |**Edm.Boolean** <br/> |**false** <br/> |Indicates whether the resource is assigned to more work on this assignment than can be done within the resource's normal working capacity.  <br/> |
|**AssignmentIsPublished** <br/> |**Edm.Boolean** <br/> |**false** <br/> |Indicates whether the assignment is published.  <br/> |
|**AssignmentMaterialActualWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The actual work for a material resource, usually expressed as a percentage.  <br/> |
|**AssignmentMaterialWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The total time scheduled for a material resource.  <br/> |
|**AssignmentModifiedDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The date and time that the assignment was modified  <br/> |
|**AssignmentModifiedRevisionCounter** <br/> |**Edm.Int32** <br/> |**false** <br/> |Keeps track of the number of times that the assignment has been modified. When the assignment is created, the **AssignmentModifiedRevisionCounter** = **1**.  <br/> |
|**AssignmentOvertimeCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The total overtime cost for an assignment, including costs for overtime work already performed, in addition to remaining overtime work.  <br/> |
|**AssignmentOvertimeWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The amount of overtime work that is scheduled to be performed on an assignment.  <br/> |
|**AssignmentPeakUnits** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The maximum percentage or number of units for which a resource is assigned at any one time for tasks.  <br/> |
|**AssignmentPercentWorkCompleted** <br/> |**Edm.Int16** <br/> |**true** <br/> |The current status of an assignment, expressed as the percentage of work that has been completed.  <br/> |
|**AssignmentRegularCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The cost fields show the total scheduled or projected cost for an assignment, based on costs already accrued, in addition to costs planned for the remaining work.  <br/> |
|**AssignmentRegularWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The total amount of regular (nonovertime) work that is scheduled to be performed on the assignment.  <br/> |
|**AssignmentRemainingCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The remaining scheduled expense that will be incurred by completing the remaining work on the assignment.  <br/> |
|**AssignmentRemainingOvertimeCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The remaining scheduled overtime expense for an assignment.  <br/> |
|**AssignmentRemainingOvertimeWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The amount of remaining scheduled overtime work on the assignment.  <br/> |
|**AssignmentRemainingRegularCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The remaining scheduled expense that will be incurred by completing the remaining scheduled regular (nonovertime) work for an assignment.  <br/> |
|**AssignmentRemainingRegularWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The amount of time, such as person-hours or days, that is still required to complete the regular (nonovertime) work for an assignment.  <br/> |
|**AssignmentRemainingWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The amount of time, such as person-hours or days, that is still required to complete both regular and overtime work for an assignment.  <br/> |
|**AssignmentResourcePlanWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The total time scheduled for the assignment in the resource plan.  <br/> |
|**AssignmentResourceType** <br/> |**Edm.Int16** <br/> |**true** <br/> |The type of resource that is associated with an assignment. For more information, see the [Microsoft.Office.Project.Server.Library.Resource.Type](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Library.Resource.Type.aspx) enumeration.  <br/> |
|**AssignmentStartDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The date when a resource is scheduled to begin working on an assignment.  <br/> |
|**AssignmentStartVariance** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The difference between an assignment's baseline start date and its currently scheduled start date.  <br/> |
|**AssignmentSV** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The **SV** (earned value schedule variance) field shows the difference in cost terms between the current progress and the baseline plan for an assignment, up to the status date or today's date.  <br/> |
|**AssignmentType** <br/> |**Edm.Int32** <br/> |**false** <br/> |Type of the assignment. **NormalAssignment**= **0**, **WorkOnlyAssignment**= **1**, **FixedCostAssignment**= **2**, **FixedCostWorkOnlyAssignment**= **3**, **EmptyAssignment**= **4**, **FixedCostGeneratedAssignment**= **100** (generated during RDS transfer), **ResourcePlanAssignment**= **101**.  <br/> |
|**AssignmentVAC** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The variance at completion (VAC) between the baseline cost and the total cost for an assignment.  <br/> |
|**AssignmentWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The total amount of time that is scheduled for an assignment.  <br/> |
|**AssignmentWorkVariance** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The difference between the originally planned baseline work on an assignment and the currently scheduled work.  <br/> |
|**CostType_R** <br/> |**Edm.String** <br/> |**true** <br/> |The **CostType** assignment custom field, which is rolled down from the resource custom field value.  <br/> |
|**Health_T** <br/> |**Edm.String** <br/> |**true** <br/> |The **Health** assignment custom field, which is rolled down from the task custom field value.  <br/> |
|**IsPublic** <br/> |**Edm.Boolean** <br/> |**false** <br/> |Specifies whether the assignment is published.  <br/> |
|**ProjectId** <br/> |**Edm.Guid** <br/> |**true** <br/> |**Key**         The GUID that identifies the project in which the assignment occurs.  <br/> |
|**ProjectName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the project.  <br/> |
|**RBS_R** <br/> |**Edm.String** <br/> |**true** <br/> |The ( **RBS**) assignment custom field, which is rolled down from the resource custom field.  <br/> |
|**ResourceDepartments_R** <br/> |**Edm.String** <br/> |**true** <br/> |The **ResourceDepartments** assignment custom field, which is rolled down from the resource custom field.  <br/> |
|**ResourceId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID that identifies the resource for the assignment.  <br/> |
|**ResourceName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the resource for the assignment.  <br/> |
|**TaskId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID that identifies the task that the assignment is for.  <br/> |
|**TaskIsActive** <br/> |**Edm.Boolean** <br/> |**false** <br/> |**True** if the task is active.  <br/> |
|**TaskName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the task that the assignment is for.  <br/> |
|**TimesheetClassId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID that identifies the timesheet class for the assignment.  <br/> |
|**TypeDescription** <br/> |**Edm.String** <br/> |**true** <br/> |The description of the assignment type.  <br/> |
|**TypeName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the assignment type. See the [Microsoft.Office.Project.Server.Library.Reporting.AssignmentType](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Library.Reporting.AssignmentType.aspx) enumeration.  <br/> |
   
> [!NOTE]
> The Property elements table includes only the default assignment custom fields: **CostType_R**, **Health_T**, **RBS_R**, and **ResourceDepartments_R**. If you create a resource custom field or a task custom field that rolls down to assignments, the **ReportingData** schema for the **Assignment** entity type would contain an additional property for each new custom field. For example, if you create a resource custom field named Test Res that rolls down, the **Assignment** entity type would include the **TestRes_R** property for that assignment custom field. 
  
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **Assignment** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property. 
  
Each **Relationship** attribute has two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **Baseline** navigation property, the primary type is **AssignmentBaseline**, and the secondary type is **Assignment**. For this type of navigation, the **FromRole** is **Assignment_Baseline**, and the **ToRole** is **AssignmentBaseline_Assignment**.
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Baseline** <br/> |[AssignmentBaseline_Assignment_Assignment_Baseline](association-assignmentbaseline_assignment_assignment_baseline-projectdata-servic.md) <br/> |Establishes navigation from a collection of assignment baselines to an assignment and from an assignment to a baseline.  <br/> |
|**Project** <br/> |[Project_Assignments_Assignment_Project](association-project_assignments_assignment_project-projectdata-service.md) <br/> |Establishes navigation from a project to a collection of assignments and from an assignment to a project.  <br/> |
|**Resource** <br/> |[Assignment_Resource_Resource_Assignments](association-element-assignment_resource-projectserverdata-service.md) <br/> |Establishes navigation from a collection of assignments to a resource and from a resource to a collection of assignments.  <br/> |
|**Task** <br/> |[Assignment_Task_Task_Assignments](association-assignment_task_task_assignments-projectdata-service.md) <br/> |Establishes navigation from a collection of assignments to a task and from a task to a collection of assignments.  <br/> |
|**TimephasedData** <br/> |[AssignmentTimephasedData_Assignment_Assignment_TimephasedData](association-element-assignment_timephaseddata-projectserverdata-service.md) <br/> |Establishes navigation from a collection of assignment timephased data to an assignment and from an assignment to timephased data.  <br/> |
   
## See also

#### Reference

[Assignments](entityset-assignments-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

