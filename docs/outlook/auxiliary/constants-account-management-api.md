---
title: "Constants (Account management API)"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: overview
localization_priority: Normal
ms.assetid: 2a15e5df-b8e3-9c37-b1ee-2881d010e30b
description: "This topic contains constant definitions, class identifiers, and interface identifiers for the Account Management API."
---

# Constants (Account management API)

This topic contains constant definitions, class identifiers, and interface identifiers for the Account Management API.
  
## Constants

|**Constant**|**Definition**|
|:-----|:-----|
|ACCT_INIT_NOSYNCH_MAPI_ACCTS  <br/> |0x00000001  <br/> |
|ACCT_INIT_NO_STORES_CHECK  <br/> |0x00000002  <br/> |
|ACCT_INIT_NO_NOTIFICATIONS <br/> |0x00000004 <br/> |
|ACCTUI_NO_WARNING  <br/> |0x0100  <br/> |
|ACCTUI_SHOW_ACCTWIZARD  <br/> |0x0400  <br/> |
|ACCTUI_SHOW_DATA_TAB  <br/> |0x0200  <br/> |
|E_ACCT_NOT_FOUND  <br/> |0x800C8101  <br/> |
|E_ACCT_UI_BUSY  <br/> |0x800C8102  <br/> |
|E_ACCT_WRONG_SORT_ORDER  <br/> |0x800C8105  <br/> |
|E_INVALIDARG  <br/> | *As defined in the Windows Software Development Kit (SDK) header file winerror.h.*  <br/> |
|E_NOTIMPL  <br/> | *As defined in the Windows SDK header file winerror.h.*  <br/> |
|E_OLK_ALREADY_INITIALIZED  <br/> |0x800C8002  <br/> |
|E_OLK_NOT_INITIALIZED  <br/> |0x800C8005  <br/> |
|E_OLK_PARAM_NOT_SUPPORTED  <br/> |0x800C8003  <br/> |
|E_OLK_PROP_READ_ONLY  <br/> |0x800C800D  <br/> |
|E_OLK_REGISTRY  <br/> |0x800C8001  <br/> |
|The following constants beginning with ENCRYPT_ are used by the [PROP_SMTP_SECURE_CONNECTION](prop_smtp_secure_connection.md) property to specify the type of encrypted connection.  <br/> ||
|ENCRYPT_CONN_AUTO  <br/> |3  <br/> |
|ENCRYPT_CONN_NO_SECURITY  <br/> |0  <br/> |
|ENCRYPT_CONN_SSL  <br/> |1  <br/> |
|ENCRYPT_CONN_TLS  <br/> |2  <br/> |
|MAPIACCT_SEND_ONLY  <br/> |0x00000001  <br/> |
|NOTIFY_ACCT_CHANGED  <br/> |1  <br/> |
|NOTIFY_ACCT_CREATED  <br/> |2  <br/> |
|NOTIFY_ACCT_DELETED  <br/> |3  <br/> |
|NOTIFY_ACCT_ORDER_CHANGED  <br/> |4  <br/> |
|NOTIFY_ACCT_PREDELETED  <br/> |5  <br/> |
|OLK_ACCOUNT_NO_FLAGS  <br/> |0  <br/> |
|S_OK  <br/> | *As defined in the Windows SDK header file winerror.h.*  <br/> |
|S_FALSE  <br/> | *As defined in the Windows SDK header file winerror.h.*  <br/> |
|SECURE_FLAG  <br/> |0x8000  <br/> |
|The following constants beginning with SMTP_ are used by the [PROP_SMTP_AUTH_METHOD](prop_smtp_auth_method.md) property and specify the authentication method.  <br/> ||
|SMTP_AUTH_SAME_AS_POP  <br/> |0  <br/> |
|SMTP_AUTH_RECEIVE_BEFORE_SEND  <br/> |2  <br/> |
|SMTP_AUTH_USER_PASS  <br/> |1  <br/> |
|The following 5 constants and macros are used by the [PROP_POP_LEAVE_ON_SERVER](prop_pop_leave_on_server.md) property and specify options for POP accounts to leave a copy of a message on the server.  <br/> ||
|LEAVE_ON_SERVER  <br/> |0x1  <br/> |
|REMOVE_AFTER  <br/> |0x2  <br/> |
|REMOVE_ON_NUKE  <br/> |0x4  <br/> |
|GET_REMOVE_AFTER_DAYS(ul)  <br/> |((ul)\>\>16)  <br/> |
|SET_REMOVE_AFTER_DAYS(days)  <br/> |((days)\<\<16)  <br/> |
   
## Class identifiers

Use the DEFINE_GUID macro defined in the Windows SDK header file guiddef.h to associate the GUID symbolic name with its value.
  
//{ed475410-b0d6-11d2-8c3b-00104b2a6676}
  
DEFINE_GUID(CLSID_OlkAccountManager, 0xed475410, 0xb0d6, 0x11d2, 0x8c, 0x3b, 0x0, 0x10, 0x4b, 0x2a, 0x66, 0x76); 
  
//{ed475411-b0d6-11d2-8c3b-00104b2a6676}
  
DEFINE_GUID(CLSID_OlkPOP3Account, 0xed475411, 0xb0d6, 0x11d2, 0x8c, 0x3b, 0x0, 0x10, 0x4b, 0x2a, 0x66, 0x76);
  
//{ed475412-b0d6-11d2-8c3b-00104b2a6676}
  
DEFINE_GUID(CLSID_OlkIMAP4Account, 0xed475412, 0xb0d6, 0x11d2, 0x8c, 0x3b, 0x0, 0x10, 0x4b, 0x2a, 0x66, 0x76);
  
//{ed475414-b0d6-11d2-8c3b-00104b2a6676}
  
DEFINE_GUID(CLSID_OlkMAPIAccount, 0xed475414, 0xb0d6, 0x11d2, 0x8c, 0x3b, 0x0, 0x10, 0x4b, 0x2a, 0x66, 0x76);
  
//{ed475418-b0d6-11d2-8c3b-00104b2a6676}
  
DEFINE_GUID(CLSID_OlkMail, 0xed475418, 0xb0d6, 0x11d2, 0x8c, 0x3b, 0x0, 0x10, 0x4b, 0x2a, 0x66, 0x76);
  
//{ed475419-b0d6-11d2-8c3b-00104b2a6676}
  
DEFINE_GUID(CLSID_OlkAddressBook, 0xed475419, 0xb0d6, 0x11d2, 0x8c, 0x3b, 0x0, 0x10, 0x4b, 0x2a, 0x66, 0x76);
  
//{ed475420-b0d6-11d2-8c3b-00104b2a6676}
  
DEFINE_GUID(CLSID_OlkStore, 0xed475420, 0xb0d6, 0x11d2, 0x8c, 0x3b, 0x0, 0x10, 0x4b, 0x2a, 0x66, 0x76);
  
//{4db5cbf0-3b77-4852-bc8e-bb81908861f3}
  
DEFINE_GUID(CLSID_OlkHotmailAccount, 0x4db5cbf0, 0x3b77, 0x4852, 0xbc, 0x8e, 0xbb, 0x81, 0x90, 0x88, 0x61, 0xf3);
  
//{4db5cbf2-3b77-4852-bc8e-bb81908861f3}
  
DEFINE_GUID(CLSID_OlkLDAPAccount, 0x4db5cbf2, 0x3b77, 0x4852, 0xbc, 0x8e, 0xbb, 0x81, 0x90, 0x88, 0x61, 0xf3);
  
## Interface identifiers

Use the DEFINE_GUID macro defined in the Windows SDK header file guiddef.h to associate the GUID symbolic name with its value.
  
//{9240A6C0-AF41-11d2-8C3B-00104B2A6676}
  
DEFINE_GUID(IID_IOlkErrorUnknown, 0x9240a6c0, 0xaf41, 0x11d2, 0x8c, 0x3b, 0x0, 0x10, 0x4b, 0x2a, 0x66, 0x76);
  
//{9240A6C1-AF41-11d2-8C3B-00104B2A6676}
  
DEFINE_GUID(IID_IOlkEnum, 0x9240a6c1, 0xaf41, 0x11d2, 0x8c, 0x3b, 0x0, 0x10, 0x4b, 0x2a, 0x66, 0x76);
  
//{9240a6c3-af41-11d2-8c3b-00104b2a6676}
  
DEFINE_GUID(IID_IOlkAccountNotify, 0x9240a6c3, 0xaf41, 0x11d2, 0x8c, 0x3b, 0x0, 0x10, 0x4b, 0x2a, 0x66, 0x76);
  
//{9240a6cb-af41-11d2-8c3b-00104b2a6676}
  
DEFINE_GUID(IID_IOlkAccountHelper, 0x9240a6cb, 0xaf41, 0x11d2, 0x8c, 0x3b, 0x0, 0x10, 0x4b, 0x2a, 0x66, 0x76); 
  
//{9240a6cd-af41-11d2-8c3b-00104b2a6676}
  
DEFINE_GUID(IID_IOlkAccountManager, 0x9240a6cd, 0xaf41, 0x11d2, 0x8c, 0x3b, 0x0, 0x10, 0x4b, 0x2a, 0x66, 0x76); 
  
//{9240a6d2-af41-11d2-8c3b-00104b2a6676}
  
DEFINE_GUID(IID_IOlkAccount, 0x9240a6d2, 0xaf41, 0x11d2, 0x8c, 0x3b, 0x0, 0x10, 0x4b, 0x2a, 0x66, 0x76);
  

