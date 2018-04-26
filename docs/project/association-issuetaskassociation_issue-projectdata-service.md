---
title: "Association IssueTaskAssociation_Issue (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: b83348b5-69a2-48b0-add9-f91dd97bb599
description: "The IssueTaskAssociation_Issue association relates an issue task association to an issue."
---

# Association: IssueTaskAssociation_Issue (ProjectData service)

The **IssueTaskAssociation_Issue** association relates an issue task association to an issue. 
  
## Definition

```XML
<Association Name="IssueTaskAssociation_Issue">
  <End Type="ReportingData.IssueTaskAssociation" Role="IssueTaskAssociation" Multiplicity="*" />
  <End Type="ReportingData.Issue" Role="Issue" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**IssueTaskAssociation_Issue** <br/> |Identifies the two entity types that form the **IssueTaskAssociation_Issue** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **IssueTaskAssociation_Issue** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the IssueTaskAssociation_Issue association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**IssueTaskAssociation** <br/> |[EntityType element: IssueTaskAssocia entitytype-issuetaskassociation-projectdata-servicetion](entitytype-issuetaskassociation-projectdata-service.md) <br/> |**\*** <br/> |There can be many issue task associations that correspond to an issue.  <br/> |
|**Issue** <br/> |[EntityType element: Issue](entitytype-issue-projectdata-service.md) <br/> |**0..1** <br/> |There is one issue that corresponds to a collection of issue task assocations.  <br/> |
   
## Remarks

The **Issue** navigation property in the **IssueTaskAssociation** entity uses the **IssueTaskAssociation_Issue** association to query for an issue that is associated with an issue task assocation. 
  
## See also

#### Reference

[EntityType element: Issue](entitytype-issue-projectdata-service.md)
  
[EntityType element: IssueTaskAssociation](entitytype-issuetaskassociation-projectdata-service.md)

