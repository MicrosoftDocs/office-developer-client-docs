﻿---
title: Refresh Method Example (VC++)
TOCTitle: Refresh Method Example (VC++)
ms:assetid: fd40488f-2af5-574a-0717-7bfb5c3f1094
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250298(v=office.15)
ms:contentKeyID: 48548906
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Refresh Method Example (VC++)


**Applies to**: Access 2013 | Office 2013

This example demonstrates using the [Refresh](refresh-method-ado.md) method to refresh the [Parameters](parameters-collection-ado.md) collection for a stored procedure [Command](command-object-ado.md) object.

``` 
 
// BeginRefreshCpp 
#import "c:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
#include <ole2.h> 
#include <stdio.h> 
#include <conio.h> 
#include "RefreshX.h" 
 
// Function declarations 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void RefreshX(void); 
void PrintProviderError(_ConnectionPtr pConnection); 
void PrintComError(_com_error &e); 
inline char* mygets(char* strDest, int n) 
{ 
 char strExBuff[10]; 
 char* pstrRet = fgets(strDest, n, stdin); 
 
 if (pstrRet == NULL) 
 return NULL; 
 
 if (!strrchr(strDest, '\n')) 
 // Exhaust the input buffer. 
 do 
 { 
 fgets(strExBuff, sizeof(strExBuff), stdin); 
 }while (!strrchr(strExBuff, '\n')); 
 else 
 // Replace '\n' with '\0' 
 strDest[strrchr(strDest, '\n') - strDest] = '\0'; 
 
 return pstrRet; 
} 
 
////////////////////////////// 
// // 
// Main Function // 
// // 
////////////////////////////// 
void main() 
{ 
 if(FAILED(::CoInitialize(NULL))) 
 return; 
 
 RefreshX(); 
 
 ::CoUninitialize(); 
} 
 
//////////////////////////////////////////// 
// // 
// RefreshX Function // 
// // 
//////////////////////////////////////////// 
 
void RefreshX(void) 
{ 
 HRESULT hr = S_OK; 
 
 // Define string variables. 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace. 
 _ConnectionPtr pConnection = NULL; 
 _CommandPtr pCmdByRoyalty = NULL; 
 _RecordsetPtr pRstByRoyalty = NULL; 
 _RecordsetPtr pRstAuthors = NULL; 
 IADORecordBinding *picRs = NULL; //Interface Pointer declared. 
 CAuthorsRs authorsrs; //C++ class object 
 
 try 
 { 
 // Open connection. 
 TESTHR(pConnection.CreateInstance(__uuidof(Connection))); 
 pConnection->Open (strCnn, "", "", adConnectUnspecified); 
 
 // Open a command object for a stored procedure, 
 // with one parameter. 
 TESTHR(pCmdByRoyalty.CreateInstance(__uuidof(Command))); 
 pCmdByRoyalty->ActiveConnection = pConnection; 
 pCmdByRoyalty->CommandText = "byroyalty"; 
 pCmdByRoyalty->CommandType = adCmdStoredProc; 
 pCmdByRoyalty->Parameters->Refresh(); 
 
 // Get parameter value and execute the command, 
 // storing the results in a recordset. 
 char *strRoyalty; 
 char strTemp[5]; 
 do 
 { 
 printf("\n\nEnter royalty : "); 
 mygets(strTemp, 5); 
 
 strRoyalty = strtok(strTemp," \t"); 
 if(strRoyalty == NULL) 
 { 
 exit(1); 
 } 
 
 // if the input is not numeric then notify the user. 
 if(!atoi(strRoyalty)) 
 { 
 printf("\nExpecting numeric value..."); 
 continue; 
 } 
 }while(!atoi(strRoyalty)); 
 
 _variant_t vtroyal; 
 vtroyal.vt = VT_I2; 
 vtroyal.iVal = atoi(strRoyalty); 
 _variant_t Index; 
 Index.vt = VT_I2; 
 Index.iVal = 1; 
 pCmdByRoyalty->GetParameters()->GetItem(Index)-> 
 PutValue(vtroyal); 
 pRstByRoyalty = pCmdByRoyalty-> 
 Execute(NULL,NULL,adCmdStoredProc); 
 
 // Open the Authors table to get author names for display. 
 TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset))); 
 pRstAuthors->Open ("authors", 
 _variant_t((IDispatch *) pConnection, true), 
 adOpenForwardOnly, adLockReadOnly, adCmdTable); 
 
 //Open an IADORecordBinding interface pointer which we'll use for 
 //Binding Recordset to a class. 
 TESTHR(pRstAuthors->QueryInterface( 
 __uuidof(IADORecordBinding),(LPVOID*)&picRs)); 
 
 //Bind the Recordset to a C++ Class here. 
 TESTHR(picRs->BindToRecordset(&authorsrs)); 
 
 // Print current data in the recordset,adding 
 // author names from Authors table. 
 printf("\n\nAuthors with %s percent royalty\n\n",strRoyalty); 
 while(!(pRstByRoyalty->EndOfFile)) 
 { 
 _bstr_t strAuthorID = pRstByRoyalty->Fields->GetItem( 
 "au_id")->Value; 
 
 printf(" %s",(LPCSTR) (_bstr_t) pRstByRoyalty->Fields-> 
 GetItem("au_id")->Value); 
 
 pRstAuthors->Filter = "au_id ='"+strAuthorID+"'"; 
 printf(", %s %s\n\n",authorsrs.lau_fnameStatus == adFldOK ? 
 authorsrs.m_szau_fname : "<NULL>", 
 authorsrs.lau_lnameStatus == adFldOK ? 
 authorsrs.m_szau_lname : "<NULL>"); 
 pRstByRoyalty->MoveNext(); 
 } 
 } 
 catch (_com_error &e) 
 { 
 PrintProviderError(pConnection); 
 PrintComError(e); 
 } 
 
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
// EndRefreshCpp 
```

**RefreshX.h**

``` 
 
// BeginRefreshH 
#include "icrsint.h" 
 
//This Class extracts lname,fname from authors table. 
class CAuthorsRs : public CADORecordBinding 
{ 
BEGIN_ADO_BINDING(CAuthorsRs) 
 // Column lname is the 2nd field in the recordset 
 ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_szau_lname, 
 sizeof(m_szau_lname), lau_lnameStatus, TRUE) 
 // Column fname is the 3rd field in the recordset. 
 ADO_VARIABLE_LENGTH_ENTRY2(3, adVarChar, m_szau_fname, 
 sizeof(m_szau_fname), lau_fnameStatus, TRUE) 
 
END_ADO_BINDING() 
 
public: 
 CHAR m_szau_fname[21]; 
 ULONG lau_fnameStatus; 
 CHAR m_szau_lname[41]; 
 ULONG lau_lnameStatus; 
}; 
// EndRefreshH 
```

