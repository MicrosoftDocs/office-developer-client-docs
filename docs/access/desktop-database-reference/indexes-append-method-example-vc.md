---
title: Indexes Append method example (VC++)
TOCTitle: Indexes Append method example (VC++)
ms:assetid: fd7a020e-19bd-db14-bcdf-d34b23002e44
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250302(v=office.15)
ms:contentKeyID: 48548918
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Indexes Append method example (VC++)


**Applies to**: Access 2013, Office 2013

The following code demonstrates how to create a new index. The index is on two columns in the table.

```cpp 
 
// BeginCreateIndexCpp 
#import "c:\Program Files\Common Files\system\ado\msadox.dll" no_namespace 
 
#include "iostream.h" 
#include "stdio.h" 
#include "conio.h" 
 
// Function declarations 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void CreateIndexX(void); 
 
////////////////////////////////////////////////////////// 
// // 
// Main Function // 
// // 
////////////////////////////////////////////////////////// 
void main() 
{ 
 if(FAILED(::CoInitialize(NULL))) 
 return; 
 
 CreateIndexX(); 
 
 ::CoUninitialize(); 
} 
 
////////////////////////////////////////////////////////// 
// // 
// CreateIndexX Function // 
// // 
////////////////////////////////////////////////////////// 
void CreateIndexX(void) 
{ 
 HRESULT hr = S_OK; 
 
 // Define ADOX object pointers. 
 // Initialize pointers on define. 
 // These are in the ADOX:: namespace. 
 _TablePtr m_pTable = NULL; 
 _IndexPtr m_pIndex = NULL; 
 _CatalogPtr m_pCatalog = NULL; 
 
 //Define other variables 
 _bstr_t strcnn("Provider='Microsoft.JET.OLEDB.4.0';" 
 "Data source = 'c:\\Program Files\\Microsoft Office\\" 
 "Office\\Samples\\Northwind.mdb';"); 
 try 
 { 
 TESTHR(hr = m_pTable.CreateInstance(__uuidof(Table))); 
 TESTHR(hr = m_pIndex.CreateInstance(__uuidof(Index))); 
 TESTHR(hr = m_pCatalog.CreateInstance(__uuidof (Catalog))); 
 
 // Open the catalog. 
 m_pCatalog->PutActiveConnection(strcnn); 
 
 // Define the table and append it to the catalog. 
 m_pTable->Name = "MyTable"; 
 m_pTable->Columns->Append("Column1",adInteger,0); 
 m_pTable->Columns->Append("Column2",adInteger,0); 
 m_pTable->Columns->Append("Column3",adVarWChar,50); 
 m_pCatalog->Tables->Append(_variant_t((IDispatch *)m_pTable)); 
 printf("Table 'MyTable' is appended.\n"); 
 
 // Define a multi-column index. 
 m_pIndex->Name = "multicolidx"; 
 m_pIndex->Columns->Append("Column1",adInteger,0); 
 m_pIndex->Columns->Append("Column2",adInteger,0); 
 
 // Append the index to the table. 
 m_pTable->Indexes->Append(_variant_t((IDispatch *)m_pIndex)); 
 printf("Index 'multicolidx' is appended.\n"); 
 
 // Delete the table. 
 m_pCatalog->Tables->Delete("MyTable"); 
 printf("Table 'MyTable' is deleted.\n"); 
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
 cout << "Error occured in CreateIndexX...."<< endl; 
 } 
} 
// EndCreateIndexCpp 
```

