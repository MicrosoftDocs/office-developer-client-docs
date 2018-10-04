﻿---
title: AppendChunk and GetChunk Methods Example (VC++)
TOCTitle: AppendChunk and GetChunk Methods Example (VC++)
ms:assetid: a511ad7c-0a52-aa8b-39b7-004ddfbddd2f
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249767(v=office.15)
ms:contentKeyID: 48546825
ms.date: 09/18/2015
mtps_version: v=office.15
---

# AppendChunk and GetChunk Methods Example (VC++)


**Applies to**: Access 2013 | Office 2013

This example uses the [AppendChunk](appendchunk-method-ado.md) and [GetChunk](getchunk-method-ado.md) methods to fill an image field with data from another record.

``` 
 
// BeginAppendChunkCpp 
#import "C:\Program Files\Common Files\System\ADO\msado15.dll" no_namespace rename("EOF", "EndOfFile") 
 
#define ChunkSize 100 
 
#include <ole2.h> 
#include <stdio.h> 
#include "conio.h" 
#include "malloc.h" 
#include "AppendChunkX.h" 
 
//Function declarations 
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);}; 
void AppendChunkX(VOID); 
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
 HRESULT hr = S_OK; 
 
 if(FAILED(::CoInitialize(NULL))) 
 return; 
 
 AppendChunkX(); 
 
 //Wait here for the user to see the output 
 printf("\n\nPress any key to continue.."); 
 getch(); 
 ::CoUninitialize(); 
} 
 
 
/////////////////////////////////////////////////////////// 
// // 
// AppendChunkX Function // 
// // 
/////////////////////////////////////////////////////////// 
VOID AppendChunkX(VOID) 
{ 
 // Define ADO object pointers. 
 // Initialize pointers on define. 
 // These are in the ADODB:: namespace. 
 _RecordsetPtr pRstPubInfo = NULL; 
 _ConnectionPtr pConnection = NULL; 
 
 //Define other variables 
 IADORecordBinding *picRs = NULL; //Interface Pointer declared.(VC++ Extensions) 
 CPubInfoRs pubrs; //C++ class object 
 
 HRESULT hr = S_OK; 
 _bstr_t strCnn("Provider='sqloledb';Data Source='MySqlServer';" 
 "Initial Catalog='pubs';Integrated Security='SSPI';"); 
 
 _bstr_t strMessage,strPubID,strPRInfo; 
 _variant_t varChunk; 
 long lngOffSet,lngLogoSize; 
 char pubId[50]; 
 lngOffSet = 0; 
 
 UCHAR chData; 
 SAFEARRAY FAR *psa; 
 SAFEARRAYBOUND rgsabound[1]; 
 rgsabound[0].lLbound = 0; 
 rgsabound[0].cElements = ChunkSize; 
 
 try 
 { 
 //Open a Connection. 
 TESTHR(pConnection.CreateInstance(__uuidof(Connection))); 
 hr = pConnection->Open(strCnn,"","",adConnectUnspecified); 
 
 TESTHR(hr= pRstPubInfo.CreateInstance(__uuidof(Recordset))); 
 
 pRstPubInfo->CursorType = adOpenKeyset; 
 pRstPubInfo->LockType = adLockOptimistic; 
 
 hr = pRstPubInfo->Open("pub_info", 
 _variant_t((IDispatch*)pConnection,true), 
 adOpenKeyset,adLockOptimistic,adCmdTable); 
 
 //Open an IADORecordBinding interface pointer which we'll use 
 //for Binding Recordset to a class 
 TESTHR(pRstPubInfo->QueryInterface( 
 __uuidof(IADORecordBinding),(LPVOID*)&picRs)); 
 
 //Bind the Recordset to a C++ Class here 
 TESTHR(picRs->BindToRecordset(&pubrs)); 
 
 //Display the available logos here 
 strMessage = "Available logos are: " + (_bstr_t)"\n\n"; 
 printf(strMessage); 
 int Counter = 0; 
 while(!(pRstPubInfo->EndOfFile)) 
 { 
 printf("\n%s",pubrs.m_sz_pubid); 
 printf("\n%s",strtok(pubrs.m_sz_prinfo,",")); 
 
 //Display 5 records at a time and wait for user to continue.. 
 if (++Counter >= 5) 
 { 
 Counter = 0; 
 printf("\nPress any key to continue..."); 
 getch(); 
 } 
 pRstPubInfo->MoveNext(); 
 } 
 
 //Prompt For a Logo to Copy 
 printf("\nEnter the ID of a logo to copy: "); 
 myscanf(pubId, sizeof(pubId)); 
 strPubID = pubId; 
 
 //Copy the logo to a variable in chunks 
 
 pRstPubInfo->Filter = "pub_id = '" + strPubID + "'"; 
 lngLogoSize = pRstPubInfo->Fields->Item["logo"]->ActualSize; 
 
 //Create a safe array to store the array of BYTES 
 rgsabound[0].cElements = lngLogoSize; 
 psa = SafeArrayCreate(VT_UI1,1,rgsabound); 
 
 long index1 = 0; 
 while(lngOffSet < lngLogoSize) 
 { 
 varChunk = pRstPubInfo->Fields-> 
 Item["logo"]->GetChunk(ChunkSize); 
 
 //Copy the data only upto the Actual Size of Field. 
 for(long index=0;index<=(ChunkSize-1);index++) 
 { 
 hr= SafeArrayGetElement(varChunk.parray,&index,&chData); 
 if(SUCCEEDED(hr)) 
 { 
 //Take BYTE by BYTE and advance Memory Location 
 hr = SafeArrayPutElement(psa,&index1,&chData); 
 index1++; 
 } 
 else 
 break; 
 } 
 lngOffSet = lngOffSet + ChunkSize; 
 } 
 lngOffSet = 0; 
 
 printf("Enter a new Pub Id: "); 
 myscanf(pubrs.m_sz_pubid, sizeof(pubrs.m_sz_pubid)); 
 strPubID = pubrs.m_sz_pubid; 
 printf("Enter descriptive text: " ); 
 mygets(pubrs.m_sz_prinfo, sizeof(pubrs.m_sz_prinfo)); 
 
 pRstPubInfo->AddNew(); 
 pRstPubInfo->Fields->GetItem("pub_id")->PutValue(strPubID); 
 pRstPubInfo->Fields->GetItem("pr_info")-> 
 PutValue(pubrs.m_sz_prinfo); 
 
 //Assign the Safe array to a variant. 
 varChunk.vt = VT_ARRAY|VT_UI1; 
 varChunk.parray = psa; 
 hr = pRstPubInfo->Fields->GetItem("logo")-> 
 AppendChunk(varChunk); 
 
 //Update the table 
 pRstPubInfo->Update(); 
 
 lngLogoSize = pRstPubInfo->Fields->Item["logo"]->ActualSize; 
 
 //Show the newly added record. 
 printf("New Record : %s\n Description : %s\n Logo Size : %s", 
 pubrs.m_sz_pubid, 
 pubrs.m_sz_prinfo,(LPCSTR)(_bstr_t)pRstPubInfo->Fields-> 
 Item["logo"]->ActualSize); 
 
 //Delete new record because this is demonstration. 
 pConnection->Execute("DELETE FROM PUB_INFO WHERE pub_id = '" 
 + strPubID +"'",NULL,adCmdText); 
 } 
 catch(_com_error &e) 
 { 
 // Notify the user of errors if any. 
 _bstr_t bstrSource(e.Source()); 
 _bstr_t bstrDescription(e.Description()); 
 
 PrintProviderError(pConnection); 
 printf("Source : %s \n Description : %s\n",(LPCSTR)bstrSource, 
 (LPCSTR)bstrDescription); 
 } 
 
 // Clean up objects before exit. 
 if (pRstPubInfo) 
 if (pRstPubInfo->State == adStateOpen) 
 pRstPubInfo->Close(); 
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
 printf("\t Error number: %x\t%s", pErr->Number,(LPCSTR) pErr->Description); 
 } 
 } 
} 
 
// EndAppendChunkCpp 
```

**AppendChunkX.h**

``` 
 
// BeginAppendChunkH 
#include "icrsint.h" 
 
//This Class extracts pubid,prinfo. 
 
class CPubInfoRs : public CADORecordBinding 
{ 
 BEGIN_ADO_BINDING(CPubInfoRs) 
 
 ADO_VARIABLE_LENGTH_ENTRY2(1, adVarChar, m_sz_pubid, 
 sizeof(m_sz_pubid), l_pubid, TRUE) 
 
 ADO_VARIABLE_LENGTH_ENTRY2(3, adVarChar, m_sz_prinfo, 
 sizeof(m_sz_prinfo), l_prinfo, TRUE) 
 
 END_ADO_BINDING() 
 
public: 
 CHAR m_sz_pubid[10]; 
 ULONG l_pubid; 
 CHAR m_sz_prinfo[200]; 
 ULONG l_prinfo; 
}; 
// EndAppendChunkH 
```

