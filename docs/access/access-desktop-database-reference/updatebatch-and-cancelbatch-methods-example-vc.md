﻿---
title: UpdateBatch and CancelBatch Methods Example (VC++)
TOCTitle: UpdateBatch and CancelBatch Methods Example (VC++)
ms:assetid: 49eb3cc7-16af-6e2b-911f-ddcf643cf699
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249227(v=office.15)
ms:contentKeyID: 48544651
ms.date: 09/18/2015
mtps_version: v=office.15
---

# UpdateBatch and CancelBatch Methods Example (VC++)


**Applies to**: Access 2013 | Office 2013

This example demonstrates the [UpdateBatch](updatebatch-method-ado.md) method in conjunction with the [CancelBatch](cancelbatch-method-ado.md) method.

``` 
 
// BeginUpdateBatchCpp 
#import "c:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
#include <ole2.h> 
#include <stdio.h> 
#include <conio.h> 
#include "UpdateBatchX.h" 
 
// Function declarations 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void UpdateBatchX(void); 
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
 
 UpdateBatchX(); 
 
 ::CoUninitialize(); 
} 
 
////////////////////////////////////////////////////////// 
// // 
// UpdateBatchX Function // 
// // 
////////////////////////////////////////////////////////// 
void UpdateBatchX(void) 
{ 
 HRESULT hr = S_OK; 
 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace. 
 _RecordsetPtr pRstTitles = NULL; 
 
 // Define string variables. 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 
 IADORecordBinding *picRs = NULL; // Interface Pointer Declared 
 CTitleRs titlers; // C++ Class Object 
 
 try 
 { 
 // Open titles table. 
 TESTHR(pRstTitles.CreateInstance(__uuidof(Recordset))); 
 pRstTitles->CursorType = adOpenKeyset; 
 pRstTitles->LockType = adLockBatchOptimistic; 
 pRstTitles->Open ("titles", strCnn, 
 adOpenKeyset, adLockBatchOptimistic, adCmdTable); 
 
 // Open IADORecordBinding interface pointer for binding 
 // Recordset to a class 
 TESTHR(pRstTitles->QueryInterface( 
 __uuidof(IADORecordBinding),(LPVOID*)&picRs)); 
 
 // Binding the Recordset to a C++ Class 
 TESTHR(picRs->BindToRecordset(&titlers)); 
 pRstTitles->MoveFirst(); 
 
 // Loop through recordset and ask user if she wants, 
 // to change the type for a specified title. 
 while (!(pRstTitles->EndOfFile)) 
 { 
 // Compare type with psychology 
 if (!strcmp( (char *)strtok(titlers.m_szt_Type," "), 
 "psychology" )) 
 { 
 printf("\n\nTitle: %s \nChange type to self_help?(y/n):", 
 titlers.m_szt_Title); 
 char chKey; 
 chKey = getch(); 
 if(toupper(chKey) == 'Y') 
 { 
 // Change type to self_help. 
 pRstTitles->Fields->GetItem("type")->Value = 
 (_bstr_t)("self_help"); 
 } 
 } 
 pRstTitles->MoveNext(); 
 } 
 
 // Ask the user if she wants to commit to all the 
 // changes made above. 
 printf("\n\nSave all changes?"); 
 char chKey; 
 chKey = getch(); 
 if(toupper(chKey) == 'Y') 
 { 
 pRstTitles->UpdateBatch(adAffectAll); 
 } 
 else 
 { 
 pRstTitles->CancelBatch(adAffectAll); 
 } 
 
 // Print current data in recordset. 
 pRstTitles->Requery(adOptionUnspecified); 
 
 // Open IADORecordBinding interface pointer for Binding Recordset to a class 
 TESTHR(pRstTitles->QueryInterface( 
 __uuidof(IADORecordBinding),(LPVOID*)&picRs)); 
 
 // ReBinding the Recordset to a C++ Class. 
 TESTHR(picRs->BindToRecordset(&titlers)); 
 
 // Move to the first record of the title table 
 pRstTitles->MoveFirst(); 
 
 //Clear the screen for the next display. 
 system("cls"); 
 
 while (!pRstTitles->EndOfFile) 
 { 
 printf("%s - %s\n", 
 titlers.lt_TitleStatus == adFldOK ? 
 titlers.m_szt_Title :"<NULL>", 
 titlers.lt_TypeStatus == adFldOK ? 
 titlers.m_szt_Type :"<NULL>"); 
 pRstTitles->MoveNext(); 
 } 
 
 pRstTitles->MoveFirst(); 
 
 // Restore original data because this is demonstration. 
 while (!(pRstTitles->EndOfFile)) 
 { 
 // Compare type with psychology 
 if(!strcmp( (char *)strtok(titlers.m_szt_Type," "), 
 "self_help" )) 
 { 
 // Change type to psychology. 
 pRstTitles->Fields->GetItem("type")->Value = 
 (_bstr_t)("psychology"); 
 } 
 pRstTitles->MoveNext(); 
 } 
 } 
 catch (_com_error &e) 
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
 
 if (pRstTitles) 
 if (pRstTitles->State == adStateOpen) 
 { 
 pRstTitles->UpdateBatch(adAffectAll); 
 pRstTitles->Close(); 
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
 printf("Error number: %x\t%s\n", pErr->Number, 
 (LPCSTR) pErr->Description); 
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
// EndUpdateBatchCpp 
```

**UpdateBatchX.h**

``` 
 
// BeginUpdateBatchH 
#include "icrsint.h" 
 
//This class extracts titles and type from Titles table 
class CTitleRs : public CADORecordBinding 
{ 
BEGIN_ADO_BINDING(CTitleRs) 
 // Column title is the 2nd field in the table 
 ADO_VARIABLE_LENGTH_ENTRY2(2,adVarChar,m_szt_Title, 
 sizeof(m_szt_Title),lt_TitleStatus,FALSE) 
 // Column type is the 3rd field in the table 
 ADO_VARIABLE_LENGTH_ENTRY2(3,adVarChar,m_szt_Type, 
 sizeof(m_szt_Type),lt_TypeStatus,TRUE) 
END_ADO_BINDING() 
 
public: 
 CHAR m_szt_Title[81]; 
 ULONG lt_TitleStatus; 
 CHAR m_szt_Type[13]; 
 ULONG lt_TypeStatus; 
}; 
// EndUpdateBatchH 
```

