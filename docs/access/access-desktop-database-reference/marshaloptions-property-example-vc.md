﻿---
title: MarshalOptions Property Example (VC++)
TOCTitle: MarshalOptions Property Example (VC++)
ms:assetid: 8c47eb55-f86d-e4c0-9617-d2ac3c91199f
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249617(v=office.15)
ms:contentKeyID: 48546236
ms.date: 09/18/2015
mtps_version: v=office.15
---

# MarshalOptions Property Example (VC++)


**Applies to**: Access 2013 | Office 2013

This example uses the [MarshalOptions](marshaloptions-property-ado.md) property to specify what rows are sent back to the server — All Rows or only Modified Rows.

``` 
 
// BeginMarshalOptionsCpp 
#import "C:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
#include <stdio.h> 
#include <ole2.h> 
#include <conio.h> 
#include <malloc.h> 
#include "MarshalOptionsX.h" 
 
// Function declarations 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void MarshalOptionsX(void); 
void PrintProviderError(_ConnectionPtr pConnection); 
void PrintComError(_com_error &e); 
 
/////////////////////////////////////////////////////////// 
// // 
// Main Function // 
// // 
/////////////////////////////////////////////////////////// 
 
void main() 
{ 
 if(FAILED(::CoInitialize(NULL))) 
 return; 
 
 MarshalOptionsX(); 
 
 printf("Press any key to continue..."); 
 getch(); 
 ::CoUninitialize(); 
} 
 
/////////////////////////////////////////////////////////// 
// // 
// Marshal Options Function // 
// // 
/////////////////////////////////////////////////////////// 
 
void MarshalOptionsX(void) 
{ 
 
 // Define string variables 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace 
 _RecordsetPtr pRstEmployees = NULL; 
 
 // Define Other Variables 
 IADORecordBinding *picRs = NULL; //Interface Pointer declared 
 CEmployeeRs emprs; //C++ Class Object 
 HRESULT hr = S_OK; 
 LPSTR strOldFirst = NULL; 
 LPSTR strOldLast = NULL; 
 
 try 
 { 
 // Open recordset with names from Employee table. 
 TESTHR(pRstEmployees.CreateInstance(__uuidof(Recordset))); 
 pRstEmployees->CursorType = adOpenKeyset; 
 pRstEmployees->LockType = adLockOptimistic; 
 pRstEmployees->CursorLocation = adUseClient; 
 pRstEmployees->Open("SELECT fname, lname FROM Employee " 
 "ORDER BY lname",strCnn, 
 adOpenKeyset, adLockOptimistic,adCmdText); 
 
 // Open an IADORecordBinding interface pointer which 
 // we'll use for Binding Recordset to a class. 
 TESTHR(pRstEmployees->QueryInterface( 
 __uuidof(IADORecordBinding),(LPVOID*)&picRs)); 
 
 // Bind the Recordset to a C++ Class here. 
 TESTHR(picRs->BindToRecordset(&emprs)); 
 
 // Store Original Data 
 strOldFirst = (LPSTR) malloc(sizeof(emprs.m_szemp_fname)); 
 strOldLast = (LPSTR) malloc(sizeof(emprs.m_szemp_lname)); 
 // Set the final character of the destination string to NULL. 
 strOldFirst[sizeof(emprs.m_szemp_fname)-1] = '\0'; 
 // The source string will get truncated if its length is 
 // longer than the length of the destination string minus one. 
 strncpy(strOldFirst,strtok(emprs.m_szemp_fname," "), 
 sizeof(emprs.m_szemp_fname)-1); 
 // Set the final character of the destination string to NULL. 
 strOldLast[sizeof(emprs.m_szemp_lname)-1] = '\0'; 
 // The source string will get truncated if its length is 
 // longer than the length of the destination string minus one. 
 strncpy(strOldLast,strtok(emprs.m_szemp_lname," "), 
 sizeof(emprs.m_szemp_lname)-1); 
 
 //Change Data in Edit Buffer 
 // Set the final character of the destination string to NULL. 
 emprs.m_szemp_fname[sizeof(emprs.m_szemp_fname)-1] = '\0'; 
 // The source string will get truncated if its length is 
 // longer than the length of the destination string minus one. 
 strncpy(emprs.m_szemp_fname,"Linda",sizeof(emprs.m_szemp_fname)-1); 
 // Set the final character of the destination string to NULL. 
 emprs.m_szemp_lname[sizeof(emprs.m_szemp_lname)-1] = '\0'; 
 // The source string will get truncated if its length is 
 // longer than the length of the destination string minus one. 
 strncpy(emprs.m_szemp_lname,"Kobara",sizeof(emprs.m_szemp_lname)-1); 
 
 // Show contents of buffer and get user input 
 printf("Edit in Progress:\n"); 
 printf("Original Data = %s %s \n",strOldFirst,strOldLast); 
 printf("Data in buffer = %s %s \n", emprs.lemp_fnameStatus == 
 adFldOK ? emprs.m_szemp_fname : "<NULL>", 
 emprs.lemp_lnameStatus == adFldOK ? 
 emprs.m_szemp_lname : "<NULL>"); 
 printf("Use Update to replace the original data with the " 
 "buffered data in the Recordset?\nEnter (y/n) :?"); 
 char opt1=getch(); 
 
 if(toupper(opt1)=='Y') 
 { 
 printf("\nWould you like to send all the rows in " 
 "the recordset back to the server?\nEnter (y/n):"); 
 char opt2 = getch(); 
 if(toupper(opt2) == 'Y') 
 { 
 { 
 pRstEmployees->MarshalOptions = adMarshalAll; 
 picRs->Update(&emprs); 
 } 
 } 
 else 
 { 
 printf("\nWould you like to send only modified " 
 "rows back to the server?\nEnter (y/n):"); 
 char opt3=getch(); 
 if(toupper(opt3) == 'Y') 
 { 
 pRstEmployees->MarshalOptions = 
 adMarshalModifiedOnly; 
 picRs->Update(&emprs); 
 } 
 } 
 } 
 // Show the resulting data 
 printf("\nData In the Recordset = %s %s\n", 
 emprs.lemp_fnameStatus == adFldOK ? 
 emprs.m_szemp_fname : "<NULL>", 
 emprs.lemp_lnameStatus == adFldOK ? 
 emprs.m_szemp_lname : "<NULL>"); 
 
 // Restore original data because this is a demonstration 
 if((strcmp(strOldFirst,emprs.m_szemp_fname)) && 
 (strcmp(strOldLast,emprs.m_szemp_lname))) 
 { 
 // Set the final character of the destination string to NULL. 
 emprs.m_szemp_fname[sizeof(emprs.m_szemp_fname)-1] = '\0'; 
 // The source string will get truncated if its length is 
 // longer than the length of the destination string minus one. 
 strncpy(emprs.m_szemp_fname,strOldFirst, 
 sizeof(emprs.m_szemp_fname)-1); 
 // Set the final character of the destination string to NULL. 
 emprs.m_szemp_lname[sizeof(emprs.m_szemp_lname)-1] = '\0'; 
 // The source string will get truncated if its length is 
 // longer than the length of the destination string minus one. 
 strncpy(emprs.m_szemp_lname,strOldLast, 
 sizeof(emprs.m_szemp_lname)-1); 
 picRs->Update(&emprs); 
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
 // Deallocate memory 
 if (strOldFirst) 
 free(strOldFirst); 
 if (strOldLast) 
 free(strOldLast); 
 
 //Release the IADORecordset Interface here 
 if (picRs) 
 picRs->Release(); 
 
 if (pRstEmployees) 
 if (pRstEmployees->State == adStateOpen) 
 pRstEmployees->Close(); 
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
 for(long i = 0; i < nCount; i++) 
 { 
 pErr = pConnection->Errors->GetItem(i); 
 printf("\t Error number: %x\t%s", pErr->Number, 
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
// EndMarshalOptionsCpp 
```

**MarshalOptionsX.h**

``` 
 
// BeginMarshalOptionsH 
 
#include "icrsint.h" 
 
//This Class extracts only fname,lname from employees table 
class CEmployeeRs : public CADORecordBinding 
{ 
BEGIN_ADO_BINDING(CEmployeeRs) 
 
 //Column fname is the 1st field in the recordset 
 ADO_VARIABLE_LENGTH_ENTRY2(1, adVarChar, m_szemp_fname, 
 sizeof(m_szemp_fname), lemp_fnameStatus, TRUE) 
 
 //Column lname is the 2nd field in the recordset 
 ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_szemp_lname, 
 sizeof(m_szemp_lname), lemp_lnameStatus, TRUE) 
 
END_ADO_BINDING() 
 
public: 
 CHAR m_szemp_fname[21]; 
 ULONG lemp_fnameStatus; 
 CHAR m_szemp_lname[31]; 
 ULONG lemp_lnameStatus; 
}; 
// EndMarshalOptionsH 
```

