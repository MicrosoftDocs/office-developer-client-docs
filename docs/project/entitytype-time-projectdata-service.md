---
title: "EntityType Time (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: d636fb03-0288-493e-939b-7d4f7361911a
description: "Contains the properties that define the reporting data for the time entity in the ProjectData service."
---

# EntityType: Time (ProjectData service)

Contains the properties that define the reporting data for the time entity in the **ProjectData** service. 
  
## Example

The following REST query uses the [TimeSet](entityset-timeset-projectdata-service.md) entity set and the **TimeByDay** key to get the time entities for the specified time range in **ProjectData**. The query is all on one line.
  
```
https://<pwa_url>/_api/ProjectData/TimeSet
    ?$filter=TimeByDay ge datetime'2014-01-01'
    and TimeByDay le datetime'2014-06-30'
```

## Definition

```XML
<EntityType Name="Time">
  <Key>
    <PropertyRef Name="TimeByDay" />
  </Key>
  <Property Name="TimeByDay" Type="Edm.DateTime" Nullable="false" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of the time entity type. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. Unlike most entity types, there are no **NavigationProperty** child elements for the **Time** entity type. 
  
The **Key** element specifies the property that is the primary key for a time query. **TimeByDay** is a day along the timeline. 
  
### Property elements

The following table lists the **Property** elements for the **Time** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of Time**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**FiscalPeriodName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the fiscal period.  <br/> |
|**FiscalQuarter** <br/> |**Edm.Int32** <br/> |**true** <br/> |A fiscal quarterly time hierarchy in timephased data.  <br/> |
|**TimeByDay** <br/> |**Edm.DateTime** <br/> |**false** <br/> |**Key**         A primary key that identifies the day along a timeline. The granularity is in days only.  <br/> |
|**TimeDayOfTheMonth** <br/> |**Edm.Byte** <br/> |**false** <br/> |The value that represents the day within the month (1-31).  <br/> |
|**TimeDayOfTheWeek** <br/> |**Edm.Byte** <br/> |**false** <br/> |The value that represents the day within the week (1-7).  <br/> |
|**TimeMonthOfTheYear** <br/> |**Edm.Byte** <br/> |**false** <br/> |The value that represents the month within the year (1-12).  <br/> |
|**TimeQuarter** <br/> |**Edm.Byte** <br/> |**false** <br/> |The value that represents the calendar quarter within the year (1-4).  <br/> |
|**TimeWeekOfTheYear** <br/> |**Edm.Byte** <br/> |**false** <br/> |The value that represents the week within the year (1-52).  <br/> |
   
### NavigationProperty elements

There are no **NavigationProperty** child elements for the **Time** entity type. 
  
## See also

#### Reference

[TimeSet](entityset-timeset-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

