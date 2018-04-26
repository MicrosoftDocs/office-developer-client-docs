---
title: "Association RiskTaskAssociation_Project (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 2a671405-3ee9-4a17-9760-3c35fcd853b4
description: "The RiskTaskAssociation_Project association relates a risk task association to a project."
---

# Association: RiskTaskAssociation_Project (ProjectData service)

The **RiskTaskAssociation_Project** association relates a risk task association to a project. 
  
## Definition

```XML
<Association Name="RiskTaskAssociation_Project">
  <End Type="ReportingData.RiskTaskAssociation" Role="RiskTaskAssociation" Multiplicity="*" />
  <End Type="ReportingData.Project" Role="Project" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**RiskTaskAssociation_Project** <br/> |Identifies the two entity types that form the **RiskTaskAssociation_Project** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **RiskTaskAssociation_Project** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the RiskTaskAssociation_Project association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**RiskTaskAssociation** <br/> |[EntityType element: RiskTaskAssociation](entitytype-risktaskassociation-projectdata-service.md) <br/> |**\*** <br/> |The collection of risk task associations in the reporting tables.  <br/> |
|**Project** <br/> |[EntityType element: Project](entitytype-project-projectdata-service.md) <br/> |**0..1** <br/> |The project object that is referenced in the **RiskTaskAssociation_Project** association.  <br/> |
   
## Remarks

The **Project** navigation property in the **RiskTaskAssociation** entity uses the **RiskTaskAssociation_Project** association to query for a project that is associated with a collection of risk task associations. 
  
## See also

#### Reference

[EntityType element: Project](entitytype-project-projectdata-service.md)
  
[EntityType element: RiskTaskAssociation](entitytype-risktaskassociation-projectdata-service.md)

