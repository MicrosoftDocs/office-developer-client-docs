---
title: "How to Remove Custom Form Definition Saved With a Message"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
ms.assetid: 6a270f0c-104a-84a1-9adf-aea166f89071
description: "Last modified: June 25, 2012"
 
 
---

# How to: Remove Custom Form Definition Saved With a Message

  
  
**Applies to**: Outlook 
  
This topic shows a code sample in C++ that converts a message that has been saved with a custom form definition to a regular message without the form definition.
  
In Microsoft Outlook 2010 or Microsoft Outlook 2013, you can share forms containing custom form pages by either publishing them to a forms library or saving the corresponding form definition with a message. A custom form saved with a message is commonly referred as a "one-off form", since the form is shared only for viewing that specific message as a one-off instance. You typically do this when the form is not published in a forms library but you want the recipient to use the custom form when opening the item. You can specify a form is a one-off in the Forms Designer, by selecting the **Send form definition with item** check box on the **Properties** page of the form. 
  
Forms containing form pages can be customized with code in Visual Basic Scripting Edition (VBScript). Messages that are saved with form definitions are generally bigger in size. For security and storage reasons, Outlook 2010 and Outlook 2013 ignore form definitions saved with any item.
  
To convert a message that is saved with a custom form definition to one without, you must remove four named properties:
  
- [PidLidFormStorage Canonical Property](pidlidformstorage-canonical-property.md)
    
- [PidLidPageDirStream Canonical Property](pidlidpagedirstream-canonical-property.md)
    
- [PidLidFormPropStream Canonical Property](pidlidformpropstream-canonical-property.md)
    
- [PidLidScriptStream Canonical Property](pidlidscriptstream-canonical-property.md)
    
In addition, you should also remove the [PidLidPropertyDefinitionStream Canonical Property](pidlidpropertydefinitionstream-canonical-property.md) that contains the definitions of custom properties saved with that message. A side effect of removing this property is that the Outlook 2010 or Outlook 2013 object models and the Outlook 2010 or Outlook 2013 user interface will no longer be able to access user properties that have been set on the message. You are still able to access these properties and their values through MAPI. Note that if you do not remove this property and the message is saved with another form definition, the [PidLidPropertyDefinitionStream Canonical Property](pidlidpropertydefinitionstream-canonical-property.md) is partially overwritten with new data and data integrity is not guaranteed. 
  
If you remove the [PidLidPropertyDefinitionStream Canonical Property](pidlidpropertydefinitionstream-canonical-property.md), then you should also remove the **INSP_PROPDEFINITION** flag from the [PidLidCustomFlag Canonical Property](pidlidcustomflag-canonical-property.md).
  
The following function,  `RemoveOneOff`, accepts as input parameters a pointer to a message and an indicator whether to remove the [PidLidPropertyDefinitionStream Canonical Property](pidlidpropertydefinitionstream-canonical-property.md). Using the message pointer, it calls [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) to obtain the appropriate property identifiers, and then calls [IMAPIProp::DeleteProps](imapiprop-deleteprops.md) to remove the named properties. It also calls [IMAPIProp::GetProps](imapiprop-getprops.md) to get the [PidLidCustomFlag Canonical Property](pidlidcustomflag-canonical-property.md) and clears the **INSP_ONEOFFFLAGS** flag and **INSP_PROPDEFINITION** flag as appropriate from that property, so that Outlook 2010 and Outlook 2013 will not look for those named properties that have been removed. 
  
```
ULONG aulOneOffIDs[] = {dispidFormStorage,  
    dispidPageDirStream, 
    dispidFormPropStream, 
    dispidScriptStream, 
    dispidPropDefStream, // dispidPropDefStream must remain next to last in list 
    dispidCustomFlag};   // dispidCustomFlag must remain last in list 
 
#define ulNumOneOffIDs (sizeof(aulOneOffIDs)/sizeof(aulOneOffIDs[0])) 
 
HRESULT RemoveOneOff(LPMESSAGE lpMessage, BOOL bRemovePropDef) 
{ 
    if (!lpMessage) return MAPI_E_INVALID_PARAMETER; 
     
    HRESULT hRes = S_OK; 
    MAPINAMEID  rgnmid[ulNumOneOffIDs]; 
    LPMAPINAMEID rgpnmid[ulNumOneOffIDs]; 
    LPSPropTagArray lpTags = NULL; 
 
    ULONG i = 0; 
    for (i = 0 ; i < ulNumOneOffIDs ; i++) 
    { 
        rgnmid[i].lpguid = (LPGUID)&amp;PSETID_Common; 
        rgnmid[i].ulKind = MNID_ID; 
        rgnmid[i].Kind.lID = aulOneOffIDs[i]; 
        rgpnmid[i] = &amp;rgnmid[i]; 
    } 
   
    hRes = lpMessage->GetIDsFromNames( 
        ulNumOneOffIDs, 
        rgpnmid, 
        0, 
        &amp;lpTags); 
    if (lpTags) 
    { 
        // The last prop is the flag value  
        // to be updated, don't count it 
        lpTags->cValues = ulNumOneOffIDs-1; 
 
        // If the prop def stream is not to be removed, don't count it 
        if (!bRemovePropDef) 
        { 
          lpTags->cValues = lpTags->cValues-1; 
        } 
 
        hRes = lpMessage->DeleteProps( 
            lpTags, 
            0); 
        if (SUCCEEDED(hRes)) 
        { 
            SPropTagArray pTag = {0}; 
            ULONG cProp = 0; 
            LPSPropValue lpCustomFlag = NULL; 
 
            // Grab dispidCustomFlag, the last tag in the array 
            pTag.cValues = 1; 
            pTag.aulPropTag[0] = CHANGE_PROP_TYPE( 
                lpTags->aulPropTag[ulNumOneOffIDs-1], 
                PT_LONG); 
 
            hRes = lpMessage->GetProps( 
                &amp;pTag, 
                fMapiUnicode, 
                &amp;cProp, 
                &amp;lpCustomFlag); 
            if (SUCCEEDED(hRes) &amp;&amp;  
                1 == cProp &amp;&amp; lpCustomFlag &amp;&amp;  
                PT_LONG == PROP_TYPE(lpCustomFlag->ulPropTag)) 
            { 
                // Clear the INSP_ONEOFFFLAGS bits so Outlook  
                // doesn't look for the props that have been deleted 
                lpCustomFlag->Value.l =  
                    lpCustomFlag->Value.l &amp; ~(INSP_ONEOFFFLAGS); 
                if (bRemovePropDef) 
                { 
                    lpCustomFlag->Value.l =  
                        lpCustomFlag->Value.l &amp; ~(INSP_PROPDEFINITION); 
                } 
                hRes = lpMessage->SetProps( 
                    1, 
                    lpCustomFlag, 
                    NULL); 
             } 
 
             hRes = lpMessage->SaveChanges(KEEP_OPEN_READWRITE); 
         } 
    } 
    MAPIFreeBuffer(lpTags); 
 
    return hRes; 
}
```

## See also

#### Concepts

[MAPI Constants](mapi-constants.md)

