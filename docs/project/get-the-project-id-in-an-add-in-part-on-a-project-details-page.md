---
title: "Get the project ID in an add-in part on a Project Details Page"
manager: soliver
ms.date: 08/10/2016
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: 009cd997-c7e5-4078-b495-c40caa29a5fb
description: "Add-in parts are hosted in iframe elements that are fully isolated from the hosting page. To get information about the current project from an add-in part on Project Details Page (PDP), you can use the window.postMessage method, an event listener, and an event handler that parses out the project ID from the message."
---

# Get the project ID in an add-in part on a Project Details Page

Add-in parts are hosted in **iframe** elements that are fully isolated from the hosting page. To get information about the current project from an add-in part on Project Details Page (PDP), you can use the **window.postMessage** method, an event listener, and an event handler that parses out the project ID from the message. 
  
## Prerequisites for creating a SharePoint-hosted add-in part that gets the project ID
<a name="Prereqs"> </a>

To use the code example in this article, you'll need either of the following:
  
- SharePoint 2013 and Project Server 2013, configured for add-in isolation. If you're developing remotely, the server must support sideloading of add-ins or you must install the add-in on a Developer Site.
  
- SharePoint Online and Project Online
    
    - Visual Studio 2013, Visual Studio 2012 with Office Developer Tools for Visual Studio 2013, or Napa
        
    - Sufficient permissions for the logged-on user:
        
        - Local administrator permissions on the development computer.
            
        - Read access to at least one project.
            
        - Permission to edit pages on the Project Web App site.
            
        - You must be logged on as someone other than the system account. The system account does not have permission to install an add-in.
    
See [Prerequisites for creating an add-in for Project Server 2013](create-a-sharepoint-hosted-project-server-add-in.md#pj15_StatusingApp_Prerequisites) for more information about add-ins for Project. See [Set up an on-premises development environment for SharePoint Add-ins](/sharepoint/dev/sp-add-ins/set-up-an-on-premises-development-environment-for-sharepoint-add-ins) for guidance about on-premises setup (including how to disable the loopback check, if necessary). If you're developing remotely, see [Developing apps for SharePoint on a remote system](/sharepoint/dev/sp-add-ins/develop-sharepoint-add-ins).
  
## Create the SharePoint-hosted add-in and client web part
<a name="CreateApp"> </a>

1. Open Visual Studio and choose **File** > **New** > **Project**.
    
2. In the **New Project** dialog box, choose **.NET Framework 4.5** from the drop-down list at the top of the dialog box. 
    
3. In the **Templates** list, choose **Visual C#** > **Office/SharePoint** > **Add-ins** > **Add-in for SharePoint 2013**.
    
4. Name the add-in GetProjectIdAddinPart, and then choose the **OK** button. 
    
5. In the **New add-in for SharePoint** dialog box, enter the URL of the PWA site that you want to use for debugging (for example:  _https://contoso.com/sites/pwasite/_).
    
6. Choose the **SharePoint-hosted** option to host your add-in, and then choose the **Finish** button. 
    
7. In **Solution Explorer**, open the shortcut menu for the GetProjectIdAddinPart project, and then choose **Add** > **New Item**.
    
8. In the **Add New Item** dialog box, choose **Client web part (Host Web)**, name the web part GetProjectId, and then choose the **Add** button. 
    
9. In the **Create Client web part** dialog box, choose the **Create a new client web part page** option, and then choose the **Finish** button. 
    
## Get the project ID in the add-in part
<a name="GetProjectId"> </a>

The GetProjectId add-in part defines its custom code in the GetProjectId.aspx page of the client web part. The logic that receives and handles the message is defined in the **head** element of the page and the page controls are defined in the **body** element of the page. 
  
1. Open the GetProjectId.aspx web part page (in the **Pages** folder). 
    
2. In the **head** element of the page, replace the code between the **script** tags with the following code. 
    
   ```js
        'use strict';
        // Define global variables.
        var hostUrl = '';
        var projectUid;
        // Set the style of the client web part page to be consistent with the host web.
                (function () {
                    var hostUrl = '';
                    var link = document.createElement('link');
                    link.setAttribute('rel', 'stylesheet');
                    if (document.URL.indexOf('?') != -1) {
                        var params = document.URL.split('?')[1].split('&');
                        for (var i = 0; i < params.length; i++) {
                            var p = decodeURIComponent(params[i]);
                            if (/^SPHostUrl=/i.test(p)) {
                                hostUrl = p.split('=')[1];
                                link.setAttribute('href', hostUrl + '/_layouts/15/defaultcss.ashx');
                                break;
                            }
                        }
                    }
                    if (hostUrl == '') {
                        link.setAttribute('href', '/_layouts/15/1033/styles/themable/corev15.css');
                    }
                    document.head.appendChild(link);
                })();
        // Get the message.
        function getProjectUid() {
            window.parent.postMessage('getprojectuid', hostUrl);
        }
        getProjectUid();
        // Add an event listener and register the event handler.
        // If the IE browser version is earlier than 9, use the attachEvent method.
        if (window.addEventListener) {
            window.addEventListener("message", onMessage, false);
        }
        else {
            if (window.attachEvent) {
                window.attachEvent("onmessage", onMessage);
            }
        }
        // Get the project ID from the message.
        function onMessage(event) {
            // Verify the message origin.
            if (hostUrl.indexOf(event.origin) != 0) return;
            // The expected message format is "<PDPProjectUid>00000000-0000-0000-0000-000000000000</PDPProjectUid>,"
            // so validate by using the length and the start and end tags.
            var length = event.data.length;
            if (length = 67) {
                var expectedStart = "<PDPProjectUid>";
                var expectedEnd = "</PDPProjectUid>";
                var endTagPosition = length - expectedEnd.length;
                var start = event.data.substr(0, expectedStart.length);
                var end = event.data.substr(endTagPosition, expectedEnd.length);
                // Parse out the project ID.
                if (start == expectedStart && end == expectedEnd) {
                    projectUid = event.data.substr(expectedStart.length, 36);
                    $get('projectUid').innerText = projectUid;
                }
            }
        }
   ```

3. Add the following code in the **body** element of the page. The code defines a span control that displays the project ID. 
    
   ```HTML
    <p>The ID for this project is:</p>
    <span id="projectUid"></span>
   ```

4. In the Elements.xml file, optionally change the name, title, description, and default size of the add-in part. This example uses the default values.
    
5. To test the add-in part, on the menu bar, choose **Debug**, **Start Debugging**. If you're prompted to modify the web.config file, choose the **OK** button. 
    
   To debug the add-in part, set appropriate breakpoints in the script that you added.
    
6. Browse to a PDP page and choose **Edit page** from the Tools menu (gear icon). 
    
7. Add the **GetProjectId Title** part to a web part on the page. The project ID displays in the **span** control on the web part page. 
    
## Next steps
<a name="NextSteps"> </a>

The add-in part in this example doesn't access Project Server data or SharePoint data. You can use the product ID to get information about the current project by using a client API, such as the JavaScript object model or the REST service.
  
In the AppManifest.xml file, specify the permissions that your add-in needs to access Project Server data or SharePoint data. 
  
See [Create add-in parts to install with your SharePoint Add-in](https://msdn.microsoft.com/library/a2664289-6c56-4cb1-987a-22367fad55eb%28Office.15%29.aspx) to learn how to set custom properties for an add-in part. 
  
## Example: Getting the project ID in an add-in part on a PDP page
<a name="CodeExample"> </a>

The following example is the complete code in the client web part's GetProjectID.aspx page. The code registers an event listener and an event handler that receives and parses a message that contains the project ID.
  
```HTML
<%@ Page language="C#" Inherits="Microsoft.SharePoint.WebPartPages.WebPartPage, Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
<%@ Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
<%@ Register Tagprefix="Utilities" Namespace="Microsoft.SharePoint.Utilities" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
<%@ Register Tagprefix="WebPartPages" Namespace="Microsoft.SharePoint.WebPartPages" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
<WebPartPages:AllowFraming ID="AllowFraming" runat="server" />
<html>
<head>
    <title></title>
    <script type="text/javascript" src="../Scripts/jquery-1.7.1.min.js"></script>
    <script type="text/javascript" src="/_layouts/15/MicrosoftAjax.js"></script>
    <script type="text/javascript" src="/_layouts/15/sp.runtime.js"></script>
    <script type="text/javascript" src="/_layouts/15/sp.js"></script>
    <script type="text/javascript">
        'use strict';
        // Define global variables.
        var hostUrl = '';
        var projectUid;
        // Set the style of the client web part page to be consistent with the host web.
        (function () {
            var hostUrl = '';
            var link = document.createElement('link');
            link.setAttribute('rel', 'stylesheet');
            if (document.URL.indexOf('?') != -1) {
                var params = document.URL.split('?')[1].split('&');
                for (var i = 0; i < params.length; i++) {
                    var p = decodeURIComponent(params[i]);
                    if (/^SPHostUrl=/i.test(p)) {
                        hostUrl = p.split('=')[1];
                        link.setAttribute('href', hostUrl + '/_layouts/15/defaultcss.ashx');
                        break;
                    }
                }
            }
            if (hostUrl == '') {
                link.setAttribute('href', '/_layouts/15/1033/styles/themable/corev15.css');
            }
            document.head.appendChild(link);
        })();
        // Get the message.
        function getProjectUid() {
            window.parent.postMessage('getprojectuid', hostUrl);
        }
        getProjectUid();
        // Add an event listener and register the event handler.
        // If the IE browser version is earlier than 9, use the attachEvent method.
        if (window.addEventListener) {
            window.addEventListener("message", onMessage, false);
        }
        else {
            if (window.attachEvent) {
                window.attachEvent("onmessage", onMessage);
            }
        }
        // Get the project ID from the message.
        function onMessage(event) {
            // Verify the message origin.
            if (hostUrl.indexOf(event.origin) != 0) return;
            // The expected message format is "<PDPProjectUid>00000000-0000-0000-0000-000000000000</PDPProjectUid>,"
            // so validate by using the length and the start and end tags.
            var length = event.data.length;
            if (length = 67) {
                var expectedStart = "<PDPProjectUid>";
                var expectedEnd = "</PDPProjectUid>";
                var endTagPosition = length - expectedEnd.length;
                var start = event.data.substr(0, expectedStart.length);
                var end = event.data.substr(endTagPosition, expectedEnd.length);
                // Parse out the project ID.
                if (start == expectedStart && end == expectedEnd) {
                    projectUid = event.data.substr(expectedStart.length, 36);
                    $get('projectUid').innerText = projectUid;
                }
            }
        }
    </script>
</head>
<body>
    <p>The ID for this project is:</p>
    <span id="projectUid"></span>
</body>
</html>

```

## See also

- [Project programming tasks](project-programming-tasks.md)
- [Create a SharePoint-hosted Project Server add-in](create-a-sharepoint-hosted-project-server-add-in.md)
- [Create add-in parts to install with your SharePoint Add-in](https://msdn.microsoft.com/library/a2664289-6c56-4cb1-987a-22367fad55eb%28Office.15%29.aspx)
    
