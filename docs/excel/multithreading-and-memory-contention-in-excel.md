---
title: "Multithreading and Memory Contention in Excel"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
keywords:
- multithreading in excel,memory contention in Excel,functions [Excel 2007], thread-safe,thread-safe functions [Excel 2007],thread-local memory [Excel 2007]
 
ms.localizationpriority: medium
ms.assetid: 86e1e842-f433-4ea9-8b13-ad2515fc50d8

---

# Multithreading and Memory Contention in Excel

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Versions of Microsoft Excel earlier than Excel 2007 use a single thread for all worksheet calculations. However, starting in Excel 2007, Excel can be configured to use from 1 to 1024 concurrent threads for worksheet calculation. On a multi-processor or multi-core computer, the default number of threads is equal to the number of processors or cores. Therefore, thread-safe cells, or cells that only contain functions that are thread safe, can be allotted to concurrent threads, subject to the usual recalculation logic of needing to be calculated after their precedents.
  
## Thread-Safe Functions

Most of the built-in worksheet functions starting in Excel 2007 are thread safe. You can also write and register XLL functions as being thread safe. Excel uses one thread (its main thread) to call all commands, thread-unsafe functions, **xlAuto** functions (except [xlAutoFree](xlautofree-xlautofree12.md) and **xlAutoFree12**), and COM and Visual Basic for Applications (VBA) functions.
  
Where an XLL function returns an **XLOPER** or **XLOPER12** with **xlbitDLLFree** set, Excel uses the same thread on which the function call was made to call **xlAutoFree** or **xlAutoFree12**. The call to **xlAutoFree** or **xlAutoFree12** is made before the next function call on that thread. 
  
For XLL developers, there are benefits for creating thread-safe functions:
  
- They allow Excel to make the most of a multi-processor or multi-core computer.
    
- They open up the possibility of using remote servers much more efficiently than can be done using a single thread.
    
Suppose that you have a single-processor computer that has been configured to use, say, *N*  threads. Suppose that a spreadsheet is running that makes a large number of calls to an XLL function that in turn sends a request for data or for a calculation to be performed to a remote server or cluster of servers. Subject to the topology of the dependency tree, Excel could call the function N times almost simultaneously. Provided that the server or servers are sufficiently fast or parallel, the recalculation time of the spreadsheet could be reduced by as much as a factor of 1/N. 
  
The key issue in writing thread-safe functions is handling contention for resources correctly. This usually means memory contention, and it can be broken down into two issues:
  
- How to create memory that you know will only be used by this thread.
    
- How to ensure that shared memory is accessed by multiple threads safely.
    
The first thing to be aware of is what memory in an XLL is accessible by all threads, and what is only accessible by the currently executing thread.
  
 **Accessible by all threads**
  
- Variables, structures, and class instances declared outside the body of a function.
    
- Static variables declared within the body of a function.
    
In these two cases, memory is set aside in the DLL's memory block created for this instance of the DLL. If another application instance loads the DLL, it gets its own copy of that memory so that there is no contention for these resources from outside this instance of the DLL.
  
 **Accessible only by the current thread**
  
- Automatic variables within function code (including function arguments).
    
In this case, memory is set aside on the stack for each instance of the function call.
  
> [!NOTE]
> The scope of dynamically allocated memory depends on the scope of the pointer that points to it: if the pointer is accessible by all threads, the memory is also. If the pointer is an automatic variable in a function, the allocated memory is effectively private to that thread. 
  
## Memory Accessible by Only One Thread: Thread-Local Memory

Given that static variables within the body of a function are accessible by all threads, functions that use them are clearly not thread safe. One instance of the function on one thread could be changing the value while another instance on another thread is assuming it is something completely different. 
  
There are two reasons for declaring static variables within a function:
  
1. Static data persist from one call to the next.
    
2. A pointer to static data can safely be returned by the function.
    
In the case of first reason, you might want to have data that persists and has meaning for all calls to the function: perhaps a simple counter that is incremented every time the function is called on any thread, or a structure that collects usage and performance data on every call. The question is how to protect the shared data or data structure. This is best done by using critical section as the next section explains.
  
If the data is intended only for use by this thread, which could be the case for reason 1 and is always the case for reason 2, the question is how to create memory that persists but is only accessible from this thread. One solution is to use the thread-local storage (TLS) API.
  
For example, consider a function that returns a pointer to an **XLOPER**.
  
```cs
LPXLOPER12 WINAPI mtr_unsafe_example(LPXLOPER12 pxArg)
{
    static XLOPER12 xRetVal; // memory shared by all threads!!!
// code sets xRetVal to a function of pxArg ...
    return &xRetVal;
}
```

This function is not thread safe because one thread can return the static **XLOPER12** while another is overwriting it. The likelihood of this happening is greater still if the **XLOPER12** needs to be passed to **xlAutoFree12**. One solution is to allocate an **XLOPER12**, return a pointer to it, and implement **xlAutoFree12** so that the **XLOPER12** memory itself is freed. This approach is used in many of the example functions shown in [Memory Management in Excel](memory-management-in-excel.md).
  
```cs
LPXLOPER12 WINAPI mtr_safe_example_1(LPXLOPER12 pxArg)
{
// pxRetVal must be freed later by xlAutoFree12
    LPXLOPER12 pxRetVal = new XLOPER12;
// code sets pxRetVal to a function of pxArg ...
    pxRetVal->xltype |= xlbitDLLFree; // Needed for all types
    return pxRetVal; // xlAutoFree12 must free this
}
```

This approach is simpler to implement than the approach outlined in the next section, which relies on the TLS API, but it has some disadvantages. First, Excel must call **xlAutoFree**/ **xlAutoFree12** whatever the type of the returned **XLOPER**/ **XLOPER12**. Second, there is a problem when returning **XLOPER**/ **XLOPER12**s that are the return value of a call to a C API callback function. The **XLOPER**/ **XLOPER12** may point to memory that needs to be freed by Excel, but the **XLOPER**/ **XLOPER12** itself must be freed in the same way it was allocated. If such an **XLOPER**/ **XLOPER12** is to be used as the return value of an XLL worksheet function, there is no easy way to inform **xlAutoFree**/ **xlAutoFree12** of the need to free both pointers in the appropriate way. (Setting both the **xlbitXLFree** and **xlbitDLLFree** does not solve the problem, as the treatment of **XLOPER/XLOPER12s** in Excel with both set is undefined and might change from version to version.) To work around this problem, the XLL can make deep copies of all Excel-allocated **XLOPER/XLOPER12s** that it returns to the worksheet. 
  
A solution that avoids these limitations is to populate and return a thread-local **XLOPER/XLOPER12**, an approach that necessitates that **xlAutoFree/xlAutoFree12** does not free the **XLOPER/XLOPER12** pointer itself. 
  
```cs
LPXLOPER12 get_thread_local_xloper12(void);
LPXLOPER12 WINAPI mtr_safe_example_2(LPXLOPER12 pxArg)
{
    LPXLOPER12 pxRetVal = get_thread_local_xloper12();
// Code sets pxRetVal to a function of pxArg setting xlbitDLLFree or
// xlbitXLFree as required.
    return pxRetVal; // xlAutoFree12 must not free this pointer!
}

```

The next question is how to set up and retrieve the thread-local memory, in other words, how to implement the function **get_thread_local_xloper12** in the previous example. This is done using the Thread Local Storage (TLS) API. The first step is to obtain a TLS index by using **TlsAlloc**, which must ultimately be released using **TlsFree**. Both are best accomplished from **DllMain**.
  
```cs
// This implementation just calls a function to set up
// thread-local storage.
BOOL TLS_Action(DWORD Reason); // Could be in another module
BOOL WINAPI DllMain(HINSTANCE hDll, DWORD Reason, void *Reserved)
{
    return TLS_Action(Reason);
}
DWORD TlsIndex; // Module scope only if all TLS access in this module
BOOL TLS_Action(DWORD DllMainCallReason)
{
    switch (DllMainCallReason)
    {
    case DLL_PROCESS_ATTACH: // The DLL is being loaded.
        if((TlsIndex = TlsAlloc()) == TLS_OUT_OF_INDEXES)
            return FALSE;
        break;
    case DLL_PROCESS_DETACH: // The DLL is being unloaded.
        TlsFree(TlsIndex); // Release the TLS index.
        break;
    }
    return TRUE;
}
```

After you obtain the index, the next step is to allocate a block of memory for each thread. The [Windows Development Documentation](https://msdn.microsoft.com/library/ms682583%28VS.85%29.aspx) recommends doing this every time the **DllMain** callback function is called with a **DLL_THREAD_ATTACH** event, and freeing the memory on every **DLL_THREAD_DETACH**. However, following this advice would cause your DLL to do unnecessary work for threads not used for recalculation. 
  
Instead, it is better to use an allocate-on-first-use strategy. First, you need to define a structure that you want to allocate for each thread. For the previous examples that return **XLOPERs** or **XLOPER12s**, the following suffices, but you can create any structure that satisfies your needs.
  
```cs
struct TLS_data
{
    XLOPER xloper_shared_ret_val;
    XLOPER12 xloper12_shared_ret_val;
// Add other required thread-local data here...
};
```

The following function gets a pointer to the thread-local instance, or allocates one if this is the first call.
  
```cs
TLS_data *get_TLS_data(void)
{
// Get a pointer to this thread's static memory.
    void *pTLS = TlsGetValue(TlsIndex);
    if(!pTLS) // No TLS memory for this thread yet
    {
        if((pTLS = calloc(1, sizeof(TLS_data))) == NULL)
        // Display some error message (omitted).
            return NULL;
        TlsSetValue(TlsIndex, pTLS); // Associate with this thread
    }
    return (TLS_data *)pTLS;
}
```

Now you can see how the thread-local **XLOPER/XLOPER12** memory is obtained: first, you get a pointer to the thread's instance of **TLS_data**, and then you return a pointer to the **XLOPER/XLOPER12** contained within it, as follows. 
  
```cs
LPXLOPER get_thread_local_xloper(void)
{
    TLS_data *pTLS = get_TLS_data();
    if(pTLS)
        return &(pTLS->xloper_shared_ret_val);
    return NULL;
}
LPXLOPER12 get_thread_local_xloper12(void)
{
    TLS_data *pTLS = get_TLS_data();
    if(pTLS)
        return &(pTLS->xloper12_shared_ret_val);
    return NULL;
}

```

The **mtr_safe_example_1** and **mtr_safe_example_2** functions can be registered as thread-safe worksheet functions when you are running Excel. However, you cannot mix the two approaches in one XLL. Your XLL can only export one implementation of **xlAutoFree** and **xlAutoFree12**, and each memory strategy requires a different approach. With **mtr_safe_example_1**, the pointer passed to **xlAutoFree/xlAutoFree12** must be freed along with any data it points to. With **mtr_safe_example_2**, only the pointed-to data should be freed.
  
Windows also provides a function **GetCurrentThreadId**, which returns the current thread's unique system-wide ID. This provides the developer with another way to make code thread safe, or to make its behavior thread specific.
  
## Memory Accessible Only by More than One Thread: Critical Sections

You should protect read/write memory that can be accessed by more than one thread using critical sections. You need a named critical section for each block of memory you want to protect. You can initialize these during the call to the **xlAutoOpen** function, and release them and set them to null during the call to the **xlAutoClose** function. You then need to contain each access to the protected block within a pair of calls to **EnterCriticalSection** and **LeaveCriticalSection**. Only one thread is permitted into the critical section at any time. Here is an example of the initialization, uninitialization, and use of a section called **g_csSharedTable**.
  
```cs
CRITICAL_SECTION g_csSharedTable; // global scope (if required)
bool xll_initialised = false; // Only module scope needed
int WINAPI xlAutoOpen(void)
{
    if(xll_initialised)
        return 1;
// Other initialisation omitted
    InitializeCriticalSection(&g_csSharedTable);
    xll_initialised = true;
    return 1;
}
int WINAPI xlAutoClose(void)
{
    if(!xll_initialised)
        return 1;
// Other cleaning up omitted.
    DeleteCriticalSection(&g_csSharedTable);
    xll_initialised = false;
    return 1;
}
#define SHARED_TABLE_SIZE 1000 /* Some value consistent with the table */
bool read_shared_table_element(unsigned int index, double &d)
{
    if(index >= SHARED_TABLE_SIZE) return false;
    EnterCriticalSection(&g_csSharedTable);
    d = shared_table[index];
    LeaveCriticalSection(&g_csSharedTable);
    return true;
}
bool set_shared_table_element(unsigned int index, double d)
{
    if(index >= SHARED_TABLE_SIZE) return false;
    EnterCriticalSection(&g_csSharedTable);
    shared_table[index] = d;
    LeaveCriticalSection(&g_csSharedTable);
    return true;
}
```

Another, perhaps safer way of protecting a block of memory is to create a class that contains its own **CRITICAL_SECTION** and whose constructor, destructor, and accessor methods take care of its use. This approach has the added advantage of protecting objects that may be initialized before **xlAutoOpen** is run, or survive after **xlAutoClose** is called, but you should be careful about creating too many critical sections and the operating system overhead that this would create. 
  
When you have code that needs access to more than one block of protected memory at the same time, you need to consider very carefully the order in which the critical sections are entered and exited. For example, the following two functions could create a deadlock.
  
```cs
// WARNING: Do not copy this code. These two functions
// can produce a deadlock and are provided for
// example and illustration only.
bool copy_shared_table_element_A_to_B(unsigned int index)
{
    if(index >= SHARED_TABLE_SIZE) return false;
    EnterCriticalSection(&g_csSharedTableA);
    EnterCriticalSection(&g_csSharedTableB);
    shared_table_B[index] = shared_table_A[index];
// Critical sections should be exited in the order
// they were entered, NOT as shown here in this
// deliberately wrong illustration.
    LeaveCriticalSection(&g_csSharedTableA);
    LeaveCriticalSection(&g_csSharedTableB);
    return true;
}
bool copy_shared_table_element_B_to_A(unsigned int index)
{
    if(index >= SHARED_TABLE_SIZE) return false;
    EnterCriticalSection(&g_csSharedTableB);
    EnterCriticalSection(&g_csSharedTableA);
    shared_table_A[index] = shared_table_B[index];
    LeaveCriticalSection(&g_csSharedTableA);
    LeaveCriticalSection(&g_csSharedTableB);
    return true;
}
```

If the first function on one thread enters **g_csSharedTableA** while the second on another thread enters **g_csSharedTableB**, both threads hang. The correct approach is to enter in a consistent order and exit in the reverse order, as follows.
  
```cs
    EnterCriticalSection(&g_csSharedTableA);
    EnterCriticalSection(&g_csSharedTableB);
    // code that accesses both blocks
    LeaveCriticalSection(&g_csSharedTableB);
    LeaveCriticalSection(&g_csSharedTableA);
```

Where possible, it is better from a thread co-operation point of view to isolate access to distinct blocks, as shown here.
  
```cs
bool copy_shared_table_element_A_to_B(unsigned int index)
{
    if(index >= SHARED_TABLE_SIZE) return false;
    EnterCriticalSection(&g_csSharedTableA);
    double d = shared_table_A[index];
    LeaveCriticalSection(&g_csSharedTableA);
    EnterCriticalSection(&g_csSharedTableB);
    shared_table_B[index] = d;
    LeaveCriticalSection(&g_csSharedTableB);
    return true;
}
```

Where there is a lot of contention for a shared resource, such as frequent short-duration access requests, you should consider using the critical section's ability to spin. This is a technique that makes waiting for the resource less processor-intensive. To do this, you can use either **InitializeCriticalSectionAndSpinCount** when initializing the section or **SetCriticalSectionSpinCount** once initialized, to set the number of times the thread loops before waiting for resources to become available. The wait operation is expensive, so spinning avoids this if the resource is freed in the meantime. On a single processor system, the spin count is effectively ignored, but you can still specify it without doing any harm. The memory heap manager uses a spin count of 4000. For more information about the use of critical sections, see the Windows SDK documentation. 
  
## See also



[Memory Management in Excel](memory-management-in-excel.md)
  
[Multithreaded Recalculation in Excel](multithreaded-recalculation-in-excel.md)
  
[Add-in Manager and XLL Interface Functions](add-in-manager-and-xll-interface-functions.md)

