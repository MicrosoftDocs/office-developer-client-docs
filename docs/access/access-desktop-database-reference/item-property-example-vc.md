﻿---
title: Item Property Example (VC++)
TOCTitle: Item Property Example (VC++)
ms:assetid: 17bfcb84-e0f7-7a24-6fc4-ab1dacd2766a
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248928(v=office.15)
ms:contentKeyID: 48543452
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Item Property Example (VC++)


**Applies to**: Access 2013 | Office 2013

This example demonstrates how the [Item](item-property-ado.md) property accesses members of a collection. The example opens the ***Authors*** table of the ***Pubs*** database with a parameterized command.

The parameter in the command issued against the database is accessed from the [Command](command-object-ado.md) object's [Parameters](parameters-collection-ado.md) collection by index and name. Then the fields of the returned [Recordset](recordset-object-ado.md) are accessed from that object's [Fields](fields-collection-ado.md) collection by index and name.

``` 
 
// BeginItemCpp 
#import "C:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
#include <ole2.h> 
#include <stdio.h> 
#include <conio.h> 
 
// Function declarations 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void ItemX(void); 
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
 
 ItemX(); 
 
 //Wait here for the user to see the output 
 printf("Press any key to continue..."); 
 getch(); 
 ::CoUninitialize(); 
} 
 
////////////////////////////////////////////////////////// 
// // 
// ItemX Function // 
// // 
////////////////////////////////////////////////////////// 
 
void ItemX(void) 
{ 
 HRESULT hr = S_OK; 
 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace. 
 _ConnectionPtr pConnection = NULL; 
 _RecordsetPtr pRst = NULL; 
 _CommandPtr pCmd = NULL; 
 _ParameterPtr pPrm = NULL; 
 FieldPtr pFld = NULL; 
 
 // Other Variables. 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 _variant_t Column[9]; 
 _variant_t vIndex; 
 
 try 
 { 
 // Open connection. 
 TESTHR(pConnection.CreateInstance(__uuidof(Connection))); 
 
 TESTHR(pRst.CreateInstance(__uuidof(Recordset))); 
 
 TESTHR(pCmd.CreateInstance(__uuidof(Command))); 
 
 //Set the array with the authors table field (column) names 
 Column[0] = "au_id"; 
 Column[1] = "au_lname"; 
 Column[2] = "au_fname"; 
 Column[3] = "phone"; 
 Column[4] = "address"; 
 Column[5] = "city"; 
 Column[6] = "state"; 
 Column[7] = "zip"; 
 Column[8] = "contract"; 
 
 _bstr_t strText("SELECT * FROM authors WHERE state = ?"); 
 pCmd->CommandText = strText; 
 
 pPrm = pCmd->CreateParameter("ItemXparm", adChar, adParamInput, 
 2, "CA"); 
 pCmd->Parameters->Append(pPrm); 
 
 pConnection->Open(strCnn, "", "", adConnectUnspecified); 
 pCmd->ActiveConnection = pConnection; 
 
 // Connection and CommandType are omitted because 
 // a Command object is provided. 
 _variant_t Conn; 
 Conn.vt = VT_ERROR; 
 Conn.scode = DISP_E_PARAMNOTFOUND; 
 
 pRst->Open((_variant_t((IDispatch *) pCmd)),Conn,adOpenStatic, 
 adLockReadOnly, -1); 
 
 printf("The Parameters collection accessed by index...\n"); 
 
 vIndex = (short) 0; 
 pPrm = pCmd->Parameters->GetItem(&vIndex); 
 printf("Parameter name = '%s', value = '%s'\n", 
 (LPCSTR)pPrm->Name, (LPSTR)(_bstr_t)pPrm->Value); 
 
 printf("\nThe Parameters collection accessed by name...\n"); 
 pPrm = pCmd->Parameters->Item["ItemXparm"]; 
 printf("Parameter name = '%s', value = '%s'\n", 
 (LPCSTR)pPrm->Name, (LPSTR)(_bstr_t)pPrm->Value); 
 
 printf("\nThe Fields collection accessed by index...\n"); 
 pRst->MoveFirst(); 
 long limit = 0; 
 limit = ((pRst->Fields->Count) - 1); 
 int intLineCnt = 8; 
 for (short iIndex = 0; iIndex <= limit; iIndex++) 
 { 
 vIndex = iIndex; 
 intLineCnt++; 
 if (intLineCnt%15 == 0) 
 { 
 printf("\nPress any key to continue...\n"); 
 getch(); 
 } 
 pFld = pRst->Fields->GetItem(&vIndex); 
 printf("Field %d : Name = '%s', ", iIndex, 
 (LPCSTR)pFld->GetName()); 
 _variant_t FldVal = pFld->GetValue(); 
 
 // Because Value is the default property of a 
 // Property object,the use of the actual keyword 
 // here is optional. 
 switch(FldVal.vt) 
 { 
 case (VT_BOOL): 
 if(FldVal.boolVal) 
 { 
 printf("Value = 'True'"); 
 } 
 else 
 { 
 printf("Value = 'False'"); 
 } 
 printf("\n"); 
 break; 
 case (VT_BSTR): 
 printf("Value = '%s'", 
 (LPCSTR)(_bstr_t)FldVal.bstrVal); 
 printf("\n"); 
 break; 
 case (VT_I4): 
 printf("Value = '%s'",(LPCSTR)FldVal.iVal); 
 printf("\n"); 
 break; 
 case (VT_EMPTY): 
 printf("Value = '%s'",(LPCSTR)FldVal.lVal); 
 printf("\n"); 
 break; 
 default: 
 break; 
 } 
 } 
 
 printf("\nThe Fields collection accessed by name...\n"); 
 pRst->MoveFirst(); 
 for (iIndex = 0; iIndex <= 8; iIndex++) 
 { 
 intLineCnt++; 
 if (intLineCnt%15 == 0) 
 { 
 printf("\nPress any key to continue...\n"); 
 getch(); 
 } 
 pFld = pRst->Fields->GetItem(Column[iIndex]); 
 printf("Field name = '%s', ",(LPCSTR)pFld->GetName()); 
 _variant_t FldVal = pFld->GetValue(); 
 
 // Because Value is the default property of a 
 // Property object,the use of the actual keyword 
 // here is optional. 
 switch(FldVal.vt) 
 { 
 case (VT_BOOL): 
 if(FldVal.boolVal) 
 { 
 printf("Value = 'True'"); 
 } 
 else 
 { 
 printf("Value = 'False'"); 
 } 
 printf("\n"); 
 break; 
 case (VT_BSTR): 
 printf("Value = '%s'", 
 (LPCSTR)(_bstr_t)FldVal.bstrVal); 
 printf("\n"); 
 break; 
 case (VT_I4): 
 printf("Value = '%s'",(LPCSTR)FldVal.iVal); 
 printf("\n"); 
 break; 
 case (VT_EMPTY): 
 printf("Value = '%s'",(LPCSTR)FldVal.lVal); 
 printf("\n"); 
 break; 
 default: 
 break; 
 } 
 } 
 } 
 catch(_com_error &e) 
 { 
 // Notify the user of errors if any. 
 // Pass a connection pointer accessed from the Recordset. 
 PrintProviderError(pConnection); 
 PrintComError(e); 
 } 
 
 // Clean up objects before exit. 
 if (pRst) 
 if (pRst->State == adStateOpen) 
 pRst->Close(); 
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
// EndItemCpp 
```

