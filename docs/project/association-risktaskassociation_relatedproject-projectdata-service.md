---
title: "Association RiskTaskAssociation_RelatedProject (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 9d93c156-cbae-4ef5-83f5-126fdba94429
description: "The RiskTaskAssociation_RelatedProject association relates risk task association to a related project."
---

# Association: RiskTaskAssociation_RelatedProject (ProjectData service)

The **RiskTaskAssociation_RelatedProject** association relates risk task association to a related project. 
  
## Definition

```XML
<Association Name="RiskTaskAssociation_RelatedProject">
  <End Type="ReportingData.RiskTaskAssociation" Role="RiskTaskAssociation" Multiplicity="*" />
  <End Type="ReportingData.Project" Role="RelatedProject" Multiplicity="0..1" />
</Association>

```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**RiskTaskAssociation_RelatedProject** <br/> |Identifies the two entity types that form the **RiskTaskAssociation_RelatedProject** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **RiskTaskAssociation_RelatedProject** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the RiskTaskAssociation_RelatedProject association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**RiskTaskAssociation** <br/> |[EntityType element: RiskTaskAssociation](entitytype-risktaskassociation-projectdata-service.md) <br/> |**\*** <br/> |The collection of risk task associations in the reporting tables.  <br/> |
|**RelatedProject** <br/> |[EntityType element: Project](entitytype-project-projectdata-service.md) <br/> |**0..1** <br/> |The related project that is referenced in the **RiskTaskAssociation_RelatedProject** association.  <br/> |
   
## Remarks

The **RelatedProject** navigation property in the **RiskTaskAssociation** entity uses the **RiskTaskAssociation_RelatedProject** association to query for a related project that is associated with a collection of risk task associations. 
  
## See also

#### Reference

[EntityType element: RiskTaskAssociation](entitytype-risktaskassociation-projectdata-service.md)
  
[EntityType element: Project](entitytype-project-projectdata-service.md)

