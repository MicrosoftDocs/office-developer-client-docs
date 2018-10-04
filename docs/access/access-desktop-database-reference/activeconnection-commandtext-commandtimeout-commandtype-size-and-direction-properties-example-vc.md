---
title: ActiveConnection, CommandText, CommandTimeout, CommandType, Size, and Direction Properties Example (VC++)
TOCTitle: ActiveConnection, CommandText, CommandTimeout, CommandType, Size, and Direction Properties Example (VC++)
ms:assetid: 254e6d48-fc07-1df0-215c-a91141238985
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249021(v=office.15)
ms:contentKeyID: 48543780
ms.date: 09/18/2015
mtps_version: v=office.15
---

# ActiveConnection, CommandText, CommandTimeout, CommandType, Size, and Direction Properties Example (VC++)


_**Applies to:** Access 2013 | Office 2013_

This example uses the [ActiveConnection](activeconnection-property-ado.md), [CommandText](commandtext-property-ado.md), [CommandTimeout](commandtimeout-property-ado.md), [CommandType](commandtype-property-ado.md), [Size](size-property-ado.md), and [Direction](direction-property-ado.md) properties to execute a stored procedure.

``` 
 
// BeginActiveConnectionCpp 
#import "C:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
#define TESTHR(x) if FAILED(x) _com_issue_error(x) 
 
#include <stdio.h> 
#include <ole2.h> 
#include "conio.h" 
#include "ActiveConnectionX.h" 
 
//Function declaration 
void ActiveConnectionX(VOID); 
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
 
 ActiveConnectionX(); 
 
 //Wait here for user to see the output.. 
 printf("\n\nPress any key to continue.."); 
 getch(); 
 
 ::CoUninitialize(); 
} 
 
 
 
/////////////////////////////////////////////////////////// 
// // 
// ActiveConnectionX Function // 
// // 
/////////////////////////////////////////////////////////// 
VOID ActiveConnectionX(VOID) 
{ 
 HRESULT hr = S_OK; 
 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace. 
 _ConnectionPtr pConnection = NULL; 
 _CommandPtr pCmdByRoyalty = NULL; 
 _RecordsetPtr pRstByRoyalty = NULL; 
 _RecordsetPtr pRstAuthors = NULL; 
 _ParameterPtr pPrmByRoyalty = NULL; 
 
 
 //Define Other variables 
 IADORecordBinding *picRs = NULL; //Interface Pointer declared.(VC++ Extensions) TCS(SPA) 
 CEmployeeRs emprs; //C++ class object TCS(SPA) 
 _bstr_t strAuthorId; 
 int intRoyalty; 
 VARIANT vtroyal ; 
 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 
 try 
 { 
 //Define a command object for a stored procedure. 
 
 TESTHR(pConnection.CreateInstance(__uuidof(Connection))); 
 hr = pConnection->Open(strCnn,"","",adConnectUnspecified); 
 
 TESTHR(pCmdByRoyalty.CreateInstance(__uuidof(Command))); 
 
 pCmdByRoyalty->ActiveConnection = pConnection; 
 pCmdByRoyalty->CommandText = "byRoyalty"; 
 pCmdByRoyalty->CommandType = adCmdStoredProc; 
 pCmdByRoyalty->CommandTimeout = 15; 
 
 //Define stored procedure's input parameter. 
 printf("Enter Royalty : "); 
 scanf("%d",&intRoyalty); 
 
 //Assign Integer value 
 vtroyal.vt = VT_I2; 
 vtroyal.iVal = intRoyalty; 
 
 TESTHR(pPrmByRoyalty.CreateInstance(__uuidof(Parameter))); 
 pPrmByRoyalty->Type = adInteger; 
 pPrmByRoyalty->Size = 3; 
 pPrmByRoyalty->Direction = adParamInput; 
 pPrmByRoyalty->Value = vtroyal; 
 pCmdByRoyalty->Parameters->Append(pPrmByRoyalty); 
 
 //Create a recordset by executing a command. 
 pRstByRoyalty = pCmdByRoyalty->Execute(NULL,NULL,adCmdStoredProc); 
 
 //Open the authors table to get author names for display. 
 
 TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset))); 
 hr = pRstAuthors->Open("authors",strCnn,adOpenForwardOnly,adLockReadOnly,adCmdTable); 
 
 //Open an IADORecordBinding interface pointer which we'll use for Binding Recordset to a class 
 TESTHR(pRstAuthors->QueryInterface(__uuidof(IADORecordBinding),(LPVOID*)&picRs)); 
 
 //Bind the Recordset to a C++ Class here 
 TESTHR(picRs->BindToRecordset(&emprs)); 
 
 
 //Print current data in the recordset ,adding author names from author table. 
 printf("Authors With %d Percent Royalty",intRoyalty); 
 
 while(!(pRstByRoyalty->EndOfFile)) 
 { 
 strAuthorId = pRstByRoyalty->Fields->Item["au_id"]->Value; 
 pRstAuthors->Filter = "au_id = '"+strAuthorId+"'"; 
 
 printf("\n\t%s, %s %s",emprs.lau_idStatus == adFldOK ? emprs.m_szau_id : "<NULL>", emprs.lau_fnameStatus == adFldOK ? emprs.m_szau_fname : "<NULL>", emprs.lau_lnameStatus == adFldOK ? emprs.m_szau_lname : "<NULL>"); 
 
 pRstByRoyalty->MoveNext(); 
 } 
 } 
 catch(_com_error &e) 
 { 
 // Notify the user of errors if any. 
 _bstr_t bstrSource(e.Source()); 
 _bstr_t bstrDescription(e.Description()); 
 
 PrintProviderError(pConnection); 
 printf("Source : %s \n Description : %s \n",(LPCSTR)bstrSource,(LPCSTR)bstrDescription); 
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
 printf("Error number: %x\t%s", pErr->Number,(LPCSTR)pErr->Description); 
 } 
 } 
} 
 
// EndActiveConnectionCpp 
```

**ActiveConnectionX.h**

``` 
 
// BeginActiveConnectionH 
#include "icrsint.h" 
 
 
//This Class extracts fname,lastname 
 
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
// EndActiveConnectionH 
```

