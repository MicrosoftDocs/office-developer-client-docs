---
title: "Schema ReportingData (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: c7f231f3-346b-4982-890f-afe014e02d6d
description: "Specifies the ReportingData namespace, which defines entity types and associations used to query the ProjectData OData service for reporting data."
---

# Schema: ReportingData (ProjectData service)

Specifies the **ReportingData** namespace, which defines entity types and associations used to query the **ProjectData** OData service for reporting data. 
  
## Definition

```
<Schema Namespace="ReportingData" xmlns:d="http://schemas.microsoft.com/ado/2007/08/dataservices" 
    xmlns:m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata" 
    xmlns="http://schemas.microsoft.com/ado/2007/05/edm">
```

The XML namespace attributes ( **xmlns**) specify the namespaces for services and metadata in the OData specification, and for the Entity Data Model (EDM) of an OData service. You can browse the ReportingData EDM by using the  `<pwa_url>/_api/projectdata/$metadata` endpoint. 
  
## Parent element

||
|:-----|
|None |
   
## Child elements

[EntityType elements](schema-reportingdata-projectdata-service.md#EntityType)
  
[Association elements](schema-reportingdata-projectdata-service.md#Association)
  
### EntityType elements
<a name="EntityType"> </a>

The **ReportingData** namespace contains the following **EntityType** elements. 
  
|**EntityType element**|**Description**|
|:-----|:-----|
|[Assignment](entitytype-assignment-projectdata-service.md) <br/> |Represents reporting data for an assignment.  <br/> |
|[AssignmentBaseline](entitytype-assignmentbaseline-projectdata-service.md) <br/> |Represents reporting data for an assignment baseline.  <br/> |
|[AssignmentBaselineTimephasedData](entitytype-assignmentbaselinetimephaseddata-projectdata-service.md) <br/> |Represents reporting data for assignment baseline timephased data.  <br/> |
|[AssignmentTimephasedData](entitytype-assignmenttimephaseddata-projectdata-service.md) <br/> |Represents reporting data for assignment timephased data.  <br/> |
|[BusinessDriver](entitytype-businessdriver-projectdata-service.md) <br/> |Represents reporting data for a business driver.  <br/> |
|[BusinessDriverDepartment](entitytype-businessdriverdepartment-projectdata-service.md) <br/> |Represents reporting data for a business driver department.  <br/> |
|[CostConstraintScenario](entitytype-costconstraintscenario-projectdata-service.md) <br/> |Represents reporting data for a cost constraint scenario.  <br/> |
|[CostScenarioProject](entitytype-costscenarioproject-projectdata-service.md) <br/> |Represents reporting data for a cost scenario project.  <br/> |
|[Deliverable](entitytype-deliverable-projectdata-service.md) <br/> |Represents reporting data for a deliverable.  <br/> |
|[Issue](entitytype-issue-projectdata-service.md) <br/> |Represents reporting data for an issue.  <br/> |
|[IssueTaskAssociation](entitytype-issuetaskassociation-projectdata-service.md) <br/> |Represents reporting data for an issue task association.  <br/> |
|[PortfolioAnalysis](entitytype-portfolioanalysis-projectdata-service.md) <br/> |Represents reporting data for a portfolio analysis.  <br/> |
|[PortfolioAnalysisProject](entitytype-portfolioanalysisproject-projectdata-service.md) <br/> |Represents reporting data for a portfolio analysis project.  <br/> |
|[Prioritization](entitytype-prioritization-projectdata-service.md) <br/> |Represents reporting data for a prioritization.  <br/> |
|[PrioritizationDriver](entitytype-prioritizationdriver-projectdata-service.md) <br/> |Represents reporting data for a prioritization driver.  <br/> |
|[PrioritizationDriverRelation](entitytype-prioritizationdriverrelation-projectdata-service.md) <br/> |Represents reporting data for a prioritization driver relation.  <br/> |
|[Project](entitytype-project-projectdata-service.md) <br/> |Represents reporting data for a project.  <br/> |
|[ProjectBaseline](entitytype-projectbaseline-projectdata-service.md) <br/> |Represents reporting data for a project baseline.  <br/> |
|[ProjectWorkflowStageData](entitytype-projectworkflowstagedata-projectdata-service.md) <br/> |Represents reporting data for project workflow stage data.  <br/> |
|[Resource](entitytype-resource-projectdata-service.md) <br/> |Represents reporting data for a resource.  <br/> |
|[ResourceConstraintScenario](entitytype-resourceconstraintscenario-projectdata-service.md) <br/> |Represents reporting data for a resource constraint scenario.  <br/> |
|[ResourceScenarioProject](entitytype-resourcescenarioproject-projectdata-service.md) <br/> |Represents reporting data for a resource scenario project.  <br/> |
|[ResourceTimephasedData](entitytype-resourcetimephaseddata-projectdata-service.md) <br/> |Represents reporting data for resource timephased data.  <br/> |
|[Risk](entitytype-risk-projectdata-service.md) <br/> |Represents reporting data for a risk.  <br/> |
|[RiskTaskAssociation](entitytype-risktaskassociation-projectdata-service.md) <br/> |Represents reporting data for a risk task association.  <br/> |
|[Task](entitytype-task-projectdata-service.md) <br/> |Represents reporting data for a task.  <br/> |
|[TaskBaseline](entitytype-taskbaseline-projectdata-service.md) <br/> |Represents reporting data for a task baseline.  <br/> |
|[TaskBaselineTimephasedData](entitytype-taskbaselinetimephaseddata-projectdata-service.md) <br/> |Represents reporting data for task baseline timephased data.  <br/> |
|[TaskTimephasedData](entitytype-tasktimephaseddata-projectdata-service.md) <br/> |Represents reporting data for task timephased data.  <br/> |
|[Time](entitytype-time-projectdata-service.md) <br/> |Represents reporting data for a time period.  <br/> |
|[Timesheet](entitytype-timesheet-projectdata-service.md) <br/> |Represents reporting data for a timesheet.  <br/> |
|[TimesheetClass](entitytype-timesheetclass-projectdata-service.md) <br/> |Represents reporting data for a timesheet class.  <br/> |
|[TimesheetLine](entitytype-timesheetline-projectdata-service.md) <br/> |Represents reporting data for a timesheet line.  <br/> |
|[TimesheetLineActualData](entitytype-timesheetlineactualdata-projectdata-service.md) <br/> |Represents reporting data for timesheet actual data.  <br/> |
|[TimesheetPeriod](entitytype-element-timesheetperiod-projectserverdata-service.md) <br/> |Represents reporting data for a timesheet period.  <br/> |
   
### Association elements
<a name="Association"> </a>

The **ReportingData** namespace contains the following **Association** elements. 
  
|**Association element**|**Description**|
|:-----|:-----|
|[Assignment_Resource_Resource_Assignments](association-element-assignment_resource-projectserverdata-service.md) <br/> |Relates assignments to a resource and relates a resource to its assignments.  <br/> |
|[Assignment_Task_Task_Assignments](association-assignment_task_task_assignments-projectdata-service.md) <br/> |Relates assignments to the task that contains them and relates a task to its assignments.  <br/> |
|[AssignmentBaseline_Assignment_Assignment_Baseline](association-assignmentbaseline_assignment_assignment_baseline-projectdata-servic.md) <br/> |Relates an assignment with its baseline.  <br/> |
|[AssignmentBaseline_AssignmentBaselineTimephasedDataSet_AssignmentBaselineTimephasedData_Baseline](association-assignmentbaseline_assignmentbaselinetimephaseddataset_assignmentbas.md) <br/> |Relates an assignment baseline with its assignment baseline timephased dataset.  <br/> |
|[AssignmentBaseline_Task_Task_AssignmentsBaselines](association-element-assignmentbaseline_task-projectserverdata-service.md) <br/> |Relates assignment baselines to a task and relates a task to its assignment baselines.  <br/> |
|[AssignmentBaselineTimephasedData_Assignment](association-assignmentbaselinetimephaseddata_assignment-projectdata-service.md) <br/> |Relates timephased data in an assignment baseline to an assignment.  <br/> |
|[AssignmentBaselineTimephasedData_Project](association-element-assignmentbaselinetimephaseddata_project-projectserverdata-s.md) <br/> |Relates timephased data in an assignment baseline to a project.  <br/> |
|[AssignmentBaselineTimephasedData_Tasks_Task_AssignmentsBaselineTimephasedData](association-assignmentbaselinetimephaseddata_tasks_task_assignmentsbaselinetimep.md) <br/> |Relates timephased data for assignment baselines to a task and relates a task to timephased data for assignment baselines.  <br/> |
|[AssignmentTimephasedData_Assignment_Assignment_TimephasedData](association-element-assignment_timephaseddata-projectserverdata-service.md) <br/> |Relates assignment timephased data to its assignment and relates an assignment to its timephased data.  <br/> |
|[AssignmentTimephasedData_Project](association-assignmenttimephaseddata_project-projectdata-service.md) <br/> |Relates assignment timephased data to a project.  <br/> |
|[AssignmentTimephasedData_Task](association-element-assignmenttimephaseddata_task-projectserverdata-service.md) <br/> |Relates assignment timephased data to a task.  <br/> |
|[BusinessDriver_CreatedByResource](association-businessdriver_createdbyresource-projectdata-service.md) <br/> |Relates business drivers to a resource.  <br/> |
|[BusinessDriver_Departments_BusinessDriverDepartment_BusinessDriver](association-element-businessdriver_departments-projectserverdata-service.md) <br/> |Relates a business driver to departments that it contains and relates business driver departments to a business driver.  <br/> |
|[BusinessDriver_ModifiedByResource](association-businessdriver_modifiedbyresource-projectdata-service.md) <br/> |Relates business drivers to a resource.  <br/> |
|[CostConstraintScenario_CostScenarioProjects_CostScenarioProject_CostConstraintScenario](association-costconstraintscenario_costscenarioprojects_costscenarioproject_cost.md) <br/> |Relates a cost constraint scenario to cost scenario projects and relates cost scenario projects to a cost constraint scenario.  <br/> |
|[CostConstraintScenario_CreatedByResource](association-costconstraintscenario_createdbyresource-projectdata-service.md) <br/> |Relates cost constraint scenarios to a resource.  <br/> |
|[CostConstraintScenario_ModifiedByResource](association-costconstraintscenario_modifiedbyresource-projectdata-service.md) <br/> |Relates cost constraint scenarios to a resource.  <br/> |
|[CostConstraintScenario_ResourceConstraintScenarios_ResourceConstraintScenario_CostConstraintScenario](association-costconstraintscenario_resourceconstraintscenarios_resourceconstrain.md) <br/> |Relates a cost constraint scenario to the resource constraint scenarios that it contains and relates resource constraint scenarios to a cost constraint scenario.  <br/> |
|[CostScenarioProject_Analysis](association-costscenarioproject_analysis-projectdata-service.md) <br/> |Relates cost scenarios projects to a portfolio analysis.  <br/> |
|[CostScenarioProject_Project](association-costscenarioproject_project-projectdata-service.md) <br/> |Relates cost scenario projects to a project.  <br/> |
|[Deliverable_DependentTasks](association-deliverable_dependenttasks-projectdata-service.md) <br/> |Relates the deliverable to its dependent tasks.  <br/> |
|[Deliverable_ParentProjects](association-element-deliverable_parentprojects-projectserverdata-service.md) <br/> |Relates the deliverable to its parent projects.  <br/> |
|[Deliverable_ParentTasks](association-deliverable_parenttasks-projectdata-service.md) <br/> |Relates deliverables to parent tasks.  <br/> |
|[Issue_RelatedRisks_Risk_RelatedIssues](association-element-issue_relatedrisks-projectserverdata-service.md) <br/> |Relates issues to related risks and risks to related issues.  <br/> |
|[Issue_SubIssues](association-issue_subissues-projectdata-service.md) <br/> |Relates issues to subissues.  <br/> |
|**Issue_Tasks_Task_Issues** <br/> |Relates an issue to tasks and relates a task to issues.  <br/> |
|[IssueTaskAssociation_Issue](association-issuetaskassociation_issue-projectdata-service.md) <br/> |Relates an issue task association to an issue.  <br/> |
|[IssueTaskAssociation_Project](association-issuetaskassociation_project-projectdata-service.md) <br/> |Relates an issue task association to a project.  <br/> |
|[IssueTaskAssociation_RelatedProject](association-issuetaskassociation_relatedproject-projectdata-service.md) <br/> |Relates an issue task association to a related project.  <br/> |
|[IssueTaskAssociation_Task](association-issuetaskassociation_task-projectdata-service.md) <br/> |Relates an issue task association to a task.  <br/> |
|[PortfolioAnalysis_AnalysisProjects_PortfolioAnalysisProject_Analysis](association-element-portfolioanalysis_analysisprojects-projectserverdata-service.md) <br/> |Relates a portfolio analysis to the analysis projects that it contains and relates portfolio analysis projects to an analysis.  <br/> |
|[PortfolioAnalysis_CostConstraintScenarios_CostConstraintScenario_Analysis](association-portfolioanalysis_costconstraintscenarios_costconstraintscenario_ana.md) <br/> |Relates a portfolio analysis to the cost constraint scenarios that it contains and relates a collection of cost constraint scenarios to its portfolio analysis.  <br/> |
|[PortfolioAnalysis_CreatedByResource](association-portfolioanalysis_createdbyresource-projectdata-service.md) <br/> |Relates portfolio analyses to the creating resource.  <br/> |
|[PortfolioAnalysis_ModifiedByResource](association-element-portfolioanalysis_modifiedbyresource-projectserverdata-servi.md) <br/> |Relates portfolio analysis to the resource that did modifications.  <br/> |
|[PortfolioAnalysis_Prioritization](association-element-portfolioanalysis_prioritization-projectserverdata-service.md) <br/> |Relates portfolio analyses to a prioritization.  <br/> |
|[PortfolioAnalysis_ResourceConstraintScenarios_ResourceConstraintScenario_Analysis](association-element-portfolioanalysis_resourceconstraintscenarios-projectserverd.md) <br/> |Relates portfolio analyses to resource constraint scenarios.  <br/> |
|[PortfolioAnalysisProject_Project](association-portfolioanalysisproject_project-projectdata-service.md) <br/> |Relates portfolio analysis projects to a project.  <br/> |
|[Prioritization_CreatedByResource](association-element-prioritization_createdbyresource-projectserverdata-service.md) <br/> |Relates prioritizations to a resource.  <br/> |
|[Prioritization_ModifiedByResource](association-element-prioritization_modifiedbyresource-projectserverdata-service.md) <br/> |Relates portfolio analysis prioritizations to the resource that modified prioritizations.  <br/> |
|[Prioritization_PrioritizationDriverRelations_PrioritizationDriverRelation_Prioritization](association-prioritization_prioritizationdriverrelations_prioritizationdriverrel.md) <br/> |Relates a prioritization to prioritization driver relations and relates prioritization driver relations to a prioritization.  <br/> |
|[Prioritization_PrioritizationDrivers_PrioritizationDriver_Prioritization](association-prioritization_prioritizationdrivers_prioritizationdriver_prioritiza.md) <br/> |Relates a prioritization to the prioritization drivers that it contains and relates a collection of prioritization drivers to its prioritization.  <br/> |
|[PrioritizationDriver_BusinessDriver](association-prioritizationdriver_businessdriver-projectdata-service.md) <br/> |Relates prioritization drivers to a business driver.  <br/> |
|[PrioritizationDriverRelation_BusinessDriver1](association-element-prioritizationdriverrelation_businessdriver1-projectserverda.md) <br/> |Relates project prioritizations in a portfolio analysis to the first business driver.  <br/> |
|[PrioritizationDriverRelation_BusinessDriver2](association-prioritizationdriverrelation_businessdriver2-projectdata-service.md) <br/> |Relates project prioritizations in a portfolio analysis to the second business driver.  <br/> |
|[Project_AssignmentBaselines_AssignmentBaseline_Project](association-element-project_assignmentbaselines-projectserverdata-service.md) <br/> |Relates a project to the assignment baselines that it contains and relates assignment baselines to a project.  <br/> |
|[Project_Assignments_Assignment_Project](association-project_assignments_assignment_project-projectdata-service.md) <br/> |Relates a project to the assignments that it contains and relates assignments to a project.  <br/> |
|[Project_Deliverables_Deliverable_Project](association-element-project_deliverables-projectserverdata-service.md) <br/> |Relates a project to the deliverables that it contains and relates deliverables to projects.  <br/> |
|[Project_Dependencies_Deliverable_DependentProjects](association-project_dependencies_deliverable_dependentprojects-projectdata-servi.md) <br/> |Relates project to dependencies and relates deliverables to dependent projects.  <br/> |
|[Project_Issues_Issue_Project](association-element-project_issues-projectserverdata-service.md) <br/> |Relates a project to the issues that it contains and relates a collection of issues to its project.  <br/> |
|[Project_Risks_Risk_Project](association-element-project_risks-projectserverdata-service.md) <br/> |Relates a project to the risks that it contains and relates a risk to its project.  <br/> |
|[Project_StagesInfo_ProjectWorkflowStageData_Project](association-project_stagesinfo_projectworkflowstagedata_project-projectdata-serv.md) <br/> |Relates a project to workflow stage information and relates workflow stage data to a project.  <br/> |
|[Project_Tasks_Task_Project](association-project_tasks_task_project-projectdata-service.md) <br/> |Relates a project to the tasks that it contains and relates a task to its project.  <br/> |
|[ProjectBaseline_Project](association-element-projectbaseline_project-projectserverdata-service.md) <br/> |Relates project baselines to a project.  <br/> |
|[ResourceConstraintScenario_CreatedByResource](association-resourceconstraintscenario_createdbyresource-projectdata-service.md) <br/> |Relates portfolio analysis resource constraint scenarios to a resource.  <br/> |
|[ResourceConstraintScenario_ModifiedByResource](association-resourceconstraintscenario_modifiedbyresource-projectdata-service.md) <br/> |Relates portfolio analysis resource constraint scenarios to a resource.  <br/> |
|[ResourceConstraintScenario_ResourceScenarioProjects_ResourceScenarioProject_ResourceConstraintScenario](association-element-resourceconstraintscenario_resourcescenarioprojects-projects.md) <br/> |Relates a resource constraint scenario to resource scenario projects and relates resource scenario projects to a resource constraint scenario.  <br/> |
|[ResourceScenarioProject_Analysis](association-element-resourcescenarioproject_analysis-projectserverdata-service.md) <br/> |Relates resource scenario projects to an analysis.  <br/> |
|[ResourceScenarioProject_CostConstraintScenario](association-resourcescenarioproject_costconstraintscenario-projectdata-service.md) <br/> |Relates resource scenario projects to a cost constraint scenario.  <br/> |
|[ResourceScenarioProject_Project](association-element-resourcescenarioproject_project-projectserverdata-service.md) <br/> |Relates a resource scenario project to its project.  <br/> |
|[ResourceTimephasedData_Resource_Resource_TimephasedInfoDataSet](association-resourcetimephaseddata_resource_resource_timephasedinfodataset-proje.md) <br/> |Relates resource timephased data to a resource and relates a resource to timephased information.  <br/> |
|[Risk_SubRisks](association-element-risk_subrisks-projectserverdata-service.md) <br/> |Relates risks to subrisks.  <br/> |
|[Risk_Tasks_Task_Risks](association-element-risk_trigeringtasks-projectserverdata-service.md) <br/> |Relates a risk to tasks and relates a task to risks.  <br/> |
|[RiskTaskAssociation_Project](association-risktaskassociation_project-projectdata-service.md) <br/> |Relates a risk task association to a project.  <br/> |
|[RiskTaskAssociation_RelatedProject](association-risktaskassociation_relatedproject-projectdata-service.md) <br/> |Relates risk task association to a related project.  <br/> |
|[RiskTaskAssociation_Risk](association-risktaskassociation_risk-projectdata-service.md) <br/> |Relates a risk task association to a risk.  <br/> |
|[RiskTaskAssociation_Task](association-risktaskassociation_task-projectdata-service.md) <br/> |Relates a risk task association to a task.  <br/> |
|[TaskBaseline_Project](association-element-taskbaseline_project-projectserverdata-service.md) <br/> |Relates task baselines to a project.  <br/> |
|[TaskBaseline_Task_Task_Baselines](association-element-taskbaseline_task-projectserverdata-service.md) <br/> |Relates a task to task baselines and relates task baselines to a task.  <br/> |
|[TaskBaseline_TaskBaselineTimephasedDataSet_TaskBaselineTimephasedData_TaskBaselines](association-taskbaseline_taskbaselinetimephaseddataset_taskbaselinetimephaseddat.md) <br/> |Relates a task baseline to task baseline timephased data and relates task baseline timephased data to task baselines.  <br/> |
|[TaskBaselineTimephasedData_Project](association-element-taskbaselinetimephaseddata_project-projectserverdata-service.md) <br/> |Relates a project to the task baseline timephased data that it contains.  <br/> |
|[TaskBaselineTimephasedData_Task_Task_BaselinesTimephasedDataSet](association-taskbaselinetimephaseddata_task_task_baselinestimephaseddataset-proj.md) <br/> |Relates task baseline timephased data to a task and relates a task to a baseline timephased dataset.  <br/> |
|[TaskTimephasedData_Project](association-tasktimephaseddata_project-projectdata-service.md) <br/> |Relates task timephased data to its project.  <br/> |
|[TaskTimephasedData_Task_Task_TimephasedInfo](association-tasktimephaseddata_task_task_timephasedinfo-projectdata-service.md) <br/> |Relates a task timephased data to a task and relates a task to timephased information.  <br/> |
|[Timesheet_Periods](association-element-timesheet_periods-projectserverdata-service.md) <br/> |Relates a timesheet period to its timesheet.  <br/> |
|[TimesheetLine_Actuals_TimesheetLineActualData_TimesheetLine](association-element-timesheetline_actuals-projectserverdata-service.md) <br/> |Relates a timesheet line to actual data and relates timesheet line actual data to a timesheet line.  <br/> |
|[TimesheetLine_ApproverResource](association-timesheetline_approverresource-projectdata-service.md) <br/> |Relates an approver resource to its timesheet line.  <br/> |
|[TimesheetLine_Timesheet_Timesheet_Lines](association-timesheetline_timesheet_timesheet_lines-projectdata-service.md) <br/> |Relates timesheet lines to a timesheet and relates a timesheet to timesheet lines.  <br/> |
|[TimesheetLine_TimesheetClass](association-element-timesheetline_timesheetclass-projectserverdata-service.md) <br/> |Relates a timesheet line to a timesheet class.  <br/> |
|[TimesheetLineActualData_LastChangedByResource](association-timesheetlineactualdata_lastchangedbyresource-projectdata-service.md) <br/> |Relates timesheet line actual data to a resource.  <br/> |
|[TimesheetLineActualData_Time](association-element-timesheetlineactualdata_time-projectserverdata-service.md) <br/> |Relates timesheet line actual data to a time entity.  <br/> |
   
## Remarks

OData queries of the Reporting tables can be used with Project Server online or on-premises. The OData schema for the **ProjectData** service contains two namespaces that are specified by **Schema** elements. The **ReportingData** namespace is used for queries of data for entities such as **Project**, **Resource**, and **Task**, and for entity associations such as project risks and resource assignments. 
  
The **ProjectData** service uses the **Microsoft.Office.Project.Server** namespace for queries of the reporting tables that return entity sets such as **Projects** and **Tasks**, and association sets such as **Ref_Projects_Tasks_Tasks**, which is the primary key that internally relates a **Projects_Tasks** association with the **Tasks** entity set. 
  
## See also

#### Reference

[Schema element: Microsoft.Office.Project.Server](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

