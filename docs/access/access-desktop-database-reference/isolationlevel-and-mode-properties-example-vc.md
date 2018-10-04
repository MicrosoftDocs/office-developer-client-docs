﻿---
title: IsolationLevel and Mode Properties Example (VC++)
TOCTitle: IsolationLevel and Mode Properties Example (VC++)
ms:assetid: 851d0dee-6583-d2e2-d598-5a404becc03d
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249579(v=office.15)
ms:contentKeyID: 48546050
ms.date: 09/18/2015
mtps_version: v=office.15
---

# IsolationLevel and Mode Properties Example (VC++)


**Applies to**: Access 2013 | Office 2013

This example uses the [Mode](mode-property-ado.md) property to open an exclusive connection, and the [IsolationLevel](isolationlevel-property-ado.md) property to open a transaction that is conducted in isolation of other transactions.

``` 
 
// BeginIsolationLevelCpp 
#import "C:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF","EndOfFile") 
 
#include <ole2.h> 
#include <stdio.h> 
#include <conio.h> 
#include "IsolationLevelX.h" 
 
// Function Declarations 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void IsolationLevelX(void); 
void PrintProviderError(_ConnectionPtr pConnection); 
void PrintComError(_com_error &e); 
 
///////////////////////////////////////////////////////////////// 
// // 
// // 
// Main Function // 
// // 
// // 
///////////////////////////////////////////////////////////////// 
 
void main() 
{ 
 if(FAILED(::CoInitialize(NULL))) 
 return; 
 
 IsolationLevelX(); 
 
 printf("Press any key to continue..."); 
 getch(); 
 ::CoUninitialize(); 
} 
 
///////////////////////////////////////////////////////////////// 
// // 
// IsolationLevelX() Function // 
// // 
///////////////////////////////////////////////////////////////// 
 
void IsolationLevelX(void) 
{ 
 // Define ADO ObjectPointers 
 // Initialize Pointers on define 
 // These are in the ADODB :: namespace 
 _RecordsetPtr pRstTitles = NULL; 
 _ConnectionPtr pConnection = NULL; 
 
 // Define other Variables 
 HRESULT hr = S_OK; 
 IADORecordBinding *picRs = NULL; // Interface Pointer Declared 
 CTitleRs titlers; // C++ Class Object 
 LPSTR p_TempStr = NULL; 
 
 //Assign Connection String to Variable 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 
 try 
 { 
 // Open Connection and Titles Table 
 TESTHR(pConnection.CreateInstance(__uuidof(Connection))); 
 pConnection->Mode = adModeShareExclusive; 
 pConnection->IsolationLevel = adXactIsolated; 
 pConnection->Open(strCnn,"","",adConnectUnspecified); 
 
 TESTHR(pRstTitles.CreateInstance(__uuidof(Recordset))); 
 pRstTitles->CursorType = adOpenDynamic; 
 pRstTitles->LockType = adLockPessimistic; 
 
 pRstTitles->Open("titles",_variant_t((IDispatch*) pConnection, 
 true),adOpenDynamic,adLockPessimistic,adCmdTable); 
 
 pConnection->BeginTrans(); 
 
 // Display Connection Mode 
 if(pConnection->Mode == adModeShareExclusive) 
 { 
 printf("Connection Mode Is Exclusive"); 
 } 
 else 
 { 
 printf("Connection Mode Is Not Exclusive"); 
 } 
 
 // Display Isolation Level 
 if(pConnection->IsolationLevel == adXactIsolated) 
 { 
 printf("\n\nTransaction is Isolated"); 
 printf("\n\nPress any key to continue...\n\n"); 
 getch(); 
 } 
 else 
 { 
 printf("\n\nTransaction is not Isolated"); 
 printf("\n\nPress any key to continue...\n\n"); 
 getch(); 
 } 
 
 // Open an IADORecordBinding interface pointer which 
 // we will use for binding Recordset to a class 
 TESTHR(pRstTitles->QueryInterface( 
 __uuidof(IADORecordBinding),(LPVOID*)&picRs)); 
 
 // Bind the Recordset to a C++ class here 
 TESTHR(picRs->BindToRecordset(&titlers)); 
 
 // Change the type of psychology titles. 
 p_TempStr = (LPSTR) malloc(sizeof(titlers.m_szau_Type)); 
 
 while (!(pRstTitles->EndOfFile)) 
 { 
 // Set the final character of the destination string to NULL. 
 p_TempStr[sizeof(titlers.m_szau_Type)-1] = '\0'; 
 // The source string will get truncated if its length is 
 // longer than the length of the destination string minus one. 
 strncpy(p_TempStr,strtok(titlers.m_szau_Type," "),sizeof(titlers.m_szau_Type)-1); 
 
 // Compare type with psychology 
 if (!strcmp(p_TempStr,"psychology")) 
 { 
 // Set the final character of the destination string to NULL. 
 titlers.m_szau_Type[sizeof(titlers.m_szau_Type)-1] = '\0'; 
 // Copy "self_help" title field 
 // The source string will get truncated if its length is 
 // longer than the length of the destination string minus one. 
 strncpy(titlers.m_szau_Type,"self_help",sizeof(titlers.m_szau_Type)-1); 
 picRs->Update(&titlers); 
 } 
 pRstTitles->MoveNext(); 
 } 
 // Print current data in recordset. 
 pRstTitles->Requery(adOptionUnspecified); 
 
 // Open again IADORecordBinding interface pointer for Binding 
 // Recordset to a class. 
 TESTHR(pRstTitles->QueryInterface( 
 __uuidof(IADORecordBinding),(LPVOID*)&picRs)); 
 
 // ReBinding the Recordset to a C++ Class 
 TESTHR(picRs->BindToRecordset(&titlers)); 
 
 // Move to the first record of the title table 
 pRstTitles->MoveFirst(); 
 
 //Clear the screen for the next display 
 system("cls"); 
 
 while (!pRstTitles->EndOfFile) 
 { 
 printf("%s - %s\n",titlers.lau_TitleStatus == adFldOK ? 
 titlers.m_szau_Title :"<NULL>", 
 titlers.lau_TypeStatus == adFldOK ? 
 titlers.m_szau_Type :"<NULL>"); 
 pRstTitles->MoveNext(); 
 } 
 } 
 catch(_com_error &e) 
 { 
 // Notify the user of errors if any. 
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
 { 
 // Restore Original Data 
 pConnection->RollbackTrans(); 
 
 pConnection->Close(); 
 } 
 
 // Deallocate the memory 
 if (p_TempStr) 
 free(p_TempStr); 
} 
 
///////////////////////////////////////////////////////////////// 
// // 
// PrintProviderError Function // 
// // 
///////////////////////////////////////////////////////////////// 
 
void PrintProviderError(_ConnectionPtr pConnection) 
{ 
 //Print Provider Errors from Connection object 
 //pErr is a record object in the Connection's Error collection 
 ErrorPtr pErr = NULL; 
 
 if((pConnection->Errors->Count)>0) 
 { 
 long nCount = pConnection->Errors->Count; 
 
 //Collection ranges from 0 to nCount-1 
 for(long i = 0;i < nCount;i++) 
 { 
 pErr = pConnection->Errors->GetItem(i); 
 printf("\t Error Number :%x \t %s",pErr->Number, 
 (LPCSTR) pErr->Description); 
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
// EndIsolationLevelCpp 
```

**IsolationLevelX.h**

``` 
 
// BeginIsolationLevelH 
 
#include "icrsint.h" 
 
//This class extracts titles and type from Title table 
 
class CTitleRs : public CADORecordBinding 
{ 
BEGIN_ADO_BINDING(CTitleRs) 
 // Column title is the 2nd field in the table 
 ADO_VARIABLE_LENGTH_ENTRY2(2,adVarChar,m_szau_Title, 
 sizeof(m_szau_Title),lau_TitleStatus,FALSE) 
 // Column type is the 3rd field in the table 
 ADO_VARIABLE_LENGTH_ENTRY2(3,adVarChar,m_szau_Type, 
 sizeof(m_szau_Type),lau_TypeStatus,TRUE) 
END_ADO_BINDING() 
 
public: 
 CHAR m_szau_Title[81]; 
 ULONG lau_TitleStatus; 
 CHAR m_szau_Type[13]; 
 ULONG lau_TypeStatus; 
}; 
// EndIsolationLevelH 
```

