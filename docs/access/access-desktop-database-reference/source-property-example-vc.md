﻿---
title: Source Property Example (VC++)
TOCTitle: Source Property Example (VC++)
ms:assetid: 2c539e8b-04a8-2fc3-052e-a0776682e16c
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249067(v=office.15)
ms:contentKeyID: 48543949
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Source Property Example (VC++)


**Applies to**: Access 2013 | Office 2013

This example demonstrates the [Source](source-property-ado-recordset.md) property by opening three [Recordset](recordset-object-ado.md) objects based on different data sources.

``` 
 
// BeginSourceCpp 
#import "c:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
#include <ole2.h> 
#include <stdio.h> 
#include <conio.h> 
 
// Function declarations 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void SourceX(void); 
void PrintProviderError(_ConnectionPtr pConnection); 
void PrintComError(_com_error &e); 
 
/////////////////////////// 
// // 
// Main Function // 
// // 
/////////////////////////// 
void main() 
{ 
 if(FAILED(::CoInitialize(NULL))) 
 return; 
 
 SourceX(); 
 
 ::CoUninitialize(); 
} 
 
/////////////////////////////////////////////// 
// // 
// SourceX Function // 
// // 
/////////////////////////////////////////////// 
void SourceX(void) 
{ 
 HRESULT hr = S_OK; 
 
 // Define string variables. 
 _bstr_t strCmdSQL("Select title,type,pubdate " 
 "FROM titles ORDER BY title"); 
 _bstr_t strSQL("SELECT title_ID AS TitleID, title AS Title, " 
 "publishers.pub_id AS PubID, pub_name AS PubName " 
 "FROM publishers INNER JOIN titles " 
 "ON publishers.pub_id = titles.pub_id " 
 "ORDER BY Title"); 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace. 
 _ConnectionPtr pConnection = NULL; 
 _RecordsetPtr pRstTitles = NULL; 
 _RecordsetPtr pRstPublishers = NULL; 
 _RecordsetPtr pRstPublishersDirect = NULL; 
 _RecordsetPtr pRstTitlesPublishers = NULL; 
 _CommandPtr pCmdSQL = NULL; 
 
 try 
 { 
 // Open a connection. 
 TESTHR(pConnection.CreateInstance(__uuidof(Connection))); 
 pConnection->Open (strCnn, "", "", adConnectUnspecified); 
 
 // Open a recordset based on a command object. 
 TESTHR(pCmdSQL.CreateInstance(__uuidof(Command))); 
 pCmdSQL->ActiveConnection = pConnection; 
 pCmdSQL->CommandText = strCmdSQL; 
 pRstTitles = pCmdSQL->Execute(NULL,NULL,adCmdText); 
 
 // Open a recordset based on a a table 
 TESTHR(pRstPublishers.CreateInstance(__uuidof(Recordset))); 
 pRstPublishers->Open ("publishers", 
 _variant_t((IDispatch *) pConnection, true), 
 adOpenForwardOnly, adLockReadOnly, adCmdTable); 
 
 // Open a recordset based on a table 
 TESTHR(pRstPublishersDirect.CreateInstance( 
 __uuidof(Recordset))); 
 pRstPublishersDirect->Open ("publishers", 
 _variant_t((IDispatch *) pConnection, true), 
 adOpenForwardOnly, adLockReadOnly, adCmdTableDirect); 
 
 // Open a recordset based on a SQL string. 
 TESTHR(pRstTitlesPublishers.CreateInstance( 
 __uuidof(Recordset))); 
 pRstTitlesPublishers->Open(strSQL, 
 _variant_t((IDispatch *) pConnection, true), 
 adOpenForwardOnly, adLockReadOnly, adCmdText); 
 
 // Use the Source property to display the source of 
 // each recordset. 
 printf("rstTitles source: \n%s\n\n", 
 (LPCSTR)(_bstr_t) pRstTitles->GetSource().bstrVal); 
 printf("rstPublishers source: \n%s\n\n", 
 (LPCSTR)(_bstr_t) pRstPublishers->GetSource().bstrVal); 
 printf("rstPublishersDirect source: \n%s\n\n", 
 (LPCSTR)(_bstr_t) pRstPublishersDirect->GetSource().bstrVal); 
 printf("rstTitlesPublishers source: \n%s\n\n", 
 (LPCSTR)(_bstr_t) pRstTitlesPublishers->GetSource().bstrVal); 
 } 
 catch (_com_error &e) 
 { 
 // Notify the user of errors if any. 
 PrintProviderError(pConnection); 
 PrintComError(e); 
 } 
 
 if (pRstTitles) 
 if (pRstTitles->State == adStateOpen) 
 pRstTitles->Close(); 
 if (pRstPublishers) 
 if (pRstPublishers->State == adStateOpen) 
 pRstPublishers->Close(); 
 if (pRstPublishersDirect) 
 if (pRstPublishersDirect->State == adStateOpen) 
 pRstPublishersDirect->Close(); 
 if (pRstTitlesPublishers) 
 if (pRstTitlesPublishers->State == adStateOpen) 
 pRstTitlesPublishers->Close(); 
 if (pConnection) 
 if (pConnection->State == adStateOpen) 
 pConnection->Close(); 
} 
 
/////////////////////////////////////////////// 
// // 
// PrintProviderError Function // 
// // 
/////////////////////////////////////////////// 
void PrintProviderError(_ConnectionPtr pConnection) 
{ 
 // Print Provider Errors from Connection object. 
 // pErr is a record object in the Connection's Error collection. 
 ErrorPtr pErr = NULL; 
 
 if( (pConnection->Errors->Count) > 0) 
 { 
 long nCount = pConnection->Errors->Count; 
 // Collection ranges from 0 to nCount -1. 
 for(long i = 0; i < nCount; i++) 
 { 
 pErr = pConnection->Errors->GetItem(i); 
 printf("Error number: %x\t%s\n", pErr->Number, 
 (LPCSTR) pErr->Description); 
 } 
 } 
} 
 
/////////////////////////////////////////////// 
// // 
// PrintComError Function // 
// // 
/////////////////////////////////////////////// 
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
// EndSourceCpp 
```

