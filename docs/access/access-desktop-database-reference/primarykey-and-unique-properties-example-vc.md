﻿---
title: PrimaryKey and Unique Properties Example (VC++)
TOCTitle: PrimaryKey and Unique Properties Example (VC++)
ms:assetid: 0aa3faf6-5165-911a-8167-4a7bdd1c7ceb
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248838(v=office.15)
ms:contentKeyID: 48543158
ms.date: 09/18/2015
mtps_version: v=office.15
---

# PrimaryKey and Unique Properties Example (VC++)


**Applies to**: Access 2013 | Office 2013

This example demonstrates the [PrimaryKey](primarykey-property-adox.md) and [Unique](unique-property-adox.md) properties of an [Index](index-object-adox.md). The code creates a new table with two columns. The **PrimaryKey** and **Unique** properties are used to make one column the primary key for which duplicate values are not allowed.

``` 
 
// BeginPrimaryKeyCpp 
#import "c:\program files\common files\system\ado\msadox.dll" no_namespace 
#import "c:\program files\common files\system\ado\msado15.dll" 
 
#include "iostream.h" 
#include "stdio.h" 
#include "conio.h" 
 
//Function Declarations 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void PrimaryKeyX(void); 
 
////////////////////////////////////////////////////////// 
// // 
// Main Function // 
// // 
////////////////////////////////////////////////////////// 
void main() 
{ 
 if(FAILED(::CoInitialize(NULL))) 
 return; 
 
 PrimaryKeyX(); 
 
 ::CoUninitialize(); 
} 
 
////////////////////////////////////////////////////////// 
// // 
// PrimaryKeyX Function // 
// // 
////////////////////////////////////////////////////////// 
void PrimaryKeyX() 
{ 
 HRESULT hr = S_OK; 
 
 // Define ADOX object pointers. 
 // Initialize pointers on define. 
 // These are in the ADOX:: namespace. 
 _CatalogPtr m_pCatalog = NULL; 
 _TablePtr m_pTableNew = NULL; 
 _IndexPtr m_pIndexNew = NULL; 
 _IndexPtr m_pIndex = NULL; 
 _ColumnPtr m_pColumn = NULL; 
 
 //Define string variable 
 _bstr_t strcnn("Provider='Microsoft.JET.OLEDB.4.0';" 
 "Data Source = 'c:\\Program Files\\" 
 "Microsoft Office\\Office\\Samples\\Northwind.mdb';"); 
 
 try 
 { 
 TESTHR(hr = m_pCatalog.CreateInstance(__uuidof(Catalog))); 
 TESTHR(hr = m_pTableNew.CreateInstance(__uuidof(Table))); 
 TESTHR(hr = m_pIndexNew.CreateInstance(__uuidof(Index))); 
 TESTHR(hr = m_pIndex.CreateInstance(__uuidof(Index))); 
 TESTHR(hr = m_pColumn.CreateInstance(__uuidof(Column))); 
 
 // Connect the catalog 
 m_pCatalog->PutActiveConnection(strcnn); 
 
 // Name new table 
 m_pTableNew->Name = "NewTable"; 
 
 // Append a numeric and a text field to new table. 
 m_pTableNew->Columns->Append("NumField", adInteger, 20); 
 m_pTableNew->Columns->Append("TextField", adVarWChar, 20); 
 
 // Append new Primary Key index on NumField column 
 // to new table 
 m_pIndexNew->Name = "NumIndex"; 
 m_pIndexNew->Columns->Append("NumField",adInteger,0); 
 // here "-1" is required instead of "true". 
 m_pIndexNew->PutPrimaryKey(-1); 
 m_pIndexNew->PutUnique(-1); 
 m_pTableNew->Indexes->Append( 
 _variant_t ((IDispatch*)m_pIndexNew)); 
 
 // Append an index on Textfield to new table. 
 // Note the different technique: Specifying index and 
 // column name as parameters of the Append method 
 m_pTableNew->Indexes->Append("TextIndex", "TextField"); 
 
 // Append the new table 
 m_pCatalog->Tables->Append(_variant_t ((IDispatch*)m_pTableNew)); 
 
 cout << m_pTableNew->Indexes->Count << " Indexes in " 
 << m_pTableNew->Name << " Table" << endl; 
 m_pCatalog->Tables->Refresh(); 
 
 _variant_t vIndex; 
 // Enumerate Indexes collection. 
 for (long lIndex = 0;lIndex < m_pTableNew->Indexes->Count; 
 lIndex++) 
 { 
 vIndex = lIndex; 
 m_pIndex = m_pTableNew->Indexes->GetItem(vIndex); 
 cout << "Index " << m_pIndex->Name << endl; 
 cout << " Primary key = " << (m_pIndex->GetPrimaryKey() ? 
 "True" : "False") << endl; 
 cout << " Unique = " << (m_pIndex->GetUnique() ? "True" : 
 "False") << endl; 
 
 // Enumerate Columns collection of each Index 
 // object. 
 cout << " Columns" << endl; 
 
 for (long lIndex = 0;lIndex < m_pIndex->Columns->Count; 
 lIndex++) 
 { 
 vIndex = lIndex ; 
 m_pColumn = m_pIndex->Columns->GetItem(vIndex); 
 cout << " " << m_pColumn->Name << endl; 
 } 
 } 
 
 // Delete new table as this is a demonstration 
 m_pCatalog->Tables->Delete(m_pTableNew->Name); 
 } 
 catch(_com_error &e) 
 { 
 // Notify the user of errors if any. 
 _bstr_t bstrSource(e.Source()); 
 _bstr_t bstrDescription(e.Description()); 
 
 printf("\n\tSource : %s \n\tdescription : %s \n ", 
 (LPCSTR)bstrSource,(LPCSTR)bstrDescription); 
 } 
 catch(...) 
 { 
 cout << "Error occured in PrimaryKeyX...."<< endl; 
 } 
 
 m_pCatalog = NULL; 
} 
// EndPrimaryKeyCpp 
```

