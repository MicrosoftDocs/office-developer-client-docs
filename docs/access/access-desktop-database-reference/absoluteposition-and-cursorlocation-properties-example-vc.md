---
title: AbsolutePosition and CursorLocation Properties Example (VC++)
TOCTitle: AbsolutePosition and CursorLocation Properties Example (VC++)
ms:assetid: a1ae63dd-296b-09b0-a898-091b855e3141
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249745(v=office.15)
ms:contentKeyID: 48546739
ms.date: 09/18/2015
mtps_version: v=office.15
---

# AbsolutePosition and CursorLocation Properties Example (VC++)


**Applies to**: Access 2013 | Office 2013

This example demonstrates how the [AbsolutePosition](absoluteposition-property-ado.md) property can track the progress of a loop that enumerates all the records of a [Recordset](recordset-object-ado.md). It uses the [CursorLocation](cursorlocation-property-ado.md) property to enable the **AbsolutePosition** property by setting the cursor to a client cursor.

``` 
 
// BeginAbsolutePositionCpp 
#import "C:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
#include <ole2.h> 
#include <stdio.h> 
#include "conio.h" 
#include "AbsolutePositionX.h" 
 
//Function Declarations 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void AbsolutePositionX(void); 
void AbsolutePosition2X(void); 
void PrintProviderError(_ConnectionPtr pConnection); 
 
/////////////////////////////////////////////////////////// 
// // 
// Main Function // 
// // 
/////////////////////////////////////////////////////////// 
void main() 
{ 
 if(FAILED(::CoInitialize(NULL))) 
 return; 
 
 AbsolutePositionX(); 
 
 
 //Clear the screen for the next display 
 printf("Press any key to continue..."); 
 getch(); 
 system("cls"); 
 
 AbsolutePosition2X(); 
 
 ::CoUninitialize(); 
} 
 
/////////////////////////////////////////////////////////// 
// // 
// AbsolutePositionX Function // 
// // 
/////////////////////////////////////////////////////////// 
 
void AbsolutePositionX(void) 
{ 
 HRESULT hr = S_OK; 
 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace. 
 _RecordsetPtr pRstEmployees = NULL; 
 
 //Define Other Variables 
 //Interface Pointer declared.(VC++ Extensions) 
 IADORecordBinding *picRs = NULL; 
 CEmployeeRs emprs; //C++ class object 
 _bstr_t strMessage; 
 char chKey; 
 
 //Open a recordset using a Client Cursor 
 //For the Employee Table 
 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 
 try 
 { 
 //Open a recordset. 
 TESTHR(pRstEmployees.CreateInstance(__uuidof(Recordset))); 
 
 //Use client cursor to enable Absoluteposition property. 
 pRstEmployees->CursorLocation = adUseClient; 
 
 //You have to explicitly pass the default Cursor type 
 //and LockType to the Recordset. 
 TESTHR( pRstEmployees->Open("employee", 
 strCnn,adOpenForwardOnly,adLockReadOnly,adCmdTable)); 
 
 // Open an IADORecordBinding interface pointer which we'll use 
 // for Binding Recordset to a class. 
 TESTHR(pRstEmployees->QueryInterface( 
 __uuidof(IADORecordBinding),(LPVOID*)&picRs)); 
 
 //Bind the Recordset to a C++ Class here 
 TESTHR(picRs->BindToRecordset(&emprs)); 
 
 strMessage= ""; 
 
 //Enumerate recordset 
 do 
 { 
 //Display Current Record Information 
 printf("Employee : %s \n record %ld of %d", 
 emprs.lau_lnameStatus == adFldOK ? 
 emprs.m_szau_lname : "<NULL>", 
 pRstEmployees->AbsolutePosition, 
 pRstEmployees->RecordCount); 
 
 printf("\nContinue?(y/n) :"); 
 
 do 
 { 
 chKey = getch(); 
 }while(chKey != 'y' && chKey !='n'); 
 
 //Clear the Screen for the next output 
 system("cls"); 
 
 if(chKey == 'n') 
 break; 
 
 strMessage = ""; 
 pRstEmployees->MoveNext(); 
 }while(!(pRstEmployees->EndOfFile)); 
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
} 
 
 
/////////////////////////////////////////////////////////// 
// // 
// AbsolutePosition2X Function // 
// // 
/////////////////////////////////////////////////////////// 
 
void AbsolutePosition2X(void) 
{ 
 HRESULT hr = S_OK; 
 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace. 
 _RecordsetPtr pRstEmployees = NULL; 
 
 //Define Other Variables 
 //Interface Pointer declared.(VC++ Extensions) 
 IADORecordBinding *picRs = NULL; 
 CEmployeeRs emprs; //C++ class object 
 _bstr_t strMessage; 
 
 //Open a recordset using a Client Cursor 
 //For the Employee Table 
 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 
 try 
 { 
 //Open a recordset. 
 TESTHR(pRstEmployees.CreateInstance(__uuidof(Recordset))); 
 
 //Use client cursor to enable Absoluteposition property. 
 pRstEmployees->CursorLocation = adUseClient; 
 
 //You have to explicitly pass the default Cursor type 
 //and LockType to the Recordset. 
 TESTHR(pRstEmployees->Open("employee", 
 strCnn,adOpenStatic,adLockReadOnly,adCmdTable)); 
 
 // Open an IADORecordBinding interface pointer which we'll use 
 // for Binding Recordset to a class. 
 TESTHR(pRstEmployees->QueryInterface( 
 __uuidof(IADORecordBinding),(LPVOID*)&picRs)); 
 
 //Bind the Recordset to a C++ Class here 
 TESTHR(picRs->BindToRecordset(&emprs)); 
 
 long lGoToPos = 21; 
 
 pRstEmployees->AbsolutePosition = (PositionEnum)lGoToPos; 
 
 //Display Current Record Information 
 printf("Employee : %s \n record %ld of %d", 
 emprs.lau_lnameStatus == adFldOK ? emprs.m_szau_lname : "<NULL>", pRstEmployees->AbsolutePosition, 
 pRstEmployees->RecordCount); 
 
 printf("\nPress any key to continue:"); 
 getch(); 
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
 long nCount = 0; 
 long i = 0; 
 
 if( (pConnection->Errors->Count) > 0) 
 { 
 nCount = pConnection->Errors->Count; 
 // Collection ranges from 0 to nCount -1. 
 for(i = 0; i < nCount; i++) 
 { 
 pErr = pConnection->Errors->GetItem(i); 
 printf("\t Error number: %x\t%s", 
 pErr->Number,(LPCSTR) pErr->Description); 
 } 
 } 
} 
 
// EndAbsolutePositionCpp 
```

**AbsolutePositionX.h**

``` 
 
// BeginAbsolutePositionH 
#include <ole2.h> 
#include <stdio.h> 
#include "icrsint.h" 
 
 
//This Class extracts lastname. 
 
class CEmployeeRs : public CADORecordBinding 
{ 
BEGIN_ADO_BINDING(CEmployeeRs) 
 
 //Column lname is the 4th field in the recordset 
 
 ADO_VARIABLE_LENGTH_ENTRY2(4, adVarChar, m_szau_lname, 
 sizeof(m_szau_lname), lau_lnameStatus, TRUE) 
 
END_ADO_BINDING() 
 
public: 
 CHAR m_szau_lname[41]; 
 ULONG lau_lnameStatus; 
 
}; 
// EndAbsolutePositionH 
```

