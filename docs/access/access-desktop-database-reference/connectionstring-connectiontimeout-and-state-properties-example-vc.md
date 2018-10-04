---
title: ConnectionString, ConnectionTimeout, and State Properties Example (VC++)
TOCTitle: ConnectionString, ConnectionTimeout, and State Properties Example (VC++)
ms:assetid: 39bd3e86-1eb8-7fcb-45c8-b9b0ae5acf83
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249143(v=office.15)
ms:contentKeyID: 48544254
ms.date: 09/18/2015
mtps_version: v=office.15
---

# ConnectionString, ConnectionTimeout, and State Properties Example (VC++)


**Applies to**: Access 2013 | Office 2013

This example demonstrates different ways of using the [ConnectionString](connectionstring-property-ado.md) property to open a [Connection](connection-object-ado.md) object. It also uses the [ConnectionTimeout](connectiontimeout-property-ado.md) property to set a connection timeout period, and the [State](state-property-ado.md) property to check the state of the connections. The GetState function is required for this procedure to run.

``` 
 
// BeingConnectionStringCpp 
#import "C:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
#include <ole2.h> 
#include <stdio.h> 
#include <conio.h> 
 
// Function declarations 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void ConnectionStringX(); 
_bstr_t GetState(int intState); 
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
 
 ConnectionStringX(); 
 
 //Wait here for user to see the output.. 
 printf("\nPress any key to continue..."); 
 getch(); 
 
 ::CoUninitialize(); 
} 
 
/////////////////////////////////////////////////////////// 
// // 
// ConnectionStringX Function // 
// // 
/////////////////////////////////////////////////////////// 
 
void ConnectionStringX() 
{ 
 // Define Connection object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace 
 _ConnectionPtr pConnection1 = NULL; 
 _ConnectionPtr pConnection2 = NULL; 
 _ConnectionPtr pConnection3 = NULL; 
 _ConnectionPtr pConnection4 = NULL; 
 
 //Define Other Variables 
 HRESULT hr = S_OK; 
 
 try 
 { 
 // Open a connection using OLE DB syntax. 
 TESTHR(pConnection1.CreateInstance(__uuidof(Connection))); 
 pConnection1->ConnectionString = 
 "Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='Pubs';Integrated Security='SSPI';"; 
 pConnection1->ConnectionTimeout = 30; 
 pConnection1->Open("","","",adConnectUnspecified); 
 printf("cnn1 state: %s\n", 
 (LPCTSTR)GetState(pConnection1->State)); 
 
 // Open a connection using a DSN and ODBC tags. 
 // It is assumed that you have create DSN 'Pubs' with a user name as 
 // 'MyUserId' and password as 'MyPassword'. 
 TESTHR(pConnection2.CreateInstance(__uuidof(Connection))); 
 pConnection2->ConnectionString = "DSN=Pubs;UID=MyUserId;PWD=MyPassword;"; 
 pConnection2->Open("","","",adConnectUnspecified); 
 printf("cnn2 state: %s\n", 
 (LPCTSTR)GetState(pConnection2->State)); 
 
 // Open a connection using a DSN and OLE DB tags. 
 TESTHR(pConnection3.CreateInstance(__uuidof(Connection))); 
 pConnection3->ConnectionString = "Data Source=Pubs;"; 
 pConnection3->Open("","","",adConnectUnspecified); 
 printf("cnn3 state: %s\n", 
 (LPCTSTR)GetState(pConnection3->State)); 
 
 // Open a connection using a DSN and individual 
 // arguments instead of a connection string. 
 // It is assumed that you have create DSN 'Pubs' with a user name as 
 // 'MyUserId' and password as 'MyPassword'. 
 TESTHR(pConnection4.CreateInstance(__uuidof(Connection))); 
 pConnection4->Open("Pubs","MyUserId","MyPassword",adConnectUnspecified); 
 printf("cnn4 state: %s\n", 
 (LPCTSTR)GetState(pConnection4->State)); 
 } 
 catch(_com_error &e) 
 { 
 // Notify user of any errors. 
 // Pass a connection pointer accessed from the Connection. 
 PrintProviderError(pConnection1); 
 if(pConnection2) 
 PrintProviderError(pConnection2); 
 if(pConnection3) 
 PrintProviderError(pConnection3); 
 if(pConnection4) 
 PrintProviderError(pConnection4); 
 PrintComError(e); 
 } 
 
 //Cleanup objects before exit. 
 if (pConnection1) 
 if (pConnection1->State == adStateOpen) 
 pConnection1->Close(); 
 if (pConnection2) 
 if (pConnection2->State == adStateOpen) 
 pConnection2->Close(); 
 if (pConnection3) 
 if (pConnection3->State == adStateOpen) 
 pConnection3->Close(); 
 if (pConnection4) 
 if (pConnection4->State == adStateOpen) 
 pConnection4->Close(); 
} 
 
/////////////////////////////////////////////////////////// 
// // 
// GetState Function // 
// // 
/////////////////////////////////////////////////////////// 
 
_bstr_t GetState(int intState) 
{ 
 _bstr_t strState; 
 switch(intState) 
 { 
 case adStateClosed: 
 strState = "adStateClosed"; 
 break; 
 case adStateOpen: 
 strState = "adStateOpen"; 
 break; 
 default: 
 ; 
 } 
 return strState; 
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
 printf("Error number: %x\t%s\n", pErr->Number, 
 (LPCSTR)pErr->Description); 
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
// EndConnectionStringCpp 
```

