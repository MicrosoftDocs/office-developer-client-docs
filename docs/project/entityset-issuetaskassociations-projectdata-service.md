---
title: "EntitySet IssueTaskAssociations (ProjectData service)"

 
manager: soliver
ms.date: 5/19/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: f8517ba4-d5fe-4f33-90f8-89358f080bbd
description: "Specifies the collection of issue task associations in the ReportingData schema."
---

# EntitySet: IssueTaskAssociations (ProjectData service)

Specifies the collection of issue task associations in the **ReportingData** schema. 
  
## Definition

```XML
<EntitySet Name="IssueTaskAssociations" EntityType="ReportingData.IssueTaskAssociation" />
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**IssueTaskAssociations** <br/> |The name of the entity set.  <br/> |
|**EntityType** <br/> |**ReportingData.IssueTaskAssociation** <br/> |The type of entity.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[EntityContainer element: ReportingData](entitycontainer-reportingdata-projectdata-service.md) <br/> |Contains definitions of entity sets for internal use in queries of the online Reporting database.  <br/> |
   
## Child elements

||
|:-----|
|None |
   
## Remarks

Each entity set has a specific page-size limit. For information about page limits for on-premises and online ProjectData queries and how to set the on-premises page limit, see [ProjectData - OData service reference](projectdataproject-odata-service-reference.md).
  

