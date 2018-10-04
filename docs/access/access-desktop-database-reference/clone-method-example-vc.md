﻿---
title: Clone Method Example (VC++)
TOCTitle: Clone Method Example (VC++)
ms:assetid: 18929a3a-cbc0-b25a-ac8c-24f5a98f0f0e
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248933(v=office.15)
ms:contentKeyID: 48543473
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Clone Method Example (VC++)


**Applies to**: Access 2013 | Office 2013

This example uses the [Clone](clone-method-ado.md) method to create copies of a [Recordset](recordset-object-ado.md) and then lets the user position the record pointer of each copy independently.

``` 
 
// BeginCloneCpp 
#import "C:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
#include <stdio.h> 
#include <ole2.h> 
#include <conio.h> 
#include "CloneX.h" 
 
// Function Declarations. 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void CloneX(void); 
void PrintProviderError(_ConnectionPtr pConnection); 
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
 
/////////////////////////////////////////////////////////// 
// // 
// Main Function // 
// // 
/////////////////////////////////////////////////////////// 
void main() 
{ 
 if(FAILED(::CoInitialize(NULL))) 
 return; 
 
 CloneX(); 
 
 //Wait here for user to see the output.. 
 printf("\nPress any key to continue..."); 
 getch(); 
 ::CoUninitialize(); 
} 
 
/////////////////////////////////////////////////////////// 
// // 
// CloneX Function // 
// // 
/////////////////////////////////////////////////////////// 
 
void CloneX() 
{ 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace. 
 _RecordsetPtr arstStores[3]; 
 
 //Define Other Variables 
 HRESULT hr = S_OK; 
 int intLoop = 0; 
 _bstr_t strSQL; 
 _bstr_t strMessage; 
 _bstr_t strFind; 
 int intLoop1 = 0; 
 char *tempStr; 
 bool boolFlag = TRUE; 
 char m_szS_stor_name[150]; 
 
 // Assign SQL statement and connection string to variables. 
 strSQL = "SELECT stor_name FROM Stores ORDER BY stor_name"; 
 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 
 try 
 { 
 // Open recordset as a static cursor type recordset. 
 arstStores[0].CreateInstance(__uuidof(Recordset)); 
 arstStores[0]->CursorType = adOpenStatic; 
 arstStores[0]->LockType = adLockBatchOptimistic; 
 
 TESTHR(arstStores[0]->Open(strSQL,strCnn, adOpenStatic, 
 adLockBatchOptimistic,adCmdText)); 
 
 // Create two clones of the original Recordset. 
 arstStores[1] = arstStores[0]->Clone(adLockUnspecified); 
 arstStores[2] = arstStores[0]->Clone(adLockUnspecified); 
 
 while (boolFlag) 
 { 
 // Loop through the array so that on each pass, 
 // the user is searching a different copy of the 
 // same Recordset. 
 for (intLoop = 1; intLoop <= 3 ; intLoop++) 
 { 
 // Ask for search string while showing where 
 // the current record pointer is for each Recordset. 
 printf("Recordsets from stores table:\n"); 
 
 _bstr_t str1 = arstStores[0]->Fields-> 
 GetItem("stor_name")->Value; 
 printf("\t1 - Original - Record pointer at %s", 
 (LPCSTR)str1); 
 
 _bstr_t str2 = arstStores[1]->Fields-> 
 GetItem("stor_name")->Value; 
 printf("\n\t2 - Clone - Record pointer at %s", 
 (LPCSTR)str2); 
 
 _bstr_t str3 = arstStores[2]->Fields-> 
 GetItem("stor_name")->Value; 
 printf("\n\t3 - Clone - Record pointer at %s", 
 (LPCSTR)str3); 
 
 printf("\n\nEnter search string for # %d, " 
 "or press Enter to quit.\n", intLoop); 
 mygets(m_szS_stor_name, 150); 
 
 // Trim the String. 
 tempStr = strtok(m_szS_stor_name, " \t"); 
 strMessage = tempStr; 
 if (tempStr == NULL) 
 { 
 boolFlag = FALSE; 
 break; 
 } 
 
 // Find the search string; if there's no 
 // match, jump to the last record. 
 intLoop1 = intLoop - 1; 
 
 arstStores[intLoop1]->Filter = "stor_name >= '" + 
 strMessage + "'"; 
 
 if (arstStores[intLoop1]->EndOfFile) 
 { 
 arstStores[intLoop1]->Filter = (long)adFilterNone; 
 arstStores[intLoop1]->MoveLast(); 
 } 
 } 
 } // End of While Loop 
 } 
 catch(_com_error &e) 
 { 
 // Notify the user of errors if any. 
 _variant_t vtConnect; 
 
 vtConnect = arstStores[0]->GetActiveConnection(); 
 
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
 if (arstStores[0]) 
 if (arstStores[0]->State == adStateOpen) 
 arstStores[0]->Close(); 
 if (arstStores[1]) 
 if (arstStores[1]->State == adStateOpen) 
 arstStores[1]->Close(); 
 if (arstStores[2]) 
 if (arstStores[2]->State == adStateOpen) 
 arstStores[2]->Close(); 
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
 printf("Error number: %x\t%s\n", pErr->Number, 
 (LPCSTR) pErr->Description); 
 } 
 } 
}; 
 
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
}; 
// EndCloneCpp 
```

**CloneX.h**

``` 
 
// BeginCloneH 
#include "icrsint.h" 
 
// This Class extracts only store name 
// from "stores" table. 
class CStores : public CADORecordBinding 
{ 
BEGIN_ADO_BINDING(CStores) 
 
 //Column stor_name is the 1st field in the recordset 
 
 ADO_VARIABLE_LENGTH_ENTRY2(1, adVarChar, m_szS_stor_name, 
 sizeof(m_szS_stor_name), lS_stor_nameStatus, FALSE) 
 
END_ADO_BINDING() 
 
public: 
 CHAR m_szS_stor_name[150]; 
 ULONG lS_stor_nameStatus; 
}; 
 
// EndCloneH 
```

