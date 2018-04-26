---
title: "EntityContainer ReportingData (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 22b825bd-462d-4013-82d7-e7a41ab2919c
description: "Contains definitions of entity sets and association sets, for internal use in queries of the ProjectData service."
---

# EntityContainer: ReportingData (ProjectData service)

Contains definitions of entity sets and association sets, for internal use in queries of the **ProjectData** service. 
  
## Definition

```XML
<Schema Namespace="Microsoft.Office.Project.Server" . . . >
  <EntityContainer Name="ReportingData" m:IsDefaultEntityContainer="true">
    <EntitySet Name="Projects" EntityType="ReportingData.Project" />
    . . .
    <AssociationSet Name="Relation_Projects_Tasks_Tasks_Project_Tasks_Project_Projects_Tasks" 
                    Association="ReportingData.Project_Tasks_Task_Project">
      <End Role="Project_Tasks" EntitySet="Projects" />
      <End Role="Task_Project" EntitySet="Tasks" />
    </AssociationSet>
    . . .
  </EntityContainer>
</Schema>
```

For example, the **Projects** entity set is the collection of data that has the [ReportingData.Project](entitytype-project-projectdata-service.md) entity type. A query such as  `http://ServerName/ProjectServerName/_api/ProjectrData/Projects` gets data for all of the projects in the Project Web App instance. 
  
> [!NOTE]
> The **AssociationSet** elements are generated for internal use by Project Server, and are not documented. 
  
Briefly, the **AssociationSet** that is shown in the Definition section is the collection of project and task associations. That is, the [Association element: Project_Tasks_Task_Project](association-project_tasks_task_project-projectdata-service.md) relates many tasks to one project and relates the project for each task. The **Relation_Projects_Tasks_Tasks_Project_Tasks_Project_Projects_Tasks** name of the **AssociationSet** is internally generated to indicate the collection of all associations of projects to tasks and all associations of tasks to projects. Fortunately, the queries that you create do not directly use association sets. 
  
## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**ReportingData** <br/> |The name of the entity container.  <br/> |
|**IsDefaultEntityContainer** <br/> |**true** <br/> |Specifies whether **ReportingData** is the default entity container.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: Microsoft.Office.Project.Server](schema-microsoft-office-project-server-projectdata-service.md) <br/> |Specifies the **Microsoft.Office.Project.Server** namespace for the OData schema that defines entity sets and association sets, which support queries of entities and associations in the Project Server Reporting database.  <br/> |
   
## Child elements

|**Element**|**Description**|
|:-----|:-----|
|[EntitySet element: AssignmentBaselines](entityset-assignmentbaselines-projectdata-service.md) <br/> |The set of assignment baseline entities.  <br/> |
|[EntitySet element: AssignmentBaselineTimephasedDataSet](entityset-assignmentbaselinetimephaseddataset-projectdata-service.md) <br/> |The set of assignment baseline timephased data set entities.  <br/> |
|[EntitySet element: Assignments](entityset-assignments-projectdata-service.md) <br/> |The set of assignment entities.  <br/> |
|[EntitySet element: AssignmentTimephasedDataSet](entityset-businessdriverdepartments-projectdata-service.md) <br/> |The set of assssignment timephased data set entities.  <br/> |
|[EntitySet element: BusinessDriverDepartments](entityset-businessdriverdepartments-projectdata-service.md) <br/> |The set of business driver department entities.  <br/> |
|[EntitySet element: BusinessDrivers](entityset-businessdrivers-projectdata-service.md) <br/> |The set of business driver entities.  <br/> |
|[EntitySet element: CostConstraintScenarios](entityset-costconstraintscenarios-projectdata-service.md) <br/> |The set of cost constraint scenario entities.  <br/> |
|[EntitySet element: CostScenarioProjects](entityset-costscenarioprojects-projectdata-service.md) <br/> |The set of cost scenario project entities.  <br/> |
|[EntitySet element: Deliverables](entityset-deliverables-projectdata-service.md) <br/> |The set of deliverable entities.  <br/> |
|[EntitySet element: Issues](entityset-deliverables-projectdata-service.md) <br/> |The set of issue entities.  <br/> |
|[EntitySet element: PortfolioAnalyses](entityset-portfolioanalyses-projectdata-service.md) <br/> |The set of portfolio analysis entities.  <br/> |
|[EntitySet element: PortfolioAnalysisProjects](entityset-portfolioanalysisprojects-projectdata-service.md) <br/> |The set of portfolio analysis project entities.  <br/> |
|[EntitySet element: PrioritizationDriverRelations](entityset-prioritizationdriverrelations-projectdata-service.md) <br/> |The set of prioritization driver relation entities.  <br/> |
|[EntitySet element: PrioritizationDrivers](entityset-prioritizationdrivers-projectdata-service.md) <br/> |The set of prioritization driver entities.  <br/> |
|[EntitySet element: Prioritizations](entityset-prioritizations-projectdata-service.md) <br/> |The set of prioritization entities.  <br/> |
|[EntitySet element: ProjectBaselines](entityset-projectbaselines-projectdata-service.md) <br/> |The set of project baseline entities.  <br/> |
|[EntitySet element: Projects](entityset-projects-projectdata-service.md) <br/> |The set of project entities.  <br/> |
|[EntitySet element: ProjectWorkflowStageDataSet](entityset-projectworkflowstagedataset-projectdata-service.md) <br/> |The set of project workflow stage data set entities.  <br/> |
|[EntitySet element: ResourceConstraintScenarios](entityset-resourceconstraintscenarios-projectdata-service.md) <br/> |The set of resource constraint scenario entities.  <br/> |
|[EntitySet element: Resources](entityset-resources-projectdata-service.md) <br/> |The set of resource entities.  <br/> |
|[EntitySet element: ResourceScenarioProjects](entityset-resourcescenarioprojects-projectdata-service.md) <br/> |The set of resource scenario project entities.  <br/> |
|[EntitySet element: ResourceTimephasedDataSet](entityset-resourcetimephaseddataset-projectdata-service.md) <br/> |The set of resource timephased data set entities.  <br/> |
|[EntitySet element: Risks](entityset-risks-projectdata-service.md) <br/> |The set of risk entities.  <br/> |
|[EntitySet element: TaskBaselines](entityset-taskbaselines-projectdata-service.md) <br/> |The set of task baseline entities.  <br/> |
|[EntitySet element: TaskBaselineTimephasedDataSet](entityset-taskbaselinetimephaseddataset-projectdata-service.md) <br/> |The set of task baseline timephased data set entities.  <br/> |
|[EntitySet element: Tasks](entityset-tasks-projectdata-service.md) <br/> |The set of task entities.  <br/> |
|[EntitySet element: TaskTimephasedDataSet](entityset-tasktimephaseddataset-projectdata-service.md) <br/> |The set of task timephased data set entities.  <br/> |
|[EntitySet element: TimeSet](entityset-timeset-projectdata-service.md) <br/> |The set of time set entities.  <br/> |
|[EntitySet element: TimesheetClasses](entityset-timesheetclasses-projectdata-service.md) <br/> |The set of timesheet class entities.  <br/> |
|[EntitySet element: TimesheetLineActualDataSet](entityset-timesheetlineactualdataset-projectdata-service.md) <br/> |The set of timesheet line actual data set entities.  <br/> |
|[EntitySet element: TimesheetLines](entityset-timesheetlines-projectdata-service.md) <br/> |The set of timesheet line entities.  <br/> |
|[EntitySet element: TimesheetPeriods](entityset-timesheetperiods-projectdata-service.md) <br/> |The set of timesheet period entities.  <br/> |
|[EntitySet element: Timesheets](entityset-timesheets-projectdata-service.md) <br/> |The set of timesheet entities.  <br/> |
   
## Remarks

The **EntityContainer** element is the only child of the **Schema** element for the **Microsoft.Office.Project.Server** namespace. The **EntityContainer** element is the default container that defines the **EntitySet** elements and **AssociationSet** elements in the **ReportingData** schema. An **EntitySet** element is a collection of entity types. An **AssociationSet** element is a collection of associations. 
  
> [!NOTE]
> The **Child elements** table lists only the **EntitySet** elements. Although the OData schema that you get with the  `http://ServerName/ProjectServerName/_api/ProjectrData/$metadata` query lists many **AssociationSet** elements, they are used internally and are not documented. 
  
Project Server uses the **EntitySet** elements and **AssociationSet** elements to create SQL queries of the Reporting tables and views in the online Project Server database. You cannot directly access the Project Server database for Project Online. 
  
## See also

#### Reference

[Schema element: ReportingData](schema-reportingdata-projectdata-service.md)

