﻿---
title: Filter and RecordCount Properties Example (VC++)
TOCTitle: Filter and RecordCount Properties Example (VC++)
ms:assetid: 361499c3-cfb4-a26b-5ed7-5c880ae7d631
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249119(v=office.15)
ms:contentKeyID: 48544161
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Filter and RecordCount Properties Example (VC++)


**Applies to**: Access 2013 | Office 2013

This example uses the [Filter](filter-property-ado.md) property to open a new [Recordset](recordset-object-ado.md) based on a specified condition applied to an existing **Recordset**. It uses the [RecordCount](recordcount-property-ado.md) property to show the number of records in the two **Recordsets**. The FilterField function is required for this procedure to run.

``` 
 
// BeginFilterCpp 
#import "C:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
#include <stdio.h> 
#include <ole2.h> 
#include <conio.h> 
#include "FilterX.h" 
 
// Function declarations 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void FilterX(void); 
_RecordsetPtr FilterField(_RecordsetPtr rstTemp, _bstr_t strField, _bstr_t strFilter); 
void FilterX2(void); 
void PrintProviderError(_ConnectionPtr pCnn1); 
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
 
void main() 
{ 
 HRESULT hr = S_OK; 
 
 if(FAILED(::CoInitialize(NULL))) 
 return; 
 
 FilterX(); 
 
 //Wait here for user to see the output.. 
 printf("\nPress any key to Continue..."); 
 getch(); 
 
 //Clear the screen for the next display 
 system("cls"); 
 
 FilterX2(); 
 
 //Wait here for user to see the output.. 
 printf("\nPress any key to Exit..."); 
 getch(); 
 ::CoUninitialize(); 
} 
 
/////////////////////////////////////////////////////////// 
// // 
// FilterX Function // 
// // 
/////////////////////////////////////////////////////////// 
 
void FilterX() 
{ 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace. 
 _RecordsetPtr rstPublishers = NULL; 
 _RecordsetPtr rstPublishersCountry = NULL; 
 
 //Define Other Variables 
 HRESULT hr = S_OK; 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 int intPublisherCount = 0; 
 long recCount = 0; 
 _bstr_t strCountry; 
 _bstr_t strMessage; 
 char *tempStr; 
 CHAR sz_CountryName[50]; 
 bool boolFlag = TRUE; 
 try 
 { 
 // Open recordset with data from Publishers table. 
 rstPublishers.CreateInstance(__uuidof(Recordset)); 
 rstPublishersCountry.CreateInstance(__uuidof(Recordset)); 
 
 rstPublishers->CursorType = adOpenStatic; 
 
 TESTHR(rstPublishers->Open("publishers",strCnn, 
 adOpenStatic , adLockReadOnly,adCmdTable)); 
 
 // Populate the Recordset. 
 intPublisherCount = rstPublishers->RecordCount; 
 
 // Get user input. 
 printf("Enter a country to filter on:"); 
 mygets(sz_CountryName, 50); 
 
 // Trim the string 
 tempStr = strtok(sz_CountryName, " \t"); 
 strCountry = tempStr; 
 if (tempStr == NULL) 
 { 
 boolFlag = FALSE; 
 } 
 
 if (boolFlag) 
 { 
 if (strcmp(sz_CountryName,"")) 
 { 
 // Open a filtered Recordset object. 
 rstPublishersCountry = FilterField(rstPublishers, 
 "Country", strCountry); 
 recCount = rstPublishersCountry->GetRecordCount(); 
 if (recCount==0) 
 { 
 printf("\nNo publishers from that country.\n"); 
 } 
 else 
 { 
 // Print number of records for the original 
 // Recordset object and the filtered Recordset 
 // object. 
 printf("\nOrders in original recordset:\n%d", 
 intPublisherCount); 
 printf("\nOrders in filtered recordset " 
 "(Country = '%s'): \n%d\n\n", (LPCSTR)strCountry , 
 rstPublishersCountry->RecordCount); 
 } 
 } 
 } 
 } 
 catch(_com_error &e) 
 { 
 // Notify the user of errors if any. 
 _variant_t vtConnect = rstPublishers->GetActiveConnection(); 
 
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
 if (rstPublishers) 
 if (rstPublishers->State == adStateOpen) 
 rstPublishers->Close(); 
 if (rstPublishersCountry) 
 if (rstPublishersCountry->State == adStateOpen) 
 rstPublishersCountry->Close(); 
} 
 
_RecordsetPtr FilterField(_RecordsetPtr rstTemp,_bstr_t strField, 
 _bstr_t strFilter) 
{ 
 // Set a filter on the specified Recordset object and then 
 // open a new Recordset object. 
 rstTemp->Filter = strField + " = '" + strFilter + "'"; 
 return rstTemp; 
} 
 
void FilterX2(void) 
{ 
 _RecordsetPtr rstPublishers; 
 CPublishers publishers; 
 
 //Define Other Variables 
 HRESULT hr = S_OK; 
 IADORecordBinding *picRs = NULL; //Interface Pointer declared... 
 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 try 
 { 
 // Open recordset with data from Publishers table. 
 rstPublishers.CreateInstance(__uuidof(Recordset)); 
 
 rstPublishers->CursorType = adOpenStatic; 
 
 TESTHR(rstPublishers->Open("SELECT * FROM publishers WHERE " 
 "Country='USA'",strCnn,adOpenStatic,adLockReadOnly, 
 adCmdText)); 
 
 //Open an IADORecordBinding interface pointer 
 //which we'll use for Binding Recordset to a class 
 TESTHR(rstPublishers->QueryInterface( 
 __uuidof(IADORecordBinding), (LPVOID*)&picRs)); 
 
 //Bind the Recordset to a C++ Class here 
 TESTHR(picRs->BindToRecordset(&publishers)); 
 
 // Print current data in recordset. 
 rstPublishers->MoveFirst(); 
 
 while (!rstPublishers->EndOfFile) 
 { 
 printf("%s, %s\n", 
 publishers.lP_pubnameStatus == adFldOK ? 
 publishers.m_szP_pubname: "<NULL>", 
 publishers.lP_countryStatus == adFldOK ? 
 publishers.m_szP_country: "<NULL>"); 
 
 rstPublishers->MoveNext(); 
 } 
 } 
 catch (_com_error &e) 
 { 
 // Notify the user of errors if any. 
 _variant_t vtConnect = rstPublishers->GetActiveConnection(); 
 
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
 
 if (rstPublishers) 
 if (rstPublishers->State == adStateOpen) 
 rstPublishers->Close(); 
} 
 
/////////////////////////////////////////////////////////// 
// // 
// PrintProviderError Function // 
// // 
/////////////////////////////////////////////////////////// 
 
void PrintProviderError(_ConnectionPtr pCnn1) 
{ 
 // Print Provider Errors from Connection object. 
 // pErr is a record object in the Connection's Error collection. 
 ErrorPtr pErr = NULL; 
 
 if( (pCnn1->Errors->Count) > 0) 
 { 
 long nCount = pCnn1->Errors->Count; 
 // Collection ranges from 0 to nCount -1. 
 for(long i = 0; i < nCount; i++) 
 { 
 pErr = pCnn1->Errors->GetItem(i); 
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
// EndFilterCpp 
```

**FilterX.h**

``` 
 
// BeginFilterH 
#include "icrsint.h" 
 
//This Class extracts only Pub Name and Country Name. 
class CPublishers : public CADORecordBinding 
{ 
BEGIN_ADO_BINDING(CPublishers) 
 
 //Column Pub Name is the 2nd field in the recordset 
 ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_szP_pubname, 
 sizeof(m_szP_pubname), lP_pubnameStatus, TRUE) 
 
 //Column Country Name is the 5th field in the recordset 
 ADO_VARIABLE_LENGTH_ENTRY2(5, adVarChar, m_szP_country , 
 sizeof(m_szP_country), lP_countryStatus, TRUE) 
 
END_ADO_BINDING() 
 
public: 
 CHAR m_szP_pubname[50]; 
 ULONG lP_pubnameStatus; 
 CHAR m_szP_country[50]; 
 ULONG lP_countryStatus; 
}; 
// EndFilterH 
```

