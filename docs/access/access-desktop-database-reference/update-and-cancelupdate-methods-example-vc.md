﻿---
title: Update and CancelUpdate Methods Example (VC++)
TOCTitle: Update and CancelUpdate Methods Example (VC++)
ms:assetid: 3660dafd-940e-f5ac-169e-15faf960742e
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249123(v=office.15)
ms:contentKeyID: 48544167
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Update and CancelUpdate Methods Example (VC++)


**Applies to**: Access 2013 | Office 2013

This example demonstrates the [Update](update-method-ado.md) method in conjunction with the [CancelUpdate](cancelupdate-method-ado.md) method.

``` 
 
// BeginUpdateCpp 
#import "C:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
#include <stdio.h> 
#include <ole2.h> 
#include <malloc.h> 
#include <conio.h> 
#include "UpdateX.h" 
 
// Function Declartion. 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void UpdateX(void); 
void UpdateX2(void); 
void PrintProviderError(_ConnectionPtr pConnection); 
void PrintComError(_com_error &e); 
 
void main() 
{ 
 if(FAILED(::CoInitialize(NULL))) 
 return; 
 
 UpdateX(); 
 
 //Wait here for user to see the output.. 
 printf("\nPress any key to continue..."); 
 getch(); 
 
 //Clear the screen for the next display 
 system("cls"); 
 
 UpdateX2(); 
 
 ::CoUninitialize(); 
} 
 
////////////////////////////////////////////////////////// 
// // 
// UpdateX Function // 
// // 
////////////////////////////////////////////////////////// 
void UpdateX(void) 
{ 
 HRESULT hr = S_OK; 
 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace. 
 _RecordsetPtr pRstEmployees = NULL; 
 
 // Define string variables. 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 
 IADORecordBinding *picRs = NULL; // Interface Pointer declared 
 CEmployeeRs emprs; // C++ Class object. 
 
 try 
 { 
 // Open recordset with names from Employee table. 
 TESTHR(pRstEmployees.CreateInstance(__uuidof(Recordset))); 
 pRstEmployees->CursorType = adOpenKeyset; 
 pRstEmployees->LockType = adLockOptimistic; 
 pRstEmployees->Open("SELECT fname, lname FROM Employee " 
 "ORDER BY lname",strCnn,adOpenKeyset,adLockOptimistic, 
 adCmdText); 
 
 // Store original data. 
 _bstr_t strOldFirst = pRstEmployees->Fields-> 
 GetItem("fname")->Value; 
 _bstr_t strOldLast = pRstEmployees->Fields-> 
 GetItem("lname")->Value; 
 
 //Change data in edit buffer. 
 pRstEmployees->Fields->GetItem("fname")->Value = 
 (_bstr_t)("Linda"); 
 pRstEmployees->Fields->GetItem("lname")->Value = 
 (_bstr_t)("Kobara"); 
 
 // Show contents of buffer and get user input. 
 printf("\n\nEdit in progress:\n\n"); 
 
 printf("Original data = %s %s \n", 
 (LPSTR)strOldFirst,(LPSTR)strOldLast); 
 
 printf("Data in buffer = %s %s", 
 (LPSTR)(_bstr_t) pRstEmployees->Fields-> 
 GetItem("fname")->Value, (LPSTR) (_bstr_t) pRstEmployees->Fields-> 
 GetItem("lname")->Value); 
 
 // Ask if the User wants to Update 
 printf("\n\nUse Update to replace the original data with the" 
 " buffered data in the Recordset? (y/n): "); 
 char chKey = getch(); 
 
 if(toupper(chKey) == 'Y') 
 pRstEmployees->Update(); 
 else 
 pRstEmployees->CancelUpdate(); 
 
 //Open an IADORecordBinding interface pointer which 
 //we'll use for binding Recordset to a class. 
 TESTHR(pRstEmployees->QueryInterface( 
 __uuidof(IADORecordBinding),(LPVOID*)&picRs)); 
 
 //Bind the Recordset to a C++ Class here. 
 TESTHR(picRs->BindToRecordset(&emprs)); 
 
 pRstEmployees->MoveFirst(); 
 
 // Show the resulting data. 
 printf("\nData in recordset = %s %s", emprs.le_fnameStatus == 
 adFldOK ? emprs.m_sze_fname : "<NULL>", 
 emprs.le_lnameStatus == adFldOK ? 
 emprs.m_sze_lname : "<NULL>"); 
 
 // Restore original data because this is a demonstration. 
 if ((strcmp((char *)strOldFirst,emprs.m_sze_fname) && 
 strcmp((char *)strOldLast,emprs.m_sze_lname))) 
 { 
 pRstEmployees->Fields->GetItem("fname")->Value = strOldFirst; 
 pRstEmployees->Fields->GetItem("lname")->Value = strOldLast; 
 pRstEmployees->Update(); 
 } 
 } 
 catch(_com_error &e) 
 { 
 // Notify the user of errors if any. 
 // Pass a connection pointer accessed from the Recordset. 
 _variant_t vtConnect = pRstEmployees->GetActiveConnection(); 
 
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
 //Release the IADORecordset Interface here 
 if (picRs) 
 picRs->Release(); 
 
 if (pRstEmployees) 
 if (pRstEmployees->State == adStateOpen) 
 pRstEmployees->Close(); 
} 
 
// The next example demonstrates the Update method 
// in conjunction with the AddNew method. 
 
////////////////////////////////////////////////////////// 
// // 
// UpdateX2 Function // 
// // 
////////////////////////////////////////////////////////// 
void UpdateX2(void) 
{ 
 HRESULT hr = S_OK; 
 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace. 
 _ConnectionPtr pConnection = NULL; 
 _RecordsetPtr pRstEmployees = NULL; 
 
 // Define string variables. 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 
 IADORecordBinding *picRs = NULL; // Interface Pointer declared 
 CEmployeeRs1 emprs; // C++ Class object. 
 
 try 
 { 
 // Open a connection. 
 TESTHR(pConnection.CreateInstance(__uuidof(Connection))); 
 pConnection->Open(strCnn,"","",NULL); 
 
 // Open recordset with data from Employee table. 
 TESTHR(pRstEmployees.CreateInstance(__uuidof(Recordset))); 
 pRstEmployees->CursorType = adOpenKeyset; 
 pRstEmployees->LockType = adLockOptimistic; 
 pRstEmployees->Open("employee", 
 _variant_t((IDispatch*)pConnection,true), 
 adOpenKeyset, adLockOptimistic,adCmdTable); 
 
 pRstEmployees->AddNew(); 
 _bstr_t strEmpID = "B-S55555M"; 
 pRstEmployees->Fields->GetItem("emp_id")->Value = strEmpID; 
 pRstEmployees->Fields->GetItem("fname")->Value = 
 (_bstr_t) ("Bill"); 
 pRstEmployees->Fields->GetItem("lname")->Value = 
 (_bstr_t) ("Sornsin"); 
 
 // Show contents of buffer and get user input. 
 printf("\n\nAddNew in progress:\n\n"); 
 
 printf("Data in buffer = %s , %s %s", 
 (LPSTR) (_bstr_t) pRstEmployees->Fields-> 
 GetItem("emp_id")->Value, 
 (LPSTR) (_bstr_t) pRstEmployees->Fields-> 
 GetItem("fname")->Value, 
 (LPSTR) (_bstr_t) pRstEmployees->Fields-> 
 GetItem("lname")->Value); 
 
 printf("\n\nUse Update to save buffer to recordset?(y/n):"); 
 char chKey = getch(); 
 
 if(toupper(chKey) == 'Y') 
 { 
 pRstEmployees->Update(); 
 
 //Open an IADORecordBinding interface pointer which 
 //we'll use for binding Recordset to a class. 
 TESTHR(pRstEmployees->QueryInterface( 
 __uuidof(IADORecordBinding),(LPVOID*)&picRs)); 
 
 //Bind the Recordset to a C++ Class here 
 TESTHR(picRs->BindToRecordset(&emprs)); 
 
 // Go to the new record and show the resulting data. 
 printf ("\n\nData in recordset = %s , %s %s", 
 emprs.le_empidStatus == adFldOK ? 
 emprs.m_sze_empid : "<NULL>", 
 emprs.le_fnameStatus == adFldOK ? 
 emprs.m_sze_fname : "<NULL>", 
 emprs.le_lnameStatus == adFldOK ? 
 emprs.m_sze_lname : "<NULL>"); 
 } 
 else 
 { 
 pRstEmployees->CancelUpdate(); 
 printf("\n\nNo new record added.\n"); 
 } 
 // Delete new data because this is a demonstration. 
 _bstr_t strSQLDelete("DELETE FROM employee WHERE emp_id = '" + 
 strEmpID + "'"); 
 pConnection->Execute(strSQLDelete ,NULL,adExecuteNoRecords); 
 } 
 
 catch(_com_error &e) 
 { 
 // Notify the user of errors if any. 
 // Pass a connection pointer accessed from the Connection. 
 PrintProviderError(pConnection); 
 PrintComError(e); 
 } 
 
 // Clean up objects before exit. 
 //Release the IADORecordset Interface here 
 if (picRs) 
 picRs->Release(); 
 
 if (pRstEmployees) 
 if (pRstEmployees->State == adStateOpen) 
 pRstEmployees->Close(); 
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
// EndUpdateCpp 
```

**UpdateX.h**

``` 
 
// BeginUpdateH 
#include "icrsint.h" 
 
//This Class extracts only fname,lname from employee table. 
class CEmployeeRs : public CADORecordBinding 
{ 
BEGIN_ADO_BINDING(CEmployeeRs) 
 // fname is the 1st field in the recordset 
 ADO_VARIABLE_LENGTH_ENTRY2(1, adVarChar, m_sze_fname, 
 sizeof(m_sze_fname), le_fnameStatus, FALSE) 
 // lname is the 2nd field in the recordset. 
 ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_sze_lname, 
 sizeof(m_sze_lname), le_lnameStatus, FALSE) 
 
END_ADO_BINDING() 
 
public: 
 CHAR m_sze_lname[31]; 
 ULONG le_lnameStatus; 
 CHAR m_sze_fname[21]; 
 ULONG le_fnameStatus; 
}; 
 
//This Class extracts only empid,fname,lname,from employee table. 
class CEmployeeRs1 : public CADORecordBinding 
{ 
BEGIN_ADO_BINDING(CEmployeeRs1) 
 // emp_id is the 1st field in the table. 
 ADO_VARIABLE_LENGTH_ENTRY2(1, adVarChar, m_sze_empid, 
 sizeof(m_sze_empid), le_empidStatus, FALSE) 
 // fname is the 2nd field in the table. 
 ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_sze_fname, 
 sizeof(m_sze_fname), le_fnameStatus, FALSE) 
 // lname is the 4rt field in the table. 
 ADO_VARIABLE_LENGTH_ENTRY2(4, adVarChar, m_sze_lname, 
 sizeof(m_sze_lname), le_lnameStatus, FALSE) 
 
END_ADO_BINDING() 
 
public: 
 CHAR m_sze_empid[10]; 
 ULONG le_empidStatus; 
 CHAR m_sze_lname[31]; 
 ULONG le_lnameStatus; 
 CHAR m_sze_fname[21]; 
 ULONG le_fnameStatus; 
}; 
// EndUpdateH 
```

