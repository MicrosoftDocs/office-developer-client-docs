---
title: "Form Configuration File [Verbs] Section"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: e7e1f371-9e9a-4bec-a0b3-87753a16f5e0
 
 
---

# Form Configuration File [Verbs] Section

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The **[Verbs]** section lists the complete set of verbs supported by the form. The format of the **[Verbs]** section is: 
  
 **[Verbs]**
  
 **Verb1** =  _string_
  
Following is an example of a **[Verbs]** section. 
  
```cpp
[Verbs]
Verb1=1
Verb2=2

```

Each verb is defined in a separate **[Verb.** _string_ **]** section. A **[Verb.** _string_ **]** section describes a single verb offered by the form. The **DisplayName** entry in a **[Verb.** _string_ **]** section specifies the command name displayed in the user interface. The **Code** entry corresponds to the verb number passed in the [IMAPIForm::DoVerb](imapiform-doverb.md) method. The syntax for the **[Verb.** _string_ **]** section is: 
  
 **[Verb.** _string_ **]**
  
 **DisplayName** =  _displayed string_
  
 **Code** =  _integer_
  
 **Flags** =  _integer_
  
 **Attribs** =  _integer_
  
Following is an example of a **[Verb.** _string_ **]** section. 
  
```cpp
[Verb.1]
DisplayName=Reply
code=1
Flags=0
Attribs=2
[Verb.2]
DisplayName=Delete
Code=2
Flags=0
Attribs=2

```

Verbs listed in this section are retrieved by a client using the [IMAPIFormInfo::CalcVerbSet method](imapiforminfo-calcverbset.md). Verbs are activated by calling the form's [IMAPIForm::DoVerb](imapiform-doverb.md) method and passing it the code number of the verb to be performed. 
  

