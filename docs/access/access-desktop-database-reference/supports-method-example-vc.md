﻿---
title: Supports Method Example (VC++)
TOCTitle: Supports Method Example (VC++)
ms:assetid: a258cf70-ecd4-20eb-efb2-21c1ca79f180
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249747(v=office.15)
ms:contentKeyID: 48546756
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Supports Method Example (VC++)


**Applies to**: Access 2013 | Office 2013

This example uses the [Supports](supports-method-ado.md) method to display the options supported by a recordset opened with different cursor types. The DisplaySupport function is required for this example to run.

``` 
 
// BeginSupportsCpp 
#import "C:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
#include <stdio.h> 
#include <ole2.h> 
#include <conio.h> 
 
//Function Declarations. 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void SupportsX(void); 
void DisplaySupport(_RecordsetPtr pRstTemp); 
void PrintProviderError(_ConnectionPtr pConnection); 
void PrintComError(_com_error &e); 
 
/////////////////////////////////////////////// 
// // 
// Main Function // 
// // 
/////////////////////////////////////////////// 
void main() 
{ 
 if(FAILED(::CoInitialize(NULL))) 
 return; 
 
 SupportsX(); 
 
 ::CoUninitialize(); 
} 
 
/////////////////////////////////////////////// 
// // 
// SupportsX Function // 
// // 
/////////////////////////////////////////////// 
void SupportsX(void) 
{ 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace. 
 _RecordsetPtr pRstTitles = NULL; 
 
 // Define Other Variables 
 HRESULT hr = S_OK; 
 
 // Assign connection string to a variable 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 
 try 
 { 
 // Open a recordset from Titles table 
 TESTHR(pRstTitles.CreateInstance(__uuidof(Recordset))); 
 
 // Fill array with CursorType constants. 
 int aintCursorType[4]; 
 aintCursorType[0] = adOpenForwardOnly; 
 aintCursorType[1] = adOpenKeyset; 
 aintCursorType[2] = adOpenDynamic; 
 aintCursorType[3] = adOpenStatic; 
 
 // Open recordset using each CursorType and optimistic locking. 
 // Then call the DisplaySupport procedure to display the 
 // supported options. 
 for (int intIndex=0; intIndex <= 3; intIndex++) 
 { 
 pRstTitles->CursorType = 
 (enum CursorTypeEnum)aintCursorType[intIndex]; 
 pRstTitles->LockType = adLockOptimistic; 
 
 // Pass the Cursor type and LockType to the Recordset. 
 pRstTitles->Open ("titles", strCnn, 
 (enum CursorTypeEnum)aintCursorType[intIndex], 
 adLockOptimistic, adCmdTable); 
 
 switch(aintCursorType[intIndex]) 
 { 
 case adOpenForwardOnly: 
 printf("\nForwardOnly cursor supports:\n"); 
 break; 
 
 case adOpenKeyset: 
 printf("\nKeyset cursor supports:\n"); 
 break; 
 
 case adOpenDynamic: 
 printf("\nDynamic cursor supports:\n"); 
 break; 
 
 case adOpenStatic: 
 printf("\nStatic cursor supports:\n"); 
 break; 
 
 default : 
 break; 
 } 
 
 DisplaySupport(pRstTitles); 
 
 printf("\n\nPress any key to continue..."); 
 getch(); 
 
 //Clear the screen for the next display. 
 system("cls"); 
 } 
 } 
 catch(_com_error &e) 
 { 
 // Notify the user of errors if any. 
 // Pass a connection pointer accessed from the Recordset. 
 _variant_t vtConnect = pRstTitles->GetActiveConnection(); 
 
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
 if (pRstTitles) 
 if (pRstTitles->State == adStateOpen) 
 pRstTitles->Close(); 
} 
 
/////////////////////////////////////////////// 
// // 
// DisplaySupport Function // 
// // 
/////////////////////////////////////////////// 
void DisplaySupport (_RecordsetPtr pRstTemp) 
{ 
 // Fill array with cursor option constants. 
 long alngConstants[11]; 
 alngConstants[0] = adAddNew; 
 alngConstants[1] = adApproxPosition; 
 alngConstants[2] = adBookmark; 
 alngConstants[3] = adDelete; 
 alngConstants[4] = adFind; 
 alngConstants[5] = adHoldRecords; 
 alngConstants[6] = adMovePrevious; 
 alngConstants[7] = adNotify; 
 alngConstants[8] = adResync; 
 alngConstants[9] = adUpdate; 
 alngConstants[10] = adUpdateBatch; 
 
 for(int intIndex=0; intIndex <= 10; intIndex++) 
 { 
 bool booSupports = pRstTemp-> 
 Supports( (enum CursorOptionEnum)alngConstants[intIndex] ); 
 
 if(booSupports) 
 { 
 switch(alngConstants[intIndex]) 
 { 
 case adAddNew : 
 printf("\n AddNew"); 
 break; 
 
 case adApproxPosition : 
 printf("\n AbsolutePosition and AbsolutePage"); 
 break; 
 
 case adBookmark : 
 printf("\n Bookmark"); 
 break; 
 
 case adDelete : 
 printf("\n Delete"); 
 break; 
 
 case adFind : 
 printf("\n Find"); 
 break; 
 
 case adHoldRecords : 
 printf("\n Holding Records"); 
 break; 
 
 case adMovePrevious : 
 printf("\n MovePrevious and Move"); 
 break; 
 
 case adNotify : 
 printf("\n Notifications"); 
 break; 
 
 case adResync : 
 printf("\n Resyncing data"); 
 break; 
 
 case adUpdate : 
 printf("\n Update"); 
 break; 
 
 case adUpdateBatch : 
 printf("\n Batch updating"); 
 break; 
 
 default : 
 break; 
 } 
 } 
 } 
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
// EndSupportsCpp 
```

