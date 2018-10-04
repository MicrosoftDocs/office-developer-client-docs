﻿---
title: OpenSchema Method Example (VC++)
TOCTitle: OpenSchema Method Example (VC++)
ms:assetid: 8654d003-2c6d-f8dc-5680-5e195ca5f9bd
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249584(v=office.15)
ms:contentKeyID: 48546083
ms.date: 09/18/2015
mtps_version: v=office.15
---

# OpenSchema Method Example (VC++)


**Applies to**: Access 2013 | Office 2013

This example uses the [OpenSchema](openschema-method-ado.md) method to display the name and type of each table in the ***Pubs*** database.

``` 
 
// BeginOpenSchemaCpp 
#import "c:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
#include <ole2.h> 
#include <stdio.h> 
#include <oleauto.h> 
#include <conio.h> 
 
// Function declarations 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void OpenSchemaX(void); 
void OpenSchemaX2(void); 
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
 
 OpenSchemaX(); 
 
 printf("Press any key to see the results of 2nd " 
 "function...\n\n"); 
 getch(); 
 
 OpenSchemaX2(); 
 
 ::CoUninitialize(); 
} 
 
/////////////////////////////////////////////////////////// 
// // 
// OpenSchemaX Function // 
// // 
/////////////////////////////////////////////////////////// 
 
void OpenSchemaX() 
{ 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace. 
 _ConnectionPtr pConnection = NULL; 
 _RecordsetPtr pRstSchema = NULL; 
 
 //Other Variables 
 HRESULT hr = S_OK; 
 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 
 try 
 { 
 // Open connection. 
 TESTHR(pConnection.CreateInstance(__uuidof(Connection))); 
 pConnection->Open (strCnn, "", "", adConnectUnspecified); 
 
 pRstSchema = pConnection->OpenSchema(adSchemaTables); 
 
 while(!(pRstSchema->EndOfFile)) 
 { 
 _bstr_t table_name = pRstSchema->Fields-> 
 GetItem("TABLE_NAME")->Value; 
 
 printf("Table Name: %s\n",(LPCSTR) table_name); 
 
 _bstr_t table_type = pRstSchema->Fields-> 
 GetItem("TABLE_TYPE")->Value; 
 
 printf("Table type: %s\n\n",(LPCSTR) table_type); 
 
 pRstSchema->MoveNext(); 
 
 int intLine = intLine + 1; 
 if (intLine % 5 == 0) 
 { 
 printf("\nPress any key to continue..."); 
 getch(); 
 //Clear the screen for the next display 
 system("cls"); 
 } 
 } 
 } 
 catch (_com_error &e) 
 { 
 // Notify the user of errors if any. 
 // Pass a connection pointer accessed from the Connection. 
 PrintProviderError(pConnection); 
 PrintComError(e); 
 } 
 
 // Clean up objects before exit. 
 if (pRstSchema) 
 if (pRstSchema->State == adStateOpen) 
 pRstSchema->Close(); 
 if (pConnection) 
 if (pConnection->State == adStateOpen) 
 pConnection->Close(); 
} 
 
/////////////////////////////////////////////////////////// 
// // 
// OpenSchemaX2 Function // 
// // 
/////////////////////////////////////////////////////////// 
void OpenSchemaX2() 
{ 
 HRESULT hr = S_OK; 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace. 
 _ConnectionPtr pConnection2 = NULL; 
 _RecordsetPtr pRstSchema = NULL; 
 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 
 try 
 { 
 // Open connection. 
 TESTHR(pConnection2.CreateInstance(__uuidof(Connection))); 
 pConnection2->Open (strCnn, "", "", adConnectUnspecified); 
 
 // Create a safearray which takes four elements,and pass it as 
 // 2nd parameter in OpenSchema method. 
 SAFEARRAY FAR* psa = NULL; 
 SAFEARRAYBOUND rgsabound; 
 _variant_t var; 
 _variant_t Array; 
 rgsabound.lLbound = 0; 
 rgsabound.cElements = 4; 
 psa = SafeArrayCreate(VT_VARIANT, 1, &rgsabound); 
 var.vt = VT_EMPTY; 
 
 long ix; 
 ix = 0; 
 SafeArrayPutElement(psa, &ix, &var); 
 
 ix= 1; 
 SafeArrayPutElement(psa, &ix, &var); 
 
 ix = 2; 
 SafeArrayPutElement(psa, &ix, &var); 
 
 var.vt = VT_BSTR; 
 char * s1 = "VIEW"; 
 _bstr_t str = s1; 
 var.bstrVal = str; 
 
 ix = 3; 
 SafeArrayPutElement(psa, &ix, &var); 
 
 Array.vt = VT_ARRAY|VT_VARIANT; 
 Array.parray = psa; 
 
 pRstSchema = pConnection2->OpenSchema(adSchemaTables,&Array); 
 
 while(!(pRstSchema->EndOfFile)) 
 { 
 printf("Table Name: %s\n", (LPCSTR) (_bstr_t) pRstSchema-> 
 Fields->GetItem("TABLE_NAME")->Value); 
 
 printf("Table type: %s\n\n",(LPCSTR) (_bstr_t) pRstSchema-> 
 Fields->GetItem("TABLE_TYPE")->Value); 
 
 pRstSchema->MoveNext(); 
 
 int intLine = intLine + 1; 
 if (intLine % 5 == 0) 
 { 
 printf("\nPress any key to continue..."); 
 getch(); 
 //Clear the screen for the next display 
 system("cls"); 
 } 
 } 
 } // End Try statement. 
 catch (_com_error &e) 
 { 
 // Notify the user of errors if any. 
 // Pass a connection pointer accessed from the Connection. 
 PrintProviderError(pConnection2); 
 PrintComError(e); 
 } 
 
 // Clean up objects before exit. 
 if (pRstSchema) 
 if (pRstSchema->State == adStateOpen) 
 pRstSchema->Close(); 
 if (pConnection2) 
 if (pConnection2->State == adStateOpen) 
 pConnection2->Close(); 
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
 for(long i = 0;i < nCount;i++) 
 { 
 pErr = pConnection->Errors->GetItem(i); 
 printf("\t Error number: %x\t%s", pErr->Number, 
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
 
 // Print COM errors. 
 printf("Error\n"); 
 printf("\tCode = %08lx\n", e.Error()); 
 printf("\tCode meaning = %s\n", e.ErrorMessage()); 
 printf("\tSource = %s\n", (LPCSTR) bstrSource); 
 printf("\tDescription = %s\n", (LPCSTR) bstrDescription); 
} 
// EndOpenSchemaCpp 
```

