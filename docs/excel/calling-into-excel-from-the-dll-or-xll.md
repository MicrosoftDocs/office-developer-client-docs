---
title: "Calling into Excel from the DLL or XLL"
manager: lindalu
ms.date: 01/22/2022
ms.audience: Developer
ms.topic: overview
keywords:
- dialog boxes [excel 2007], invoking excel commands, DLLs [Excel 2007], calling into Excel,passing arguments to C API functions [Excel 2007], commands [Excel 2007], invoking with dialog boxes,commands [Excel 2007], accessible from DLL/XLL,Excel4 function [Excel 2007],Excel12 function [Excel 2007], XLCallVer function [Excel 2007], operRes argument [Excel 2007], functions [Excel 2007], accessible from DLL/XLL,Excel12v function [Excel 2007],DLL-only functions [Excel 2007],C API [Excel 2007], passing arguments,count argument [Excel 2007], commands [Excel 2007], calling in international versions,DLL-only commands [Excel 2007], international versions [Excel 2007], calling functions and commands, XLLs [Excel 2007], calling into Excel, Excel 4v function [Excel 2007], xlfn argument [Excel 2007], functions [Excel 2007], calling in international versions
ms.assetid: 616e3def-e4ec-4f3c-bc65-3b92710da1e6

ms.localizationpriority: high
---

# Calling into Excel from the DLL or XLL

**Applies to**: Excel 2013 | Office 2013 | Visual Studio
  
Microsoft Excel enables your DLL to access built-in Excel commands, worksheet functions, and macro sheet functions. These are available both from DLL commands and functions called from Visual Basic for Applications (VBA), and from registered XLL commands and functions called directly by Excel.
  
## Excel4, Excel4v, Excel12, and Excel12v Functions

Excel enables your DLL to access the commands and functions through the callback functions [Excel4](excel4-excel12.md), [Excel4v](excel4v-excel12v.md), [Excel12](excel4-excel12.md), and [Excel12v](excel4v-excel12v.md).
  
The **Excel4** and **Excel4v** functions were introduced in Excel version 4. They work with the **XLOPER** data structure. Excel 2007 introduced two new callback functions, **Excel12** and **Excel12v**, which work with the **XLOPER12** data structure. The **Excel4** and **Excel4v** functions are exported by the library Xlcall32.lib, which must be included in your DLL or XLL project. **Excel12** and **Excel12v** are included in the SDK C++ source file Xlcall.cpp, which must be included in your project if you want to access Excel functionality by using **XLOPER12** structures.
  
The following code shows the function prototypes for these four functions. The first three arguments are the same except that the second argument is a pointer to an **XLOPER** in the first pair and a pointer to an **XLOPER12** in the second pair. The calling convention is **_cdecl** in **Excel4** and **Excel12** to permit the variable argument lists. The ellipsis represents pointers to **XLOPER** values for **Excel4** and **XLOPER12** values for **Excel12**. The number of pointers equals the value of the  _count_ parameter.
  
**All versions of Excel**
  
 `int _cdecl Excel4(int xlfn, LPXLOPER operRes, int count,... );`
  
 `int pascal Excel4v(int xlfn, LPXLOPER operRes, int count, LPXLOPER opers[]);`
  
**Starting in Excel 2007**
  
 `int _cdecl Excel12(int xlfn, LPXLOPER12 operRes, int count,... );`
  
 `int pascal Excel12v(int xlfn, LPXLOPER12 operRes, int count, LPXLOPER12 opers[]);`
  
For the DLL to be able to call **Excel4**, **Excel4v**, **Excel12**, or **Excel12v**, Excel must pass control to the DLL. This means that these C API callbacks can be called only in the following scenarios:
  
- From within an XLL command that Excel has called directly or via VBA.

- From within an XLL worksheet or macro sheet function that Excel has called directly or via VBA.

You cannot call the Excel C API in the following scenarios:
  
- From an operating system event (for example, from the [DllMain](/windows/win32/dlls/dllmain.md) function).

- From a background thread that your DLL created.

### Return values

All four of these functions return an integer value that informs the caller whether the function or command was called successfully. The values returned can be any of the following:
  
|**Return value**|**Defined in Xlcall.h as**|**Description**|
|:-----|:-----|:-----|
|0  <br/> |**xlretSuccess** <br/> |The function or command executed successfully. This does not mean that the execution was error free. For example, **Excel4** could return **xlretSuccess** when calling the function **FIND**, even though it evaluated to **#VALUE!** because the search text could not be found. You should inspect the type and value of the returned **XLOPER/XLOPER12** where this is a possibility.  <br/> |
|1  <br/> |**xlretAbort** <br/> |A command macro was stopped by the user clicking the **CANCEL** button or pressing the ESC key.  <br/> |
|2  <br/> |**xlretInvXlfn** <br/> |The supplied function or command code is not valid. This error can occur when the calling function does not have permission to call the function or command. For example, a worksheet function cannot call a macro sheet information function or a command function.  <br/> |
|4  <br/> |**xlretInvCount** <br/> |The number of arguments supplied in the call is not correct.  <br/> |
|8  <br/> |**xlretInvXloper** <br/> |One or more of the argument **XLOPER** or **XLOPER12** values are not properly formed or populated.  <br/> |
|16  <br/> |**xlretStackOvfl** <br/> |Excel detected a risk that the operation might overflow its stack and, therefore, did not call the function.  <br/> |
|32  <br/> |**xlretFailed** <br/> |The command or function failed for a reason not described by one of the other return values. An operation that would require too much memory, for example, would fail with this error. This could happen during an attempt to convert a very large reference to an **xltypeMulti** array by using the [xlCoerce](xlcoerce.md) function.  <br/> |
|64  <br/> |**xlretUncalced** <br/> |The operation attempted to retrieve the value of an uncalculated cell. To preserve recalculation integrity in Excel, worksheet functions are not permitted to do this. However, XLL commands and functions registered as macro sheet functions are permitted to access uncalculated cell values.  <br/> |
|128  <br/> |**xlretNotThreadSafe** <br/> |(Starting in Excel 2007) An XLL worksheet function registered as thread safe attempted to call a C API function that is not thread safe. For example, a thread-safe function cannot call the XLM function **xlfGetCell**.  <br/> |
|256  <br/> |**xlRetInvAsynchronousContext** <br/> |(Starting in Excel 2010) The asynchronous function handle is invalid.  <br/> |
|512  <br/> |**xlretNotClusterSafe** <br/> |(Starting in Excel 2010) The call is not supported on clusters.  <br/> |
   
If the function returns one of the failure values in the table (that is, it does not return **xlretSuccess**), the **XLOPER** or **XLOPER12** return value will also be set to **#VALUE!**. In certain circumstances, checking for this might be a sufficient test of success, but you should note that a call can return both **xlretSuccess** and **#VALUE!**.
  
If a call to the C API results in either **xlretUncalced** or **xlretAbort**, your DLL or XLL code should return control to Excel before making any other C API calls (other than calls to the [xlfree](xlfree.md) function to release Excel-allocated memory resources in **XLOPER** and **XLOPER12** values).
  
### Command or Function Enumeration Argument: xlfn

The  _xlfn_ argument is the first argument to the callback functions and is a 32-bit signed integer. Its value should be one of the function or command enumerations defined in the SDK header file Xlcall.h, as shown in the following example. 
  
```cs
// Excel function numbers. 
#define xlfCount 0
#define xlfIsna 2
#define xlfIserror 3
#define xlfSum 4
#define xlfAverage 5
#define xlfMin 6
#define xlfMax 7
#define xlfRow 8
#define xlfColumn 9
#define xlfNa 10
...
// Excel command numbers. 
#define xlcBeep (0 | xlCommand)
#define xlcOpen (1 | xlCommand)
#define xlcOpenLinks (2 | xlCommand)
#define xlcCloseAll (3 | xlCommand)
#define xlcSave (4 | xlCommand)
#define xlcSaveAs (5 | xlCommand)
#define xlcFileDelete (6 | xlCommand)
#define xlcPageSetup (7 | xlCommand)
#define xlcPrint (8 | xlCommand)
#define xlcPrinterSetup (9 | xlCommand)
...
```

All worksheet and macro sheet functions are in the range from 0 (**xlfCount**) through 0x0fff hexadecimal, although the highest assigned number in Excel 2013 is 547 decimal, 0x0223 hexadecimal (**xlfFloor_precise**).
  
All command functions are in the range from 0x8000 hexadecimal (**xlcBeep**) through 0x8fff hexadecimal, although the highest assigned number in Excel 2013 is 0x8328 hexadecimal (**xlcHideallInkannots**). These are defined in the header file as `(n | xlCommand)` where `n` is a decimal number greater than or equal to 0 and **xlCommand** is defined as 0x8000 hexadecimal.
  
### Invoking Excel Commands that Use Dialog Boxes

Some of the command codes correspond to actions in Excel that use dialog boxes. For example, **xlcFileDelete** takes a single argument: a file name or mask. This can be invoked with the dialog box so that the user has the opportunity to cancel or modify the delete operation. It can also be called without the dialog box, in which case the file or files are deleted without any further interaction, assuming they exist and the caller has permission. To call such commands in their dialog box form, the command enumeration must be combined by using the bitwise OR operation with 0x1000 (**xlPrompt**).
  
The following code example deletes files in the current directory matching the mask my_data\*.bak, displaying a dialog box only if the argument is true.
  
```cs
bool delete_my_backup_files(bool show_dialog)
{
    XLOPER12 xResult, xFilter;
    xFilter.xltype = xltypeStr;
    xFilter.val.str = L"\014my_data*.bak"; // String length: 14 octal
    int cmd;
    if(show_dialog)
        cmd = xlcFileDelete | xlPrompt;
    else
        cmd = xlcFileDelete;
// xResult should be Boolean TRUE if successful, in which
// case return true; otherwise, false.
    return (Excel12(cmd, &xResult, 1, &xFilter) == xlretSuccess
        && xResult.xltype == xltypeBool
        && xResult.val.xbool == 1);
}
```

### Calling Functions and Commands in International Versions

You can configure Excel to display functions and XLM command names in a variety of languages. Some C API commands and functions operate on strings that are interpreted as function or command names. For example, **xlcFormula** takes a string argument that is intended to be placed in a specified cell. For your add-in to work with all language settings, you can supply the English string names and set the bit 0x2000 (**xlIntl**) in the function or command enumeration.
  
The following code example places the equivalent of `=SUM(X1:X100)` in cell A2 on the active sheet. Note that it uses the Framework function, **TempActiveRef**, to create a temporary external reference **XLOPER**. The formula will appear in A2 in the correct locale-determined language (for example, `=SOMME(X1:X100)` if the language is French).
  
```cs
int WINAPI InternationlExample(void)
{
    XLOPER12 xSum, xResult;
    xSum.xltype = xltypeStr;
    xSum.val.str = L"\015=SUM(X1:X100)";
    Excel12(xlcFormula | xlIntl, &xResult, 2,
        &xSum, TempActiveRef(2,2,1,1));
    return 1;
}

```

> [!NOTE]
> Because the result of the call to **Excel12** is not required, zero (NULL) could be passed as the second argument instead of the address of **xResult**. This is discussed more in the next section. 
  
### DLL-Only Functions and Commands

Excel supports a small number of functions that are only accessible from a DLL or XLL. These are defined in the header file as `(n | xlSpecial)` where `n` is a decimal number greater than or equal to 0 and `xlSpecial` is defined as 0x4000 hexadecimal. These functions are listed in the following table and documented in the [API Function Reference](excel-xll-sdk-api-function-reference.md).
  
||||
|:-----|:-----|:-----|
|[xlFree](xlfree.md) <br/> |0 | xlSpecial  <br/> |Frees Excel-allocated memory resources.  <br/> |
|[xlStack](xlstack.md) <br/> |1 | xlSpecial  <br/> |Returns the free space on the Excel stack.  <br/> |
|[xlCoerce](xlcoerce.md) <br/> |2 | xlSpecial  <br/> |Converts between **XLOPER** and **XLOPER12** types  <br/> |
|[xlSet](xlset.md) <br/> |3 | xlSpecial  <br/> |Provides a fast method of setting cell values.  <br/> |
|[xlSheetId](xlsheetid.md) <br/> |4 | xlSpecial  <br/> |Obtains a worksheet name from its internal ID.  <br/> |
|[xlSheetNm](xlsheetnm.md) <br/> |5 | xlSpecial  <br/> |Obtains a worksheet internal ID from its name.  <br/> |
|[xlAbort](xlabort.md) <br/> |6 | xlSpecial  <br/> |Verifies whether the user clicked the **CANCEL** button or pressed the ESC key.  <br/> |
|[xlGetInst](xlgetinst.md) <br/> |7 | xlSpecial  <br/> |Gets the Excel instance handle.  <br/> |
|[xlGetHwnd](xlgethwnd.md) <br/> |8 | xlSpecial  <br/> |Gets the Excel main window handle.  <br/> |
|[xlGetName](xlgetname.md) <br/> |9 | xlSpecial  <br/> |Gets the path and file name of the DLL.  <br/> |
|[xlEnableXLMsgs](xlenablexlmsgs.md) <br/> |10 | xlSpecial  <br/> |This function is deprecated and no longer needs to be called.  <br/> |
|[xlDisableXLMsgs](xldisablexlmsgs.md) <br/> |11 | xlSpecial  <br/> |This function is deprecated and no longer needs to be called.  <br/> |
|[xlDefineBinaryName](xldefinebinaryname.md) <br/> |12 | xlSpecial  <br/> |Defines a persistent binary storage name.  <br/> |
|[xlGetBinaryName](xlgetbinaryname.md) <br/> |13 | xlSpecial  <br/> |Gets a persistent binary storage name's data.  <br/> |

## Return value XLOPER/XLOPER12: operRes

The  _operRes_ argument is the second argument to the callbacks and is a pointer to an **XLOPER** (**Excel4** and **Excel4v**) or **XLOPER12** (**Excel12** and **Excel12v**). After a successful call, it contains the return value of the function or command. **operRes** can be set to zero (NULL pointer) if no return value is required. The previous contents of **operRes** are overwritten so that any memory previously pointed to must be freed before to the call to avoid memory leaks.
  
If the function or command cannot be called (for example, if the arguments are incorrect), **operRes** is set to the error **#VALUE!**. A command always returns **Boolean** **TRUE** if it is successful, or **FALSE** if it failed or the user canceled it.
  
## Number of Subsequent Arguments: count

The  _count_ argument is the third argument to the callbacks and is a 32-bit signed integer. It should be set to the number of subsequent arguments, counting from 1. If a function or command takes no arguments, it should be set to zero. In Microsoft Office Excel 2003, the maximum number of arguments that any function can take is 30, although most take fewer than this. Starting in Excel 2007, the maximum number of arguments that any function can take was increased to 255.
  
With **Excel4** and **Excel12**,  _count_ is the number of pointers to **XLOPER** or **XLOPER12** values that are being passed. You should be very careful not to pass fewer arguments than the value that  _count_ is set to. This would result in Excel reading ahead into the stack and trying to process invalid **XLOPER** or **XLOPER12** values, which could cause an application crash.
  
With **Excel4v** and **Excel12v**,  _count_ is the size of the array of pointers to **XLOPER** or **XLOPER12** values that is being passed as the next and final argument. Again, you should be very careful not to pass a smaller array than  _count_ elements in size, as this will result in the bounds of the array being overrun.
  
## Passing Arguments to C API Functions

Both **Excel4** and **Excel12** take variable length argument lists, after  _count_, which are interpreted as pointers to **XLOPER** and **XLOPER12** values, respectively. **Excel4v** and **Excel12v** take a single argument, after  _count_, which is a pointer to an array of pointers to **XLOPER** values in the case of **Excel4v**, and to **XLOPER12** values in the case of **Excel12v**.
  
The array forms, **Excel4v** and **Excel12v**, enable you to code a call to the C API cleanly when the number of arguments is variable. The following example shows a function that takes a variable-sized array of numbers and uses Excel worksheet functions, via the C API, to calculate the sum, average, minimum, and maximum.
  
```cs
void Excel12v_example(double *dbl_array, int size, double &sum, double &average, double &min, double &max)
{
// 30 is the limit in Excel 2003. 255 is the limit in Excel 2007.
// Use the lower limit to be safe, although it is better to make
// the function version-aware and use the correct limit.
    if(size < 1 || size > 30)
        return;
// Create an array of XLOPER12 values.
    XLOPER12 *xOpArray = (XLOPER12 *)malloc(size * sizeof(XLOPER12));
// Create an array of pointers to XLOPER12 values.
    LPXLOPER12 *xPtrArray =
        (LPXLOPER12 *)malloc(size * sizeof(LPXLOPER12));
// Initialize and populate the array of XLOPER12 values
// and set up the pointers in the pointer array.
    for(int i = 0; i < size; i++)
    {
        xOpArray[i].xltype = xltypeNum;
        xOpArray[i].val.num = dbl_array[i];
        xPtrArray[i] = xOpArray + i;
    }
    XLOPER12 xResult;
    int retval;
    int fn[4] = {xlfSum, xlfAverage, xlfMin, xlfMax};
    double *result_ptr[4] = {&sum, &average, &min, &max};
    for(i = 0; i < 4; i++)
    {
        retval = Excel12v(fn[i], &xResult, size, xPtrArray);
        if(retval == xlretSuccess && xResult.xltype == xltypeNum)
            *result_ptr[i] = xResult.val.num;
    }
    free(xPtrArray);
    free(xOpArray);
}

```

Replacing references to **XLOPER12** values with **XLOPER**, and **Excel12v** with **Excel4v**, in the preceding code would result in a function that would work with all versions of Excel. This operation of the Excel functions **SUM**, **AVERAGE**, **MIN**, and **MAX** is simple enough that it would be more efficient to code them in C and avoid the overhead of preparing the arguments and calling into Excel. However, many of the functions Excel contains are more complex, making this approach useful in some cases.
  
The [xlfRegister](xlfregister-form-1.md) topic provides another example of working with **Excel4v** and **Excel12v**. When registering an XLL worksheet function, you can supply a descriptive string for each argument that is used in the **Paste Function** dialog box. Therefore, the number of total arguments being supplied to **xlfRegister** depends on the number of arguments your XLL function takes and will vary from one function to the next.
  
Where you always call a C API function or command with the same number of arguments, you want to avoid the extra step of creating an array of pointers for those arguments. In those cases, it is simpler and cleaner to use **Excel4** and **Excel12**. For example, when registering XLL functions and commands, you need to supply the full path and file name of the DLL or XLL. You can obtain the file name in a call to **xlfGetName** and then release it with a call to **xlFree**, as shown in the following example for both **Excel4** and **Excel12**.
  
```cs
XLOPER xDllName;
if(Excel4(xlfGetName, &xDllName, 0) == xlretSuccess)
{
    // Use the name, and 
    // then free the memory that Excel allocated for the string.
    Excel4(xlFree, 0, 1, &xDllName);
}
XLOPER12 xDllName;
if(Excel12(xlfGetName, &xDllName, 0) == xlretSuccess)
{
    // Use the name, and
    // then free the memory that Excel allocated for the string.
    Excel12(xlFree, 0, 1, &xDllName);
}

```

In practice, the function, **Excel12v_example**, could be coded more efficiently by creating a single **xltypeMulti** **XLOPER12** argument, and calling the C API by using **Excel12**, as shown in the following example.
  
```cs
void Excel12_example(double *dbl_array, int size, double &sum, double &average, double &min, double &max)
{
// In this implementation, the upper limit is the largest
// single column array (equals 2^20, or 1048576, rows in Excel 2007).
    if(size < 1 || size > 1048576)
        return;
// Create an array of XLOPER12 values.
    XLOPER12 *xOpArray = (XLOPER12 *)malloc(size * sizeof(XLOPER12));
// Create and initialize an xltypeMulti array
// that represents a one-column array.
    XLOPER12 xOpMulti;
    xOpMulti.xltype = xltypeMulti;
    xOpMulti.val.array.lparray = xOpArray;
    xOpMulti.val.array.columns = 1;
    xOpMulti.val.array.rows = size;
// Initialize and populate the array of XLOPER12 values.
    for(int i = 0; i < size; i++)
    {
        xOpArray[i].xltype = xltypeNum;
        xOpArray[i].val.num = dbl_array[i];
    }
    XLOPER12 xResult;
    int fn[4] = {xlfSum, xlfAverage, xlfMin, xlfMax};
    double *result_ptr[4] = {&sum, &average, &min, &max};
    for(i = 0; i < 4; i++)
    {
        Excel12(fn[i], &xResult, 1, &xOpMulti);
        if(xResult.xltype == xltypeNum)
            *result_ptr[i] = xResult.val.num;
    }
    free(xOpArray);
}

```

> [!NOTE]
> In this case, the return value of **Excel12** is ignored. The code instead checks that the returned **XLOPER12** is **xltypeNum** to determine whether the call was successful.
  
## XLCallVer

In addition to the callbacks **Excel4**, **Excel4v**, **Excel12**, and **Excel12v**, Excel exports a function **XLCallVer**, which returns the version of the C API currently running.
  
The function prototype is as follows:
  
 `int pascal XLCallVer(void);`
  
You can call this function, which is thread safe, from any XLL command or function.
  
In Excel 97 through Excel 2003, **XLCallVer** returns 1280 = 0x0500 hex = 5 x 256, which indicates Excel version 5. Starting in Excel 2007, it returns 3072 = 0x0c00 hex = 12 x 256, which similarly indicates version 12.
  
Although you can use this to determine whether the new C API is available at run time, you might prefer to detect the running version of Excel by using `Excel4(xlfGetWorkspace, &version, 1, &arg)`, where `arg` is a numeric **XLOPER** set to 2. The function returns a string **XLOPER**, version, which can then be coerced to an integer. The reason for relying on the Excel version rather than the C API version is that there are differences between Excel 2000, Excel 2002, and Excel 2003 that your add-in may also need to detect. For example, changes were made to the accuracy of some of the statistics functions.
  
## See also

- [Creating XLLs](creating-xlls.md)  
- [Accessing XLL Code in Excel](accessing-xll-code-in-excel.md)  
- [Excel XLL SDK API Function Reference](excel-xll-sdk-api-function-reference.md)  
- [C API Callback Functions Excel4, Excel12](c-api-callback-functions-excel4-excel12.md)  
- [Developing Excel XLLs](developing-excel-xlls.md)
