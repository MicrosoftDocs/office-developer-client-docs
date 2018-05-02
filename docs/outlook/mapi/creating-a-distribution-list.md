---
title: "Creating a Distribution List"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: b63a6024-910d-4569-a3b4-c3ebf0b32c3d
description: "Last modified: July 23, 2011"
 
 
---

# Creating a Distribution List

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Clients can create a distribution list directly into a modifiable container such as the personal address book (PAB).
  
 **To create a distribution list in the PAB**
  
1. Create a sized property tag array with one property tag, **PR_DEF_CREATE_DL** ( [PidTagDefCreateDl](pidtagdefcreatedl-canonical-property.md)), as follows:
    
  ```
  SizedPropTagArray(1, tagaDefaultDL) =
  {
      1,
      {
          PR_DEF_CREATE_DL
      }
  };
  ```

2. Call [IAddrBook::GetPAB](iaddrbook-getpab.md) to retrieve the entry identifier of the PAB. If there is an error or **GetPAB** returns zero or NULL, do not continue. 
    
  ```
  LPENTRYID peidPAB = NULL;
  ULONG cbeidPAB = 0;
  lpIAddrBook->GetPAB(&amp;cbeidPAB, &amp;peidPAB);
  ```

3. Call [IAddrBook::OpenEntry](iaddrbook-openentry.md) to open the PAB. The  _ulObjType_ output parameter should be set to MAPI_ABCONT. 
    
  ```
  ULONG ulObjType = 0;
  LPABCONT lpPABCont = NULL;
  lpIAddrBook->OpenEntry(cbeidPAB, peidPAB,
                  NULL,
                  MAPI_MODIFY,
                  &amp;ulObjType,
                  &amp;lpPABCont);
  ```

4. Call the PAB's [IMAPIProp::GetProps](imapiprop-getprops.md) method to retrieve the PR_DEF_CREATE_DL property, the template that it uses to create a distribution list. 
    
  ```
  lpPABCont->GetProps(0,
              tagaDefaultDL,
              &amp;lpspvDefDLTpl);
  
  ```

5. If **GetProps** fails: 
    
1. Call the PAB's [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method to open the **PR_CREATE_TEMPLATES** ( [PidTagCreateTemplates](pidtagcreatetemplates-canonical-property.md)) property with the **IMAPITable** interface. 
    
2. Create a property restriction to search for the row with the **PR_ADDRTYPE** ( [PidTagAddressType](pidtagaddresstype-canonical-property.md)) column equal to "MAPIPDL." 
    
3. Call [IMAPITable::FindRow](imapitable-findrow.md) to locate this row. 
    
6. Save the entry identifier returned by either **GetProps** or **FindRow**.
    
  ```
  peidDefDLTpl = lpspvDefDLTpl->Value.bin.pb;
  cbeidDefDLTpl = lpspvDefDLTpl->Value.bin.cb;
  
  ```

7. Call the PAB's [IABContainer::CreateEntry](iabcontainer-createentry.md) method to create a new entry using the template represented by the saved entry identifier. Do not assume that the object returned will be a distribution list rather than a messaging user when this call is remoted. Notice that the CREATE_CHECK_DUP flag is passed in the  _ulFlags_ parameter to prevent the entry from being added twice. 
    
  ```
  lpPABCont->CreateEntry(cbeidDefDLTpl,
                  peidDefDLTPL,
                  CREATE_CHECK_DUP_STRICT,
                  &amp;lpNewPABEntry);
  ```

8. Call the new entry's **IUnknown::QueryInterface** method, passing IID_IDistList as the interface identifier, to determine if the entry is a distribution list and supports the [IDistList : IMAPIContainer](idistlistimapicontainer.md) interface. Because **CreateEntry** returns an **IMAPIProp** pointer rather than the more specific **IMailUser** or **IDistList** pointer, check that a distribution list object was created. If **QueryInterface** succeeds, you can be sure that you have created a distribution list rather than a messaging user. 
    
9. Call the distribution list's [IMAPIProp::SetProps](imapiprop-setprops.md) method to set its display name and other properties. 
    
10. Call the distribution list's [IABContainer::CreateEntry](iabcontainer-createentry.md) method to add one or more messaging users. 
    
11. Call the distribution list's [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method when you're ready to save it. To retrieve the entry identifier of the saved distribution list, set the KEEP_OPEN_READWRITE flag and then call [IMAPIProp::GetProps](imapiprop-getprops.md) requesting the **PR_ENTRYID** ( [PidTagEntryId](pidtagentryid-canonical-property.md)) property.
    
12. Release the new distribution list and the PAB by calling their **IUnknown::Release** methods. 
    
13. Call [MAPIFreeBuffer](mapifreebuffer.md) to release the memory for the entry identifier of the PAB and the sized property tag array. 
    

