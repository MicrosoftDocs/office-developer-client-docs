---
title: Introduction to interoperability between COM and .NET
TOCTitle: Introduction to interoperability between COM and .NET
ms:assetid: 6b2d099a-ec6f-4099-aaf6-e61003fe5a32
ms:contentKeyID: 55119776
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Introduction to interoperability between COM and .NET

The Component Object Model (COM) and .NET development have vastly different type systems and mechanisms for object lifetime management, interface creation, and interface inheritance. 

For example, a Variant type in COM is a System.Object data type in the .NET Framework. To create an object, a COM client calls [CoCreateInstance](https://docs.microsoft.com/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance), whereas a managed client can use keywords such as new or New that are built in to a managed programming language. 

While COM does not support classical inheritance and a COM client manages an internal reference count provided by [IUnknown](https://docs.microsoft.com/windows/desktop/api/unknwn/nn-unknwn-iunknown) to free a coclass, a managed client relies on the common language runtime (CLR) garbage collector provided by the .NET Framework to free an object. 

Given such differences between COM and .NET development, developing a managed client on a COM object model requires a mechanism that resolves these differences. The Runtime Callable Wrapper (RCW) is a mechanism that promotes transparent communication between COM and the managed programming model.

This topic gives a high-level description of how the RCW facilitates communication between COM and the managed programming model. Note that even though this topic uses Visual Studio to illustrate the RCW mechanism, you can use an interop assembly outside of Visual Studio to develop a managed client.

## Facilitating interoperability: the Interop Assembly and RCW

### Compile time

An interop assembly defines managed interfaces that map to a COM-based type library and that a managed client can interact with. To use an interop assembly in Visual Studio, first add a reference to the corresponding COM component. Visual Studio will automatically generate a local copy of the interop assembly. The interop assembly contains one namespace, under which there is a managed equivalent interface of each COM object in the COM object model. 

<!--no figure! 

Figure 1 illustrates a managed client that wants to use a COM type library that defines coclass X. The managed client calls class X, which is the managed equivalent interface for coclass X, as defined in the interop assembly. At compile time, the managed project is compiled with information about class X from the interop assembly.

Figure 1. A managed application compiled with an interop assembly that interoperates with an unmanaged type library
-->
  

In general, as long as you set a reference to a type library, Visual Studio generates a copy of an interop assembly for that type library. Any number of interop assemblies can exist to describe the same COM type. However, a type library can have only one Primary Interop Assembly (PIA), which is the interop assembly published by the type library. Unlike other interop assemblies, the PIA is not generated every time you add a reference in Visual Studio. Instead, you install the PIA to the global assembly cache (GAC) just once on a computer. When you add a reference to the type library, Visual Studio automatically loads the PIA.

To program a managed solution for Outlook, you should use the Outlook PIA. To incorporate information from the Outlook PIA into a managed add-in, first you must install the Outlook PIA in the GAC. If you are using Visual Studio to create the managed project, after adding a reference to the Outlook type library, Visual Studio loads the PIA. In the object browser, under the namespace Microsoft.Office.Interop.Outlook, you can see managed interfaces that have names corresponding to objects in the Outlook object model. For example, the Account interface corresponds to the Account object in the Outlook object model. When you compile the managed project, this information is incorporated in your executable.

### Run time

At run time, with the information provided by an interop assembly, the .NET Framework CLR creates an RCW for each coclass the managed client interacts with. Note that the runtime creates only one RCW for each coclass, regardless of how many interfaces the client has obtained from the coclass. The RCW is a .NET Framework class type that wraps around the COM coclass. The RCW keeps track of the instances of the coclass and releases references to them only when the client no longer needs the RCW. This way, a managed client does not have to manage the lifetime of an object the way an unmanaged client would under COM.

<!-- No figure! 

Figure 2 illustrates an RCW intercepting an API call from a managed client at run time, and using information from the interop assembly, transparently mapping the call to the corresponding API in the COM coclass. The following process describes how this happens:

1.  The managed client calls method A' of class X' as defined in the interop assembly for a COM type library.

2.  If an RCW does not yet exist for class X', the .NET Framework runtime uses information from the interop assembly and creates an RCW for class X'.

3.  The RCW intercepts the call to method A', translates the arguments into corresponding COM types, and invokes method A of coclass X as defined in the COM type library.

Figure 2. An RCW intercepts a call from a managed executable and maps it to a coclass in an unmanaged type library
-->
  

## See also

- [Why use the Outlook PIA](why-use-the-outlook-pia.md)
- [Installing and referencing the Outlook PIA](installing-and-referencing-the-outlook-pia.md)

