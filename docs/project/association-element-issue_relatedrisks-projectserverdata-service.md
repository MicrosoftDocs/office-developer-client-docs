---
title: "Association element Issue_RelatedRisks (ProjectServerData service)"

 
manager: luken
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 1949a26e-4b8f-4919-beb7-74b8ccaa568d
description: "The Issue_RelatedRisks_Risk_RelatedIssues association relates issues to related risks and risks to related issues."
---

# Association element: Issue_RelatedRisks (ProjectServerData service)

The **Issue_RelatedRisks_Risk_RelatedIssues** association relates issues to related risks and risks to related issues. 
  
## Definition

```XML
<Association Name="Issue_RelatedRisks_Risk_RelatedIssues">
  <End Type="ReportingData.Risk" Role="Risk_RelatedIssues" Multiplicity="*" />
  <End Type="ReportingData.Issue" Role="Issue_RelatedRisks" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Issue_RelatedRisks_Risk_RelatedIssues** <br/> |Identifies the entity types and the navigation properties that form the two-way association for issues and risks. In the first half of the name, **Issues** is the entity type and **RelateRisks** is the navigation property. In the second half of the name, **Risk** is the entity type and **RelatedIssues** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **Issue_RelatedRisks_Risk_RelatedIssues** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the Issue_RelatedRisks_Risk_RelatedIssues association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**Issue_RelatedRisks** <br/> |[EntityType element: Issue](entitytype-issue-projectdata-service.md) <br/> |**\*** <br/> |There can be many issues that correspond with related risks.  <br/> |
|**Risk_RelatedIssues** <br/> |[EntityType element: Risk](entitytype-risk-projectdata-service.md) <br/> |**\*** <br/> |There can be many risks that correspond with related issues.  <br/> |
   
## Remarks

One end of the association is the **Issue** entity, and the other end is the **Risk** entity. The **Issue** entity type contains the **RelatedRisks** navigation property, where the **FromRole** defines **Issue_RelatedRisks** as the start of the association to get the collection of related risks in a collection of issues. Similarly, the **Risk** entity type contains the **RelatedIssues** navigation property, where the **FromRole** defines **Risk_RelatedIssues** as the start of the association to get the related issues that are associated with a collection of risks. 
  
## See also

#### Reference

[EntityType element: Issue](entitytype-issue-projectdata-service.md)
  
[EntityType element: Risk](entitytype-risk-projectdata-service.md)

