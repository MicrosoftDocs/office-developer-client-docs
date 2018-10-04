﻿---
title: Append and CreateParameter Methods Example (VC++)
TOCTitle: Append and CreateParameter Methods Example (VC++)
ms:assetid: d979bd89-2d17-e977-a222-11d3c24fd84d
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250095(v=office.15)
ms:contentKeyID: 48548052
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Append and CreateParameter Methods Example (VC++)


**Applies to**: Access 2013 | Office 2013

This example uses the [Append](append-method-ado.md) and [CreateParameter](createparameter-method-ado.md) methods to execute a stored procedure with an input parameter.

``` 
 
// BeginAppendCpp 
#import "C:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
#include <ole2.h> 
#include <stdio.h> 
#include "conio.h" 
#include "AppendX.h" 
 
//Function declaration 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void AppendX(VOID); 
void PrintProviderError(_ConnectionPtr pConnection); 
 
/////////////////////////////////////////////////////////// 
// // 
// Main Function // 
// // 
/////////////////////////////////////////////////////////// 
void main() 
{ 
 HRESULT hr = S_OK; 
 
 if(FAILED(::CoInitialize(NULL))) 
 return; 
 
 AppendX(); 
 
 //Wait here for the user to see the output. 
 printf("\n\nPress any key to continue..."); 
 getch(); 
 ::CoUninitialize(); 
} 
 
 
/////////////////////////////////////////////////////////// 
// // 
// AppendX Function // 
// // 
/////////////////////////////////////////////////////////// 
VOID AppendX(VOID) 
{ 
 
 HRESULT hr = S_OK; 
 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace. 
 _RecordsetPtr pRstByRoyalty = NULL; 
 _RecordsetPtr pRstAuthors = NULL; 
 _CommandPtr pcmdByRoyalty = NULL; 
 _ParameterPtr pprmByRoyalty = NULL; 
 _ConnectionPtr pConnection = NULL; 
 
 
 //Define Other variables 
 IADORecordBinding *picRs = NULL; //Interface Pointer declared.(VC++ Extensions) 
 CEmployeeRs emprs; //C++ class object 
 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 
 _bstr_t strMessage, strAuthorID; 
 
 int intRoyalty; 
 VARIANT vtRoyalty; 
 
 try 
 { 
 //Open a Connection. 
 TESTHR(pConnection.CreateInstance(__uuidof(Connection))); 
 hr = pConnection->Open(strCnn,"","",adConnectUnspecified); 
 pConnection->CursorLocation = adUseClient; 
 
 //Open Command Object with one Parameter 
 TESTHR(pcmdByRoyalty.CreateInstance(__uuidof(Command))); 
 pcmdByRoyalty->CommandText = "byroyalty"; 
 pcmdByRoyalty->CommandType = adCmdStoredProc; 
 
 //Get parameter value and append parameter 
 printf("Enter Royalty: "); 
 scanf("%d",&intRoyalty); 
 
 //Define Integer/variant. 
 vtRoyalty.vt = VT_I2; 
 vtRoyalty.iVal = intRoyalty; 
 pprmByRoyalty = pcmdByRoyalty->CreateParameter("percentage",adInteger,adParamInput,sizeof(int),vtRoyalty); 
 pcmdByRoyalty->Parameters->Append(pprmByRoyalty); 
 
 pprmByRoyalty->Value = vtRoyalty; 
 
 //Create Recordset by executing the command 
 pcmdByRoyalty->ActiveConnection = pConnection; 
 pRstByRoyalty = pcmdByRoyalty->Execute(NULL,NULL,adCmdStoredProc); 
 
 //Open the authors table to get author names for display 
 TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset))); 
 
 //You have to explicitly pass the default Cursor type and LockType to the Recordset here 
 hr = pRstAuthors->Open("authors",_variant_t((IDispatch*)pConnection,true),adOpenForwardOnly,adLockReadOnly,adCmdTable); 
 
 //Open an IADORecordBinding interface pointer which we'll use for Binding Recordset to a class 
 TESTHR(pRstAuthors->QueryInterface(__uuidof(IADORecordBinding),(LPVOID*)&picRs)); 
 
 //Bind the Recordset to a C++ Class here 
 TESTHR(picRs->BindToRecordset(&emprs)); 
 
 //Print current data in the recordset, adding 
 //author names from author table. 
 printf("Authors with %d percent royalty ",intRoyalty); 
 
 while(!(pRstByRoyalty->EndOfFile)) 
 { 
 strAuthorID = pRstByRoyalty->Fields->Item["au_id"]->Value; 
 pRstAuthors->Filter = "au_id = '"+strAuthorID+"'"; 
 
 printf("\n" "%s, %s %s",emprs.lau_idStatus == adFldOK ? emprs.m_szau_id : "<NULL>", emprs.lau_fnameStatus == adFldOK ? emprs.m_szau_fname : "<NULL>", emprs.lau_lnameStatus == adFldOK ? emprs.m_szau_lname : "<NULL>"); 
 
 pRstByRoyalty->MoveNext(); 
 } 
 } 
 catch(_com_error &e) 
 { 
 _bstr_t bstrSource(e.Source()); 
 _bstr_t bstrDescription(e.Description()); 
 
 PrintProviderError(pConnection); 
 
 printf("\n Source : %s \n Description : %s \n",(LPCSTR)bstrSource,(LPCSTR)bstrDescription); 
 } 
 
 // Clean up objects before exit. 
 //Release the IADORecordset Interface here 
 if (picRs) 
 picRs->Release(); 
 
 if (pRstByRoyalty) 
 if (pRstByRoyalty->State == adStateOpen) 
 pRstByRoyalty->Close(); 
 if (pRstAuthors) 
 if (pRstAuthors->State == adStateOpen) 
 pRstAuthors->Close(); 
 if (pConnection) 
 if (pConnection->State == adStateOpen) 
 pConnection->Close(); 
} 
 
 
/////////////////////////////////////////////////////////// 
// // 
// PrintProviderError Function // 
// // 
/////////////////////////////////////////////////////////// 
 
VOID PrintProviderError(_ConnectionPtr pConnection) 
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
 printf("Error number: %x\n Error Description: %s\n", pErr->Number,(LPCSTR) pErr->Description); 
 } 
 } 
} 
// EndAppendCpp 
```

**AppendX.h**

``` 
 
// BeginAppendH 
#include "icrsint.h" 
 
 
//This Class extracts only author id,fname,lastname 
 
class CEmployeeRs : public CADORecordBinding 
{ 
BEGIN_ADO_BINDING(CEmployeeRs) 
 
 //Column au_id is the 1st field in the recordset 
 
 ADO_VARIABLE_LENGTH_ENTRY2(1, adVarChar, m_szau_id, 
 sizeof(m_szau_id), lau_idStatus, TRUE) 
 
 ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_szau_lname, 
 sizeof(m_szau_lname), lau_lnameStatus, TRUE) 
 
 ADO_VARIABLE_LENGTH_ENTRY2(3, adVarChar, m_szau_fname, 
 sizeof(m_szau_fname), lau_fnameStatus, TRUE) 
 
END_ADO_BINDING() 
 
public: 
 
 CHAR m_szau_id[20]; 
 ULONG lau_idStatus; 
 
 CHAR m_szau_fname[40]; 
 ULONG lau_fnameStatus; 
 
 CHAR m_szau_lname[40]; 
 ULONG lau_lnameStatus; 
 
}; 
// EndAppendH 
```

