---
title: "Memory Management in Excel"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: overview
keywords:
- xloper12 memory [excel 2007],managing memory in Excel,Excel stack,strings [Excel 2007], managing memory,memory management in Excel,XLOPER memory [Excel 2007],memory [Excel 2007], management guidelines
 
localization_priority: Normal
ms.assetid: 3bf5195b-6235-43cf-8795-0c7b0a63a095
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# Memory Management in Excel

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Memory management is the most important concern if you want to create efficient and stable XLLs. Failure to manage memory well can lead to a range of problems in Microsoft Excel—from minor problems such as inefficient memory allocation and initialization and small memory leaks, to major problems such as the destabilization of Excel.
  
Mismanagement of memory is the most common source of serious add-in-related problems. Therefore, you should build your project with a consistent and well-thought-through strategy on memory management. 
  
Memory management became more complex in Microsoft Office Excel 2007 with the introduction of multithreaded workbook recalculation. If you want to create and export thread-safe worksheet functions, you must manage the resulting conflicts that can occur when multiple threads compete for access.
  
There are memory considerations for the following three data structure types:
  
- **XLOPER**s and **XLOPER12**s
    
- Strings that are not in an **XLOPER** or **XLOPER12**
    
- **FP** and **FP12** arrays 
    
## XLOPER/XLOPER12 Memory

The **XLOPER**/ **XLOPER12** data structure has a few sub-types that contain pointers to blocks of memory, namely strings ( **xltypeStr**), arrays ( **xltypeMulti**) and external references ( **xltypeRef**). Note also that **xltypeMulti** arrays can contain string **XLOPER**/ **XLOPER12s** that in turn point to other blocks of memory. 
  
An **XLOPER**/ **XLOPER12** can be created in several ways: 
  
- By Excel when preparing arguments to be passed to an XLL function
    
- By Excel when returning an **XLOPER** or **XLOPER12** in a C API call 
    
- By your DLL when creating arguments to be passed to a C API call
    
- By your DLL when creating an XLL function return value
    
A block of memory within one of the memory-pointing types can be allocated in several ways:
  
- It can be a static block within your DLL outside any function code, in which case you do not have to allocate or free the memory.
    
- It can be a static block within your DLL within some function code, in which case you do not have to allocate or free the memory.
    
- It can be dynamically allocated and freed by your DLL in several possible ways: **malloc** and **free**, **new** and **delete**, and so on.
    
- It can be dynamically allocated by Excel.
    
Given the number of possible origins for **XLOPER**/ **XLOPER12** memory and the number of situations in which the **XLOPER**/ **XLOPER12** might have had that memory assigned, it is not surprising that this subject can seem very difficult. However, the complexity can be greatly reduced if you follow several rules and guidelines. 
  
### Rules for Working with XLOPER/XLOPER12

- Do not try to free memory or overwrite **XLOPERs**/ **XLOPER12**s that are passed as arguments to your XLL function. You should treat such arguments as read-only. For more information, see "Returning **XLOPER** or **XLOPER12** by Modifying Arguments in Place" in [Known Issues in Excel XLL Development](known-issues-in-excel-xll-development.md).
    
- If Excel has allocated memory for an **XLOPER**/ **XLOPER12** returned to your DLL in a call to the C API: 
    
  - You must free the memory when you no longer need the **XLOPER**/ **XLOPER12** using a call to [xlFree](xlfree.md). Do not use any other method, such as free or delete, to release the memory.
    
  - If the returned type is **xltypeMulti**, do not overwrite any **XLOPER**/ **XLOPER12**s within the array, especially if they contain strings, and especially not where you are trying to overwrite with a string.
    
  - If you want to return the **XLOPER**/ **XLOPER12** to Excel as your DLL function's return value, you must tell Excel that there is memory that Excel must release when done. 
    
- You must only call **xlFree** on an **XLOPER**/ **XLOPER12** that was created as the return value to a C API call. 
    
- If your DLL has allocated memory for an **XLOPER**/ **XLOPER12** that you want to return to Excel as your DLL function's return value, you must tell Excel that there is memory that the DLL must release. 
    
### Guidelines for Memory Management

- Be consistent in your DLL in the method that you use to allocate and release memory. Avoid mixing methods. A good approach is to wrap the method that you are using up in a memory class or structure, within which you can change the method used without altering your code in many places.
    
- When you create **xltypeMulti** arrays within your DLL, be consistent in the way that you allocate memory for strings: always dynamically allocate the memory for them or always use static memory. If you do this, when you are freeing the memory, you will know that you must either always or never free the strings. 
    
- Make deep copies of Excel-allocated memory when you are copying an Excel-created **XLOPER**/ **XLOPER12**.
    
- Do not put Excel-allocated string **XLOPER**/ **XLOPER12**s within **xltypeMulti** arrays. Make deep copies of the strings and store pointers to the copies in the array. 
    
## Freeing Excel-Allocated XLOPER/XLOPER12 Memory

Consider the following XLL command, which uses **xlGetName** to obtain a string containing the path and file name of the DLL and displays it in an alert dialog box using **xlcAlert**.
  
```cs
int WINAPI show_DLL_name(void)
{
    XLOPER12 xDllName;
    if(Excel12(xlfGetName, &amp;xDllName, 0) == xlretSuccess)
    {
        // Display the name.
        Excel12(xlcAlert, 0, 1, &amp;xDllName);
        // Free the memory that Excel allocated for the string.
        Excel12(xlFree, 0, 1, &amp;xDllName);
    }
    return 1;
}

```

When the function no longer needs the memory pointed to by **xDllName**, it can free it using a call to the [xlFree function](xlfree.md), one of the DLL-only C API functions. 
  
The **xlFree** function is fully documented in the function reference section (see [C API Functions That Can Be Called Only from a DLL or XLL](c-api-functions-that-can-be-called-only-from-a-dll-or-xll.md)), but be aware of the following:
  
- You can pass pointers to more than one **XLOPER**/ **XLOPER12**s in a single call to **xlFree**, limited only by the number of function arguments supported in the running version of Excel (30 in Excel 2003, 255 starting in Excel 2007).
    
- **xlFree** sets the contained pointer to **NULL** to ensure that an attempt to free an **XLOPER**/ **XLOPER12** that has already been freed is safe. **xlFree** is the only C API function that modifies its arguments. 
    
- You can safely call **xlFree** on any **XLOPER**/ **XLOPER12** used for the return value of a call to the C API, regardless of whether it contains a pointer to memory. 
    
## Returning XLOPER/XLOPER12s to be freed by Excel

Suppose you wanted to modify the example command in the previous section and change it to a worksheet function that returns the DLL path and file name when passed a **Boolean** **true** argument, and **#N/A** otherwise. Clearly you cannot call **xlFree** to release the string memory before returning it to Excel. However, if it is not freed at some point, the add-in will leak memory every time the function is called. To work around this problem, you can set a bit in the **xltype** field of the **XLOPER**/ **XLOPER12**, defined as **xlbitXLFree** in xlcall.h. Setting this tells Excel that it must free the returned memory when it has finished copying the value out. 
  
### Example

The following code example shows the XLL command in the previous section converted into an XLL worksheet function.
  
```cs
LPXLOPER12 WINAPI get_DLL_name(int calculation_trigger)
{
    static XLOPER12 xRtnValue; // Not thread-safe
    Excel12(xlfGetName, &amp;xRtnValue, 0);
// If xlfGetName failed, xRtnValue will be #VALUE!
    if(xRtnValue.xltype == xltypeStr)
    {
// Tell Excel to free the string memory after
// it has copied out the return value.
        xRtnValue.xltype |= xlbitXLFree;
    }
    return &amp;xRtnValue;
}
```

XLL functions that use **XLOPER**/ **XLOPER12**s must be declared as taking and returning pointers to **XLOPER**/ **XLOPER12**s. The use in this example of a static **XLOPER12** within the function is not thread safe. You could incorrectly register this function as thread safe, but you would risk **xRtnValue** being overwritten by one thread before another thread had finished with it. 
  
You must set **xlbitXLFree** after the call to the Excel callback that allocates it. If you set it before this, it is overwritten and does not have the effect that you want. If you intend to use the value as an argument in a call to another C API function before returning it to the worksheet, you should set this bit after any such call. Otherwise, you will confuse functions that do not mask this bit before checking the **XLOPER**/ **XLLOPER12** type. 
  
## Returning XLOPER/XLOPER12s to be freed by the DLL

A similar problem to this occurs when your XLL has allocated memory for an **XLOPER**/ **XLOPER12** and wants to return it to Excel. Excel recognizes another bit that can be set in the **xltype** field of the **XLOPER**/ **XLOPER12**, defined as **xlbitDLLFree** in xlcall.h. 
  
When Excel receives **an XLOPER**/ **XLOPER12** with this bit set, it tries to call a function that should be exported by the XLL called [xlAutoFree](xlautofree-xlautofree12.md) (for **XLOPER**s) or **xlAutoFree12** (for **XLOPER12**s). This function is described more fully in the function reference (see [Add-in Manager and XLL Interface Functions](add-in-manager-and-xll-interface-functions.md)), but an example minimal implementation is given here. Its purpose is to free the **XLOPER**/ **XLOPER12** memory in a way that is consistent with how it was originally allocated. 
  
### Examples

The following example function does the same as the previous function except that it includes the text "The full pathname for this DLL is " before the DLL name.
  
```cs
#include <string.h>
LPXLOPER12 WINAPI get_DLL_name_2(int calculation_trigger)
{
    static XLOPER12 xRtnValue; // Not thread-safe
    Excel12(xlfGetName, &amp;xRtnValue, 0);
// If xlfGetName failed, xRtnValue will be #VALUE!
    if(xRtnValue.xltype != xltypeStr)
        return &amp;xRtnValue;
// Make a copy of the DLL path and file name.
    wchar_t *leader = L"The full pathname for this DLL is ";
    size_t leader_len = wcslen(leader);
    size_t dllname_len = xRtnValue.val.str[0];
    size_t msg_len = leader_len + dllname_len;
    wchar_t *msg_text = (wchar_t *)malloc(msg_len + 1);
    wcsncpy_s(msg_text + 1, leader, leader_len);
    wcsncpy_s(msg_text + 1 + leader_len, xRtnValue.val.str + 1,
        dllname_len);
    msg_text[0] = msg_len;
// Now the original string has been copied Excel can free it.
    Excel12(xlFree, 0, 1, &amp;xRtnValue);
// Now reuse the XLOPER12 for the new string.
    xRtnValue.val.str = msg_text;
// Tell Excel to call back into the DLL to free the string
// memory after it has copied out the return value.
    xRtnValue.xltype     = xltypeStr | xlbitDLLFree;
    return &amp;xRtnValue;
}
```

A minimally sufficient implementation of **xlAutoFree12** in the XLL that exported the previous function would be as follows. 
  
```cs
void WINAPI xlAutoFree12(LPXLOPER12 p_oper)
{
    if(p_oper->xltype == (xltypeStr | xlbitDLLFree))
        free(p_oper->val.str);
}
```

This implementation is only sufficient if the XLL only returns **XLOPER12** strings, and those strings are only allocated using **malloc**. Note that the test 
  
 ` if(p_oper->xltype == xltypeStr) `
  
would fail in this case because **xlbitDLLFree** is set. 
  
In general, **xlAutoFree** and **xlAutoFree12** should be implemented so that they free memory associated with XLL-created **xltypeMulti** arrays and **xltypeRef** external references. 
  
You might decide to implement your XLL functions so that they ALL return dynamically allocated **XLOPER**s and **XLOPER12**s. In this case, you would need to set **xlbitDLLFree** on all such **XLOPER**s and **XLOPER12**s regardless of the sub-type. You would also need to implement **xlAutoFree** and **xlAutoFree12** so that this memory was freed and also any memory pointed to within the **XLOPER**/ **XLOPER12**. This approach is one way to make the return value thread safe. For example, the previous function could be rewritten as follows.
  
```cs
#include <string.h>
LPXLOPER12 WINAPI get_DLL_name_3(int calculation_trigger)
{
// Thread-safe
    LPXLOPER12 pxRtnValue = (LPXLOPER12)malloc(sizeof(XLOPER12));
    Excel12(xlfGetName, pxRtnValue, 0);
// If xlfGetName failed, pxRtnValue will be #VALUE!
    if(pxRtnValue->xltype != xltypeStr)
    {
// Even though an error type does not point to memory,
// Excel needs to pass this oper to xlAutoFree12 to
// free pxRtnValue itself.
        pxRtnValue->xltype |= xlbitDLLFree;
        return pxRtnValue;
    }
// Make a copy of the DLL path and file name.
    wchar_t *leader = L"The full pathname for this DLL is ";
    size_t leader_len = wcslen(leader);
    size_t dllname_len = pxRtnValue->val.str[0];
    size_t msg_len = leader_len + dllname_len;
    wchar_t *msg_text = (wchar_t *)malloc(msg_len + 1);
    wcsncpy_s(msg_text + 1, leader, leader_len);
    wcsncpy_s(msg_text + 1 + leader_len, pxRtnValue->val.str + 1,
        dllname_len);
    msg_text[0] = msg_len;
// Now the original string has been copied Excel can free it.
    Excel12(xlFree, 0, 1, pxRtnValue);
// Now reuse the XLOPER12 for the new string.
    pxRtnValue->val.str = msg_text;
    pxRtnValue->xltype = xltypeStr | xlbitDLLFree;
    return pxRtnValue;
}
void WINAPI xlAutoFree12(LPXLOPER12 p_oper)
{
    if(p_oper->xltype == (xltypeStr | xlbitDLLFree))
        free(p_oper->val.str);
    free(p_oper);
}
```

For more information about **xlAutoFree** and **xlAutoFree12**, see [xlAutoFree/xlAutoFree12](xlautofree-xlautofree12.md).
  
## Returning Modify-in-Place Arguments

Excel allows an XLL function to return a value by modifying an argument in place. You can only do this with an argument passed in as a pointer. To work like this, the function must be registered in a way that tells Excel which argument will be modified. 
  
This method of returning a value is supported for all data types that can be passed by pointer but is especially useful for the following types:
  
- Length-counted and null-terminated ASCII byte strings
    
- Length-counted and null-terminated Unicode wide character strings (starting in Excel 2007)
    
- **FP** floating-point arrays 
    
- **FP12** floating-point arrays (starting in Excel 2007) 
    
> [!NOTE]
> You should not try to return **XLOPER**s or **XLOPER12**s in this manner. For more information, see [Known Issues in Excel XLL Development](known-issues-in-excel-xll-development.md). 
  
The advantage of using this technique, instead of just using the return statement, is that Excel allocates the memory for the return values. Once Excel has finished reading the returned data, it releases the memory. This takes the memory management tasks away from the XLL function. This technique is thread safe: If called concurrently by Excel on different threads, each function call on each thread has its own buffer.
  
It is useful for the previously listed data types in particular because the mechanism for calling back into the DLL to free memory post-return that exists for **XLOPER**/ **XLOPER12**s does not exist for simple strings and **FP**/ **FP12** arrays. Therefore, when returning a DLL-created string or floating-point array, you have the following choices: 
  
- Set a persistent pointer to a dynamically allocated buffer, return the pointer. On the next call to the function (1) check that the pointer is not null, (2) free the resources allocated on the previous call and reset the pointer to null, (3) reuse the pointer for a newly allocated block of memory.
    
- Create your strings and arrays in a static buffer that does not need to be freed, and return a pointer to that.
    
- Modify an argument in place, writing your string or array directly into the space set aside by Excel.
    
Otherwise, you must create an **XLOPER**/ **XLOPER12**, and use **xlbitDLLFree** and **xlAutoFree**/ **xlAutoFree12** to release the resources. 
  
The last option might be the simplest in those cases in which you are being passed an argument of the same type as the return value. The key point to remember is that the buffer sizes are limited and you must be very careful not to overrun them. Getting this wrong could crash Excel. Buffer sizes for strings and **FP**/ **FP12** arrays are discussed next. 
  
## Strings

Problems with the management of string memory are arguably the most common cause of instability in applications and add-ins. It is understandable perhaps, given the variety of ways in which strings are handled: null-terminated or length-counted (or both); static or dynamic buffers; fixed length or almost unlimited length; operating-system managed memory (for example, OLE Bstr) or unmanaged strings; and so on.
  
C/C++ programmers are most familiar with null-terminated strings. The standard C library is designed to work with such strings. Static string literals in code are compiled into null-terminated strings. Alternatively, Excel works with length-counted strings that are not in general null-terminated. The combination of these facts requires a clear and consistent approach within your DLL/XLL regarding how you handle strings and string memory.
  
The most common problems are as follows:
  
- The passing of a null or invalid pointer to a function that expects a valid pointer and does not or cannot check the pointer's validity itself.
    
- The overrunning of the bounds of a string buffer by a function that does not or cannot check the length of the buffer against the length of the string being written.
    
- Trying to free string buffer memory that is either static, or has been freed already, or was not allocated in a way that is consistent with how it is being freed.
    
- Memory leaks that result from strings being allocated and then not freed, usually in a frequently called function.
    
### Rules for Strings

As with **XLOPER**/ **XLOPER**s, there are rules and guidelines you should follow. The guidelines are the same as given in the previous section. The rules here are an extension of the rules specifically for strings.
  
 **Rules:**
  
- Do not try to free memory or overwrite string **XLOPER**/ **XLOPER12**s or simple length-counted or null-terminated strings passed as arguments to your XLL function. You should treat such arguments as read-only.
    
- Where Excel allocates memory for a string **XLOPER**/ **XLOPER12** for the return value of a C API callback function, use **xlFree** to free it, or set **xlbitXLFree** if returning it to Excel from an XLL function. 
    
- Where your DLL dynamically allocates a string buffer for an **XLOPER**/ **XLOPER12**, free it in a way consistent with how you allocated it when done, or set **xlbitDLLFree** if returning it to Excel from an XLL function and then free it in **xlAutoFree**/ **xlAutoFree12**.
    
- If Excel has allocated memory for an **xltypeMulti** array returned to your DLL in a call to the C API, do not overwrite any string **XLOPER**/ **XLOPER12**s within the array. Such arrays must only be freed using **xlFree**, or, if being returned by an XLL function, by setting **xlbitXLFree**.
    
### String Types Supported

**C API xltypeStr XLOPER/XLOPER12s**

|**Byte strings: **XLOPER****|**Wide character strings: **XLOPER12****|
|:-----|:-----|
|All versions of Excel  <br/> |Starting in Excel 2007  <br/> |
|Max length: 255 extended ASCII bytes  <br/> |Maximum length 32,767 Unicode chars  <br/> |
|First (unsigned) byte = length  <br/> |First Unicode character = length  <br/> |
   
> [!IMPORTANT]
> Do not assume null termination of **XLOPER** or **XLOPER12** strings. 
  
**C/C++ strings**

|**Byte strings**|**Wide character strings**|
|:-----|:-----|
|Null-terminated ( **char** *) "C" Max length: 255 extended ASCII bytes  <br/> |Null-terminated ( **wchar_t** *) "C%" Maximum length 32,767 Unicode chars  <br/> |
|Length-counted ( **unsigned char** *) "D"  <br/> |Length-counted ( **wchar_t** *) "D%"  <br/> |
   
### Strings in xltypeMulti XLOPER/XLOPER12 Arrays

In several cases, Excel creates an **xltypeMulti** array for use in your DLL/XLL. Several of the XLM information functions return such arrays. For example, the C API function **xlfGetWorkspace**, when passed the argument  *44*  , returns an array containing strings that describe all the currently registered DLL procedures. The C API function **xlfDialogBox** returns a modified copy of its array argument, containing deep copies of the strings. Perhaps the most common way an XLL encounters an **xltypeMulti** array is where it has been passed as an argument to an XLL function, or it has been coerced to this type from a range reference. In these latter cases, Excel creates deep copies of the strings in the source cells and points to these within the array. 
  
Where you want to modify these strings in your DLL, you should make your own deep copies. When you are creating your own **xltypeMulti** arrays, you should not place Excel-allocated string **XLOPER**/ **XLOPER12**s within them. This risks you not freeing them correctly later, or not freeing them at all. Again, you should make deep copies of the strings and store pointers to the copies in the array.
  
 **Examples**
  
The following example function creates a dynamically allocated copy of a length-counted Unicode string. Note that the caller must ultimately free the memory allocated in this example using **delete**[], and that the source string is not assumed to be null terminated. The copy string is truncated if necessary for safety, and is not null terminated.
  
```cs
#include <string.h>
#define MAX_V12_STRBUFFLEN    32678
    
wchar_t * deep_copy_wcs(const wchar_t *p_source)
{
    if(!p_source)
        return NULL;
    size_t source_len = p_source[0];
    bool truncated = false;
    if(source_len >= MAX_V12_STRBUFFLEN)
    {
        source_len = MAX_V12_STRBUFFLEN - 1; // Truncate the copy
        truncated = true;
    }
    wchar_t *p_copy = new wchar_t[source_len + 1];
    wcsncpy_s(p_copy, p_source, source_len + 1);
    if(truncated)
        p_copy[0] = source_len;
    return p_copy;
}
```

This function can then be safely used to copy an **XLOPER12**, as shown in the following exportable XLL function that returns a copy of its argument if it is a string. All other types are returned as a zero-length string. Note that ranges are not handled—the function returns **#VALUE!**. The function must be registered as taking a type U argument so that references are passed in as values. This is equivalent to the built-in worksheet function **T()** except that **AsText** also converts errors to zero-length strings. This code example assumes that **xlAutoFree12** frees the passed-in pointer, and also its contents, using **delete**.
  
```cs
LPXLOPER12 WINAPI AsText(LPXLOPER12 pArg)
{
    LPXLOPER12 pRtnVal = new XLOPER12;
// If the input was an array, only operate on the top-left element.
    LPXLOPER *pTemp;
    if(pArg->xltype == xltypeMulti)
        pTemp = pArg->val.array.lparray;
    else
        pTemp = pArg;
    switch(pTemp->xltype)
    {
        case xltypeErr:
        case xltypeNum:
        case xltypeMissing:
        case xltypeNil:
        case xltypeBool:
            pRtnVal->xltype = xltypeStr | xlbitDLLFree;
            pRtnVal->val.str = deep_copy_wcs(L"\000");
            return pRtnVal;
        case xltypeStr:
            pRtnVal->xltype = xltypeStr | xlbitDLLFree;
            pRtnVal->val.str = deep_copy_wcs(pTemp->val.str);
            return pRtnVal;
        
        default: // xltypeSRef, xltypeRef, xltypeFlow, xltypeInt
            pRtnVal->xltype = xltypeErr | xlbitDLLFree;
            pRtnVal->val.err = xlerrValue;
            return pRtnVal;
    }
}
```

### Returning Modify-in-Place String Arguments

Arguments registered as types **F**, **G**, **F%**, and **G%** can be modified in place. When Excel is preparing string arguments for these types, it creates a maximum length buffer. Then it copies the argument string into that, even if this string is very much shorter. This enables the XLL function to write its return value directly into the same memory. 
  
Buffer sizes set apart for these types are as follows:
  
- **Byte strings:** 256 bytes including the length counter (type G) or null-termination (type F). 
    
- **Unicode strings:** 32,768 wide characters (65,536 bytes) including the length counter (type G%) or null-termination (type F%). 
    
> [!NOTE]
> You cannot call such a function directly from Visual Basic for Applications (VBA) because you cannot ensure that a sufficiently large buffer has been allocated. You can only call such a function from another DLL safely if you have explicitly passed a big enough buffer. 
  
Here is an example of an XLL function that reverses a passed-in null-terminated wide character string using the standard library function **wcsrev**. The argument in this case would be registered as type **F%**.
  
```cs
void WINAPI reverse_text_xl12(wchar_t *text)
{
    _wcsrev(text);
}
```

## Persistent Storage (Binary Names)

Binary names are defined and associated with blocks of binary, that is, unstructured, data that is stored together with the workbook. They are created using the function [xlDefineBinaryName](xldefinebinaryname.md), and the data is retrieved using the function [xlGetBinaryName](xlgetbinaryname.md). Both functions are described in more detail in the function reference (see [C API Functions That Can Be Called Only from a DLL or XLL](c-api-functions-that-can-be-called-only-from-a-dll-or-xll.md)), and both use the **xltypeBigData** **XLOPER**/ **XLOPER12**. 
  
For information about known issues that limit the practical applications of binary names, see [Known Issues in Excel XLL Development](known-issues-in-excel-xll-development.md).
  
## Excel Stack

Excel shares its stack space with all the DLLs it has loaded. Stack space is usually more than adequate for ordinary use, and you do not need to be concerned about it as long as you follow a few guidelines: 
  
- Do not pass very large structures as arguments to functions by value on the stack. Pass pointers or references instead.
    
- Do not return large structures on the stack. Return pointers to static or dynamically allocated memory, or use arguments passed by reference.
    
- Do not declare very large automatic variable structures in the function code. If you need them, declare them as static.
    
- Do not call functions recursively unless you are sure the depth of recursion will always be shallow. Try using a loop instead.
    
When a DLL calls back into Excel using the C API, Excel first checks whether there is enough space on the stack for the worst-case usage call that could be made. If it thinks there might be insufficient room, it will fail the call to be safe, even though there might actually have been enough space for that particular call. In this case, the callbacks return the code **xlretFailed**. For ordinary use of the C API and the stack, this is an unlikely cause of the failure of a C API call.
  
If you are concerned, or just curious, or you want to eliminate lack of stack space as a reason for an unexplained failure, you can find out how much stack space there is with a call to the [xlStack](xlstack.md) function. 
  
## See also

#### Concepts

[Multithreaded Recalculation in Excel](multithreaded-recalculation-in-excel.md)
  
[Multithreading and Memory Contention in Excel](multithreading-and-memory-contention-in-excel.md)
  
[Developing Excel XLLs](developing-excel-xlls.md)

