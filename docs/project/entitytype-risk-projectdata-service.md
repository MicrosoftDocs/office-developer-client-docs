---
title: "EntityType Risk (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 22e3e080-964d-4434-a633-73ac4c7b4cb7
description: "Contains the properties that define the reporting data for a risk in the ProjectData service."
---

# EntityType: Risk (ProjectData service)

Contains the properties that define the reporting data for a risk in the **ProjectData** service. 
  
## Example

The following REST query uses the [Risks](entityset-risks-projectdata-service.md) entity set and the **RiskId** key to get the specified risk and properties. The query is all on one line. 
  
```
https://<pwa_url>/_api/ProjectData/Risks
    ?$filter=RiskId eq guid'50569763-3ec4-4ab5-9c89-0ff07ae70c95'
    &amp;$select=Title,Status,Tasks

```

## Definition

```XML
<EntityType Name="Risk">
  <Key>
    <PropertyRef Name="ProjectId" />
    <PropertyRef Name="RiskId" />
  </Key>
  <Property Name="ProjectId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="Project" Relationship="ReportingData.Project_Risks_Risk_Project" ToRole="Project_Risks" FromRole="Risk_Project" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of a risk and navigation properties of that risk. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as related issues and affected tasks, that are associated with a risk. A navigation property uses an **Association** element in a query for a related entity collection 
  
The **Key** elements specify the properties that are the primary keys for a risk query. **ProjectId** is the project GUID and **RiskId** is the risk GUID. 
  
### Property elements

The following table lists the **Property** elements for the **Risk** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of Risk**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**AssignedToResource** <br/> |**Edm.String** <br/> |**true** <br/> |The resource to which a risk is assigned.  <br/> |
|**Category** <br/> |**Edm.String** <br/> |**true** <br/> |The category of a risk.  <br/> |
|**ContingencyPlan** <br/> |**Edm.String** <br/> |**true** <br/> |The contingency plan for a risk.  <br/> |
|**Cost** <br/> |**Edm.Double** <br/> |**true** <br/> |The total projected cost for a risk.  <br/> |
|**CostExposure** <br/> |**Edm.Double** <br/> |**true** <br/> |The overall threat of risk, calculated by multiplying the cost by the risk probability.  <br/> |
|**CreateByResource** <br/> |**Edm.String** <br/> |**true** <br/> |The resource that created a risk.  <br/> |
|**CreatedDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The date and time when a risk was created.  <br/> |
|**Description** <br/> |**Edm.String** <br/> |**true** <br/> |The text field for a risk description.  <br/> |
|**DueDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The due date for a risk.  <br/> |
|**Exposure** <br/> |**Edm.Double** <br/> |**true** <br/> |The overall threat of a risk, calculated by multiplying the risk probability by the impact.  <br/> |
|**Impact** <br/> |**Edm.Double** <br/> |**true** <br/> |The magnitude of the impact if a risk happens.  <br/> |
|**IsFolder** <br/> |**Edm.Boolean** <br/> |**false** <br/> |**True** if the risk is a folder in the SharePoint list.  <br/> |
|**ItemRelativeUrlPath** <br/> |**Edm.String** <br/> |**true** <br/> |The relative URL of the risk.  <br/> |
|**MitigationPlan** <br/> |**Edm.String** <br/> |**true** <br/> |A plan for handling problems that are related to risk factors.  <br/> |
|**ModifiedByResource** <br/> |**Edm.String** <br/> |**true** <br/> |The user who modified a risk.  <br/> |
|**ModifiedDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The date and time when a risk was modified.  <br/> |
|**NumberOfAttachments** <br/> |**Edm.Int32** <br/> |**true** <br/> |The number of attachments for a risk.  <br/> |
|**Owner** <br/> |**Edm.String** <br/> |**true** <br/> |The owner of a risk.  <br/> |
|**Probability** <br/> |**Edm.Double** <br/> |**true** <br/> |The percent probability that a risk will happen.  <br/> |
|**ProjectId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies a project with a risk.  <br/> |
|**ProjectName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the associated project.  <br/> |
|**RiskId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of a risk.  <br/> |
|**Status** <br/> |**Edm.String** <br/> |**true** <br/> |The status of a risk.  <br/> |
|**Title** <br/> |**Edm.String** <br/> |**true** <br/> |The title or name of a risk.  <br/> |
|**TriggerDescription** <br/> |**Edm.String** <br/> |**true** <br/> |The description of the trigger that causes a risk.  <br/> |
|**TriggerTask** <br/> |**Edm.String** <br/> |**true** <br/> |The condition that triggers the contingency plan (for example, date, exposure over threshold, tasks not completed, or other user-assigned values).  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **Risk** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property. 
  
There are two types of **Relationship** attributes. One type contains two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **Project** navigation property, the primary type is **Project**, and the secondary type is **Risk**. For this type of navigation, the **FromRole** is **Project_Risks**, and the **ToRole** is **Risk_Project**.
  
The other type of **Relationship** attribute contains a single pair of names. The first name in the pair is the primary type in the navigation. The second name in the pair is the secondary type in the navigation. For example, in the **Project** navigation property relationship, **Project_Risks** is the primary type and **Risk_Project** is the secondary type. 
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Project** <br/> |[Project_Risks_Risk_Project](association-element-project_risks-projectserverdata-service.md) <br/> |Relates a project to a collection of risks and a risk to a project.  <br/> |
|**RelatedIssues** <br/> |[Issue_RelatedRisks_Risk_RelatedIssues](association-element-issue_relatedrisks-projectserverdata-service.md) <br/> |Relates a collection of issues to related risks and a collection of risks to related issues.  <br/> |
|**SubRisks** <br/> |[Risk_Subrisks](association-element-risk_subrisks-projectserverdata-service.md) <br/> |Relates a collection of risks to a subrisk.  <br/> |
|**Tasks** <br/> |[Risk_Tasks_Task_Risks](association-element-risk_trigeringtasks-projectserverdata-service.md) <br/> |Relates the collection of tasks associated with a risk to the collection of risks associated with a task.  <br/> |
   
## See also

#### Reference

[Risks](entityset-risks-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

