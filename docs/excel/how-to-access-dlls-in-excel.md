---
title: "Access DLLs in Excel"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: overview
keywords:
- accessing dlls [excel 2007],DLLs [Excel 2007], accessing in Excel
ms.assetid: e2bfd6ea-efa3-45c1-a5b8-2ccb8650c6ab

ms.localizationpriority: high
---

# Access DLLs in Excel

**Applies to**: Excel 2013 | Office 2013 | Visual Studio
  
You can access a DLL function or command in Microsoft Excel in several ways:
  
- Through a Microsoft Visual Basic for Applications (VBA) code module in which the function or command has been made available using a **Declare** statement.

- Through an XLM macro sheet by using the **CALL** or **REGISTER** functions.

- Directly from the worksheet or from a customized item in the user interface (UI).

This documentation does not cover XLM functions. It is recommended that you use either of the other two approaches.
  
To be accessed directly from the worksheet or from a customized item in the UI, the function or command must first be registered with Excel. For information about registering commands and functions, see [Accessing XLL Code in Excel](accessing-xll-code-in-excel.md).
  
## Calling DLL functions and commands from VBA

You can access DLL functions and commands in VBA by using the **Declare** statement. This statement has one syntax for commands and one for functions.
  
- **Syntax 1 - commands**

  ```vb
  [Public | Private] Declare Sub name Lib "libname" [Alias "aliasname"] [([arglist])]
  ```

- **Syntax 2 - functions**

  ```vb
  [Public | Private] Declare Function name Lib "libname" [Alias "aliasname"] [([arglist])] [As type]
  ```

The optional **Public** and **Private** keywords specify the scope of the imported function: the entire Visual Basic project or just the Visual Basic module, respectively. The name is the name that you want to use in the VBA code. If this differs from the name in the DLL, you must use the Alias "aliasname" specifier, and you should give the name of the function as exported by the DLL. If you want to access a DLL function by reference to a DLL ordinal number, you must provide an alias name, which is the ordinal prefixed by **#**.
  
Commands should return **void**. Functions should return types that VBA can recognize **ByVal**. This means that some types are more easily returned by modifying arguments in place: strings, arrays, user-defined types, and objects.
  
> [!NOTE]
> VBA cannot check that the argument list and return stated in the Visual Basic module are the same as coded in the DLL. You should check this yourself very carefully, because a mistake could cause Excel to crash.
  
When the function or command's arguments are not passed by reference or pointer, they must be preceded by the **ByVal** keyword in the **arglist** declaration. When a C/C++ function takes pointer arguments, or a C++ function takes reference arguments, they should be passed **ByRef**. The keyword **ByRef** can be omitted from argument lists because it is the default in VBA.
  
### Argument types in C/C++ and VBA

You should note the following when you compare the declarations of argument types in C/C++ and VBA.
  
- A VBA **String** is passed as a pointer to a byte-string BSTR structure when passed ByVal, and as a pointer to a pointer when passed **ByRef**.

- A VBA **Variant** that contains a string is passed as a pointer to a Unicode wide-character string BSTR structure when passed **ByVal**, and as a pointer to a pointer when passed **ByRef**.

- The VBA **Integer** is a 16-bit type equivalent to a signed short in C/C++.

- The VBA **Long** is a 32-bit type equivalent to a signed int in C/C++.

- Both VBA and C/C++ allow the definition of user-defined data types, using the **Type** and **struct** statements respectively.

- Both VBA and C/C++ support the **Variant** data type, defined for C/C++ in the Windows OLE/COM header files as VARIANT.

- VBA arrays are OLE **SafeArrays**, defined for C/C++ in the Windows OLE/COM header files as **SAFEARRAY**.

- The VBA **Currency** data type is passed as a structure of type **CY**, defined in the Windows header file wtypes.h, when passed **ByVal**, and as a pointer to this when passed **ByRef**.

In VBA, data elements in user-defined data types are packed to 4-byte boundaries, whereas in Visual Studio, by default, they are packed to 8-byte boundaries. Therefore you must enclose the C/C++ structure definition in a `#pragma pack(4) … #pragma pack()` block to avoid elements being misaligned.
  
The following is an example of equivalent user type definitions.
  
```vb
Type VB_User_Type
    i As Integer
    d As Double
    s As String
End Type

```

```cpp
#pragma pack(4)
struct C_user_type
{
    short iVal;
    double dVal;
    BSTR bstr; // VBA String type is a byte string
}
#pragma pack() // restore default

```

VBA supports a greater range of values in some cases than Excel supports. The VBA double is IEEE compliant, supporting subnormal numbers that are currently rounded down to zero on the worksheet. The VBA **Date** type can represent dates as early as 1-Jan-0100 using negative serialized dates. Excel only allows serialized dates greater than or equal to zero. The VBA **Currency** type—a scaled 64-bit integer—can achieve accuracy not supported in 8-byte doubles, and so is not matched in the worksheet.
  
Excel only passes Variants of the following types to a VBA user-defined function.
  
|**VBA data type**|**C/C++ Variant type bit flags**|**Description**|
|:-----|:-----|:-----|
|Double  <br/> |**VT_R8** <br/> ||
|Boolean  <br/> |**VT_BOOL** <br/> ||
|Date  <br/> |**VT_DATE** <br/> ||
|String  <br/> |**VT_BSTR** <br/> |OLE Bstr byte string  <br/> |
|Range  <br/> |**VT_DISPATCH** <br/> |Range and cell references  <br/> |
|Variant containing an array  <br/> |**VT_ARRAY** | **VT_VARIANT** <br/> |Literal arrays  <br/> |
|Ccy  <br/> |**VT_CY** <br/> |64-bit integer scaled to permit 4 decimal places of accuracy. |
|Variant containing an error  <br/> |**VT_ERROR** <br/> ||
||**VT_EMPTY** <br/> |Empty cells or omitted arguments  <br/> |

You can check the type of a passed-in Variant in VBA using the **VarType**, except that the function returns the type of the range's values when called with references. To determine if a **Variant** is a **Range** reference object, you can use the **IsObject** function.
  
You can create **Variants** that contain arrays of variants in VBA from a **Range** by assigning its **Value** property to a **Variant**. Any cells in the source range that are formatted using the standard currency format for the regional settings in force at the time are converted to array elements of type **Currency**. Any cells formatted as dates are converted to array elements of type **Date**. Cells containing strings are converted to wide-character **BSTR** Variants. Cells containing errors are converted to **Variants** of type **VT_ERROR**. Cells containing **Boolean** **True** or **False** are converted to **Variants** of type **VT_BOOL**.
  
> [!NOTE]
> The **Variant** stores **True** as -1 and **False** as 0. Numbers not formatted as dates or currency amounts are converted to Variants of type **VT_R8**.
  
### Variant and string arguments

Excel works internally with wide-character Unicode strings. When a VBA user-defined function is declared as taking a **String** argument, Excel converts the supplied string to a byte-string in a locale-specific way. If you want your function to be passed a Unicode string, your VBA user-defined function should accept a **Variant** instead of a **String** argument. Your DLL function can then accept that **Variant** BSTR wide-character string from VBA.
  
To return Unicode strings to VBA from a DLL, you should modify a **Variant** string argument in place. For this to work, you must declare the DLL function as taking a pointer to the **Variant** and in your C/C++ code, and declare the argument in the VBA code as `ByRef varg As Variant`. The old string memory should be released, and the new string value created by using the OLE Bstr string functions only in the DLL.
  
To return a byte string to VBA from a DLL, you should modify a byte-string BSTR argument in place. For this to work, you must declare the DLL function as taking a pointer to a pointer to the BSTR and in your C/C++ code, and declare the argument in the VBA code as ' **ByRef varg As String**'.
  
You should only handle strings that are passed in these ways from VBA using the OLE BSTR string functions to avoid memory-related problems. For example, you must call **SysFreeString** to free the memory before overwriting the passed in string, and **SysAllocStringByteLen** or **SysAllocStringLen** to allocate space for a new string.
  
You can create Excel worksheet errors as **Variants** in VBA by using the **CVerr** function with arguments as shown in the following table. Worksheet errors can also be returned to VBA from a DLL using **Variants** of type **VT_ERROR**, and with the following values in the **ulVal** field.
  
|**Error**|**Variant ulVal value**|**CVerr argument**|
|:-----|:-----|:-----|
|#NULL!  <br/> |2148141008  <br/> |2000  <br/> |
|#DIV/0!  <br/> |2148141015  <br/> |2007  <br/> |
|#VALUE!  <br/> |2148141023  <br/> |2015  <br/> |
|#REF!  <br/> |2148141031  <br/> |2023  <br/> |
|#NAME?  <br/> |2148141037  <br/> |2029  <br/> |
|#NUM!  <br/> |2148141044  <br/> |2036  <br/> |
|#N/A  <br/> |2148141050  <br/> |2042  <br/> |

Note that the Variant **ulVal** value given is equivalent to the **CVerr** argument value plus x800A0000 hexadecimal.
  
## Calling DLL functions directly from the worksheet

You cannot access Win32 DLL functions from the worksheet without, for example, using VBA or XLM as interfaces, or without letting Excel know about the function, its arguments, and its return type in advance. The process of doing this is called registration.
  
The ways in which the functions of a DLL can be accessed in the worksheet are as follows:
  
- Declare the function in VBA as described previously and access it via a VBA user-defined function.

- Call the DLL function using CALL on an XLM macro sheet, and access it via an XLM user-defined function.

- Use an XLM or VBA command to call the XLM **REGISTER** function, which provides the information that Excel needs to recognize the function when it is entered into a worksheet cell.

- Turn the DLL into an XLL and register the function using the C API **xlfRegister** function when the XLL is activated.

The fourth approach is self-contained: the code that registers the functions and the function code are both contained in the same code project. Making changes to the add-in does not involve making changes to an XLM sheet or to a VBA code module. To do this in a well-managed way while still staying within the capabilities of the C API, you must turn your DLL into an XLL and load the resulting add-in by using the Add-in Manager. This enables Excel to call a function that your DLL exposes when the add-in is loaded or activated, from which you can register all of the functions your XLL contains, and carry out any other DLL initialization.
  
## Calling DLL commands directly from Excel

Win32 DLL commands are not accessible directly from Excel dialog boxes and menus without there being an interface, such as VBA, or without the commands being registered in advance.
  
The ways in which you can access the commands of a DLL are as follows:
  
- Declare the command in VBA as described previously and access it via a VBA macro.

- Call the DLL command using **CALL** on an XLM macro sheet, and access it via an XLM macro.

- Use an XLM or VBA command to call the XLM **REGISTER** function, which provides the information Excel needs to recognize the command when it is entered into a dialog box that expects the name of a macro command.

- Turn the DLL into an XLL and register the command using the C API **xlfRegister** function.

As discussed earlier in the context of DLL functions, the fourth approach is the most self-contained, keeping the registration code close to the command code. To do this, you must turn your DLL into an XLL and load the resulting add-in using the Add-in Manager. Registering commands in this way also lets you attach the command to an element of the user interface, such as a custom menu, or to set up an event trap that calls the command on a given keystroke or other event.
  
All XLL commands that are registered with Excel are assumed by Excel to be of the following form.
  
```cpp
int WINAPI my_xll_cmd(void)
{
// Function code...
    return 1;
}
```

> [!NOTE]
> Excel ignores the return value unless it is called from an XLM macro sheet, in which case the return value is converted to **TRUE** or **FALSE**. You should therefore return 1 if your command executed successfully, and 0 if it failed or was canceled by the user.
  
## DLL memory and multiple DLL instances

When an application loads a DLL, the DLL's executable code is loaded into the global heap so that it can be run, and space is allocated on the global heap for its data structures. Windows uses memory mapping to make these areas of memory appear as if they are in the application's process so that the application can access them.
  
If a second application then loads the DLL, Windows does not make another copy of the DLL executable code, as that memory is read-only. Windows maps the DLL executable code memory to the processes of both applications. It does, however, allocate a second space for a private copy of the DLL's data structures and maps this copy to the second process only. This ensures that neither application can interfere with the DLL data of the other.
  
This means that DLL developers do not have to be concerned about static and global variables and data structures being accessed by more than one application, or more than one instance of the same application. Every instance of every application gets its own copy of the DLL's data.
  
DLL developers do need to be concerned about the same instance of an application calling their DLL many times from different threads, because this can result in contention for that instance's data. For more information, see [Memory Management in Excel](memory-management-in-excel.md).
  
## See also

- [Developing DLLs](developing-dlls.md)
- [Calling into Excel from the DLL or XLL](calling-into-excel-from-the-dll-or-xll.md)
