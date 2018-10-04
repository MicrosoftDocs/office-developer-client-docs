﻿---
title: CompareBookmarks Method Example (VC++)
TOCTitle: CompareBookmarks Method Example (VC++)
ms:assetid: 41d092dc-da36-7e44-3c25-cc68bffc6f16
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249191(v=office.15)
ms:contentKeyID: 48544460
ms.date: 09/18/2015
mtps_version: v=office.15
---

# CompareBookmarks Method Example (VC++)


**Applies to**: Access 2013 | Office 2013

This example demonstrates the [CompareBookmarks](comparebookmarks-method-ado.md) method. The relative value of bookmarks is seldom needed unless a particular bookmark is somehow special.

Designate a random row of a [Recordset](recordset-object-ado.md) derived from the ***Authors*** table as the target of a search. Then display the position of each row relative to that target.

``` 
 
// BeginCompareBookmarksCpp 
#import "C:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
#include <ole2.h> 
#include <stdio.h> 
#include <conio.h> 
#include <time.h> 
#include <stdlib.h> 
 
// Function declarations 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void CompareBookMarksX(void); 
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
 
 CompareBookMarksX(); 
 
 printf("Press any key to continue..."); 
 getch(); 
 ::CoUninitialize(); 
} 
 
////////////////////////////////////////////////////////// 
// // 
// CompareBookMarksX Function // 
// // 
////////////////////////////////////////////////////////// 
 
void CompareBookMarksX(void) 
{ 
 HRESULT hr = S_OK; 
 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace. 
 _RecordsetPtr pRstAuthors = NULL; 
 _variant_t vTarget; 
 _bstr_t strAns; 
 _bstr_t strTitle; 
 strTitle = "CompareBookmarks Example"; 
 try 
 { 
 TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset))); 
 
 pRstAuthors->Open("SELECT * FROM authors ORDER BY au_id", strCnn, 
 adOpenStatic, adLockReadOnly, adCmdText); 
 
 long count = pRstAuthors->RecordCount; 
 printf("Rows in the Recordset = %d\n", count); 
 if (count == 0) 
 exit(1); //Exit if an empty recordset 
 
 srand( (unsigned)time( NULL ) ); //Randomize 
 
 count = int(rand() % (count-1)); //Get position between 1 and count-1 
 if(!count) {count++;}; 
 
 printf("Randomly chosen row position = %d\n", count); 
 
 _variant_t vtBookMark = (short)adBookmarkFirst; 
 
 pRstAuthors->Move(count,vtBookMark); //Move row to random position 
 
 vTarget = pRstAuthors->Bookmark; //Remember the mystery row. 
 count = 0; 
 long intLineCnt = 3; 
 pRstAuthors->MoveFirst(); 
 
 while (!(pRstAuthors->EndOfFile)) //Loop through recordset 
 { 
 intLineCnt++; 
 if (intLineCnt%20 == 0) 
 { 
 printf("\nPress any key to continue...\n"); 
 getch(); 
 } 
 long result = pRstAuthors->CompareBookmarks( 
 pRstAuthors->Bookmark, vTarget); 
 
 if (result == adCompareNotEqual) 
 printf("Row %d: Bookmarks are not equal. %d\n", count, result); 
 else if (result == adCompareNotComparable) 
 printf("Row %d: Bookmarks are not comparable.\n", count); 
 else 
 { 
 switch(result) 
 { 
 case adCompareLessThan: 
 strAns = "less than"; 
 break; 
 case adCompareEqual: 
 strAns = "equal to"; 
 break; 
 case adCompareGreaterThan: 
 strAns = "greater than"; 
 break; 
 default: 
 strAns = "in error comparing to"; 
 break; 
 } 
 printf ("Row position %d is %s the target.\n", 
 count,(LPCSTR)strAns); 
 } 
 count++; 
 pRstAuthors->MoveNext(); 
 } 
 } 
 catch(_com_error &e) 
 { 
 // Notify the user of errors if any. 
 // Pass a connection pointer accessed from the Recordset. 
 _variant_t vtConnect = pRstAuthors->GetActiveConnection(); 
 
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
 if (pRstAuthors) 
 if (pRstAuthors->State == adStateOpen) 
 pRstAuthors->Close(); 
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
 printf("Error number: %x\t%s\n", pErr->Number, 
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
// EndCompareBookmarksCpp 
```

