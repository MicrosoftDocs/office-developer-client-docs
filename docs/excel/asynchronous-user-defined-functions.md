---
title: "Asynchronous user-defined functions"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: 142eb27e-fb6f-4da3-bfb7-a88115bbb5d5

---

# Asynchronous user-defined functions

**Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Microsoft Excel 2013 can call user-defined functions asynchronously. Calling functions asynchronously can improve performance by allowing several calculations to run at the same time. When you run user-defined functions on a compute cluster, calling functions asynchronously enables several computers to be used to complete the calculations.
  
## When to use asynchronous user-defined functions

Some user-defined functions must wait for external resources. While they wait, the Excel calculation thread is blocked. In Excel 2013, user-defined functions can run asynchronously. This frees the calculation thread to run other calculations while the user-defined function waits.
  
In Excel 2007, programmers could run multiple user-defined functions at the same time by increasing the number of threads used in multiple-thread recalculations. This method has drawbacks primarily because the number of threads is a setting scoped to an application and cannot be controlled at the level of a single function or an add-in.
  
Programmers should use asynchronous user-defined function calls when the function must wait for external resources. For example, a function that sends a SOAP request over the Internet must wait for the network to deliver the request, the remote server to complete the request, and the network to return the result. In this case, there is no significant computing occurring and Excel can continue with other calculations.
  
Programmers can also use asynchronous user-defined functions when a function is sending requests to a compute cluster. In this case, there is not only network latency to wait for, but the cluster can execute separate calls on separate servers. By not waiting for each call to finish, the calls can be overlapped to improve performance. In some cases this improvement is significant.
  
> [!NOTE]
> User-defined functions cannot be registered as both asynchronous and cluster safe. 
  
## Writing an asynchronous user-defined function

Asynchronous user-defined functions must keep track of a handle and use that handle when informing Excel that the function call is finished. An asynchronous user-defined function is split into two pieces. The first piece is the standard UDF entry point, which will launch a second, separate asynchronous operation. Callbacks into Excel should be made during the UDF entry point. The first launching portion of the function will then return control of its calculation thread to Excel, which will continue calculation. When the second asynchronous operation is complete, it must call back into Excel and provide Excel with its result. 
  
> [!NOTE]
> Any arguments passed into the UDF that are needed by the asynchronous portion the function must be deep copied because Excel frees these arguments when the UDF entry point returns. 
  
Excel provides a set of events that an XLL add-in can use in order to manage the life cycle of asynchronous UDF calls. These events indicate that Excel is finished with calculations or that the calculation was canceled.
  
### Declaring an asynchronous function

You must declare asynchronous user-defined functions as asynchronous when they are registered. This is performed by adding a parameter that points to a XLOPER12 structure, represented by "X" in the registration type string, anywhere in the list of UDF parameters. Excel uses this parameter to pass the asynchronous call handle. The XLL add-in must pass the asynchronous call handle and the result of the function back to Excel when the result is ready. In addition, the return type of the UDF should be **void**, designated by ">" as the first character in the type string. The return type is void because the synchronous part of the UDF does not return a value to Excel. Instead, the XLL add-in returns a value asynchronously through a callback. 
  
You can declare asynchronous functions as thread-safe and then the synchronous part of the UDF is used in a multi-threaded recalculation. 
  
The following code example shows an asynchronous user-defined function registered by using "\>QX" as the registration type string:
  
```cpp
void MyAsyncUDF(LPXLOPER12 arg1, LPXLOPER12 pxAsyncHandle)
{
…
}
```

### Returning values

When the result of the asynchronous call is ready, the XLL add-in returns the result to Excel by performing a callback of type [xlAsyncReturn](xlasyncreturn.md).
  
**xlAsyncReturn** is the only callback you can use on non-calculation threads during recalculation. Therefore, the asynchronous part of an asynchronous UDF should not perform any other callbacks. 
  
### Handling events

Starting in Excel 2010, XLLs can receive events designed to manage the asynchronous function life cycle. For more information, see [Handling Events](handling-events.md).
  
## See also

- [Developing Excel XLLs](developing-excel-xlls.md)

