---
title: "ADO NumericScale and Precision Properties Example (VC++)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: f0bc84c6-5563-509c-9b4e-3fb45c70a04e
description: "This example uses the NumericScale and Precision properties to display the numeric scale and precision of fields in the Discounts table of the Pubs database."
---

# ADO NumericScale and Precision Properties Example (VC++)

This example uses the [NumericScale](numericscale-property-ado.md) and [Precision](precision-property-ado.md) properties to display the numeric scale and precision of fields in the ** *Discounts* ** table of the ** *Pubs* ** database. 
  
```
 
// BeginNumericScaleCpp 
#import "C:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
#include <ole2.h> 
#include <stdio.h> 
#include <conio.h> 
 
// Function declarations 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void NumericScaleX(void); 
void PrintProviderError(_ConnectionPtr pConnection); 
void PrintComError(_com_error &amp;e); 
 
/////////////////////////////////////////////////////////// 
// // 
// Main Function // 
// // 
/////////////////////////////////////////////////////////// 
 
void main() 
{ 
 if(FAILED(::CoInitialize(NULL))) 
 return; 
 
 NumericScaleX(); 
 
 ::CoUninitialize(); 
} 
 
/////////////////////////////////////////////////////////// 
// // 
// NumericScaleX Function // 
// // 
/////////////////////////////////////////////////////////// 
 
void NumericScaleX(void) 
{ 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace 
 _RecordsetPtr pRstDiscounts = NULL; 
 FieldsPtr fldTemp = NULL; 
 
 //Define Other Variables 
 HRESULT hr = S_OK; 
 _variant_t Index; 
 Index.vt = VT_I2; 
 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 
 try 
 { 
 // Open recordset. 
 TESTHR(pRstDiscounts.CreateInstance(__uuidof(Recordset))); 
 pRstDiscounts->Open("discounts", strCnn, adOpenForwardOnly, 
 adLockReadOnly, adCmdTable); 
 
 // Display numeric scale and precision of 
 // numeric and small integer fields. 
 fldTemp = pRstDiscounts->GetFields(); 
 
 for (int intLoop=0;intLoop < (int)fldTemp->GetCount();intLoop++) 
 { 
 Index.iVal = intLoop; 
 
 if ((fldTemp->GetItem(Index)->Type == adNumeric) 
 || (fldTemp->GetItem(Index)->Type == adSmallInt)) 
 { 
 printf("Field: %s\n" ,(LPCSTR)fldTemp-> 
 GetItem(Index)->GetName()); 
 printf("Numeric scale: %d\n", fldTemp-> 
 GetItem(Index)->GetNumericScale()); 
 printf("Precision: %d\n", fldTemp-> 
 GetItem(Index)->GetPrecision()); 
 } 
 } 
 } 
 catch(_com_error &amp;e) 
 { 
 // Notify the user of errors if any. 
 // Pass a connection pointer accessed from the Recordset. 
 _variant_t vtConnect = pRstDiscounts->GetActiveConnection(); 
 
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
 if (pRstDiscounts) 
 if (pRstDiscounts->State == adStateOpen) 
 pRstDiscounts->Close(); 
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
 
void PrintComError(_com_error &amp;e) 
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
// EndNumericScaleCpp 

```


