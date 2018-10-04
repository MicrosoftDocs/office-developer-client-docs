﻿---
title: BOF, EOF, and Bookmark Properties Example (VC++)
TOCTitle: BOF, EOF, and Bookmark Properties Example (VC++)
ms:assetid: d3cf9ace-07d7-6f92-983c-49c8d4216e20
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250055(v=office.15)
ms:contentKeyID: 48547914
ms.date: 09/18/2015
mtps_version: v=office.15
---

# BOF, EOF, and Bookmark Properties Example (VC++)


**Applies to**: Access 2013 | Office 2013

The first function in this example uses the [BOF](bof-eof-properties-ado.md) and [EOF](bof-eof-properties-ado.md) properties to display a message if a user tries to move past the first or last record of a [Recordset](recordset-object-ado.md). It uses the [Bookmark](bookmark-property-ado.md) property to let the user flag a record in a **Recordset** and return to it later.

The second function uses the Bookmark property to place the **Bookmark** of every other record from a **Recordset** into an array, and then filters the Recordset using the array.

``` 
 
// BeginBOFCpp 
#import "C:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
#include <ole2.h> 
#include <stdio.h> 
#include <conio.h> 
#include "BofEofBookmark.h" 
 
// Function declarations 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void BOFX(void); 
void BookmarkX(void); 
void PrintProviderError(_ConnectionPtr pConnection); 
void PrintComError(_com_error &e); 
 
/////////////////////////////////////////////////////////// 
// // 
// BOFX Function // 
// // 
/////////////////////////////////////////////////////////// 
 
void main() 
{ 
 if(FAILED(::CoInitialize(NULL))) 
 return; 
 
 BOFX(); 
 
 //Clear the screen for the next display 
 system("cls"); 
 
 BookmarkX(); 
 
 printf("Press any key to continue..."); 
 getch(); 
 
 ::CoUninitialize(); 
} 
 
/////////////////////////////////////////////////////////// 
// // 
// BOFX Function // 
// // 
/////////////////////////////////////////////////////////// 
 
void BOFX(void) 
{ 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace 
 _RecordsetPtr rstPublishers = NULL; 
 
 //Define Other Variables 
 HRESULT hr = S_OK; 
 IADORecordBinding *picRs = NULL; //Interface Pointer declared. 
 CPublishers Publs; 
 
 bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 _bstr_t strMessage; 
 _variant_t VarBookmark; 
 int intCommand = 0; 
 _variant_t TempPublisher; 
 
 try 
 { 
 // Open recordset with data from Publishers table. 
 TESTHR(rstPublishers.CreateInstance(__uuidof(Recordset))); 
 rstPublishers->CursorType = adOpenStatic; 
 
 // Use client cursor to enable absolutePosition property. 
 rstPublishers->CursorLocation = adUseClient; 
 rstPublishers->Open("select pub_id, pub_name from publishers" 
 " order by pub_name", strCnn, adOpenStatic, 
 adLockBatchOptimistic, adCmdText); 
 
 //Open an IADORecordBinding interface pointer 
 //which will be used for Binding Recordset to a class 
 TESTHR(rstPublishers->QueryInterface( 
 __uuidof(IADORecordBinding), (LPVOID*)&picRs)); 
 
 //Bind the Recordset to a C++ Class here 
 TESTHR(picRs->BindToRecordset(&Publs)); 
 
 rstPublishers->MoveFirst(); 
 
 while (true) // Continuous loop. 
 { 
 // Display information about the current record 
 // and get user input 
 printf("Publisher:%s \n Record %d of %d\n\n", 
 Publs.lP_pubnameStatus == adFldOK ? 
 Publs.m_szP_pubname : "<NULL>", 
 rstPublishers->AbsolutePosition, 
 rstPublishers->RecordCount); 
 printf("Enter command:\n "); 
 printf("[1 - next / 2 - previous /\n"); 
 printf(" 3 - set bookmark / 4 - go to bookmark /\n"); 
 printf(" 5 - quit ]\n"); 
 
 scanf("%d", &intCommand); 
 if ((intCommand < 1) || (intCommand > 4)) 
 break; // Out of range entry exits program loop. 
 
 switch(intCommand) 
 { 
 // Move forward or backward, trapping for BOF or EOF 
 case 1: 
 rstPublishers->MoveNext(); 
 if (rstPublishers->EndOfFile) 
 { 
 printf("\nCannot move past the last record." 
 " Try again...\n"); 
 rstPublishers->MoveLast(); 
 } 
 break; 
 
 case 2: 
 rstPublishers->MovePrevious(); 
 if (rstPublishers->BOF) 
 { 
 printf("\nCannot move before the first record." 
 " Try again...\n"); 
 rstPublishers->MoveFirst(); 
 } 
 break; 
 
 // store the bookmark of the current record. 
 case 3: 
 VarBookmark = rstPublishers->Bookmark; 
 // Go to the record indicated by the 
 // stored bookmark 
 break; 
 
 case 4: 
 // Check for whether bookmark set for a record 
 if (VarBookmark.vt == VT_EMPTY) 
 printf("No Bookmark set!\n"); 
 else 
 rstPublishers->Bookmark = VarBookmark; 
 break; 
 
 default: 
 break; 
 } 
 } 
 } 
 catch (_com_error &e) 
 { 
 printf("Error in BOFx...\n"); 
 // Notify the user of errors if any. 
 _variant_t vtConnect = rstPublishers->GetActiveConnection(); 
 
 // GetActiveConnection returns connect string if connection 
 // is not open, else returns Connection object. 
 switch(vtConnect.vt) 
 { 
 case VT_BSTR: 
 printf("Error:\n"); 
 printf("Code = %08lx\n", e.Error()); 
 printf("Message = %s\n", e.ErrorMessage()); 
 printf("Source = %s\n", (LPCSTR) e.Source()); 
 printf("Description = %s\n", (LPCSTR) e.Description()); 
 break; 
 case VT_DISPATCH: 
 PrintProviderError(vtConnect); 
 break; 
 default: 
 printf("Errors occured."); 
 break; 
 } 
 printf("Press any key to continue..."); 
 getch(); 
 } 
 
 
 // Clean up objects before exit. 
 //Release the IADORecordset Interface here 
 if (picRs) 
 picRs->Release(); 
 
 if (rstPublishers) 
 if (rstPublishers->State == adStateOpen) 
 rstPublishers->Close(); 
} 
 
/////////////////////////////////////////////////////////// 
// // 
// BookmarkX Function // 
// // 
/////////////////////////////////////////////////////////// 
 
void BookmarkX(void) 
{ 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace. 
 _RecordsetPtr rstAuthors = NULL; 
 
 //Define Other Variables 
 IADORecordBinding *picRs = NULL; //Interface Pointer declared. 
 CAuthors Authrs; 
 HRESULT hr = S_OK; 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 _variant_t vBookmark; 
 
 // Variable declaration for safe arrays. 
 SAFEARRAY FAR* psa; 
 
 // define ARRAY/ VARIANT variant. 
 vBookmark.vt = VT_ARRAY|VT_VARIANT; 
 SAFEARRAYBOUND rgsabound[1]; 
 rgsabound[0].lLbound = 0; 
 rgsabound[0].cElements = 11; 
 long ii = 0; 
 
 try 
 { 
 rstAuthors.CreateInstance(__uuidof(Recordset)); 
 // Set The Cursor Location 
 rstAuthors->CursorLocation = adUseClient; 
 rstAuthors->PutActiveConnection((_variant_t)strCnn); 
 
 // Open Authors table 
 TESTHR(rstAuthors->Open("select * from authors",strCnn, 
 adOpenStatic,adLockBatchOptimistic,adCmdText)); 
 
 //Open an IADORecordBinding interface pointer 
 //which we'll use for binding Recordset to a class 
 TESTHR(rstAuthors->QueryInterface(__uuidof(IADORecordBinding), 
 (LPVOID*)&picRs)); 
 
 //Bind the Recordset to a C++ Class here 
 TESTHR(picRs->BindToRecordset(&Authrs)); 
 
 printf("Number of Records before filtering: %d\n", 
 rstAuthors->RecordCount); 
 
 // Create safearrays to store array of variant 
 psa = SafeArrayCreate(VT_VARIANT,1,rgsabound); 
 
 // Store bookmark of every other record into an array. 
 while ((!rstAuthors->EndOfFile) && (ii < 11)) 
 { 
 SafeArrayPutElement(psa,&ii,&rstAuthors->Bookmark); 
 //ii = ii +1; 
 ii++; 
 rstAuthors->Move(2); 
 } 
 
 vBookmark.parray = psa; 
 
 // Filter the Record with the array of bookmarks. 
 rstAuthors->put_Filter(vBookmark); 
 printf("Number of Records after filtering: %d\n", 
 rstAuthors->RecordCount); 
 rstAuthors->MoveFirst(); 
 
 while (!rstAuthors->EndOfFile) 
 { 
 printf("%d %s\n",rstAuthors->AbsolutePosition, 
 Authrs.lau_lnameStatus == adFldOK ? 
 Authrs.m_szau_lname : "<NULL>"); 
 rstAuthors->MoveNext(); 
 } 
 } 
 catch (_com_error &e) 
 { 
 // Notify the user of errors if any. 
 _variant_t vtConnect = rstAuthors->GetActiveConnection(); 
 
 // GetActiveConnection returns connect string if connection 
 // is not open, else returns Connection object. 
 switch(vtConnect.vt) 
 { 
 case VT_BSTR: 
 printf("Error:\n"); 
 printf("Code = %08lx\n", e.Error()); 
 printf("Message = %s\n", e.ErrorMessage()); 
 printf("Source = %s\n", (LPCSTR) e.Source()); 
 printf("Description = %s\n", (LPCSTR) e.Description()); 
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
 
 if (rstAuthors) 
 if (rstAuthors->State == adStateOpen) 
 rstAuthors->Close(); 
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
 long nCount = 0; 
 long i = 0; 
 
 if( (pConnection->Errors->Count) > 0) 
 { 
 nCount = pConnection->Errors->Count; 
 // Collection ranges from 0 to nCount -1. 
 for(i = 0; i < nCount; i++) 
 { 
 pErr = pConnection->Errors->GetItem(i); 
 printf("Error number: %x\t%s\n", pErr->Number, 
 (LPCSTR) pErr->Description); 
 } 
 } 
} 
// EndBOFCpp 
```

**BofEofBookmark.h**

``` 
 
// BeginBOFEOFH 
#include "icrsint.h" 
 
//This Class extracts only pubid,lastname and hire_date 
class CPublishers : public CADORecordBinding 
{ 
BEGIN_ADO_BINDING(CPublishers) 
 
 //Column title is the 2nd field in the recordset 
 ADO_VARIABLE_LENGTH_ENTRY2(1, adVarChar, m_szP_pubid, 
 sizeof(m_szP_pubid), lP_pubidStatus, FALSE) 
 
 //Column type is the 3rd field in the recordset 
 ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_szP_pubname, 
 sizeof(m_szP_pubname), lP_pubnameStatus, TRUE) 
 
END_ADO_BINDING() 
 
public: 
 CHAR m_szP_pubid; 
 ULONG lP_pubidStatus; 
 CHAR m_szP_pubname[40]; 
 ULONG lP_pubnameStatus; 
}; 
 
//This Class extracts only authorlastname 
 
class CAuthors : public CADORecordBinding 
{ 
BEGIN_ADO_BINDING(CAuthors) 
 
 //Column authorlname is the 2nd field in the recordset 
 ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_szau_lname, 
 sizeof(m_szau_lname), lau_lnameStatus, FALSE) 
 
END_ADO_BINDING() 
 
public: 
 CHAR m_szau_lname[40]; 
 ULONG lau_lnameStatus; 
}; 
// EndBOFEOFH 
```

