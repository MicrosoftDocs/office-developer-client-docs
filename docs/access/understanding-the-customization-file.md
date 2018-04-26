---
title: "Understanding the Customization File"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: overview
  
localization_priority: Normal
ms.assetid: 98fd5ec1-d5bd-cdd2-5eb5-9a1682fbed79
description: "Each section header in the customization file consists of square brackets ([] ) containing a type and parameter. The four section types are indicated by the literal strings connect , sql , userlist , or logs . The parameter is the literal string, the default, a user-specified identifier, or nothing."
---

# Understanding the Customization File

Each section header in the customization file consists of square brackets ( **[]** ) containing a type and parameter. The four section types are indicated by the literal strings **connect**, **sql**, **userlist**, or **logs**. The parameter is the literal string, the default, a user-specified identifier, or nothing. 
  
Therefore, each section is marked with one of the following section headers:
  
```
 
[ connect   default     ]
[ connect   identifier  ]
[ sql       default     ]
[ sql       identifier  ]
[ userlist  identifier  ]
[ logs                  ]
```

The section headers have the following parts.
  
|**Part**|**Description**|
|:-----|:-----|
|**connect** <br/> |A literal string that modifies a connection string.  <br/> |
|**sql** <br/> |A literal string that modifies a command string.  <br/> |
|**userlist** <br/> |A literal string that modifies the access rights of a specific user.  <br/> |
|**logs** <br/> |A literal string that specifies a log file recording operational errors.  <br/> |
|**default** <br/> |A literal string that is used if no identifier is specified or found.  <br/> |
| *identifier*  <br/> | A string that matches a string in the **connect** or **command** string.  <br/>  Use this section if the section header contains **connect** and the identifier string is found in the connection string.  <br/>  Use this section if the section header contains **sql** and the identifier string is found in the command string.  <br/>  Use this section if the section header contains **userlist** and the identifier string matches a **connect** section identifier.  <br/> |
   
The **DataFactory** calls the handler, passing client parameters. The handler searches for whole strings in the client parameters that match identifiers in the appropriate section headers. If a match is found, the contents of that section are applied to the client parameter. 
  
A particular section is used under the following circumstances:
  
- A **connect** section is used if the value part of the client connect string keyword, " **Data Source=** *value*  ", matches a **connect** section identifier  *.* 
    
- An **sql** section is used if the client command string contains a string that matches an **sql** section identifier. 
    
- A **connect** or **sql** section with a default parameter is used if there is no matching identifier. 
    
- A **userlist** section is used if the **userlist** section identifier matches a **connect** section identifier. If there is a match, the contents of the **userlist** section are applied to the connection governed by the **connect** section. 
    
- If the string in a connection or command string does not match the identifier in any **connect** or **sql** section header, and there is no **connect** or **sql** section header with a default parameter, then the client string is used without modification. 
    
- The **logs** section is used whenever the **DataFactory** is in operation. 
    

