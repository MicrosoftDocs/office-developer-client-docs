---
title: "About persisting TZDEFINITION to a stream to commit to a binary property"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
localization_priority: Normal
ms.assetid: 0dec535d-d48f-39a5-97d5-0bd109134b3b
description: "The time zone properties, PidLidAppointmentTimeZoneDefinitionEndDisplay, PidLidAppointmentTimeZoneDefinitionRecur, and PidLidAppointmentTimeZoneDefinitionStartDisplay are binary named properties, each of which contains a stream that maps to the persisted format of a TZDEFINITION structure."
---

# About persisting TZDEFINITION to a stream to commit to a binary property

The time zone properties, [PidLidAppointmentTimeZoneDefinitionEndDisplay](http://msdn.microsoft.com/library/7b6193cb-612b-408e-b9bc-285df313e2cc%28Office.15%29.aspx), [PidLidAppointmentTimeZoneDefinitionRecur](http://msdn.microsoft.com/library/52fd57a0-9e34-4452-9ecd-2acb454446c9%28Office.15%29.aspx), and [PidLidAppointmentTimeZoneDefinitionStartDisplay](http://msdn.microsoft.com/library/08239670-3211-420c-99d7-0056ed967cb8%28Office.15%29.aspx) are binary named properties, each of which contains a stream that maps to the persisted format of a [TZDEFINITION](tzdefinition.md) structure. 
  
This topic describes a little endian format that can be used when persisting **TZDEFINITION** to a stream to commit to one of three binary properties. Use the same endian format in a parser to interpret a stream value obtained from one of these properties. 
  
```cpp
BYTE  bMajorVersion;    // breaking change
BYTE  bMinorVersion;    // extensibility
WORD  cbHeader;         // size of following data until TZREG sub structure
WORD  wFlags;
if (TZDEFINITION_FLAG_VALID_GUID)
   GUID  guid;                // guid
if (TZDEFINITION_FLAG_VALID_KEYNAME)     
    WORD   cchKeyName;        // does not include null char
    WCHAR  rgchKeyName;       // not null terminated
    WORD  cRules;             // number of rules
// for each rule
   BYTE        bMajorVersion;         // breaking change
   BYTE        bMinorVersion;         // extensibility
   WORD        cbRule;                // size of following data
   WORD        wFlags;                // flags
   SYSTEMTIME  stStart;               // GMT when this rule starts
// Following are the fields of the TZREG sub structure
   long        lBias;                // offset from GMT
   long        lStandardBias;        // offset from bias during standard time
   long        lDaylightBias;        // offset from bias during daylight time
   SYSTEMTIME  stStandardDate;       // time to switch to standard time
   SYSTEMTIME  stDaylightDate;       // time to switch to daylight time
```

The major version number is used to make a breaking change. Clients that are unfamiliar with the major version number should treat the property as if it is not there. Clients writing the structure should specify the constant **TZ_BIN_VERSION_MAJOR**. 
  
The minor version number is used for extensibility. Clients that are unfamiliar with the minor version number should read the data that they understand, and skip over the data that might be appended to each rule or to the overall stream. Clients writing the structure should specify the constant **TZ_BIN_VERSION_MINOR**. 
  
If a parser does not understand the major version of the header, it should not read the rest of the structure and behave as if the data is missing. If a parser does not understand the minor version of the header, it should use **cbHeader** to ignore the portions that it does not understand and advance to read the portions of the stream that it understands. 
  
The value of **wFlags** is always **TZDEFINITION_FLAG_VALID_KEYNAME**. The key name has a maximum size of **MAX_PATH**. 
  
If a parser does not recognize the major version of a rule, the client should ignore the rule, and use **cbRule** to advance to the next rule. If a parser does not recognize the minor version of a rule, the client should only parse the parts of the rule that it understands. 
  
When persisting a **TZDEFINITION** structure to a stream, a parser should not try to write any information that it does not understand. 
  
The maximum number of rules is 1024.
  
Note that the [TZREG](tzreg.md) structure is persisted here differently than when persisted alone, so the same code cannot be used to parse it. 
  
## See also



[Constants (Outlook exported APIs)](constants-outlook-exported-apis.md)
  
[Parse a stream from a binary property to read the TZDEFINITION structure](how-to-parse-stream-from-binary-property-to-read-tzdefinition-structure.md)
  
[Read time zone properties from an appointment](how-to-read-time-zone-properties-from-an-appointment.md)

