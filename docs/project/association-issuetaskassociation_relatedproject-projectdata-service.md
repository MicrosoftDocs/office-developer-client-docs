---
title: "Association IssueTaskAssociation_RelatedProject (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: da690afa-0744-4d5c-b2bc-dff308e37ba6
description: "The IssueTaskAssociation_RelatedProject association relates a related project to an issue task association."
---

# Association: IssueTaskAssociation_RelatedProject (ProjectData service)

The **IssueTaskAssociation_RelatedProject** association relates a related project to an issue task association. 
  
## Definition

```XML
<Association Name="IssueTaskAssociation_RelatedProject">
  <End Type="ReportingData.Project" Role="RelatedProject" Multiplicity="0..1" />
  <End Type="ReportingData.IssueTaskAssociation" Role="IssueTaskAssociation" Multiplicity="*" />
</Association>

```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**IssueTaskAssociation_RelatedProject** <br/> |Identifies the two entity types that form the **IssueTaskAssociation_RelatedProject** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **IssueTaskAssociation_RelatedProject** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the IssueTaskAssociation_RelatedProject association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**IssueTaskAssociation** <br/> |[EntityType element: IssueTaskAssociation](entitytype-issuetaskassociation-projectdata-service.md) <br/> |**\*** <br/> |The collection of issue task associations in the reporting tables.  <br/> |
|**RelatedProject** <br/> |[EntityType element: Project](entitytype-project-projectdata-service.md) <br/> |**0..1** <br/> |The related project that is referenced in the **IssueTaskAssociation_RelatedProject** association.  <br/> |
   
## Remarks

The **RelatedProject** navigation property in the **IssueTaskAssociation** entity uses the **IssueTaskAssociation_RelatedProject** association to query for a related project that is associated with a collection of issue task associations. 
  
## See also

#### Reference

[EntityType element: IssueTaskAssociation](entitytype-issuetaskassociation-projectdata-service.md)
  
[EntityType element: Project](entitytype-project-projectdata-service.md)

