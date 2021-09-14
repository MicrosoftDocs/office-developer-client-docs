---
title: "Compatibility between the 32-bit and 64-bit versions of Office"
ms.date: 09/14/2021
ms.audience: ITPro
ms.assetid: ff49dc9e-daf8-43cf-8802-51c2537ed561
description: "Find out how the 32-bit version of Office is compatible with the 64-bit version of Office."
localization_priority: Priority
---

# Compatibility between the 32-bit and 64-bit versions of Office

Find out how the 32-bit version of Office is compatible with the 64-bit version of Office.
  
Office applications are available in 32-bit and 64-bit versions. 
  
The 64-bit versions of Office enable you to move more data around for increased capability, for example when you work with large numbers in Microsoft Excel 2010. When writing 32-bit code, you can use the 64-bit version of Office without any changes. However, when you write 64-bit code, you should ensure that your code contains specific keywords and conditional compilation constants to ensure that the code is backward compatible with earlier version of Office, and that the correct code is being executed if you mix 32-bit and 64-bit code.
  
Visual Basic for Applications 7.0 (VBA 7) is released in the 64-bit versions for Office, and it works with both 32-bit and 64-bit applications. The changes described in this article apply only to the 64-bit versions of Office. Using the 32-bit versions of Microsoft Office enable you to use solutions built in previous versions of Office without further modifications.
  
> [!NOTE]
> By default, when you install a 64-bit version of Office you also install the 32-bit version alongside it. You must explicitly select the Microsoft Office 64-bit version installation option. 
  
In VBA 7, you must update existing Windows API statements (**Declare** statements) to work with the 64-bit version. Additionally, you must update address pointers and display window handles in user-defined types that are used by these statements. This is discussed in more detail in this article as well as compatibility issues between the 32-bit and 64-bit versions and suggested solutions. 
  
## Comparing 32-bit and 64-bit systems
<a name="odc_office_Compatibility32bit64bit_Comparing32BitSystemsto64BitSystems"> </a>

Applications built with the 64-bit versions of Office can reference larger address spaces than 32-bit versions. This means you can use more physical memory for data than before, potentially reducing the overhead spent moving data in and out of physical memory
  
In addition to referring specific locations (known as pointers) in physical memory, you can also use addresses to reference display window identifiers (known as handles). The size (in bytes) of the pointer or handle depends on whether you're using a 32-bit or 64-bit system. 
  
If you want to run your existing solutions with the 64-bit versions of Office, be aware of the following:
  
- Native 64-bit processes in Office cannot load 32-bit binaries. This is expected to be a common issue when you have existing Microsoft ActiveX controls and existing add-ins.
    
- VBA previously didn't have a pointer data type, so you had to use 32-bit variables to store pointers and handles. These variables now truncate 64-bit values returned by API calls when using **Declare** statements. 
    
## VBA 7 code base
<a name="odc_office_Compatibility32bit64bit_IntroducingVBA7CodeBase"> </a>

VBA 7 replaces the VBA code base in Office 2007 and earlier versions. VBA 7 is available in both the 32-bit and 64-bit versions of Office. It provides two conditional compilation constants: 
  
- **VBA7** - Helps ensure the backward compatibility of your code by testing whether your application is using VBA 7 or the previous version of VBA. 
    
- **Win64** Tests whether code is running as 32-bit or 64-bit. 
    
With certain exceptions, the macros in a document that work in the 32-bit version of the application also work in the 64-bit version.
  
## ActiveX control and COM add-in compatibility
<a name="odc_office_Compatibility32bit64bit_ActiveXControlCOMAddinCompatibility"> </a>

Existing 32-bit ActiveX controls, are not compatible with the 64-bit versions of Office. For ActiveX controls and COM objects:
  
- If you have the source code, generate a 64-bit version yourself.
- If you don't have the source code, contact the vendor for an updated version.
    
Native 64-bit processes in Office cannot load 32-bit binaries. This includes the common controls of **MSComCtl** (TabStrip, Toolbar, StatusBar, ProgressBar, TreeView, ListViews, ImageList, Slider, ImageComboBox) and the controls of **MSComCt2** (Animation, UpDown, MonthView, DateTimePicker, FlatScrollBar). These controls were installed by 32-bit versions of Office earlier than Office 2010. You'll need to find an alternative for your existing VBA solutions that use these controls when you migrate the code to the 64-bit versions of Office. 
  
## API compatibility
<a name="odc_office_Compatibility32bit64bit_ApplicationProgrammingInterfaceCompatibility"> </a>

The combination of VBA and type libraries gives you lots of functionality to create Office applications. However, sometimes you must communicate directly with the computer's operating system and other components, such as when you manage memory or processes, when working with UI elements linke windows and controls, or when modifying the Windows registry. In these scenarios, your best option is to use one of the external functions that are embedded in DLL files. You do this in VBA by making API calls using **Declare** statements. 
  
> [!NOTE]
> Microsoft provides a Win32API.txt file that contains 1,500 Declare statements and a tool to copy the **Declare** statement that you want into your code. However, these statements are for 32-bit systems and must be converted to 64-bit by using the information discussed later in this article. Existing **Declare** statements won't compile in 64-bit VBA until they've been marked as safe for 64-bit by using the **PtrSafe** attribute. You can find examples of this type of conversion at Excel MVP Jan Karel Pieterse's website at [https://www.jkp-ads.com/articles/apideclarations.asp](https://www.jkp-ads.com/articles/apideclarations.asp). 
> The [Office Code Compatibility Inspector user's guide](https://docs.microsoft.com/previous-versions/office/office-2010/ee833946(v=office.14)) is a useful tool to inspect the syntax of API **Declare** statements for the **PtrSafe** attribute, if needed, and the appropriate return type. 
  
**Declare** statements resemble one of the following, depending on whether you are calling a subroutine (which has no return value) or a function (which does have a return value). 
  
```vb
Public/Private Declare Sub SubName Lib "LibName" Alias "AliasName" (argument list)
Public/Private Declare Function FunctionName Lib "Libname" alias "aliasname" (argument list) As Type

```

The **SubName** function or **FunctionName** function is replaced by the actual name of the procedure in the DLL file and represents the name that is used when the procedure is called from VBA code. You can also specify an **AliasName** argument for the name of the procedure. The name of the DLL file that contains the procedure being called follows the **Lib** keyword. And finally, the argument list contains the parameters and the data types that must be passed to the procedure. 
  
The following **Declare** statement opens a  *subkey*  in the Windows registry and replaces its value. 
  
```vb
Declare Function RegOpenKeyA Lib "advapi32.dll" (ByVal Key As Long, ByVal SubKey As String, NewKey As Long) As Long
```

The Windows.h (window handle) entry for the **RegOpenKeyA** function is as follows: 
  
```vb
LONG RegOpenKeyA ( HKEY hKey, LPCSTR lpSubKey, HKEY *phkResult );
```

In Visual C and Microsoft Visual C++, the previous example compiles correctly for both 32-bit and 64-bit. This is because HKEY is defined as a pointer, whose size reflects the memory size of the platform that the code is compiled in.
  
In previous versions of VBA, there was no specific pointer data type so the **Long** data type was used. And because the **Long** data type is always 32-bits, this breaks when used on a system with 64-bit memory because the upper 32-bits might be truncated or might overwrite other memory addresses. Either of these situations can result in unpredictable behavior or system crashes. 
  
To resolve this, VBA includes a true  *pointer*  data type: **LongPtr**. This new data type enables you to write the original **Declare** statement correctly as: 
  
```vb
Declare PtrSafe Function RegOpenKeyA Lib "advapire32.dll" (ByVal hKey as LongPtr, ByVal lpSubKey As String, phkResult As LongPtr) As Long
```

This data type and the new **PtrSafe** attribute enable you to use this **Declare** statement on either 32-bit or 64-bit systems. The **PtrSafe** attribute indicates to the VBA compiler that the **Declare** statement is targeted for the 64-bit version of Office. Without this attribute, using the **Declare** statement in a 64-bit system will result in a compile-time error. The **PtrSafe** attribute is optional on the 32-bit version of Office. This enables existing **Declare** statements to work as they always have. 
  
The following table provides more information about the new qualifier and data typeas well as another data type, two conversion operators, and three functions.
  
|Type|Item|Description|
|:-----|:-----|:-----|
|Qualifier  <br/> |**PtrSafe** <br/> |Indicates that the **Declare** statement is compatible with 64-bits. This attribute is mandatory on 64-bit systems.  <br/> |
|Data Type  <br/> |**LongPtr** <br/> |A variable data type which is a 4-bytes data type on 32-bit versions and an 8-byte data type on 64-bit versions of Microsoft Office. This is the recommended way of declaring a pointer or a handle for new code but also for legacy code if it has to run in the 64-bit version of Office. It is only supported in the VBA 7 runtime on 32-bit and 64-bit. Note that you can assign numeric values to it but not numeric types.  <br/> |
|Data Type  <br/> |**LongLong** <br/> |This is an 8-byte data type which is available only in 64-bit versions of Microsoft Office. You can assign numeric values but not numeric types (to avoid truncation).  <br/> |
|Conversion Operator  <br/> |**CLngPtr** <br/> |Converts a simple expression to a **LongPtr** data type.  <br/> |
|Conversion Operator  <br/> |**CLngLng** <br/> |Converts a simple expression to a **LongLong** data type.  <br/> |
|Function  <br/> |**VarPtr** <br/> |Variant converter. Returns a **LongPtr** on 64-bit versions, and a **Long** on 32-bit versions (4 bytes).  <br/> |
|Function  <br/> |**ObjPtr** <br/> |Object converter. Returns a **LongPtr** on 64-bit versions, and a **Long** on 32-bit versions (4 bytes).  <br/> |
|Function  <br/> |**StrPtr** <br/> |String converter. Returns a **LongPtr** on 64-bit versions, and a **Long** on 32-bit versions (4 bytes).  <br/> |
   
The follow example shows how to use some of these items in a **Declare** statement. 
  
```vb
Declare PtrSafe Function RegOpenKeyA Lib "advapi32.dll" (ByVal Key As LongPtr, ByVal SubKey As String, NewKey As LongPtr) As Long
```

Note that **Declare** statements without the **PtrSafe** attribute are assumed not to be compatible with the 64-bit version of Office. 
  
There are two conditional compilation constants: **VBA7** and **Win64**. To ensure backward compatibility with previous versions of Microsoft Office, you use the **VBA7** constant (this is the more typical case) to prevent 64-bit code from being used in the earlier version of Office. For code that is different between the 32-bit version and the 64-bit version, such as calling a math API that uses **LongLong** for its 64-bit version and **Long** for its 32-bit version, you use the **Win64** constant. The following code shows the use of these two constants. 
  
```vb
#if Win64 then
   Declare PtrSafe Function MyMathFunc Lib "User32" (ByVal N As LongLong) As LongLong
#else
   Declare Function MyMathFunc Lib "User32" (ByVal N As Long) As Long
#end if
#if VBA7 then
   Declare PtrSafe Sub MessageBeep Lib "User32" (ByVal N AS Long)
#else
   Declare Sub MessageBeep Lib "User32" (ByVal N AS Long)
#end if
```

To summarize, if you write 64-bit code and intend to use it in previous versions of Office, you will want to use the **VBA7** conditional compilation constant. However, if you write 32-bit code in Office, that code works as is in previous versions of Office without the need for the compilation constant. If you want to ensure that you are using 32-bit statements for 32-bit versions and 64-bit statements for 64-bit versions, your best option is to use the **Win64** conditional compilation constant. 
  
## Using conditional compilation attributes
<a name="odc_office_Compatibility32bit64bit_UsingConditionalCompilationAttributes"> </a>

The following example shows VBA code written for 32-bit that needs to be updated. Notice the data types in the legacy code that are updated to use **LongPtr** because they refer to handles or pointers. 
  
### VBA code written for 32-bit versions
  
```vb
Declare Function SHBrowseForFolder Lib "shell32.dll" _
  Alias "SHBrowseForFolderA" (lpBrowseInfo As BROWSEINFO) As LongPtr
  
Public Type BROWSEINFO
  hOwner As Long
  pidlRoot As Long
  pszDisplayName As String
  lpszTitle As String
  ulFlags As Long
  lpfn As Long
  lParam As Long
  iImage As Long
End Type
```

### VBA code rewritten for 64-bit versions
  
```vb
#if VBA7 then    ' VBA7 
Declare PtrSafe Function SHBrowseForFolder Lib "shell32.dll" _
  Alias "SHBrowseForFolderA" (lpBrowseInfo As BROWSEINFO) As Long
Public Type BROWSEINFO
  hOwner As LongPtr
  pidlRoot As Long
  pszDisplayName As String
  lpszTitle As String
  ulFlags As Long
  lpfn As LongPtr
  lParam As LongPtr
  iImage As Long
End Type
 
#else    ' Downlevel when using previous version of VBA7
Declare Function SHBrowseForFolder Lib "shell32.dll" _
  Alias "SHBrowseForFolderA" (lpBrowseInfo As BROWSEINFO) As Long
Public Type BROWSEINFO
  hOwner As Long
  pidlRoot As Long
  pszDisplayName As String
  lpszTitle As String
  ulFlags As Long
  lpfn As Long
  lParam As Long
  iImage As Long
End Type
 
#end if
Sub TestSHBrowseForFolder ()
    Dim bInfo As BROWSEINFO
    Dim pidList As Long
    bInfo.pidlRoot = 0&amp;
    bInfo.ulFlags = &amp;H1
    pidList = SHBrowseForFolder(bInfo)
End Sub
```

<a name="odc_office_Compatibility32bit64bit_FrequentlyAskedQuestions"> </a>

## Frequently asked questions

#### When should I use the 64-bit version of Office?
  
This is more a matter of which host application (Excel, Word, and so forth) you are using. For example, Excel is able to handle much larger worksheets with the 64-bit version of Microsoft Office.
  
#### Can I install 64-bit and 32-bit versions of Office side-by-side?
  
No.
  
#### When should I convert Long parameters to LongPtr?
  
You need to check the Windows API documentation on the Microsoft Developers Network for the function you want to call. Handles and pointers need to be converted to **LongPtr**. As an example, the documentation for [RegOpenKeyA](/windows/win32/api/winreg/nf-winreg-regopenkeyexa.md) provides the following signature: 
  
```cs
LONG WINAPI RegOpenKeyEx(
  __in        HKEY hKey,
  __in_opt    LPCTSTR lpSubKey,
  __reserved  DWORD ulOptions,
  __in        REGSAM samDesired,
  __out       PHKEY phkResult
);
```

The parameters are defined as:
  
|Parameter|Description|
|:-----|:-----|
|hKey [in]  <br/> |A  *handle*  to an open registry key.  <br/> |
|lpSubKey [in, optional]  <br/> |The name of the registry subkey to be opened.  <br/> |
|ulOptions  <br/> |This parameter is reserved and must be zero.  <br/> |
|samDesired [in]  <br/> |A mask that specifies the desired access rights to the key.  <br/> |
|phkResult [out]  <br/> |A  *pointer*  to a variable that receives a handle to the opened key.  <br/> |
   
In [Win32API_PtrSafe.txt](/office/troubleshoot/office/win32api_ptrsafe-with-64-bit-support.md), the **Declare** statement is defined as: 
  
```vb
Declare PtrSafe Function RegOpenKeyEx Lib "advapi32.dll" Alias "RegOpenKeyExA" (ByVal hKey As LongPtr , ByVal lpSubKey As String, ByVal ulOptions As Long, ByVal samDesired As Long, phkResult As LongPtr ) As Long
```

#### Should I convert pointers and handles in structures?
  
Yes. See the **MSG** type in Win32API_PtrSafe.txt: 
  
```vb
Type MSG
    hwnd As LongPtr 
    message As Long
    wParam As LongPtr 
    lParam As LongPtr 
    time As Long
    pt As POINTAPI
End TypeF
```

#### When should I use strptr, varpt, and objptr?
  
You should use these functions to retrieve pointers to strings, variables and objects, respectively. On the 64-bit version of Office, these functions will return a 64-bit **LongPtr**, which can be passed to **Declare** statements. The use of these functions has not changed from previous versions of VBA. The only difference is that they now return a **LongPtr**.
  
## See also
<a name="odc_office_Compatibility32bit64bit_AdditionalResources"> </a>

- [Anatomy of a Declare Statement](https://docs.microsoft.com/previous-versions/aa671659(v=vs.71))
