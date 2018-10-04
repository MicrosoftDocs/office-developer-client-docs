﻿---
title: Cancel Method Example (VC++)
TOCTitle: Cancel Method Example (VC++)
ms:assetid: bb5edaeb-0361-3b83-7483-bb43c5cb083f
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249900(v=office.15)
ms:contentKeyID: 48547393
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Cancel Method Example (VC++)


**Applies to**: Access 2013 | Office 2013

This example uses the [Cancel](cancel-method-ado.md) method to cancel a command executing on a [Connection](connection-object-ado.md) object if the connection is busy.

``` 
 
// BeginCancelCpp 
#import "C:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
#include <ole2.h> 
#include <stdio.h> 
#include<conio.h> 
 
// Function declarations 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void CancelX(); 
void PrintProviderError(_ConnectionPtr pConnection); 
void PrintComError(_com_error &e); 
 
/////////////////////////////////////////////////////////// 
// // 
// Main Function // 
// // 
/////////////////////////////////////////////////////////// 
 
void main() 
{ 
 if(FAILED(::CoInitialize(NULL))) 
 return; 
 
 CancelX(); 
 
 //Wait here for user to see the output.. 
 printf("\nPress any key to continue..."); 
 getch(); 
 
 ::CoUninitialize(); 
} 
 
/////////////////////////////////////////////////////////// 
// // 
// CancelX Function // 
// // 
/////////////////////////////////////////////////////////// 
 
void CancelX() 
{ 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace 
 _ConnectionPtr pConnection = NULL; 
 
 //Define Other Variables 
 HRESULT hr = S_OK; 
 _bstr_t strCmdChange; 
 _bstr_t strCmdRestore; 
 BOOL booChanged = FALSE; 
 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 
 try 
 { 
 // open a connection. 
 TESTHR(pConnection.CreateInstance(__uuidof(Connection))); 
 pConnection->Open(strCnn,"","",adConnectUnspecified); 
 
 // Define command strings. 
 strCmdChange = "UPDATE titles SET type = 'self_help' " 
 "WHERE type = 'psychology'"; 
 
 strCmdRestore = "UPDATE titles SET type = 'psychology' " 
 "WHERE type = 'self_help'"; 
 
 // Begin a transaction, then execute a command asynchronously. 
 pConnection->BeginTrans(); 
 pConnection->Execute(strCmdChange,NULL,adAsyncExecute); 
 
 // do something else for a little while - this could be changed 
 for (int i = 1; i<=100000 ;i++) 
 { 
 // i = i + i; 
 printf("%d\n", i); 
 } 
 
 // If the command has NOT completed, cancel the execute 
 // and roll back the transaction. Otherwise, commit the 
 // transaction. 
 if ((pConnection->GetState())) 
 { 
 pConnection->Cancel(); 
 pConnection->RollbackTrans(); 
 booChanged = FALSE; 
 printf("Update canceled.\n"); 
 printf("GetState = %d\n", pConnection->GetState()); 
 } 
 else 
 { 
 pConnection->CommitTrans(); 
 booChanged = TRUE; 
 printf("Update complete.\n"); 
 
 } 
 
 // If the change was made, restore the data 
 // because this is a demonstration. 
 if (booChanged) 
 { 
 pConnection->Execute(strCmdRestore,NULL,0); 
 printf("Data restored.\n"); 
 } 
 } 
 catch(_com_error &e) 
 { 
 // Notify user of any errors that result from 
 // executing the query. 
 // Pass a connection pointer accessed from the Connection. 
 PrintProviderError(pConnection); 
 PrintComError(e); 
 } 
 
 // Cleanup object before exit 
 if (pConnection) 
 if (pConnection->State == adStateOpen) 
 pConnection->Close(); 
} 
 
/////////////////////////////////////////////////////////// 
// // 
// PrintProviderError Function // 
// // 
/////////////////////////////////////////////////////////// 
 
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
 printf("Error number: %x\t%s", pErr->Number, 
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
// EndCancelCpp 
```

