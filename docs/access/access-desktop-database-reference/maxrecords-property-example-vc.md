﻿---
title: MaxRecords Property Example (VC++)
TOCTitle: MaxRecords Property Example (VC++)
ms:assetid: 007936cf-a91c-c447-69f2-8286f3f868e6
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248778(v=office.15)
ms:contentKeyID: 48542910
ms.date: 09/18/2015
mtps_version: v=office.15
---

# MaxRecords Property Example (VC++)


**Applies to**: Access 2013 | Office 2013

This example uses the [MaxRecords](maxrecords-property-ado.md) property to open a [Recordset](recordset-object-ado.md) containing the 10 most expensive titles in the ***Titles*** table.

``` 
 
// BeginMaxRecordsCpp 
#import "C:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF","EndOfFile") 
 
#include <ole2.h> 
#include <stdio.h> 
#include <conio.h> 
#include "MaxRecordsX.h" 
 
// Function Declarations 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void MaxRecordsX(void); 
void PrintProviderError(_ConnectionPtr pConnection); 
void PrintComError(_com_error &e); 
 
////////////////////////////////////////////////////////////// 
// // 
// Main Function // 
// // 
////////////////////////////////////////////////////////////// 
 
void main() 
{ 
 if(FAILED(::CoInitialize(NULL))) 
 return; 
 
 MaxRecordsX(); 
 
 printf("Press any key to continue..."); 
 getch(); 
 ::CoUninitialize(); 
} 
 
// MaxRecordsX() Function 
void MaxRecordsX(void) 
{ 
 // Define ADO ObjectPointers 
 // Initialize Pointers on define 
 // These are in the ADODB :: namespace 
 _RecordsetPtr pRstTemp = NULL; 
 
 // Define Other Variables 
 IADORecordBinding *picRs = NULL; // Interface Pointer Declared 
 CTitleRs titlers; // C++ Class Object 
 HRESULT hr = S_OK; 
 
 try 
 { 
 //Assign Connection String to Variable 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 
 // Open Recordset containing the 10 most expensive titles in the 
 // Titles table. 
 TESTHR(pRstTemp.CreateInstance(__uuidof(Recordset))); 
 
 pRstTemp->MaxRecords=10; 
 
 pRstTemp->Open("SELECT title,price FROM Titles " 
 "ORDER BY Price DESC",strCnn,adOpenForwardOnly, 
 adLockReadOnly,adCmdText); 
 
 // Open an IADORecordBinding interface pointer which 
 // we will use for binding Recordset to a class 
 TESTHR(pRstTemp->QueryInterface( 
 __uuidof(IADORecordBinding),(LPVOID*)&picRs)); 
 
 // Bind the Recordset to a C++ class here 
 TESTHR(picRs->BindToRecordset(&titlers)); 
 
 // Display the contents of the Recordset 
 printf("Top Ten Titles by Price:\n\n"); 
 
 while(!(pRstTemp->EndOfFile)) 
 { 
 printf("%s --- %6.2lf\n\n",titlers.lau_TitleStatus == 
 adFldOK ? titlers.m_szau_Title : "<NULL>", 
 titlers.lau_PriceStatus == adFldOK ? 
 titlers.m_szau_Price : 0.00); 
 pRstTemp->MoveNext(); 
 } 
 } 
 catch(_com_error &e) 
 { 
 // Notify the user of errors if any. 
 // Pass a connection pointer accessed from the Recordset. 
 _variant_t vtConnect = pRstTemp->GetActiveConnection(); 
 
 // GetActiveConnection returns connect string if connection 
 // is not open, else returns Connection object. 
 switch(vtConnect.vt) 
 { 
 case VT_BSTR: 
 PrintComError(e); 
 break; 
 case VT_DISPATCH: 
 PrintProviderError(vtConnect); 
 break; 
 default: 
 printf("Errors occured."); 
 break; 
 } 
 } 
 
 // Clean up objects before exit. 
 //Release the IADORecordset Interface here 
 if (picRs) 
 picRs->Release(); 
 
 if (pRstTemp) 
 if (pRstTemp->State == adStateOpen) 
 pRstTemp->Close(); 
}; 
 
////////////////////////////////////////////////////////////// 
// // 
// PrintProviderError Function // 
// // 
////////////////////////////////////////////////////////////// 
 
void PrintProviderError(_ConnectionPtr pConnection) 
{ 
 //Print Provider Errors from Connection object 
 //pErr is a record object in the Connection's Error collection 
 ErrorPtr pErr = NULL; 
 
 if((pConnection->Errors->Count)>0) 
 { 
 long nCount = pConnection->Errors->Count; 
 
 //Collection ranges from 0 to nCount-1 
 for(long i = 0;i < nCount;i++) 
 { 
 pErr = pConnection->Errors->GetItem(i); 
 printf("\t Error Number :%x \t %s",pErr->Number, 
 pErr->Description); 
 } 
 } 
} 
 
/////////////////////////////////////////////////////////// 
// // 
// PrintComError Function // 
// // 
/////////////////////////////////////////////////////////// 
 
void PrintComError(_com_error &e) 
{ 
 _bstr_t bstrSource(e.Source()); 
 _bstr_t bstrDescription(e.Description()); 
 
 // Print Com errors. 
 printf("Error\n"); 
 printf("\tCode = %08lx\n", e.Error()); 
 printf("\tCode meaning = %s\n", e.ErrorMessage()); 
 printf("\tSource = %s\n", (LPCSTR) bstrSource); 
 printf("\tDescription = %s\n", (LPCSTR) bstrDescription); 
} 
// EndMaxRecordsCpp 
```

