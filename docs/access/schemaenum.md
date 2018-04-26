---
title: "SchemaEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 6147b682-3c4f-ea91-fff6-ac73107d206d

---

# SchemaEnum

Specifies the type of schema **Recordset** that the [OpenSchema](openschema-method-ado.md) method retrieves. 
  
 **Remarks**
  
Additional information about the function and columns returned for each ADO constant can be found in topics of Appendix B of the  *OLE DB Programmers Reference*  . The name of each topic is listed in parentheses in the Description section of the table below. 
  
Additional information about the function and columns returned for each ADO MD constant can be found in topics of Chapter 23 of the  *OLE DB for OLAP*  documentation. The name of each topic is listed in parentheses and marked with an asterisk (*) in the Description column of the table below. 
  
Translate the data types of columns in the OLE DB documentation to ADO data types by referring to the Description column of the ADO [DataTypeEnum](datatypeenum.md) topic. For example, an OLE DB data type of **DBTYPE_WSTR** is equivalent to an ADO data type of **adWChar**. 
  
ADO generates schema-like results for the constants, **adSchemaDBInfoKeywords** and **adSchemaDBInfoLiterals**. ADO creates a **Recordset**, then fills each row with the values returned respectively by the **IDBInfo::GetKeywords** and **IDBInfo::GetLiteralInfo** methods. Additional information about these methods can be found in the IDBInfo section of the  *OLE DB Programmer's Reference.* 
  
|**Constant**|**Value**|**Description**|**Constraint Columns**|
|:-----|:-----|:-----|:-----|
|**adSchemaAsserts** <br/> |0  <br/> |Returns the assertions defined in the catalog that are owned by a given user. (ASSERTIONS Rowset)  <br/> |CONSTRAINT_CATALOG          CONSTRAINT_SCHEMA          CONSTRAINT_NAME  <br/> |
|**adSchemaCatalogs** <br/> |1  <br/> |Returns the physical attributes associated with catalogs accessible from the DBMS. (CATALOGS Rowset)  <br/> |CATALOG_NAME  <br/> |
|**adSchemaCharacterSets** <br/> |2  <br/> |Returns the character sets defined in the catalog that are accessible to a given user. (CHARACTER_SETS Rowset)  <br/> |CHARACTER_SET_CATALOG          CHARACTER_SET_SCHEMA          CHARACTER_SET_NAME  <br/> |
|**adSchemaCheckConstraints** <br/> |5  <br/> |Returns the check constraints defined in the catalog that are owned by a given user. (CHECK_CONSTRAINTS Rowset)  <br/> |CONSTRAINT_CATALOG          CONSTRAINT_SCHEMA          CONSTRAINT_NAME  <br/> |
|**adSchemaCollations** <br/> |3  <br/> |Returns the character collations defined in the catalog that are accessible to a given user. (COLLATIONS Rowset)  <br/> |COLLATION_CATALOG          COLLATION_SCHEMA          COLLATION_NAME  <br/> |
|**adSchemaColumnPrivileges** <br/> |13  <br/> |Returns the privileges on columns of tables defined in the catalog that are available to, or granted by, a given user. (COLUMN_PRIVILEGES Rowset)  <br/> |TABLE_CATALOG          TABLE_SCHEMA          TABLE_NAME          COLUMN_NAME          GRANTOR          GRANTEE  <br/> |
|**adSchemaColumns** <br/> |4  <br/> |Returns the columns of tables (including views) defined in the catalog that are accessible to a given user. (COLUMNS Rowset)  <br/> |TABLE_CATALOG          TABLE_SCHEMA          TABLE_NAME          COLUMN_NAME  <br/> |
|**adSchemaColumnsDomainUsage** <br/> |11  <br/> |Returns the columns defined in the catalog that are dependent on a domain defined in the catalog and owned by a given user. (COLUMN_DOMAIN_USAGE Rowset)  <br/> |DOMAIN_CATALOG          DOMAIN_SCHEMA          DOMAIN_NAME          COLUMN_NAME  <br/> |
|**adSchemaConstraintColumnUsage** <br/> |6  <br/> |Returns the columns used by referential constraints, unique constraints, check constraints, and assertions, defined in the catalog and owned by a given user. (CONSTRAINT_COLUMN_USAGE Rowset)  <br/> |TABLE_CATALOG          TABLE_SCHEMA          TABLE_NAME          COLUMN_NAME  <br/> |
|**adSchemaConstraintTableUsage** <br/> |7  <br/> |Returns the tables that are used by referential constraints, unique constraints, check constraints, and assertions defined in the catalog and owned by a given user. (CONSTRAINT_TABLE_USAGE Rowset)  <br/> |TABLE_CATALOG          TABLE_SCHEMA          TABLE_NAME  <br/> |
|**adSchemaCubes** <br/> |32  <br/> |Returns information about the available cubes in a schema (or the catalog, if the provider does not support schemas). (CUBES Rowset\*)  <br/> |CATALOG_NAME          SCHEMA_NAME          CUBE_NAME  <br/> |
|**adSchemaDBInfoKeywords** <br/> |30  <br/> |Returns a list of provider-specific keywords. (IDBInfo::GetKeywords \*)  <br/> |\<None\>  <br/> |
|**adSchemaDBInfoLiterals** <br/> |31  <br/> |Returns a list of provider-specific literals used in text commands. (IDBInfo::GetLiteralInfo \*)  <br/> |\<None\>  <br/> |
|**adSchemaDimensions** <br/> |33  <br/> |Returns information about the dimensions in a given cube. It has one row for each dimension. (DIMENSIONS Rowset \*)  <br/> |CATALOG_NAME          SCHEMA_NAME          CUBE_NAME          DIMENSION_NAME          DIMENSION_UNIQUE_NAME  <br/> |
|**adSchemaForeignKeys** <br/> |27  <br/> |Returns the foreign key columns defined in the catalog by a given user. (FOREIGN_KEYS Rowset)  <br/> |PK_TABLE_CATALOG          PK_TABLE_SCHEMA          PK_TABLE_NAME          FK_TABLE_CATALOG          FK_TABLE_SCHEMA          FK_TABLE_NAME  <br/> |
|**adSchemaHierarchies** <br/> |34  <br/> |Returns information about the hierarchies available in a dimension. (HIERARCHIES Rowset \*)  <br/> |CATALOG_NAME          SCHEMA_NAME          CUBE_NAME          DIMENSION_UNIQUE_NAME          HIERARCHY_NAME          HIERARCHY_UNIQUE_NAME  <br/> |
|**adSchemaIndexes** <br/> |12  <br/> |Returns the indexes defined in the catalog that are owned by a given user. (INDEXES Rowset)  <br/> |TABLE_CATALOG          TABLE_SCHEMA          INDEX_NAME          TYPE          TABLE_NAME  <br/> |
|**adSchemaKeyColumnUsage** <br/> |8  <br/> |Returns the columns defined in the catalog that are constrained as keys by a given user. (KEY_COLUMN_USAGE Rowset)  <br/> |CONSTRAINT_CATALOG          CONSTRAINT_SCHEMA          CONSTRAINT_NAME          TABLE_CATALOG          TABLE_SCHEMA          TABLE_NAME          COLUMN_NAME  <br/> |
|**adSchemaLevels** <br/> |35  <br/> |Returns information about the levels available in a dimension. (LEVELS Rowset\*)  <br/> |CATALOG_NAME          SCHEMA_NAME          CUBE_NAME          DIMENSION_UNIQUE_NAME          HIERARCHY_UNIQUE_NAME          LEVEL_NAME          LEVEL_UNIQUE_NAME  <br/> |
|**adSchemaMeasures** <br/> |36  <br/> |Returns information about the available measures. (MEASURES Rowset \*)  <br/> |CATALOG_NAME          SCHEMA_NAME          CUBE_NAME          MEASURE_NAME          MEASURE_UNIQUE_NAME  <br/> |
|**adSchemaMembers** <br/> |38  <br/> |Returns information about the available members. (MEMBERS Rowset \*)  <br/> |CATALOG_NAME          SCHEMA_NAME          CUBE_NAME          DIMENSION_UNIQUE_NAME          HIERARCHY_UNIQUE_NAME          LEVEL_UNIQUE_NAME          LEVEL_NUMBER          MEMBER_NAME          MEMBER_UNIQUE_NAME          MEMBER_CAPTION          MEMBER_TYPE          Tree operator (For more information, see the OLE DB for OLAP documentation.)  <br/> |
|**adSchemaPrimaryKeys** <br/> |28  <br/> |Returns the primary key columns defined in the catalog by a given user. (PRIMARY_KEYS Rowset)  <br/> |PK_TABLE_CATALOG          PK_TABLE_SCHEMA          PK_TABLE_NAME  <br/> |
|**adSchemaProcedureColumns** <br/> |29  <br/> |Returns information about the columns of rowsets returned by procedures. (PROCEDURE_COLUMNS Rowset)  <br/> |PROCEDURE_CATALOG          PROCEDURE_SCHEMA          PROCEDURE_NAME          COLUMN_NAME  <br/> |
|**adSchemaProcedureParameters** <br/> |26  <br/> |Returns information about the parameters and return codes of procedures. (PROCEDURE_PARAMETERS Rowset)  <br/> |PROCEDURE_CATALOG          PROCEDURE_SCHEMA          PROCEDURE_NAME          PARAMETER_NAME  <br/> |
|**adSchemaProcedures** <br/> |16  <br/> |Returns the procedures defined in the catalog that are owned by a given user. (PROCEDURES Rowset)  <br/> |PROCEDURE_CATALOG          PROCEDURE_SCHEMA          PROCEDURE_NAME          PROCEDURE_TYPE  <br/> |
|**adSchemaProperties** <br/> |37  <br/> |Returns information about the available properties for each level of the dimension. (PROPERTIES Rowset \*)  <br/> |CATALOG_NAME          SCHEMA_NAME          CUBE_NAME          DIMENSION_UNIQUE_NAME          HIERARCHY_UNIQUE_NAME          LEVEL_UNIQUE_NAME          MEMBER_UNIQUE_NAME          PROPERTY_TYPE          PROPERTY_NAME  <br/> |
|**adSchemaProviderSpecific** <br/> |-1  <br/> |Used if the provider defines its own nonstandard schema queries.  <br/> |\<Provider specific\>  <br/> |
|**adSchemaProviderTypes** <br/> |22  <br/> |Returns the (base) data types supported by the data provider. (PROVIDER_TYPES Rowset)  <br/> |DATA_TYPE          BEST_MATCH  <br/> |
|**AdSchemaReferentialConstraints** <br/> |9  <br/> |Returns the referential constraints defined in the catalog that are owned by a given user. (REFERENTIAL_CONSTRAINTS Rowset)  <br/> |CONSTRAINT_CATALOG          CONSTRAINT_SCHEMA          CONSTRAINT_NAME  <br/> |
|**adSchemaSchemata** <br/> |17  <br/> |Returns the schemas (database objects) that are owned by a given user. (SCHEMATA Rowset)  <br/> |CATALOG_NAME          SCHEMA_NAME          SCHEMA_OWNER  <br/> |
|**adSchemaSQLLanguages** <br/> |18  <br/> |Returns the conformance levels, options, and dialects supported by the SQL-implementation processing data defined in the catalog. (SQL_LANGUAGES Rowset)  <br/> |\<None\>  <br/> |
|**adSchemaStatistics** <br/> |19  <br/> |Returns the statistics defined in the catalog that are owned by a given user. (STATISTICS Rowset)  <br/> |TABLE_CATALOG          TABLE_SCHEMA          TABLE_NAME  <br/> |
|**adSchemaTableConstraints** <br/> |10  <br/> |Returns the table constraints defined in the catalog that are owned by a given user. (TABLE_CONSTRAINTS Rowset)  <br/> |CONSTRAINT_CATALOG          CONSTRAINT_SCHEMA          CONSTRAINT_NAME          TABLE_CATALOG          TABLE_SCHEMA          TABLE_NAME          CONSTRAINT_TYPE  <br/> |
|**adSchemaTablePrivileges** <br/> |14  <br/> |Returns the privileges on tables defined in the catalog that are available to, or granted by, a given user. (TABLE_PRIVILEGES Rowset)  <br/> |TABLE_CATALOG          TABLE_SCHEMA          TABLE_NAME          GRANTOR          GRANTEE  <br/> |
|**adSchemaTables** <br/> |20  <br/> |Returns the tables (including views) defined in the catalog that are accessible to a given user. (TABLES Rowset)  <br/> |TABLE_CATALOG          TABLE_SCHEMA          TABLE_NAME          TABLE_TYPE  <br/> |
|**adSchemaTranslations** <br/> |21  <br/> |Returns the character translations defined in the catalog that are accessible to a given user. (TRANSLATIONS Rowset)  <br/> |TRANSLATION_CATALOG          TRANSLATION_SCHEMA          TRANSLATION_NAME  <br/> |
|**adSchemaTrustees** <br/> |39  <br/> |Reserved for future use.  <br/> |
  
 <br/> |
|**adSchemaUsagePrivileges** <br/> |15  <br/> |Returns the USAGE privileges on objects defined in the catalog that are available to, or granted by, a given user. (USAGE_PRIVILEGES Rowset)  <br/> |OBJECT_CATALOG          OBJECT_SCHEMA          OBJECT_NAME          OBJECT_TYPE          GRANTOR          GRANTEE  <br/> |
|**adSchemaViewColumnUsage** <br/> |24  <br/> |Returns the columns on which viewed tables, defined in the catalog and owned by a given user, are dependent. (VIEW_COLUMN_USAGE Rowset)  <br/> |VIEW_CATALOG          VIEW_SCHEMA          VIEW_NAME  <br/> |
|**adSchemaViews** <br/> |23  <br/> |Returns the views defined in the catalog that are accessible to a given user. (VIEWS Rowset)  <br/> |TABLE_CATALOG          TABLE_SCHEMA          TABLE_NAME  <br/> |
|**adSchemaViewTableUsage** <br/> |25  <br/> |Returns the tables on which viewed tables, defined in the catalog and owned by a given user, are dependent. (VIEW_TABLE_USAGE Rowset)  <br/> |VIEW_CATALOG          VIEW_SCHEMA          VIEW_NAME  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.Schema.ASSERTS  <br/> |
|AdoEnums.Schema.CATALOGS  <br/> |
|AdoEnums.Schema.CHARACTERSETS  <br/> |
|AdoEnums.Schema.CHECKCONSTRAINTS  <br/> |
|AdoEnums.Schema.COLLATIONS  <br/> |
|AdoEnums.Schema.COLUMNPRIVILEGES  <br/> |
|AdoEnums.Schema.COLUMNS  <br/> |
|AdoEnums.Schema.COLUMNSDOMAINUSAGE  <br/> |
|AdoEnums.Schema.CONSTRAINTCOLUMNUSAGE  <br/> |
|AdoEnums.Schema.CONSTRAINTTABLEUSAGE  <br/> |
|AdoEnums.Schema.CUBES  <br/> |
|AdoEnums.Schema.DBINFOKEYWORDS  <br/> |
|AdoEnums.Schema.DBINFOLITERALS  <br/> |
|AdoEnums.Schema.DIMENSIONS  <br/> |
|AdoEnums.Schema.FOREIGNKEYS  <br/> |
|AdoEnums.Schema.HIERARCHIES  <br/> |
|AdoEnums.Schema.INDEXES  <br/> |
|AdoEnums.Schema.KEYCOLUMNUSAGE  <br/> |
|AdoEnums.Schema.LEVELS  <br/> |
|AdoEnums.Schema.MEASURES  <br/> |
|AdoEnums.Schema.MEMBERS  <br/> |
|AdoEnums.Schema.PRIMARYKEYS  <br/> |
|AdoEnums.Schema.PROCEDURECOLUMNS  <br/> |
|AdoEnums.Schema.PROCEDUREPARAMETERS  <br/> |
|AdoEnums.Schema.PROCEDURES  <br/> |
|AdoEnums.Schema.PROPERTIES  <br/> |
|AdoEnums.Schema.PROVIDERSPECIFIC  <br/> |
|AdoEnums.Schema.PROVIDERTYPES  <br/> |
|AdoEnums.Schema.REFERENTIALCONTRAINTS  <br/> |
|AdoEnums.Schema.SCHEMATA  <br/> |
|AdoEnums.Schema.SQLLANGUAGES  <br/> |
|AdoEnums.Schema.STATISTICS  <br/> |
|AdoEnums.Schema.TABLECONSTRAINTS  <br/> |
|AdoEnums.Schema.TABLEPRIVILEGES  <br/> |
|AdoEnums.Schema.TABLES  <br/> |
|AdoEnums.Schema.TRANSLATIONS  <br/> |
|AdoEnums.Schema.TRUSTEES  <br/> |
|AdoEnums.Schema.USAGEPRIVILEGES  <br/> |
|AdoEnums.Schema.VIEWCOLUMNUSAGE  <br/> |
|AdoEnums.Schema.VIEWS  <br/> |
|AdoEnums.Schema.VIEWTABLEUSAGE  <br/> |
   

