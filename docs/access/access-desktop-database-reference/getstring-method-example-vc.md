---
title: GetString Method Example (VC++)
TOCTitle: GetString Method Example (VC++)
ms:assetid: 2f82bfcb-5bb1-275f-e53b-155a8a155980
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249078(v=office.15)
ms:contentKeyID: 48544007
ms.date: 09/18/2015
mtps_version: v=office.15
---

# GetString Method Example (VC++)


**Applies to**: Access 2013 | Office 2013

This example demonstrates the [GetString](getstring-method-ado.md) method.

Assume you are debugging a data access problem and want a quick, simple way of printing the current contents of a small [Recordset](recordset-object-ado.md).

``` 
 
// BeginGetStringCpp 
#import "C:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
#include <ole2.h> 
#include <stdio.h> 
#include <conio.h> 
#include <string.h> 
 
// Function declarations 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void GetStringX(void); 
void PrintProviderError(_ConnectionPtr pConnection); 
void PrintComError(_com_error &e); 
 
////////////////////////////////////////////////////////// 
// // 
// Main Function // 
// // 
////////////////////////////////////////////////////////// 
 
void main() 
{ 
 if(FAILED(::CoInitialize(NULL))) 
 return; 
 
 GetStringX(); 
 
 ::CoUninitialize(); 
} 
 
////////////////////////////////////////////////////////// 
// // 
// GetStringX Function // 
// // 
////////////////////////////////////////////////////////// 
 
void GetStringX(void) 
{ 
 HRESULT hr = S_OK; 
 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace. 
 _ConnectionPtr pConnection = NULL; 
 _RecordsetPtr pRstAuthors = NULL; 
 
 // Define string variables. 
 _bstr_t strCnn("Provider='sqloledb';Data Source='localhost';" 
 "Initial Catalog='Northwind';Integrated Security='SSPI';"); 
 _bstr_t varOutput; 
 char *strPrompt = "Enter a state (CA, IN, KS, MD, MI, OR, TN, UT): "; 
 char strState[2], *pState; 
 
 try 
 { 
 // Open connection. 
 TESTHR(pConnection.CreateInstance(__uuidof(Connection))); 
 
 // Open a command object for a stored procedure, 
 // with one parameter. 
 TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset))); 
 
 printf("%s",strPrompt); 
 gets(strState); 
 
 pState = strtok(strState," \t"); 
 
 char strQry[100] = "SELECT au_fname, au_lname, address, city " 
 "FROM authors WHERE state = "; 
 
 strcat(strQry,"'"); 
 strcat(strQry,pState); 
 strcat(strQry,"'"); 
 
 _bstr_t strQuery(strQry); 
 
 pConnection->Open (strCnn, "", "", adConnectUnspecified); 
 
 pRstAuthors->Open(strQuery, _variant_t((IDispatch*)pConnection, 
 true), 
 adOpenStatic, adLockReadOnly, adCmdText); 
 
 if (pRstAuthors->RecordCount > 0) 
 { 
 // Use all defaults: get all rows, TAB column delimiter, 
 // CARRIAGE RETURN row delimiter, empty-string null delimiter 
 long lRecCount = pRstAuthors->RecordCount; 
 _bstr_t varTab("\t"); 
 _bstr_t varRet("\r"); 
 _bstr_t varNull(""); 
 varOutput = pRstAuthors->GetString(adClipString,lRecCount, 
 varTab,varRet,varNull); 
 printf("State = '%s'\n", strState); 
 printf ("Name Address City\n"); 
 printf ("%s\n", (LPCTSTR)varOutput); 
 } 
 else 
 { 
 printf("\nNo rows found for state = '%s'\n",pState); 
 } 
 // Clean up objects before exit. 
 pRstAuthors->Close(); 
 pConnection->Close(); 
 } 
 
 catch(_com_error &e) 
 { 
 // Notify the user of errors if any. 
 // Pass a connection pointer accessed from the Recordset. 
 PrintProviderError(pConnection); 
 PrintComError(e); 
 } 
} 
 
////////////////////////////////////////////////////////// 
// // 
// PrintProviderError Function // 
// // 
////////////////////////////////////////////////////////// 
 
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
 printf("\t Error number: %x\t%s", pErr->Number, 
 pErr->Description); 
 } 
 } 
} 
 
////////////////////////////////////////////////////////// 
// // 
// PrintComError Function // 
// // 
////////////////////////////////////////////////////////// 
 
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
// EndGetStringCpp 
```

