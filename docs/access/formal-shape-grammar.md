---
title: "Formal Shape Grammar"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: a3220569-8804-3dc3-7f9f-b4f8cdab1316
description: "This is the formal grammar for creating any shape command:"
---

# Formal Shape Grammar

This is the formal grammar for creating any shape command:
  
- Required grammatical terms are text strings delimited by angle brackets ("\<\>").
    
- Optional terms are delimited by square brackets ("[ ]").
    
- Alternatives are indicated by a virgule ("|").
    
- Repeating alternatives are indicated by an ellipsis ("...").
    
-  *Alpha*  indicates a string of alphabetical letters. 
    
-  *Digit*  indicates a string of numbers. 
    
-  *Unicode-digit*  indicates a string of unicode digits. 
    
All other terms are literals.
  
|**Term**|**Definition**|
|:-----|:-----|
|\<shape-command\>  <br/> |SHAPE [\<table-exp\> [[AS] \<alias\>]][\<shape-action\>]  <br/> |
|\<table-exp\>  <br/> |{<provider-command-text>} |
  
(<shape-command>) |
  
TABLE <quoted-name> |
  
<quoted-name>  <br/> |
|\<shape-action\>  <br/> |APPEND \<aliased-field-list\> |  <br/> COMPUTE \<aliased-field-list\> [BY \<field-list\>]  <br/> |
|\<aliased-field-list\>  <br/> |\<aliased-field\> [, \<aliased-field...\>]  <br/> |
|\<aliased-field\>  <br/> |\<field-exp\> [[AS] \<alias\>]  <br/> |
|\<field-exp\>  <br/> |(\<relation-exp\>) |  <br/> \<calculated-exp\> |  <br/> \<aggregate-exp\> |  <br/> \<new-exp\>  <br/> |
|\<relation_exp\>  <br/> |\<table-exp\> [[AS] \<alias\>]  <br/> \<table-exp\> [[AS] \<alias\>]  <br/> |
|\<relation-cond-list\>  <br/> |\<relation-cond\> [, \<relation-cond\>...]  <br/> |
|\<relation-cond\>  <br/> |\<field-name\> TO \<child-ref\>  <br/> |
|\<child-ref\>  <br/> |\<field-name\> |  <br/> PARAMETER \<param-ref\>  <br/> |
|\<param-ref\>  <br/> |\<number\>  <br/> |
|\<field-list\>  <br/> |\<field-name\> [, \<field-name\>]  <br/> |
|\<aggregate-exp\>  <br/> |SUM(\<qualified-field-name\>) |  <br/> AVG(\<qualified-field-name\>) |  <br/> MIN(\<qualified-field-name\>) |  <br/> MAX(\<qualified-field-name\>) |  <br/> COUNT(\<qualified-alias\> | \<qualified-name\>) |  <br/> STDEV(\<qualified-field-name\>) |  <br/> ANY(\<qualified-field-name\>)  <br/> |
|\<calculated-exp\>  <br/> |CALC(\<expression\>)  <br/> |
|\<qualified-field-name\>  <br/> |\<alias\>.[\<alias\>...]\<field-name\>  <br/> |
|\<alias\>  <br/> |\<quoted-name\>  <br/> |
|\<field-name\>  <br/> |\<quoted-name\> [[AS] \<alias\>]  <br/> |
|\<quoted-name\>  <br/> |"\<string\>" |  <br/> '\<string\>' |  <br/> [\<string\>] |  <br/> \<name\>  <br/> |
|\<qualified-name\>  <br/> |alias[.alias...]  <br/> |
|\<name\>  <br/> |alpha [ alpha | digit | _ | # | : | ...]  <br/> |
|\<number\>  <br/> |digit [digit...]  <br/> |
|\<new-exp\>  <br/> |NEW \<field-type\> [(\<number\> [, \<number\>])]  <br/> |
|\<field-type\>  <br/> |An OLE DB or ADO data type.  <br/> |
|\<string\>  <br/> |unicode-char [unicode-char...]  <br/> |
|\<expression\>  <br/> |A Visual Basic for Applications expression whose operands are other non-CALC columns in the same row.  <br/> |
   

