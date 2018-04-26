---
title: "Find Method Example (VC++)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: dc6adb54-48ef-475e-7b52-435ac0fc63ff
description: "This example uses the Recordset object's Find method to locate and count the number of business titles in the Pubs database. The example assumes the underlying provider does not support similar functionality."
---

# Find Method Example (VC++)

This example uses the [Recordset](recordset-object-ado.md) object's [Find](find-method-ado.md) method to locate and count the number of business titles in the ** *Pubs* ** database. The example assumes the underlying provider does not support similar functionality. 
  
```
 
// BeginFindCpp 
#import "C:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
#include <ole2.h> 
#include <stdio.h> 
#include <conio.h> 
#include "FindX.h" 
 
// Function declarations 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void FindX(void); 
void PrintProviderError(_ConnectionPtr pConnection); 
void PrintComError(_com_error &amp;e); 
 
////////////////////////////////////////////////////////// 
// // 
// Main Function // 
// // 
////////////////////////////////////////////////////////// 
 
void main() 
{ 
 if(FAILED(::CoInitialize(NULL))) 
 return; 
 
 FindX(); 
 
 //Wait here for the user to see the output. 
 printf("Press any key to continue..."); 
 getch(); 
 ::CoUninitialize(); 
} 
 
////////////////////////////////////////////////////////// 
// // 
// FindX Function // 
// // 
////////////////////////////////////////////////////////// 
 
void FindX(void) 
{ 
 HRESULT hr = S_OK; 
 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace. 
 _ConnectionPtr pConnection = NULL; 
 _RecordsetPtr pRstTitles = NULL; 
 IADORecordBinding *picRs = NULL; //Interface Pointer declared. 
 CTitlesRs titlers; //C++ class object 
 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 
 try 
 { 
 // Open connection. 
 TESTHR(pConnection.CreateInstance(__uuidof(Connection))); 
 pConnection->Open (strCnn, "", "", adConnectUnspecified); 
 
 // Open title Table 
 TESTHR(pRstTitles.CreateInstance(__uuidof(Recordset))); 
 
 pRstTitles->Open("SELECT title_id FROM titles", 
 _variant_t((IDispatch *)pConnection), 
 adOpenStatic, adLockReadOnly, adCmdText); 
 
 // The default parameters are sufficient to search forward 
 // through a Recordset. 
 
 pRstTitles->Find ("title_id LIKE 'BU%'",0,adSearchForward,""); 
 
 //Open an IADORecordBinding interface pointer which 
 //we'll use for Binding Recordset to a class 
 TESTHR(pRstTitles->QueryInterface( 
 __uuidof(IADORecordBinding),(LPVOID*)&amp;picRs)); 
 
 //Bind the Recordset to a C++ Class here 
 TESTHR(picRs->BindToRecordset(&amp;titlers)); 
 
 // Skip the current record to avoid finding the same 
 // row repeatedly. The bookmark is redundant because Find 
 // searches from the current position. 
 int count = 0; 
 
 //Continue if last find succeeded. 
 while (!(pRstTitles->EndOfFile)) 
 { 
 printf("Title ID: %s\n",titlers.lt_titleidStatus == adFldOK ? 
 titlers.m_szt_titleid : "<NULL>"); 
 count++; //Count the last title found. 
 
 _variant_t mark = pRstTitles->Bookmark; //Note current pos. 
 pRstTitles->Find("title_id LIKE 'BU%'", 1, adSearchForward, 
 mark); 
 } 
 printf("The number of business titles is %d\n",count); 
 } 
 catch(_com_error &amp;e) 
 { 
 // Notify the user of errors if any. 
 // Pass a connection pointer accessed from the Recordset. 
 PrintProviderError(pConnection); 
 PrintComError(e); 
 } 
 
 // Clean up objects before exit. 
 //Release the IADORecordset Interface here 
 if (picRs) 
 picRs->Release(); 
 
 if (pRstTitles) 
 if (pRstTitles->State == adStateOpen) 
 pRstTitles->Close(); 
 if (pConnection) 
 if (pConnection->State == adStateOpen) 
 pConnection->Close(); 
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
 (LPCSTR)pErr->Description); 
 } 
 } 
} 
 
////////////////////////////////////////////////////////// 
// // 
// PrintComError Function // 
// // 
////////////////////////////////////////////////////////// 
 
void PrintComError(_com_error &amp;e) 
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
// EndFindCpp 

```

 **FindX.h**
  
```
 
// BeginFindH 
#include "icrsint.h" 
 
//This Class extracts only titleId from Titles table. 
class CTitlesRs : public CADORecordBinding 
{ 
BEGIN_ADO_BINDING(CTitlesRs) 
 
 // Column title_id is the 1st field in the recordset 
 // from Titles table. 
 ADO_VARIABLE_LENGTH_ENTRY2(1, adVarChar, m_szt_titleid, 
 sizeof(m_szt_titleid), lt_titleidStatus, FALSE) 
 
END_ADO_BINDING() 
 
public: 
 CHAR m_szt_titleid[150]; 
 ULONG lt_titleidStatus; 
}; 
// EndFindH 

```


