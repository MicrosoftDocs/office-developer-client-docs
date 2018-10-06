---
title: Open and Close Methods Example (VC++)
TOCTitle: Open and Close Methods Example (VC++)
ms:assetid: 34493c4d-a60a-96b3-b94b-f93e306a66a7
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249112(v=office.15)
ms:contentKeyID: 48544132
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Open and Close Methods Example (VC++)


**Applies to**: Access 2013 | Office 2013

This example uses the **Open** and [Close](close-method-ado.md) methods on both [Recordset](recordset-object-ado.md) and [Connection](connection-object-ado.md) objects that have been opened.

```cpp 
 
// BeginOpenCpp 
#import "C:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
#include <oledb.h> 
#include <stdio.h> 
#include <conio.h> 
#include "OpenX.h" 
 
// Function declarations 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void OpenX(void); 
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
 
 OpenX(); 
 
 ::CoUninitialize(); 
} 
 
/////////////////////////////////////////////////////////// 
// // 
// OpenX Function // 
// // 
/////////////////////////////////////////////////////////// 
 
void OpenX(void) 
{ 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace 
 _RecordsetPtr pRstEmployee = NULL; 
 _ConnectionPtr pConnection = NULL; 
 
 // Define string variables. 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 
 // Define Other Variables. 
 HRESULT hr = S_OK; 
 IADORecordBinding *picRs = NULL; // Interface Pointer declared. 
 CEmployeeRs emprs; // C++ Class object 
 DBDATE varDate; 
 
 try 
 { 
 // open connection and record set 
 TESTHR(pConnection.CreateInstance(__uuidof(Connection))); 
 pConnection->Open(strCnn,"","",adConnectUnspecified); 
 
 TESTHR(pRstEmployee.CreateInstance(__uuidof(Recordset))); 
 pRstEmployee->Open("Employee", 
 _variant_t((IDispatch *)pConnection,true), adOpenKeyset, 
 adLockOptimistic, adCmdTable); 
 
 // Open an IADORecordBinding interface pointer which we'll 
 // use for Binding Recordset to a class. 
 TESTHR(pRstEmployee->QueryInterface( 
 __uuidof(IADORecordBinding),(LPVOID*)&picRs)); 
 
 //Bind the Recordset to a C++ Class here. 
 TESTHR(picRs->BindToRecordset(&emprs)); 
 
 // Assign the first employee record's hire date 
 // to a variable, then change the hire date. 
 varDate = emprs.m_sze_hiredate; 
 printf("\nOriginal data\n"); 
 printf("\tName - Hire Date\n"); 
 printf(" %s %s - %d/%d/%d\n\n", 
 emprs.le_fnameStatus == adFldOK ? 
 emprs.m_sze_fname : "<NULL>", 
 emprs.le_lnameStatus == adFldOK ? 
 emprs.m_sze_lname : "<NULL>", 
 emprs.le_hiredateStatus == adFldOK ? 
 emprs.m_sze_hiredate.month : 0, 
 emprs.le_hiredateStatus == adFldOK ? 
 emprs.m_sze_hiredate.day : 0, 
 emprs.le_hiredateStatus == adFldOK ? 
 emprs.m_sze_hiredate.year : 0); 
 
 emprs.m_sze_hiredate.year=1900; 
 emprs.m_sze_hiredate.month=1; 
 emprs.m_sze_hiredate.day=1; 
 picRs->Update(&emprs); 
 
 printf("\nChanged data\n"); 
 printf("\tName - Hire Date\n"); 
 printf(" %s %s - %d/%d/%d\n\n", 
 emprs.le_fnameStatus == adFldOK ? 
 emprs.m_sze_fname : "<NULL>", 
 emprs.le_lnameStatus == adFldOK ? 
 emprs.m_sze_lname : "<NULL>", 
 emprs.le_hiredateStatus == adFldOK ? 
 emprs.m_sze_hiredate.month : 0, 
 emprs.le_hiredateStatus == adFldOK ? 
 emprs.m_sze_hiredate.day : 0, 
 emprs.le_hiredateStatus == adFldOK ? 
 emprs.m_sze_hiredate.year : 0); 
 
 // Requery Recordset and reset the hire date. 
 pRstEmployee->Requery(adOptionUnspecified); 
 // Open an IADORecordBinding interface pointer which we'll 
 // use for Binding Recordset to a class. 
 TESTHR(pRstEmployee->QueryInterface( 
 __uuidof(IADORecordBinding),(LPVOID*)&picRs)); 
 
 // Rebind the Recordset to a C++ Class here. 
 TESTHR(picRs->BindToRecordset(&emprs)); 
 emprs.m_sze_hiredate = varDate; 
 picRs->Update(&emprs); 
 printf("\nData after reset\n"); 
 printf("\tName - Hire Date\n"); 
 printf(" %s %s - %d/%d/%d",emprs.le_fnameStatus == adFldOK ? 
 emprs.m_sze_fname : "<NULL>", 
 emprs.le_lnameStatus == adFldOK ? 
 emprs.m_sze_lname : "<NULL>", 
 emprs.le_hiredateStatus == adFldOK ? 
 emprs.m_sze_hiredate.month : 0, 
 emprs.le_hiredateStatus == adFldOK ? 
 emprs.m_sze_hiredate.day : 0, 
 emprs.le_hiredateStatus == adFldOK ? 
 emprs.m_sze_hiredate.year : 0); 
 } 
 catch(_com_error &e) 
 { 
 // Notify the user of errors if any. 
 // Pass a connection pointer accessed from the Connection. 
 PrintProviderError(pConnection); 
 PrintComError(e); 
 } 
 
 // Clean up objects before exit. 
 if (pRstEmployee) 
 if (pRstEmployee->State == adStateOpen) 
 pRstEmployee->Close(); 
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
// EndOpenCpp 
```

**OpenX.h**

```cpp 
 
// BeginOpenH 
#include "icrsint.h" 
 
// This Class extracts only fname,lastname and 
// hire_date from employee table 
class CEmployeeRs : public CADORecordBinding 
{ 
 
BEGIN_ADO_BINDING(CEmployeeRs) 
 
 // Column fname is the 2nd field in the table 
 ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_sze_fname, 
 sizeof(m_sze_fname), le_fnameStatus, FALSE) 
 
 // Column lname is the 4th field in the table. 
 ADO_VARIABLE_LENGTH_ENTRY2(4, adVarChar, m_sze_lname, 
 sizeof(m_sze_lname), le_lnameStatus, FALSE) 
 
 // Column hiredate is the 8th field in the table. 
 ADO_VARIABLE_LENGTH_ENTRY2(8, adDBDate,m_sze_hiredate, 
 sizeof(m_sze_hiredate), le_hiredateStatus, TRUE) 
 
END_ADO_BINDING() 
 
public: 
 CHAR m_sze_fname[21]; 
 ULONG le_fnameStatus; 
 CHAR m_sze_lname[31]; 
 ULONG le_lnameStatus; 
 DBDATE m_sze_hiredate; 
 ULONG le_hiredateStatus; 
}; 
// EndOpenH 
```

