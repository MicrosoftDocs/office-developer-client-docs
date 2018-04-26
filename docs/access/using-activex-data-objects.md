---
title: "Using ActiveX Data Objects"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm5285627
  
localization_priority: Normal
ms.assetid: 64055c45-7a27-2296-468a-015362898329

description: "Microsoft Access provides three object models to use in the creation, maintaining and managing of your Access databases and their related data by using Visual Basic."
---

# Using ActiveX Data Objects

Microsoft Access provides three object models to use in the creation, maintaining and managing of your Access databases and their related data by using Visual Basic.
  
## Microsoft ActiveX Data Objects (ADO)

ADO contains the objects needed to create, maintain, and delete records in a given datasource.
  
## Microsoft ADO Ext. for DDL and Security (ADOX)

ADOX provides the Data Definition Language(DDL) objects needed to create a new database and its contained objects in addition to the objects needed to manage security.
  
 **Microsoft Jet and Replication Objects 2.5 Library (JRO)**
  
Since ADO objects were designed to work with many databases in addition to Microsoft Jet databases, functionality specific to Jet was broken out into the JRO library.
  
The following table lists the functionality provided by each compared to DAO.
  
|**Functionality**|**DAO**|**ADO<sup>1</sup>**|**ADOX<sup>2</sup>**|**JRO           (MDB's Only)**|
|:-----|:-----|:-----|:-----|:-----|
|Create Recordsets  <br/> |X  <br/> |X  <br/> |||
|Edit Startup properties  <br/> |X  <br/> |X\*\*  <br/> |||
|Support ANSI92 SQL\*\*\*  <br/> ||X  <br/> |X  <br/> ||
|Create Tables  <br/> |X  <br/> ||X  <br/> ||
|Create New Database  <br/> |X  <br/> ||X\*  <br/> ||
|Edit Existing Table properties  <br/> |X  <br/> ||X  <br/> ||
|Create table relationships  <br/> |X  <br/> ||X\*  <br/> ||
|Edit security settings  <br/> |X  <br/> ||X\*  <br/> ||
|Support for Compression attribute for column data  <br/> |||X  <br/> ||
|Edit stored, basic SQL queries or views  <br/> |X  <br/> ||X\*  <br/> ||
|Create permanent queries that are accessible only through code.  <br/> |||X\*  <br/> ||
|Create queries accessible through database container/UI and code.  <br/> |X  <br/> ||||
|Compact/Encode database  <br/> |X  <br/> |||X<sup>4</sup> <br/> |
|Refresh Cache  <br/> |X  <br/> |||X  <br/> |
|Make Database Replicable  <br/> |X  <br/> |||X<sup>3</sup> <br/> |
|Make Database Replicas  <br/> |X  <br/> |||X<sup>3</sup> <br/> |
|Synchronize Replicas  <br/> |X  <br/> |||X<sup>3</sup> <br/> |
|Edit Database properties  <br/> |X  <br/> ||||
|Create custom database properties  <br/> |X  <br/> ||||
|Edit table column properties  <br/> |X  <br/> ||||
   
\* Only available when working with Microsoft Access databases. Future versions of the SQL Provider may provide this functionality in Microsoft Access projects (.adp).
  
\*\* Only available when working with Access projects.
  
\*\*\* Though the Access database engine does support some ANSI 92 SQL it is not yet fully ANSI92 compliant.
  
<sup>1</sup> Uses **Connection** object to reference to database 
  
<sup>2</sup> Uses **Catalog** object to reference database 
  
<sup>3</sup> Uses **Replica** object to reference database 
  
<sup>4</sup> Uses **JetEngine** object to reference database 
  
> [!NOTE]
> Unlike DAO, ADO and ADOX objects can perform the marked actions in databases other then Jet as long as the provider for those databases supports that action. 
  

