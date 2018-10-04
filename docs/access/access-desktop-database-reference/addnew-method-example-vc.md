﻿---
title: AddNew Method Example (VC++)
TOCTitle: AddNew Method Example (VC++)
ms:assetid: 137cdc3e-2def-36e4-b71d-625fdf0147c1
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248909(v=office.15)
ms:contentKeyID: 48543370
ms.date: 09/18/2015
mtps_version: v=office.15
---

# AddNew Method Example (VC++)


**Applies to**: Access 2013 | Office 2013

This example uses the [AddNew](addnew-method-ado.md) method to create a new record with the specified name.

``` 
 
// Note: When adding the record. You need to get the data from the user 
// The employee id must be formatted as first,middle and last initial, 
// five numbers,then M or F to signify the gender.For example,the 
// employee id for Bill A. Sorensen would be "BAS55555M". 
 
// BeginAddNewCpp 
#import "C:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
 
#include <ole2.h> 
#include <stdio.h> 
#include "conio.h" 
#include "AddNewX.h" 
 
//Function declaration 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void AddNewX(VOID); 
void PrintProviderError(_ConnectionPtr pConnection); 
inline int myscanf(char* strDest, int n) 
{ 
 char strExBuff[10]; 
 char* pstrRet = fgets(strDest, n, stdin); 
 
 if (pstrRet == NULL) 
 return 0; 
 
 if (!strrchr(strDest, '\n')) 
 // Exhaust the input buffer. 
 do 
 { 
 fgets(strExBuff, sizeof(strExBuff), stdin); 
 }while (!strrchr(strExBuff, '\n')); 
 else 
 // Replace '\n' with '\0' 
 strDest[strrchr(strDest, '\n') - strDest] = '\0'; 
 
 return strlen(strDest); 
} 
 
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
 
 if (SUCCEEDED(hr)) 
 { 
 AddNewX(); 
 
 //Wait here for the user to see the output 
 printf("Press any key to continue..."); 
 getch(); 
 
 ::CoUninitialize(); 
 } 
} 
 
 
/////////////////////////////////////////////////////////// 
// // 
// AddNewX Function // 
// // 
/////////////////////////////////////////////////////////// 
VOID AddNewX(VOID) 
{ 
 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 _RecordsetPtr pRstEmployees = NULL; 
 _ConnectionPtr pConnection = NULL; 
 
 //Define Other variables 
 IADORecordBinding *picRs = NULL; //Interface Pointer declared.(VC++ Extensions) 
 CEmployeeRs emprs; //C++ class object 
 
 HRESULT hr = S_OK; 
 
 //Replace Data Source value with your server name. 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 _bstr_t strId; 
 _bstr_t strMessage; 
 
 try 
 { 
 //Open a connection 
 TESTHR(pConnection.CreateInstance(__uuidof(Connection))); 
 pConnection->Open(strCnn,"","",adConnectUnspecified); 
 
 //Open employee table 
 TESTHR(pRstEmployees.CreateInstance(__uuidof(Recordset))); 
 
 //You have to explicitly pass the Cursor type and LockType to the Recordset here 
 pRstEmployees->Open("employee",_variant_t((IDispatch *) pConnection, true), 
 adOpenKeyset,adLockOptimistic,adCmdTable); 
 
 
 //Open an IADORecordBinding interface pointer which we'll use for Binding 
 //Recordset to a class 
 TESTHR(pRstEmployees->QueryInterface(__uuidof(IADORecordBinding),(LPVOID*)&picRs)); 
 
 
 //Bind the Recordset to a C++ Class here 
 TESTHR(picRs->BindToRecordset(&emprs)); 
 
 // Get data from the user.The employee id must be formatted as 
 // first,middle and last initial,five numbers,then M or F to 
 // signify the gender.For example,the employee id for 
 // Bill A. Sorensen would be "BAS55555M". 
 
 printf("Enter Employee Id: "); 
 myscanf(emprs.m_sz_empid, sizeof(emprs.m_sz_empid)); 
 strId = emprs.m_sz_empid; 
 printf("Enter First Name: "); 
 myscanf(emprs.m_sz_fname, sizeof(emprs.m_sz_fname)); 
 printf("Enter Last Name:"); 
 myscanf(emprs.m_sz_lname, sizeof(emprs.m_sz_lname)); 
 
 //Proceed if the user actually entered some thing 
 //for the id, the first and the last name. 
 
 if(strcmp(emprs.m_sz_empid,"") && strcmp(emprs.m_sz_fname,"") && 
 strcmp(emprs.m_sz_lname,"")) 
 { 
 //This adds a new record to the table 
 //if (FAILED(hr = picRs->AddNew(&emprs))) 
 //_com_issue_error(hr); 
 TESTHR(picRs->AddNew(&emprs)); 
 
 //Show the newly added data 
 printf("New Record: %s %s %s \n", emprs.lemp_empidStatus == adFldOK ? emprs.m_sz_empid : "<NULL>", emprs.lemp_fnameStatus == adFldOK ? emprs.m_sz_fname : "<NULL>", emprs.lemp_lnameStatus == adFldOK ? emprs.m_sz_lname : "<NULL>"); 
 } 
 else 
 printf("Please enter an employee id, first name and last name.\n"); 
 
 //Delete the new record because this is a demonstration. 
 pConnection->Execute("DELETE FROM EMPLOYEE WHERE emp_id = '"+strId+"'", 
 NULL,adCmdText); 
 } 
 catch(_com_error &e) 
 { 
 // Notify the user of errors if any. 
 _variant_t vtConnect = pRstEmployees->GetActiveConnection(); 
 
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
 
 if (pRstEmployees) 
 if (pRstEmployees->State == adStateOpen) 
 pRstEmployees->Close(); 
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
 printf("\n\t Error number: %x\t%s", pErr->Number, (LPCSTR)pErr->Description); 
 } 
 } 
} 
// EndAddNewCpp 
```

**AddNewX.h**

``` 
 
// BeginAddNewH 
#include "icrsint.h" 
 
 
//This Class extracts empid, fname and lastname 
 
class CEmployeeRs : public CADORecordBinding 
{ 
BEGIN_ADO_BINDING(CEmployeeRs) 
 
 //Column empid is the 1st field in the recordset 
 
 ADO_VARIABLE_LENGTH_ENTRY2(1, adVarChar, m_sz_empid, 
 sizeof(m_sz_empid), lemp_empidStatus, TRUE) 
 
 ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_sz_fname, 
 sizeof(m_sz_fname), lemp_fnameStatus, TRUE) 
 
 ADO_VARIABLE_LENGTH_ENTRY2(4, adVarChar, m_sz_lname, 
 sizeof(m_sz_lname), lemp_lnameStatus, TRUE) 
 
END_ADO_BINDING() 
 
public: 
 
 CHAR m_sz_empid[10]; 
 ULONG lemp_empidStatus; 
 CHAR m_sz_fname[40]; 
 ULONG lemp_fnameStatus; 
 CHAR m_sz_lname[41]; 
 ULONG lemp_lnameStatus; 
 
}; 
// EndAddNewH 
```

