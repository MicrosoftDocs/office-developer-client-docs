---
title: SchemaEnum (Access desktop database reference)
TOCTitle: SchemaEnum
ms:assetid: 6147b682-3c4f-ea91-fff6-ac73107d206d
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249359(v=office.15)
ms:contentKeyID: 48545208
ms.date: 09/18/2015
mtps_version: v=office.15
---

# SchemaEnum


**Applies to**: Access 2013 | Office 2013

Specifies the type of schema **Recordset** that the [OpenSchema](openschema-method-ado.md) method retrieves.

**Remarks**

Additional information about the function and columns returned for each ADO constant can be found in topics of Appendix B of the *OLE DB Programmers Reference*. The name of each topic is listed in parentheses in the Description section of the table below.

Additional information about the function and columns returned for each ADO MD constant can be found in topics of Chapter 23 of the *OLE DB for OLAP* documentation. The name of each topic is listed in parentheses and marked with an asterisk (\*) in the Description column of the table below.

Translate the data types of columns in the OLE DB documentation to ADO data types by referring to the Description column of the ADO [DataTypeEnum](datatypeenum.md) topic. For example, an OLE DB data type of **DBTYPE\_WSTR** is equivalent to an ADO data type of **adWChar**.

ADO generates schema-like results for the constants, **adSchemaDBInfoKeywords** and **adSchemaDBInfoLiterals**. ADO creates a **Recordset**, then fills each row with the values returned respectively by the **IDBInfo::GetKeywords** and **IDBInfo::GetLiteralInfo** methods. Additional information about these methods can be found in the IDBInfo section of the *OLE DB Programmer's Reference.*

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Constant</p></th>
<th><p>Value</p></th>
<th><p>Description</p></th>
<th><p>Constraint Columns</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>adSchemaAsserts</strong></p></td>
<td><p>0</p></td>
<td><p>Returns the assertions defined in the catalog that are owned by a given user. (ASSERTIONS Rowset)</p></td>
<td><p>CONSTRAINT_CATALOG<br />
CONSTRAINT_SCHEMA<br />
CONSTRAINT_NAME</p></td>
</tr>
<tr class="even">
<td><p><strong>adSchemaCatalogs</strong></p></td>
<td><p>1</p></td>
<td><p>Returns the physical attributes associated with catalogs accessible from the DBMS. (CATALOGS Rowset)</p></td>
<td><p>CATALOG_NAME</p></td>
</tr>
<tr class="odd">
<td><p><strong>adSchemaCharacterSets</strong></p></td>
<td><p>2</p></td>
<td><p>Returns the character sets defined in the catalog that are accessible to a given user. (CHARACTER_SETS Rowset)</p></td>
<td><p>CHARACTER_SET_CATALOG<br />
CHARACTER_SET_SCHEMA<br />
CHARACTER_SET_NAME</p></td>
</tr>
<tr class="even">
<td><p><strong>adSchemaCheckConstraints</strong></p></td>
<td><p>5</p></td>
<td><p>Returns the check constraints defined in the catalog that are owned by a given user. (CHECK_CONSTRAINTS Rowset)</p></td>
<td><p>CONSTRAINT_CATALOG<br />
CONSTRAINT_SCHEMA<br />
CONSTRAINT_NAME</p></td>
</tr>
<tr class="odd">
<td><p><strong>adSchemaCollations</strong></p></td>
<td><p>3</p></td>
<td><p>Returns the character collations defined in the catalog that are accessible to a given user. (COLLATIONS Rowset)</p></td>
<td><p>COLLATION_CATALOG<br />
COLLATION_SCHEMA<br />
COLLATION_NAME</p></td>
</tr>
<tr class="even">
<td><p><strong>adSchemaColumnPrivileges</strong></p></td>
<td><p>13</p></td>
<td><p>Returns the privileges on columns of tables defined in the catalog that are available to, or granted by, a given user. (COLUMN_PRIVILEGES Rowset)</p></td>
<td><p>TABLE_CATALOG<br />
TABLE_SCHEMA<br />
TABLE_NAME<br />
COLUMN_NAME<br />
GRANTOR<br />
GRANTEE</p></td>
</tr>
<tr class="odd">
<td><p><strong>adSchemaColumns</strong></p></td>
<td><p>4</p></td>
<td><p>Returns the columns of tables (including views) defined in the catalog that are accessible to a given user. (COLUMNS Rowset)</p></td>
<td><p>TABLE_CATALOG<br />
TABLE_SCHEMA<br />
TABLE_NAME<br />
COLUMN_NAME</p></td>
</tr>
<tr class="even">
<td><p><strong>adSchemaColumnsDomainUsage</strong></p></td>
<td><p>11</p></td>
<td><p>Returns the columns defined in the catalog that are dependent on a domain defined in the catalog and owned by a given user. (COLUMN_DOMAIN_USAGE Rowset)</p></td>
<td><p>DOMAIN_CATALOG<br />
DOMAIN_SCHEMA<br />
DOMAIN_NAME<br />
COLUMN_NAME</p></td>
</tr>
<tr class="odd">
<td><p><strong>adSchemaConstraintColumnUsage</strong></p></td>
<td><p>6</p></td>
<td><p>Returns the columns used by referential constraints, unique constraints, check constraints, and assertions, defined in the catalog and owned by a given user. (CONSTRAINT_COLUMN_USAGE Rowset)</p></td>
<td><p>TABLE_CATALOG<br />
TABLE_SCHEMA<br />
TABLE_NAME<br />
COLUMN_NAME</p></td>
</tr>
<tr class="even">
<td><p><strong>adSchemaConstraintTableUsage</strong></p></td>
<td><p>7</p></td>
<td><p>Returns the tables that are used by referential constraints, unique constraints, check constraints, and assertions defined in the catalog and owned by a given user. (CONSTRAINT_TABLE_USAGE Rowset)</p></td>
<td><p>TABLE_CATALOG<br />
TABLE_SCHEMA<br />
TABLE_NAME</p></td>
</tr>
<tr class="odd">
<td><p><strong>adSchemaCubes</strong></p></td>
<td><p>32</p></td>
<td><p>Returns information about the available cubes in a schema (or the catalog, if the provider does not support schemas). (CUBES Rowset*)</p></td>
<td><p>CATALOG_NAME<br />
SCHEMA_NAME<br />
CUBE_NAME</p></td>
</tr>
<tr class="even">
<td><p><strong>adSchemaDBInfoKeywords</strong></p></td>
<td><p>30</p></td>
<td><p>Returns a list of provider-specific keywords. (IDBInfo::GetKeywords *)</p></td>
<td><p>&lt;None&gt;</p></td>
</tr>
<tr class="odd">
<td><p><strong>adSchemaDBInfoLiterals</strong></p></td>
<td><p>31</p></td>
<td><p>Returns a list of provider-specific literals used in text commands. (IDBInfo::GetLiteralInfo *)</p></td>
<td><p>&lt;None&gt;</p></td>
</tr>
<tr class="even">
<td><p><strong>adSchemaDimensions</strong></p></td>
<td><p>33</p></td>
<td><p>Returns information about the dimensions in a given cube. It has one row for each dimension. (DIMENSIONS Rowset *)</p></td>
<td><p>CATALOG_NAME<br />
SCHEMA_NAME<br />
CUBE_NAME<br />
DIMENSION_NAME<br />
DIMENSION_UNIQUE_NAME</p></td>
</tr>
<tr class="odd">
<td><p><strong>adSchemaForeignKeys</strong></p></td>
<td><p>27</p></td>
<td><p>Returns the foreign key columns defined in the catalog by a given user. (FOREIGN_KEYS Rowset)</p></td>
<td><p>PK_TABLE_CATALOG<br />
PK_TABLE_SCHEMA<br />
PK_TABLE_NAME<br />
FK_TABLE_CATALOG<br />
FK_TABLE_SCHEMA<br />
FK_TABLE_NAME</p></td>
</tr>
<tr class="even">
<td><p><strong>adSchemaHierarchies</strong></p></td>
<td><p>34</p></td>
<td><p>Returns information about the hierarchies available in a dimension. (HIERARCHIES Rowset *)</p></td>
<td><p>CATALOG_NAME<br />
SCHEMA_NAME<br />
CUBE_NAME<br />
DIMENSION_UNIQUE_NAME<br />
HIERARCHY_NAME<br />
HIERARCHY_UNIQUE_NAME</p></td>
</tr>
<tr class="odd">
<td><p><strong>adSchemaIndexes</strong></p></td>
<td><p>12</p></td>
<td><p>Returns the indexes defined in the catalog that are owned by a given user. (INDEXES Rowset)</p></td>
<td><p>TABLE_CATALOG<br />
TABLE_SCHEMA<br />
INDEX_NAME<br />
TYPE<br />
TABLE_NAME</p></td>
</tr>
<tr class="even">
<td><p><strong>adSchemaKeyColumnUsage</strong></p></td>
<td><p>8</p></td>
<td><p>Returns the columns defined in the catalog that are constrained as keys by a given user. (KEY_COLUMN_USAGE Rowset)</p></td>
<td><p>CONSTRAINT_CATALOG<br />
CONSTRAINT_SCHEMA<br />
CONSTRAINT_NAME<br />
TABLE_CATALOG<br />
TABLE_SCHEMA<br />
TABLE_NAME<br />
COLUMN_NAME</p></td>
</tr>
<tr class="odd">
<td><p><strong>adSchemaLevels</strong></p></td>
<td><p>35</p></td>
<td><p>Returns information about the levels available in a dimension. (LEVELS Rowset*)</p></td>
<td><p>CATALOG_NAME<br />
SCHEMA_NAME<br />
CUBE_NAME<br />
DIMENSION_UNIQUE_NAME<br />
HIERARCHY_UNIQUE_NAME<br />
LEVEL_NAME<br />
LEVEL_UNIQUE_NAME</p></td>
</tr>
<tr class="even">
<td><p><strong>adSchemaMeasures</strong></p></td>
<td><p>36</p></td>
<td><p>Returns information about the available measures. (MEASURES Rowset *)</p></td>
<td><p>CATALOG_NAME<br />
SCHEMA_NAME<br />
CUBE_NAME<br />
MEASURE_NAME<br />
MEASURE_UNIQUE_NAME</p></td>
</tr>
<tr class="odd">
<td><p><strong>adSchemaMembers</strong></p></td>
<td><p>38</p></td>
<td><p>Returns information about the available members. (MEMBERS Rowset *)</p></td>
<td><p>CATALOG_NAME<br />
SCHEMA_NAME<br />
CUBE_NAME<br />
DIMENSION_UNIQUE_NAME<br />
HIERARCHY_UNIQUE_NAME<br />
LEVEL_UNIQUE_NAME<br />
LEVEL_NUMBER<br />
MEMBER_NAME<br />
MEMBER_UNIQUE_NAME<br />
MEMBER_CAPTION<br />
MEMBER_TYPE<br />
Tree operator (For more information, see the OLE DB for OLAP documentation.)</p></td>
</tr>
<tr class="even">
<td><p><strong>adSchemaPrimaryKeys</strong></p></td>
<td><p>28</p></td>
<td><p>Returns the primary key columns defined in the catalog by a given user. (PRIMARY_KEYS Rowset)</p></td>
<td><p>PK_TABLE_CATALOG<br />
PK_TABLE_SCHEMA<br />
PK_TABLE_NAME</p></td>
</tr>
<tr class="odd">
<td><p><strong>adSchemaProcedureColumns</strong></p></td>
<td><p>29</p></td>
<td><p>Returns information about the columns of rowsets returned by procedures. (PROCEDURE_COLUMNS Rowset)</p></td>
<td><p>PROCEDURE_CATALOG<br />
PROCEDURE_SCHEMA<br />
PROCEDURE_NAME<br />
COLUMN_NAME</p></td>
</tr>
<tr class="even">
<td><p><strong>adSchemaProcedureParameters</strong></p></td>
<td><p>26</p></td>
<td><p>Returns information about the parameters and return codes of procedures. (PROCEDURE_PARAMETERS Rowset)</p></td>
<td><p>PROCEDURE_CATALOG<br />
PROCEDURE_SCHEMA<br />
PROCEDURE_NAME<br />
PARAMETER_NAME</p></td>
</tr>
<tr class="odd">
<td><p><strong>adSchemaProcedures</strong></p></td>
<td><p>16</p></td>
<td><p>Returns the procedures defined in the catalog that are owned by a given user. (PROCEDURES Rowset)</p></td>
<td><p>PROCEDURE_CATALOG<br />
PROCEDURE_SCHEMA<br />
PROCEDURE_NAME<br />
PROCEDURE_TYPE</p></td>
</tr>
<tr class="even">
<td><p><strong>adSchemaProperties</strong></p></td>
<td><p>37</p></td>
<td><p>Returns information about the available properties for each level of the dimension. (PROPERTIES Rowset *)</p></td>
<td><p>CATALOG_NAME<br />
SCHEMA_NAME<br />
CUBE_NAME<br />
DIMENSION_UNIQUE_NAME<br />
HIERARCHY_UNIQUE_NAME<br />
LEVEL_UNIQUE_NAME<br />
MEMBER_UNIQUE_NAME<br />
PROPERTY_TYPE<br />
PROPERTY_NAME</p></td>
</tr>
<tr class="odd">
<td><p><strong>adSchemaProviderSpecific</strong></p></td>
<td><p>-1</p></td>
<td><p>Used if the provider defines its own nonstandard schema queries.</p></td>
<td><p>&lt;Provider specific&gt;</p></td>
</tr>
<tr class="even">
<td><p><strong>adSchemaProviderTypes</strong></p></td>
<td><p>22</p></td>
<td><p>Returns the (base) data types supported by the data provider. (PROVIDER_TYPES Rowset)</p></td>
<td><p>DATA_TYPE<br />
BEST_MATCH</p></td>
</tr>
<tr class="odd">
<td><p><strong>AdSchemaReferentialConstraints</strong></p></td>
<td><p>9</p></td>
<td><p>Returns the referential constraints defined in the catalog that are owned by a given user. (REFERENTIAL_CONSTRAINTS Rowset)</p></td>
<td><p>CONSTRAINT_CATALOG<br />
CONSTRAINT_SCHEMA<br />
CONSTRAINT_NAME</p></td>
</tr>
<tr class="even">
<td><p><strong>adSchemaSchemata</strong></p></td>
<td><p>17</p></td>
<td><p>Returns the schemas (database objects) that are owned by a given user. (SCHEMATA Rowset)</p></td>
<td><p>CATALOG_NAME<br />
SCHEMA_NAME<br />
SCHEMA_OWNER</p></td>
</tr>
<tr class="odd">
<td><p><strong>adSchemaSQLLanguages</strong></p></td>
<td><p>18</p></td>
<td><p>Returns the conformance levels, options, and dialects supported by the SQL-implementation processing data defined in the catalog. (SQL_LANGUAGES Rowset)</p></td>
<td><p>&lt;None&gt;</p></td>
</tr>
<tr class="even">
<td><p><strong>adSchemaStatistics</strong></p></td>
<td><p>19</p></td>
<td><p>Returns the statistics defined in the catalog that are owned by a given user. (STATISTICS Rowset)</p></td>
<td><p>TABLE_CATALOG<br />
TABLE_SCHEMA<br />
TABLE_NAME</p></td>
</tr>
<tr class="odd">
<td><p><strong>adSchemaTableConstraints</strong></p></td>
<td><p>10</p></td>
<td><p>Returns the table constraints defined in the catalog that are owned by a given user. (TABLE_CONSTRAINTS Rowset)</p></td>
<td><p>CONSTRAINT_CATALOG<br />
CONSTRAINT_SCHEMA<br />
CONSTRAINT_NAME<br />
TABLE_CATALOG<br />
TABLE_SCHEMA<br />
TABLE_NAME<br />
CONSTRAINT_TYPE</p></td>
</tr>
<tr class="even">
<td><p><strong>adSchemaTablePrivileges</strong></p></td>
<td><p>14</p></td>
<td><p>Returns the privileges on tables defined in the catalog that are available to, or granted by, a given user. (TABLE_PRIVILEGES Rowset)</p></td>
<td><p>TABLE_CATALOG<br />
TABLE_SCHEMA<br />
TABLE_NAME<br />
GRANTOR<br />
GRANTEE</p></td>
</tr>
<tr class="odd">
<td><p><strong>adSchemaTables</strong></p></td>
<td><p>20</p></td>
<td><p>Returns the tables (including views) defined in the catalog that are accessible to a given user. (TABLES Rowset)</p></td>
<td><p>TABLE_CATALOG<br />
TABLE_SCHEMA<br />
TABLE_NAME<br />
TABLE_TYPE</p></td>
</tr>
<tr class="even">
<td><p><strong>adSchemaTranslations</strong></p></td>
<td><p>21</p></td>
<td><p>Returns the character translations defined in the catalog that are accessible to a given user. (TRANSLATIONS Rowset)</p></td>
<td><p>TRANSLATION_CATALOG<br />
TRANSLATION_SCHEMA<br />
TRANSLATION_NAME</p></td>
</tr>
<tr class="odd">
<td><p><strong>adSchemaTrustees</strong></p></td>
<td><p>39</p></td>
<td><p>Reserved for future use.</p></td>
<td><p><br />
</p></td>
</tr>
<tr class="even">
<td><p><strong>adSchemaUsagePrivileges</strong></p></td>
<td><p>15</p></td>
<td><p>Returns the USAGE privileges on objects defined in the catalog that are available to, or granted by, a given user. (USAGE_PRIVILEGES Rowset)</p></td>
<td><p>OBJECT_CATALOG<br />
OBJECT_SCHEMA<br />
OBJECT_NAME<br />
OBJECT_TYPE<br />
GRANTOR<br />
GRANTEE</p></td>
</tr>
<tr class="odd">
<td><p><strong>adSchemaViewColumnUsage</strong></p></td>
<td><p>24</p></td>
<td><p>Returns the columns on which viewed tables, defined in the catalog and owned by a given user, are dependent. (VIEW_COLUMN_USAGE Rowset)</p></td>
<td><p>VIEW_CATALOG<br />
VIEW_SCHEMA<br />
VIEW_NAME</p></td>
</tr>
<tr class="even">
<td><p><strong>adSchemaViews</strong></p></td>
<td><p>23</p></td>
<td><p>Returns the views defined in the catalog that are accessible to a given user. (VIEWS Rowset)</p></td>
<td><p>TABLE_CATALOG<br />
TABLE_SCHEMA<br />
TABLE_NAME</p></td>
</tr>
<tr class="odd">
<td><p><strong>adSchemaViewTableUsage</strong></p></td>
<td><p>25</p></td>
<td><p>Returns the tables on which viewed tables, defined in the catalog and owned by a given user, are dependent. (VIEW_TABLE_USAGE Rowset)</p></td>
<td><p>VIEW_CATALOG<br />
VIEW_SCHEMA<br />
VIEW_NAME</p></td>
</tr>
</tbody>
</table>


### ADO/WFC equivalent

Package: **com.ms.wfc.data**

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Constant</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AdoEnums.Schema.ASSERTS</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.Schema.CATALOGS</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.Schema.CHARACTERSETS</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.Schema.CHECKCONSTRAINTS</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.Schema.COLLATIONS</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.Schema.COLUMNPRIVILEGES</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.Schema.COLUMNS</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.Schema.COLUMNSDOMAINUSAGE</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.Schema.CONSTRAINTCOLUMNUSAGE</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.Schema.CONSTRAINTTABLEUSAGE</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.Schema.CUBES</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.Schema.DBINFOKEYWORDS</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.Schema.DBINFOLITERALS</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.Schema.DIMENSIONS</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.Schema.FOREIGNKEYS</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.Schema.HIERARCHIES</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.Schema.INDEXES</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.Schema.KEYCOLUMNUSAGE</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.Schema.LEVELS</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.Schema.MEASURES</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.Schema.MEMBERS</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.Schema.PRIMARYKEYS</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.Schema.PROCEDURECOLUMNS</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.Schema.PROCEDUREPARAMETERS</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.Schema.PROCEDURES</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.Schema.PROPERTIES</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.Schema.PROVIDERSPECIFIC</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.Schema.PROVIDERTYPES</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.Schema.REFERENTIALCONTRAINTS</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.Schema.SCHEMATA</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.Schema.SQLLANGUAGES</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.Schema.STATISTICS</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.Schema.TABLECONSTRAINTS</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.Schema.TABLEPRIVILEGES</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.Schema.TABLES</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.Schema.TRANSLATIONS</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.Schema.TRUSTEES</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.Schema.USAGEPRIVILEGES</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.Schema.VIEWCOLUMNUSAGE</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.Schema.VIEWS</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.Schema.VIEWTABLEUSAGE</p></td>
</tr>
</tbody>
</table>

