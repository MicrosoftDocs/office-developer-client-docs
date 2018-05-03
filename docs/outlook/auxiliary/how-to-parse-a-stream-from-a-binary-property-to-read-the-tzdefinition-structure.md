---
title: "How to Parse a stream from a binary property to read the TZDEFINITION structure"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
 
localization_priority: Normal
ms.assetid: 039b3a45-bd57-51f5-1485-a3f6d1bde85a
description: "This topic shows how to read the TZDEFINITION structure from the persisted format stored in a binary property."
---

# How to: Parse a stream from a binary property to read the TZDEFINITION structure

This topic shows how to read the [TZDEFINITION](tzdefinition.md) structure from the persisted format stored in a binary property. 
  
```
TZDEFINITION* BinToTZDEFINITION(ULONG cbDef, LPBYTE lpbDef) 
{ 
    if (!lpbDef) return NULL; 
 
    // Update this if parsing code is changed. 
    // This checks the size up to the flag member. 
    if (cbDef &amp;lt; 2*sizeof(BYTE) + 2*sizeof(WORD)) return NULL; 
 
    TZDEFINITION tzDef = {0}; 
    TZRULE* lpRules = NULL; 
    LPBYTE lpPtr = lpbDef; 
    WORD cchKeyName = NULL; 
    WCHAR* szKeyName = NULL; 
    WORD i = 0; 
 
    BYTE bMajorVersion = *((BYTE*)lpPtr); 
    lpPtr += sizeof(BYTE); 
    BYTE bMinorVersion = *((BYTE*)lpPtr); 
    lpPtr += sizeof(BYTE); 
 
    // We only understand TZ_BIN_VERSION_MAJOR 
    if (TZ_BIN_VERSION_MAJOR != bMajorVersion) return NULL; 
 
    // We only understand if &amp;gt;= TZ_BIN_VERSION_MINOR 
    if (TZ_BIN_VERSION_MINOR &amp;gt; bMinorVersion) return NULL; 
 
    lpPtr += sizeof(WORD); 
 
    tzDef.wFlags = *((WORD*)lpPtr); 
    lpPtr += sizeof(WORD); 
 
    if (TZDEFINITION_FLAG_VALID_GUID &amp;amp; tzDef.wFlags) 
    { 
        if (lpbDef + cbDef - lpPtr &amp;lt; sizeof(GUID)) return NULL; 
        tzDef.guidTZID = *((GUID*)lpPtr); 
        lpPtr += sizeof(GUID); 
    } 
 
    if (TZDEFINITION_FLAG_VALID_KEYNAME &amp;amp; tzDef.wFlags) 
    { 
        if (lpbDef + cbDef - lpPtr &amp;lt; sizeof(WORD)) return NULL; 
        cchKeyName = *((WORD*)lpPtr); 
        lpPtr += sizeof(WORD); 
        if (cchKeyName) 
        { 
            if (lpbDef + cbDef - lpPtr &amp;lt; (BYTE)sizeof(WORD)*cchKeyName) return NULL; 
            szKeyName = (WCHAR*)lpPtr; 
            lpPtr += cchKeyName*sizeof(WORD); 
        } 
    } 
 
    if (lpbDef+ cbDef - lpPtr &amp;lt; sizeof(WORD)) return NULL; 
    tzDef.cRules = *((WORD*)lpPtr); 
    lpPtr += sizeof(WORD); 
    if (tzDef.cRules) 
    { 
        lpRules = new TZRULE[tzDef.cRules]; 
        if (!lpRules) return NULL; 
 
        LPBYTE lpNextRule = lpPtr; 
        BOOL bRuleOK = false; 

```

## See also

#### Concepts

[About persisting TZDEFINITION to a stream to commit to a binary property](about-persisting-tzdefinition-to-a-stream-to-commit-to-a-binary-property.md)
  
[How to: Read time zone properties from an appointment](how-to-read-time-zone-properties-from-an-appointment.md)

