---
title: Attributes and Name Properties Example (VC++)
TOCTitle: Attributes and Name Properties Example (VC++)
ms:assetid: 612b7d4a-b92d-5afd-eeaa-28d7ad1a880a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249356(v=office.15)
ms:contentKeyID: 48545203
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Attributes and Name Properties Example (VC++)


**Applies to**: Access 2013 | Office 2013

This example displays the value of the [Attributes](attributes-property-ado.md) property for [Connection](connection-object-ado.md), [Field](field-object-ado.md), and [Property](property-object-ado.md) objects. It uses the [Name](name-property-ado.md) property to display the name of each **Field** and **Property** object.

``` 
 
// BeginAttributesCpp 
#import "C:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
#include <ole2.h> 
#include <stdio.h> 
#include <conio.h> 
 
// Function declarations 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void AttributesX(); 
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
 
 AttributesX(); 
 
 //Wait here for user to see the output.. 
 printf("\nPress any key to continue..."); 
 getch(); 
 
 ::CoUninitialize(); 
} 
 
 
/////////////////////////////////////////////////////////// 
// // 
// AttributesX Function // 
// // 
/////////////////////////////////////////////////////////// 
 
void AttributesX() 
{ 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace 
 _RecordsetPtr pRstEmployee = NULL; 
 _ConnectionPtr pConnection = NULL; 
 FieldsPtr fldLoop = NULL; 
 PropertiesPtr proLoop = NULL; 
 
 //Define Other Variables 
 HRESULT hr = S_OK; 
 _variant_t Index; 
 Index.vt = VT_I2; 
 int j=0; 
 //Open a recordset using a Client Cursor 
 //For the Employee Table 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 
 try 
 { 
 // open connection and record set 
 TESTHR(pConnection.CreateInstance(__uuidof(Connection))); 
 pConnection->Open(strCnn,"","",adConnectUnspecified); 
 
 TESTHR(pRstEmployee.CreateInstance(__uuidof(Recordset))); 
 pRstEmployee->Open("Employee", _variant_t((IDispatch *)pConnection,true), adOpenForwardOnly, 
 adLockReadOnly, adCmdTable); 
 
 // Display the attributes of Connection. 
 printf("Connection attributes: %d \n", pConnection->Attributes); 
 
 // Display the attribute of the employee table's 
 //fields 
 printf("\nFields attributes:\n"); 
 fldLoop = pRstEmployee->GetFields(); 
 
 for (int i = 0; i < (int)fldLoop->GetCount(); i++) 
 { 
 Index.iVal=i; 
 printf (" %s = %d \n",(LPSTR)fldLoop->GetItem(Index)->GetName(), 
 (int)fldLoop->GetItem(Index)->GetAttributes()); 
 } 
 
 // Display Fields of the Employee table which are NULLBALE 
 printf("\nNULLABLE Fields :"); 
 
 for (int i1 = 0; i1 < (int)fldLoop->GetCount(); i1++) 
 { 
 Index.iVal = i1; 
 
 if (fldLoop->GetItem(Index)->GetAttributes() & adFldIsNullable) 
 { 
 printf ("%s \n", (LPSTR)fldLoop->GetItem(Index)->GetName()); 
 } 
 } 
 
 // Display the attributes of the Employee tables's 
 // properties 
 printf("\nProperty attributes:\n"); 
 proLoop = pRstEmployee->GetProperties(); 
 
 for (int i2 = 0; i2 < (int)proLoop->GetCount(); i2++) 
 { 
 j= j+1; 
 Index.iVal=i2; 
 printf (" %s = %d \n", (LPSTR)(_bstr_t)proLoop->GetItem(Index)->GetName() 
 ,(int)proLoop->GetItem(Index)->GetAttributes()); 
 
 if (((j % 23) == 0) || ( i2==6)) 
 { 
 printf("\nPress any key to continue..."); 
 getch(); 
 
 //Clear the screen for the next display 
 system("cls"); 
 j=0; 
 } 
 
 } 
 } 
 catch(_com_error &e) 
 { 
 // Notify the user of errors if any. 
 
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
 long nCount = 0; 
 long i = 0; 
 
 if( (pConnection->Errors->Count) > 0) 
 { 
 nCount = pConnection->Errors->Count; 
 
 // Collection ranges from 0 to nCount -1. 
 for(i = 0; i < nCount; i++) 
 { 
 pErr = pConnection->Errors->GetItem(i); 
 printf("\t Error number: %x\t%s", (LPCSTR) pErr->Number, (LPCSTR) pErr->Description); 
 } 
 } 
} 
 
/////////////////////////////////////////////////////////// 
// // 
// PrintComError Function // 
// // 
/////////////////////////////////////////////////////////// 
 
VOID PrintComError(_com_error &e) 
{ 
 _bstr_t bstrSource(e.Source()); 
 _bstr_t bstrDescription(e.Description()); 
 
 // Print Com errors. 
 printf("\nError\n"); 
 printf("Code = %08lx\n", e.Error()); 
 printf("Code meaning = %s\n", e.ErrorMessage()); 
 printf("Source = %s\n", (LPCSTR) bstrSource); 
 printf("Description = %s\n", (LPCSTR) bstrDescription); 
} 
// EndAttributesCpp 
```

**AttributesX.h**

``` 
 
// BeginAttributesH 
#include "icrsint.h" 
 
//This class extracts LastName, FirstName, FaxPhone from Employees table 
 
class CEmployeeRs : public CADORecordBinding 
{ 
BEGIN_ADO_BINDING(CEmployeeRs) 
 
 // Column LastName is the 2nd field in the table 
 ADO_VARIABLE_LENGTH_ENTRY2(2,adVarChar,m_szemp_LastName, 
 sizeof(m_szemp_LastName),lemp_LastNameStatus,TRUE) 
 
 // Column FirstName is the 17th field in the table 
 ADO_VARIABLE_LENGTH_ENTRY2(17,adVarChar,m_szemp_FirstName, 
 sizeof(m_szemp_FirstName),lemp_FirstNameStatus,TRUE) 
 
 // Column FaxPhone is the 18th field in the table 
 ADO_VARIABLE_LENGTH_ENTRY2(18,adVarChar,m_szemp_Faxphone, 
 sizeof(m_szemp_Faxphone),lemp_FaxphoneStatus,TRUE) 
 
END_ADO_BINDING() 
 
public: 
 CHAR m_szemp_LastName[21]; 
 ULONG lemp_LastNameStatus; 
 CHAR m_szemp_FirstName[11]; 
 ULONG lemp_FirstNameStatus; 
 CHAR m_szemp_Faxphone[25]; 
 ULONG lemp_FaxphoneStatus; 
}; 
 
// EndAttributesH 
```

