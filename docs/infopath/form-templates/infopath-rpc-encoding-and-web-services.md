---
title: "InfoPath, RPC Encoding and Web Services"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: f8d7b944-a8fd-9c5f-8f66-0f1b628b7c6e
description: "Web services can expose one of two styles for binding to their Web methods in the Web Service Description Language (WSDL) contract that describes them: Document or RPC."
---

# InfoPath, RPC Encoding and Web Services

Web services can expose one of two styles for binding to their Web methods in the Web Service Description Language (WSDL) contract that describes them: Document or RPC. Additionally, each of these two styles of binding can be specified as either literal or encoded. The most common implementations for each type are: document/literal and RPC/encoded. However, Microsoft InfoPath only supports connecting to Web services that use the document/literal style.
  
Most Web service development tools provide a switch for specifying what kind of Web service that you want to create. If you are developing a Web service that you will be connecting to from InfoPath, you should specify document/literal as your Web service's style and encoding.
  
However, if you do not control the Web service that you want to work with, and you must connect to a Web service uses the RPC/encoded style, you can use a .NET proxy service to connect to an RPC/encoded Web service.
  
## Using a .NET Proxy Service to Connect to a Web Service

If you do not control the RPC/encoded Web service that you want to work with, you can create a document/literal proxy Microsoft .NET Web service that provides wrapper functions for each of the Web methods, you want to invoke from the RPC/encoded Web service. You can then work with the proxy document/literal Web service from InfoPath.
  
.NET Framework code can work with any kind of Web service (both RPC/encoded and document/literal), and all .NET Web services use the document/literal style and encoding. Because the .NET Framework can communicate with any kind of Web service, you can create a .NET Web service that has methods that make calls to the RPC/encoded Web service. The .NET Web service will act as a translator that enables InfoPath to make document/literal style calls to the .NET Web service which in turn can make RPC/encoded style calls to the original Web service.
  
The prerequisites for creating such a proxy Microsoft .NET Web service are a Microsoft Windows or Microsoft Windows Server computer that is running Internet Information Services (IIS) with ASP.NET installed on which to deploy the proxy Web service. When you create an InfoPath solution, you will point to the proxy Web service instead of the RPC/encoded Web service. The proxy Web service will then make calls to the RPC/encoded service.
  
## Creating a Proxy Web Service Using Visual Studio

1. Create a new **ASP.NET Web Service Application** project.

2. In the **Solution Explorer**, right-click the **References** folder of your new project, and then click **Add Web Reference**.

3. In the **Add Web Reference** dialog box, type in the URL of the RPC/encoded Web service that you want to work with, and then click **Go**.

4. Click **Add Reference**.

5. Open the .asmx file for your Web service and add one Web Service method to call each Web Service method from the referenced RPC/encoded Web service.

6. To view a list of the methods in the reference RPC/encoded Web server, display the **Class View** window. For each Web Service method, you will see three methods. For example, if the Web Service method is called `doSearch`, then you will see three methods called `doSearch`, `BegindoSearch`, and `EnddoSearch`. You only have to create a wrapper Web Service method for the `doSearch` method. Be sure to match the exact method signature and return type.

7. Within each wrapper method, you have to write code to make a call to the referenced RPC/encoded Web service as shown in the following example.

  ```cs
    [WebMethod] 
    public string[] doSearch(string keyword) 
    { 
        SearchService srch = new SearchService(); 
        return srch.doSearch(keyword); 
    } 
    
  ```

8. If the RPC/encoded Web service requires authentication, you can hard code the credentials required to connect to the RPC/encoded Web service into the source code for the proxy .NET Web service, or you can use code like the following example.

  ```cs
    myProxy.Credentials = System.Net.CredentialCache.DefaultCredentials; 
    
  ```

For more information, search for the Microsoft Knowledge Base article "HOW TO: Pass Current Credentials to an ASP.NET Web Service" on <https://support.microsoft.com/>.

## Creating a Proxy Web Service Without Visual Studio .NET

Alternatively, you can create a proxy Web service by using the tools that are provided with the .NET Framework Software Development Kit, which can be downloaded from MSDN.
  
Use the Web Services Description Language Tool (Wsdl.exe) to create the code file for your proxy Web service. This code file can be compiled by using the C# command-line compiler (csc.exe) or the Visual Basic .NET command-line compiler (vbc.exe), which are also included with the .NET Framework SDK. After the Web Services Description Language tool has generated the code file, rename the file name extension to .asmx and open the file in any text editor. On the very first line of the document, add the following page directive:
  
```cs
<%@ WebService Language="C#" class="GoogleSearchServiceWrapper" %> 
```

Go to the end of the code file and create a call to each Web Service method in the RPC/encoded Web service. The following code sample shows the code for a .NET Web service that connects to the Google Web service, which uses the RPC/encoded style of development. There is a placeholder for where the wsdl.exe generated code should go.
  
```cs
<%@ WebService Language="C#" class="GoogleSearchServiceWrapper" %> 
 
using System; 
using System.Web.Services; 
 
// The auto-generated code from the wsdl.exe tool goes here. 
 
[WebService] 
public class GoogleSearchServiceWrapper : System.Web.Services.WebService  
{ 
    [WebMethod] 
    public System.Byte[] doGetCachedPage(System.String key, System.String url) 
    { 
        GoogleSearchService srch = new GoogleSearchService(); 
        return srch.doGetCachedPage(key, url); 
    } 
 
    [WebMethod] 
    public System.String doSpellingSuggestion(System.String key, System.String phrase) 
    { 
        GoogleSearchService srch = new GoogleSearchService(); 
        return srch.doSpellingSuggestion(key, phrase); 
    } 
 
    [WebMethod] 
    public GoogleSearchResult doGoogleSearch(System.String key, 
      System.String q, 
      System.Int32 start, 
      System.Int32 maxResults, 
      System.Boolean filter, 
      System.String restrict, 
      System.Boolean safeSearch, 
      System.String lr, 
      System.String ie, 
      System.String oe) 
    {
        GoogleSearchService srch = new GoogleSearchService();
           return srch.doGoogleSearch(key, q, start, maxResults, 
               filter, restrict, safeSearch, lr, ie, oe); 
    } 
}
```
