---
title: "Create, retrieve, update, and delete projects"
manager: soliver
ms.date: 8/10/2016
ms.audience: Developer
localization_priority: Normal
ms.assetid: 6b690938-05bc-46a3-a40e-30f081403767
description: "Get the current ProjectContext instance; retrieve and iterate through the collection of published projects on the server; create, retrieve, check out, and delete a project by using the Project Server JavaScript object model; and change a project's properties."
---

# Create, retrieve, update, and delete projects

The scenarios in this article show how to get the current **ProjectContext** instance; retrieve and iterate through the collection of published projects on the server; create, retrieve, check out, and delete a project by using the Project Server JavaScript object model; and change a project's properties. 
  
> [!NOTE]
> These scenarios define custom code in the markup of a SharePoint application page but do not use the code-behind file that Visual Studio 2012 creates for the page. 
  
## Prerequisites for working with Project Server 2013 projects in the JavaScript object model

To perform the scenarios that are described in this article, you must install and configure the following products:
  
- SharePoint Server 2013
    
- Project Server 2013
    
- Visual Studio 2012
    
- Office Developer Tools for Visual Studio 2012
    
You must also have permissions to deploy the extension to SharePoint Server 2013 and to contribute to projects.
  
> [!NOTE]
> These instructions assume that you are developing on the computer that is running Project Server 2013. 
  
## Create the Visual Studio solution
<a name="pj15_CRUDProjectsJSOM_Setup"> </a>

The following steps create a Visual Studio 2012 solution that contains a SharePoint project and an application page. The page contains the logic for working with projects.
  
### To create the SharePoint project in Visual Studio

1. On the computer that is running Project Server 2013, run Visual Studio 2012 as an administrator.
    
2. On the menu bar, choose **File**, **New**, **Project**.
    
3. In the **New Project** dialog box, choose **.NET Framework 4.5** from the drop-down list at the top of the dialog box. 
    
4. In the **Office/SharePoint** template category, choose **SharePoint Solutions**, and then choose the **SharePoint 2013 Project** template. 
    
5. Name the project ProjectsJSOM, and then choose the **OK** button. 
    
6. In the **SharePoint Customization Wizard** dialog box, choose **Deploy as a farm solution**, and then choose the **Finish** button. 
    
7. Edit the value of the **Site URL** property for the **ProjectsJSOM** project to match the URL of the Project Web App instance (for example,  `http://ServerName/PWA`).
    
### To create the application page in Visual Studio

1. In **Solution Explorer**, open the shortcut menu for the **ProjectsJSOM** project, and then add a SharePoint "Layouts" mapped folder. 
    
2. In the **Layouts** folder, open the shortcut menu for the **ProjectsJSOM** folder, and then add a new SharePoint application page named ProjectsList.aspx.
    
3. Open the shortcut menu for the **ProjectsList.aspx** page and choose **Set as Startup Item**.
    
4. In the markup for the **ProjectsList.aspx** page, define user interface controls inside the "Main" **asp:Content** tags, as follows. 
    
   ```HTML
    <table width="100%" id="tblProjects">
        <tr id="headerRow">
            <th width="25%" align="left">Name</th>
            <th width="25%" align="left">Description</th>
            <th width="25%" align="left">Start Date</th>
            <th width="25%" align="left">ID</th>
        </tr>
    </table>
    <textarea id="txtGuid" rows="1" cols="35">Paste the project GUID here.</textarea>
    <button id="btnSend" type="button"></button><br />
    <span id="spanMessage" style="color: #FF0000;"></span>
   ```

   > [!NOTE]
   > These controls may not be used in every scenario. For example, the "Create projects" scenario does not use the **textarea** and **button** controls. 
  
5. After the closing **span** tag, add a **SharePoint:ScriptLink** tag, a **SharePoint:FormDigest** tag, and **script** tags, as follows. 
    
   ```HTML
    <SharePoint:ScriptLink id="ScriptLink" name="PS.js" runat="server" ondemand="false" localizable="false" loadafterui="true" />
    <SharePoint:FormDigest id="FormDigest" runat="server" />
    <script type="text/javascript">
        // Replace this comment with the code for your scenario.
    </script>
   ```

   The **SharePoint:ScriptLink** tag references the PS.js file, which defines the JavaScript object model for Project Server 2013. The **SharePoint:FormDigest** tag generates a message digest for security validation when required by operations that update server content. 
    
6. Replace the placeholder comment with the code from one of the following procedures:
    
   - [Create Project Server 2013 projects by using the JavaScript object model](#pj15_CRUDProjectsJSOM_CreateProjects)
    
   - [Update Project Server 2013 projects by using the JavaScript object model](#pj15_CRUDProjectsJSOM_UpdateProjects)
    
   - [Delete Project Server 2013 projects by using the JavaScript object model](#pj15_CRUDProjectsJSOM_DeleteProjects)
    
7. To test the application page, on the menu bar, choose **Debug**, **Start Debugging**. If you are prompted to modify the web.config file, choose **OK**.
    
## Create Project Server 2013 projects by using the JavaScript object model
<a name="pj15_CRUDProjectsJSOM_CreateProjects"> </a>

The procedure in this section creates projects by using the JavaScript object model. The procedure includes the following high-level steps:
  
1. Get the current **ProjectContext** instance. 
    
2. Create a **ProjectCreationInformation** object to specify initial properties for your project. Specify the required **name** property by using the **ProjectCreationInformation.set_name** function. 
    
3. Retrieve the published projects from the server by using the **ProjectContext.get_projects** function. The **get_projects** function returns a **ProjectCollection** object. 
    
4. Add the new project to the collection by using the **ProjectCollection.add** function and passing in the **ProjectCreationInformation** object. 
    
5. Update the collection by using the **ProjectCollection.update** function and the **ProjectContext.waitForQueueAsync** function. The **update** function returns a **QueueJob** object that you pass to **waitForQueueAsync**. This call also publishes the project.
    
Paste the following code between the **script** tags that you added in the **To create the application page in Visual Studio** procedure. 
  
```js
    // Declare a global variable to store the project collection.
    var projects;
    // Ensure that the PS.js file is loaded before your custom code runs.
    SP.SOD.executeOrDelayUntilScriptLoaded(CreateProject, "PS.js");
    // Add a project the projects collection.
    function CreateProject() {
        
        // Initialize the current client context.
        var projContext = PS.ProjectContext.get_current();
        // Initialize a ProjectCreationInformation object and specify properties
        // for the new project.
        // The Name property is required and must be unique.
        var creationInfo = new PS.ProjectCreationInformation();
        creationInfo.set_name("Test Project 1");
        // Specify optional properties for the new project.
        // If not specified, the Start property uses the current date and the
        // EnterpriseProjectTypeId property uses the default EPT.
        creationInfo.set_description("Created through the JSOM.");
        creationInfo.set_start("2013-10-01 09:00:00.000");
        // Get the projects collection.
        projects = projContext.get_projects();
        // Add the new project to the projects collection.
        projects.add(creationInfo);
        // Add a second project to use in the deleting projects procedure.
        creationInfo.set_name("Test Project 2");
        projects.add(creationInfo);
        // Submit the request to update the collection on the server
        var updateJob = projects.update();
        projContext.waitForQueueAsync(updateJob, 10, GetProjects);
    }
    // Get the projects collection.
    function GetProjects(response) {
        // This call demonstrates that you can get the context from the 
        // ProjectCollection object.
        var projContext = projects.get_context();
        // Register the request for information that you want to run on the server.
        // This call includes an optional "Include" parameter to request only the Name, Description,
        // StartDate, and Id properties of the projects in the collection.
        projContext.load(projects, 'Include(Name, Description, StartDate, Id)');
        // Run the request on the server.
        projContext.executeQueryAsync(IterateThroughProjects, QueryFailed);
    }
    // Iterate through the projects collection.
    function IterateThroughProjects(response) {
        // Get the enumerator and iterate through the collection.
        var enumerator = projects.getEnumerator();
        while (enumerator.moveNext()) {
            var project = enumerator.get_current();
            // Create and populate a row with the values for the project's Name, Description,
            // StartDate, and Id properties.
            var row = tblProjects.insertRow();
            row.insertCell().innerText = project.get_name();
            row.insertCell().innerText = project.get_description();
            row.insertCell().innerText = project.get_startDate();
            row.insertCell().innerText = project.get_id();
        }
        // This scenario does not use the textarea or button controls.
        $get("txtGuid").disabled = true;
        $get("btnSend").disabled = true;
    }
    function QueryFailed(sender, args) {
        $get("spanMessage").innerText = 'Request failed: ' + args.get_message();
    }
```

## Update Project Server 2013 projects by using the JavaScript object model
<a name="pj15_CRUDProjectsJSOM_UpdateProjects"> </a>

The procedure in this section updates the **startDate** property of a project by using the JavaScript object model. The procedure includes the following high-level steps: 
  
1. Get the current **ProjectContext** instance. 
    
2. Retrieve the published projects from the server by using the **ProjectContext.get_projects** function. The **get_projects** function returns a **ProjectCollection** object. 
    
3. Run the request on the server by using the **ProjectContext.load** function and the **ProjectContext.executeQueryAsync** function. 
    
4. Retrieve a **PublishedProject** object by using the **ProjectContext.getById** function. 
    
5. Check out the target project by using the **Project.checkOut** function. The **checkOut** function returns the draft version of the published project. 
    
6. Change the project's start date by using the **DraftProject.set_startDate** function. 
    
7. Publish the project by using the **DraftProject.publish** function and the **ProjectContext.waitForQueueAsync** function. The **publish** function returns a **QueueJob** object that you pass to **waitForQueueAsync**.
    
Paste the following code between the **script** tags that you added in the **To create the application page in Visual Studio** procedure. 
  
```js
    // Declare global variables.
    var projContext;
    var projects;
    // Ensure that the PS.js file is loaded before your custom code runs.
    SP.SOD.executeOrDelayUntilScriptLoaded(GetProjects, "PS.js");
    // Get the projects collection.
    function GetProjects() {
        // Initialize the current client context.
        projContext = PS.ProjectContext.get_current();
        // Get the projects collection.
        projects = projContext.get_projects();
        // Register the request for information that you want to run on the server.
        // This call includes an optional "Include" parameter to request only the Name, Description,
        // StartDate, and Id properties of the projects in the collection.
        projContext.load(projects, 'Include(Name, Description, StartDate, Id)');
        // Run the request on the server.
        projContext.executeQueryAsync(IterateThroughProjects, QueryFailed);
    }
    // Iterate through the projects collection.
    function IterateThroughProjects(response) {
        // Get the enumerator and iterate through the collection.
        var enumerator = projects.getEnumerator();
        while (enumerator.moveNext()) {
            var project = enumerator.get_current();
            // Create and populate a row with the values for the project's Name, Description,
            // StartDate, and Id properties.
            var row = tblProjects.insertRow();
            row.insertCell().innerText = project.get_name();
            row.insertCell().innerText = project.get_description();
            row.insertCell().innerText = project.get_startDate();
            row.insertCell().innerText = project.get_id();
        }
        // Initialize button properties.
        $get("btnSend").onclick = function () { ChangeProject(); };
        $get("btnSend").innerText = "Update";
    }
    // Change the project's start date.
    function ChangeProject() {
        // Get the identifier of the target project.
        var targetGuid = $get("txtGuid").innerText;
        // Get the target project and then check it out. The checkOut function
        // returns the draft version of the project.
        var project = projects.getById(targetGuid);
        var draftProject = project.checkOut();
        // Set the new property value and then publish the project.
        // Specify "true" to also check the project in.
        draftProject.set_startDate("2013-12-31 09:00:00.000");
        var publishJob = draftProject.publish(true);
        // Register the job that you want to run on the server and specify the
        // timeout duration and callback function.
        projContext.waitForQueueAsync(publishJob, 10, QueueJobSent);
    }
    // Print the JobState return code, which gives the status of the queue job.
    function QueueJobSent(response) {
        $get("spanMessage").innerText = 'JobState = ' + response + '. Wait a few seconds, then refresh the page to see your changes.';
    }
    function QueryFailed(sender, args) {
        $get("spanMessage").innerText = 'Request failed: ' + args.get_message();
    }
```

## Delete Project Server 2013 projects by using the JavaScript object model
<a name="pj15_CRUDProjectsJSOM_DeleteProjects"> </a>

The procedure in this section deletes a project by using the JavaScript object model. The procedure includes the following high-level steps:
  
1. Get the current **ProjectContext** instance. 
    
2. Retrieve the published projects from the server by using the **ProjectContext.get_projects** function. The **get_projects** function returns a **ProjectCollection** object. 
    
3. Run the request on the server by using the **ProjectContext.load** function and the **ProjectContext.executeQueryAsync** function. 
    
4. Retrieve a **PublishedProject** object by using the **ProjectCollection.getById** function. 
    
5. Delete the project by passing it to the **ProjectCollection.remove** function. 
    
6. Update the collection by using the **ProjectCollection.update** function and the **ProjectContext.waitForQueueAsync** function. The **update** function returns a **QueueJob** object that you pass to **waitForQueueAsync**.
    
Paste the following code between the **script** tags that you added in the **To create the application page in Visual Studio** procedure. 
  
```js
    // Declare global variables.
    var projContext;
    var projects;
    // Ensure that the PS.js file is loaded before your custom code runs.
    SP.SOD.executeOrDelayUntilScriptLoaded(GetProjects, "PS.js");
    // Get the projects collection.
    function GetProjects() {
        // Initialize the current client context.
        projContext = PS.ProjectContext.get_current();
        // Get the projects collection.
        projects = projContext.get_projects();
        // Register the request for information that you want to run on the server.
        // This call includes an optional "Include" parameter to request only the Name, Description,
        // StartDate, and Id properties of the projects in the collection.
        projContext.load(projects, 'Include(Name, Description, StartDate, Id)');
        // Run the request on the server.
        projContext.executeQueryAsync(IterateThroughProjects, QueryFailed);
    }
    // Iterate through the projects collection.
    function IterateThroughProjects(response) {
        // Get the enumerator and iterate through the collection.
        var enumerator = projects.getEnumerator();
        while (enumerator.moveNext()) {
            var project = enumerator.get_current();
            // Create and populate a row with the values for the project's Name, Description,
            // StartDate, and Id properties.
            var row = tblProjects.insertRow();
            row.insertCell().innerText = project.get_name();
            row.insertCell().innerText = project.get_description();
            row.insertCell().innerText = project.get_startDate();
            row.insertCell().innerText = project.get_id();
        }
        // Initialize button properties.
        $get("btnSend").onclick = function () { DeleteProject(); };
        $get("btnSend").innerText = "Delete";
    }
    // Delete the project.
    function DeleteProject() {
        // Get the identifier of the target project.
        var targetGuid = $get("txtGuid").innerText;
        // Get the target project and then remove it from the collection.
        var project = projects.getById(targetGuid);
        projects.remove(project);
        var removeJob = projects.update();
        // Register the job that you want to run on the server and specify the
        // timeout duration and callback function.
        projContext.waitForQueueAsync(removeJob, 10, QueueJobSent);
    }
    // Print the JobState return code, which gives the status of the queue job.
    function QueueJobSent(response) {
        $get("spanMessage").innerText = 'JobState = ' + response + '. Wait a few seconds, then refresh the page to see your changes.';
    }
    function QueryFailed(sender, args) {
        $get("spanMessage").innerText = 'Request failed: ' + args.get_message();
    }
```

<a name="pj15_CRUDProjectsJSOM_AR"> </a>

## See also

- [Project programming tasks](project-programming-tasks.md)
- [Client-side object model (CSOM) for Project 2013](client-side-object-model-csom-for-project-2013.md)
    

