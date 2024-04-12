---
title: "InitFramework"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- InitFramework
keywords:
- initframework function [excel 2007]
 
ms.localizationpriority: medium
ms.assetid: c472a14a-92a6-46f6-924c-db8d6199d6fb

---

# InitFramework

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Framework library function that initializes the Framework library, which simply initializes the temporary **XLOPER**/ **XLOPER12** memory data structures, freeing any memory that has already been allocated. 
  
```cs
short WINAPI InitFramework(void);
```

## Parameters

This function takes no arguments.
  
## Return value

This function does not return a value.
  
## Example

This example uses the **InitFramework** function to free all temporary memory. 
  
 `\SAMPLES\EXAMPLE\EXAMPLE.C`
  
```cs
short WINAPI InitFrameworkExample(void)
{
    InitFramework();
    return 1;
}
```

## See also



[Functions in the Framework Library](functions-in-the-framework-library.md)

