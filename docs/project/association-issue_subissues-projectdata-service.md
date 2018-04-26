---
title: "Association Issue_SubIssues (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 887d838f-9c17-4e03-b52a-e37e9fd6f831
description: "The Issue_SubIssues association relates issues to subissues."
---

# Association: Issue_SubIssues (ProjectData service)

The **Issue_SubIssues** association relates issues to subissues. 
  
## Definition

```XML
<Association Name="Issue_SubIssues">
  <End Type="ReportingData.Issue" Role="SubIssues" Multiplicity="*" />
  <End Type="ReportingData.Issue" Role="Issue" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Issue_SubIssues** <br/> |Identifies the two entity types that form the **Issue_SubIssues** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **Issue_SubIssues** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the Issue_SubIssues association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**Issue** <br/> |[EntityType element: Issue](entitytype-issue-projectdata-service.md) <br/> |**\*** <br/> |The collection of issues in the reporting tables.  <br/> |
|**SubIssues** <br/> |[EntityType element: Issue](entitytype-issue-projectdata-service.md) <br/> |**\*** <br/> |The collection of subissues in the reporting tables.  <br/> |
   
## Remarks

The **SubIssues** navigation property in the **Issue** entity uses the **Issue_SubIssues** association to query for subissues that are associated with a collection of issues. 
  
## See also

#### Reference

[EntityType element: Issue](entitytype-issue-projectdata-service.md)

