---
title: "Schema Microsoft.Office.Project.Server (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 78c499a7-00e6-47bc-88c6-18040efbc99b
description: "The Microsoft.Office.Project.Server namespace contains the ReportingData entity container, which defines entity sets and association sets for queries of the ProjectData service."
---

# Schema: Microsoft.Office.Project.Server (ProjectData service)

The **Microsoft.Office.Project.Server** namespace contains the **ReportingData** entity container, which defines entity sets and association sets for queries of the **ProjectData** service. 
  
## Definition

```
<Schema Namespace="Microsoft.Office.Project.Server" 
    xmlns:d="http://schemas.microsoft.com/ado/2007/08/dataservices" 
    xmlns:m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata" 
    xmlns="http://schemas.microsoft.com/ado/2007/05/edm">
```

The XML namespace attributes ( **xmlns**) specify the namespaces for services and metadata in the OData specification, and for the Entity Data Model (EDM) of an OData service.
  
## Parent element

||
|:-----|
|None |
   
## Child elements

|**Element**|**Description**|
|:-----|:-----|
|**Using element** <br/> |Specifies the namespace of the **EntityContainer** element for **ReportingData** and alias of the namespace, for internal use.  <br/> |
|[EntityContainer element: ReportingData](entitycontainer-reportingdata-projectdata-service.md) <br/> |Contains definitions of entity sets and association sets, for internal use in queries of the Project Server reporting tables.  <br/> |
   
## Remarks

OData queries of the reporting tables can be used online or on-premises with Project Server. The OData schema for the **ProjectData** service uses two namespaces, **ReportingData** and **Microsoft.Office.Project.Server**, in the creation of **Schema** elements. The **Microsoft.Office.Project.Server** namespace is used by the **ProjectData** service for internal queries of the Reporting database. The **ReportingData** namespace is used for external queries of data. 
  
## See also

#### Reference

[Schema element: ReportingData](schema-reportingdata-projectdata-service.md)

