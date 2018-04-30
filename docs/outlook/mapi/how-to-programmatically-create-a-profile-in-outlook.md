---
title: "How to Programmatically Create a Profile in Outlook"
 
 
manager: soliver
ms.date: 6/2/2016
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 2a8561a9-df09-453a-b415-c45910625870
description: "This topic describes how to programmatically update a profile in Outlook 2016 by adding a MAPI property to the emsuid section of the Profile object."
---

# How to: Programmatically Create a Profile in Outlook

This topic describes how to programmatically update a profile in Outlook 2016 by adding a MAPI property to the **emsuid** section of the Profile object. 
  
 **Last modified:** June 02, 2016 
  
 * **Applies to:** Office 365 | Outlook | Outlook 2016 * 
  
In MAPI, you can update a profile by setting the property **PR_PROFILE_USER_SMTP_EMAIL_ADDRESS_W (0x6641001F)**, as indicated in the procedure below. 
  
### Set the property for Outlook 2016

1. Make sure Outlook 2016 is property configured.
    
2. Using the [IMAPIProp](https://msdn.microsoft.com/en-us/library/cc815525.aspx) interface, go to the Outlook Profile section. 
    
     This can be difficult in Outlook's MAPI, since in 2010 and above there is no longer the global profile section. To find the Profile section, find the property PR_EMSMDB_SECTION_UID (0x3D150102). The value will be the GUID of the profile section persisted in binary form, which will be used in the subsequent steps. You will need to remember this value. 
    
3. Add the property **PR_PROFILE_USER_SMTP_EMAIL_ADDRESS_W**. 
    
4. Set the property **0x6641001F** on the store and the **emsuid** section for all providers. 
    
5. Set the property **PR_DISPLAY_NAME**. 
    
## Code example

```
// CreateProfile.cpp : Defines the entry point for the console application.
//
#include "stdafx.h"
#include <Windows.h>
#include <MAPIX.h>
#include <MAPIUtil.h>
#include <EdkMdb.h>
#include <iostream>
#include <vector>
#include <map>
using namespace std;
#define PR_PROFILE_USER_SMTP_EMAIL_ADDRESS					PROP_TAG(PT_TSTRING, pidProfileMin+0x41)
#define PR_PROFILE_USER_SMTP_EMAIL_ADDRESS_W				PROP_TAG(PT_UNICODE, pidProfileMin+0x41)
#define PR_EMSMDB_SECTION_UID								PROP_TAG(PT_BINARY, 0x3D15)
#define MAPI_FORCE_ACCESS									0x80000
STDMETHODIMP GetGlobalProfileSection(LPSERVICEADMIN lpSvcAdmin, LPMAPIUID lpMapiUid, ULONG ulFlags, LPPROFSECT * lppProfSect);
STDMETHODIMP GetEMSMDBVarProfileSection(LPSERVICEADMIN lpSvcAdmin, LPPROFSECT lpGlobalProfSection, LPPROFSECT * lppProfSect);
std::map<ULONG, LPWSTR> PropValueMap
{
	{
		PR_DISPLAY_NAME_W,
		L"Anthony"
	},
	{
		PR_PROFILE_USER_SMTP_EMAIL_ADDRESS_W,
		L"=SMTP:anthony@contoso.com"
	}
};
int _tmain(int argc, _TCHAR* argv[])
{
	HRESULT				hRes = S_OK;            // Result from MAPI calls.
	LPPROFADMIN			lpProfAdmin = NULL;     // Profile Admin object.
	LPSERVICEADMIN		lpSvcAdmin = NULL;      // Service Admin object.
	LPMAPITABLE			lpMsgSvcTable = NULL;   // Table to hold services.
	LPSRowSet			lpSvcRows = NULL;       // Rowset to hold results of table query.
	vector<SPropValue>	rgvals;
	SRestriction		sres;                   // Restriction structure.
	SPropValue			SvcProps;               // Property structure for restriction.
	LPPROFSECT			lpGlobalProfSection = nullptr;
	LPPROFSECT			lpEmsMdbVarProfSect = nullptr;
	SPropValue			spvSmtpAddressW;
	SPropValue			spvDisplayName;
	// This indicates columns we want returned from HrQueryAllRows.
	enum { iSvcName, iSvcUID, cptaSvc };
	SizedSPropTagArray(cptaSvc, sptCols) = { cptaSvc, PR_SERVICE_NAME, PR_SERVICE_UID };
	string ProfileName = "MAPIProfile";
	// Initialize MAPI.
	if (FAILED(hRes = MAPIInitialize(NULL)))
	{
		cout << "Error initializing MAPI.";
		goto error;
	}
	// Get an IProfAdmin interface.
	if (FAILED(hRes = MAPIAdminProfiles(0,              // Flags.
		&amp;lpProfAdmin))) // Pointer to new IProfAdmin.
	{
		cout << "Error getting IProfAdmin interface.";
		goto error;
	}
	// Create a new profile.
	if (FAILED(hRes = lpProfAdmin->CreateProfile((LPTSTR)ProfileName.c_str(),     // Name of new profile.
													nullptr,          // Password for profile.
													0,          // Handle to parent window.
													0)))        // Flags.
	{
		cout << "Error creating profile.";
		goto error;
	}
	// Get an IMsgServiceAdmin interface off of the IProfAdmin interface.
	if (FAILED(hRes = lpProfAdmin->AdminServices((LPTSTR)ProfileName.c_str(),     // Profile that we want to modify.
													nullptr,          // Password for that profile.
													0,          // Handle to parent window.
													0,             // Flags.
													&amp;lpSvcAdmin))) // Pointer to new IMsgServiceAdmin.
	{
		cout << "Error getting IMsgServiceAdmin interface.";
		goto error;
	}
	// Create the new message service for Exchange.
	if (FAILED(hRes = lpSvcAdmin->CreateMsgService("MSEMS",     // Name of service from MAPISVC.INF.
													NULL,        // Display name of service.
													NULL,        // Handle to parent window.
													NULL)))      // Flags.
	{
		cout << "Error creating Exchange message service.";
		goto error;
	}
	// You now have to obtain the entry id for the new service.
	// You can do this by getting the message service table
	// and getting the entry that corresponds to the new service.
	if (FAILED(hRes = lpSvcAdmin->GetMsgServiceTable(0,                 // Flags.
													&amp;lpMsgSvcTable)))  // Pointer to table.
	{
		cout << "Error getting Message Service Table.";
		goto error;
	}
	// Set up restriction to query table.
	sres.rt = RES_CONTENT;
	sres.res.resContent.ulFuzzyLevel = FL_FULLSTRING;
	sres.res.resContent.ulPropTag = PR_SERVICE_NAME;
	sres.res.resContent.lpProp = &amp;SvcProps;
	SvcProps.ulPropTag = PR_SERVICE_NAME;
	SvcProps.Value.lpszA = "MSEMS";
	// Query the table to obtain the entry for the newly created message service.
	if (FAILED(hRes = HrQueryAllRows(lpMsgSvcTable,
										(LPSPropTagArray)&amp;sptCols,
										&amp;sres,
										NULL,
										0,
										&amp;lpSvcRows)))
	{
		cout << "Error querying table for new message service.";
		goto error;
	}
	ZeroMemory(&amp;spvSmtpAddressW, sizeof(spvSmtpAddressW));
	spvSmtpAddressW.ulPropTag = PR_PROFILE_USER_SMTP_EMAIL_ADDRESS_W;
	spvSmtpAddressW.Value.lpszW = PropValueMap[PR_PROFILE_USER_SMTP_EMAIL_ADDRESS_W];
	rgvals.push_back(spvSmtpAddressW);
	// Configure the message service by using the previous properties.
	//if (FAILED(hRes = lpSvcAdmin->ConfigureMsgService(
	//													(LPMAPIUID)lpSvcRows->aRow->lpProps[iSvcUID].Value.bin.lpb, // Entry ID of service to configure.
	//													NULL,                                                       // Handle to parent window.
	//													0,                                                          // Flags.
	//													rgvals.size(),                                                          // Number of properties we are setting.
	//													rgvals.data())))                                                    // Pointer to SPropValue array.
	//{
	//	cout << "Error configuring message service.";
	//	goto error;
	//}
	if (FAILED(hRes = GetGlobalProfileSection(
													lpSvcAdmin, 
													(LPMAPIUID)lpSvcRows->aRow->lpProps[iSvcUID].Value.bin.lpb, 
													MAPI_MODIFY, 
													&amp;lpGlobalProfSection)))
	{
		cout << "Error attempting to get the Global Profile Section.";
		goto error;
	}
	if (FAILED(hRes = lpGlobalProfSection->SetProps(
													rgvals.size(),
													rgvals.data(),
													nullptr)))
	{
		cout << "Error attempting to set the smtp address.";
		goto error;
	}
	if (FAILED(hRes = lpGlobalProfSection->SaveChanges(
														KEEP_OPEN_READWRITE)))
	{
		cout << "Error attempting to save after setting the smtp address";
		goto error;
	}
	if (FAILED(hRes = GetEMSMDBVarProfileSection(lpSvcAdmin, lpGlobalProfSection, &amp;lpEmsMdbVarProfSect)))
	{
		goto error;
	}
	ZeroMemory(&amp;spvDisplayName, sizeof(spvDisplayName));
	spvDisplayName.ulPropTag = PR_DISPLAY_NAME_W;
	spvDisplayName.Value.lpszW = PropValueMap[PR_DISPLAY_NAME_W];
	rgvals.push_back(spvDisplayName);
	if (FAILED(hRes = lpEmsMdbVarProfSect->SetProps(
													rgvals.size(),
													rgvals.data(),
													nullptr)))
	{
		cout << "Error call set props on the ems mdb var prof sect using the smtp address";
		goto error;
	}
	if (FAILED(hRes = lpEmsMdbVarProfSect->SaveChanges(
														KEEP_OPEN_READWRITE)))
	{
		cout << "Error attempting to save after setting the smtp address on the ems mdb var prof sect";
		goto error;
	}
cleanup:
	// Clean up
	if (lpEmsMdbVarProfSect) lpEmsMdbVarProfSect->Release();
	if (lpGlobalProfSection) lpGlobalProfSection->Release();
	if (lpSvcRows) FreeProws(lpSvcRows);
	if (lpMsgSvcTable) lpMsgSvcTable->Release();
	if (lpSvcAdmin) lpSvcAdmin->Release();
	if (lpProfAdmin) lpProfAdmin->Release();
	MAPIUninitialize();
	return 0;
error:
	cout << " hRes = 0x" << hex << hRes << dec << endl;
	goto cleanup;
}
STDMETHODIMP GetGlobalProfileSection(LPSERVICEADMIN lpSvcAdmin, LPMAPIUID lpMapiUid, ULONG ulFlags, LPPROFSECT * lppProfSect)
{
	HRESULT			hRes = MAPI_E_CALL_FAILED;
	LPPROFSECT		lpProfSect = nullptr;
	LPPROFSECT		lpEmsMdbVarProfSect = nullptr;
	ULONG			cValues = 0;
	LPSPropValue	lpProps = nullptr;
	SizedSPropTagArray(1, spta) = { 1, { PR_EMSMDB_SECTION_UID } };
	*lppProfSect = nullptr;
	hRes = lpSvcAdmin->OpenProfileSection(lpMapiUid,
		0,
		MAPI_FORCE_ACCESS,
		&amp;lpProfSect);
	if (FAILED(hRes) || lpProfSect == nullptr)
	{
		return hRes;
	}
	hRes = lpProfSect->GetProps((LPSPropTagArray)&amp;spta, 0, &amp;cValues, &amp;lpProps);
	if (FAILED(hRes) || lpProps == nullptr || cValues == 0)
	{
		return hRes;
	}
	if (lpProps[0].ulPropTag != PR_EMSMDB_SECTION_UID)
	{
		hRes = lpProps[0].Value.err;
		goto Cleanup;
	}
	hRes = lpSvcAdmin->OpenProfileSection((LPMAPIUID)lpProps->Value.bin.lpb, 0, ulFlags, &amp;lpEmsMdbVarProfSect);
	if (FAILED(hRes) || lpEmsMdbVarProfSect == nullptr)
	{
		goto Cleanup;
	}
	*lppProfSect = lpEmsMdbVarProfSect;
Cleanup:
	if (lpProps)
	{
		MAPIFreeBuffer(lpProps);
	}
	if (lpProfSect)
	{
		lpProfSect->Release();
	}
	return hRes;
}
STDMETHODIMP GetEMSMDBVarProfileSection(LPSERVICEADMIN lpSvcAdmin, LPPROFSECT lpGlobalProfSection, LPPROFSECT * lppProfSect)
{
	HRESULT hRes = MAPI_E_CALL_FAILED;
	SizedSPropTagArray(1, sptaStoreProviders) = { 1, { PR_STORE_PROVIDERS } };
	ULONG				cValues = 0;
	LPSPropValue		lpProps = nullptr;
	LPPROFSECT			lpProfSect = nullptr;
	if (!lpSvcAdmin || !lpGlobalProfSection || !lppProfSect)
		return E_INVALIDARG;
	*lppProfSect = nullptr;
	if (FAILED(hRes = lpGlobalProfSection->GetProps(
		(LPSPropTagArray)&amp;sptaStoreProviders,
		0,
		&amp;cValues,
		&amp;lpProps)) || cValues == 0 || lpProps == nullptr)
	{
		cout << "Error attempting to get the PR_STORE_PROVIDERS property " << endl;
		goto Cleanup;
	}
	if (lpProps->ulPropTag != sptaStoreProviders.aulPropTag[0])
	{
		hRes = lpProps->Value.err;
		goto Cleanup;
	}
	if (FAILED(hRes = lpSvcAdmin->OpenProfileSection(
		(LPMAPIUID)lpProps->Value.bin.lpb,
		0,
		MAPI_FORCE_ACCESS | MAPI_MODIFY,
		&amp;lpProfSect)) || lpProfSect == nullptr)
	{
		cout << "Could not open the profile section using the PR_STORE_PROVIDERS property " << endl;
		goto Cleanup;
	}
	*lppProfSect = lpProfSect;
Cleanup:
	if (lpProps)
	{
		MAPIFreeBuffer(lpProps);
		lpProps = nullptr;
	}
	return hRes;
}
```

## Use MFCMAPI to configure Outlook profiles

[MFCMAPI](http://mfcmapi.codeplex.com) provides access to MAPI stores to facilitate investigation of Exchange and Outlook issues and to provide developers support for MAPI development. 
  
## See also

[How To: Create an Outlook profile using MFCMAPI](https://msdn.microsoft.com/en-us/library/office/mt723322.aspx)
  

