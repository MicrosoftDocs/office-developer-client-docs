---
title: "Accessing Project Online enterprise custom fields"
manager: soliver
ms.date: 11/08/2016
ms.audience: Developer
localization_priority: Normal
ms.assetid: 25509631-fa14-49d8-b594-cfacf5355c38
description: "Project Online is an Office 365 service that companies can extend to meet business needs. One extension area is Enterprise Custom Fields (ECFs). ECFs are typed value fields that can be added to projects, resources, and tasks. The following table lists ECFs that associate with projects, resources, and tasks, and provides an example of a value for an instance of that ECF:"
---

# Accessing Project Online enterprise custom fields

Project Online is an Office 365 service that companies can extend to meet business needs. One extension area is Enterprise Custom Fields (ECFs). ECFs are typed value fields that can be added to projects, resources, and tasks. The following table lists ECFs that associate with projects, resources, and tasks, and provides an example of a value for an instance of that ECF:
  
|ECF Name|ECF Type|Association|Example Value|
|:-----|:-----|:-----|:-----|
|Justification  <br/> |TEXT  <br/> |Project  <br/> |An end user can record vital statistics and health data, with results that include a health evaluation and an individualized action plan towards better health.  <br/> |
|Risk Rating  <br/> |TEXT  <br/> |Project  <br/> |Low  <br/> |
|ROI  <br/> |NUMBER  <br/> |Project  <br/> |2.10  <br/> |
|Total Cost  <br/> |COST  <br/> |Project  <br/> |$1,031,514  <br/> |
|Launch Team  <br/> |TEXT  <br/> |Resources  <br/> |Yes  <br/> |
|Position Role  <br/> |TEXT  <br/> |Resources  <br/> |Tester  <br/> |
|Flag Status  <br/> |FLAG  <br/> |Task  <br/> |No  <br/> |
|Health  <br/> |TEXT  <br/> |Task  <br/> |Not specified  <br/> |
   
ECFs are defined at the Project Web Application (PWA) instance, external from any project, resource, or task. Yet, they can become associated with a project, resource, or task. This article provides an introductory look at custom fields using a sample application and focuses on retrieving ECF values. 
  
You can download the complete sample at https://github.com/OfficeDev/Project-CSOM-Read-Enterprise-CustomFields.
  
Additionally, Project Online supports local custom fields as read-only entities specific to the specific project, resource, or task. For more information on local custom fields, see the sample https://github.com/OfficeDev/Project-CSOM-Read-Local-CustomFields\.
  
## Background materials

A previous article, [Developing a Project Online application using the client-side object model](developing-a-project-online-application-using-the-client-side-object-model.md), provides background and the initial orientation for developing applications using CSOM. Refer to this article for the following items:
  
- Background information about Project, stand-alone and cloud-based editions 
    
- Development environment (Visual Studio editions and software libraries)
    
- Visual Studio project setup for a .NET application using the CSOM library
    
- Connecting to the Project Online service
    
## Preliminaries (class-level declarations)

The class for this application defines two data items: the project context and the pwaECF dictionary.
  
The project context object is part of the Project CSOM, and connects the application and the PWA instance. All requests to the service use the project context.
  
```cs
private static ProjectContext projContext = 
     new ProjectContext("https://Contoso216.sharepoint.com/sites/pwa");

```

The context needs the connection endpoint to create an instance in an application. The connection endpoint is the URL of your PWA instance. 
  
The pwaECF dictionary stores the project ECFs defined at the PWA level. The dictionary uses the ECF.InternalName as the key, and the CustomField object as the value. The dictionary is populated in the ListPWACustomFields method, and then used as a reference in the Main method. 
  
```cs
    //Dictionary of ECFs
        static Dictionary<String, CustomField> pwaECF = new Dictionary<string, CustomField>();

```

## Main method

The Main method manages the application flow. As with other applications that use the Project Online CSOM, Main initializes the project context. 
  
1. Retrieve and list the ECFs in the Project Online PWA.
    
   This functionality is implemented in the ListPWACustomFields method.
    
2. Retrieve projects with custom fields and non-custom fields.
    
   When retrieving projects with ECFs, the query request to the Project Online service needs to include the following items: 
    
   - **IncludeCustomFields** &ndash; This item requests the service to return a collection of PublishedProjects where each published project includes an extension that supports custom fields. Unless this item is specified, Project Online returns PublishedProject objects that do not include Custom Field data.
    
   - **IncludeCustomFields.CustomFields** &ndash; This item requests the service to populate the PublishedProject objects with CustomFields data.
    
   The following request specifies the project Id and Name, as well as the object extension for custom fields and the custom field values.
    
   ```cs
        var projBlk = projContext.LoadQuery(
        projContext.Projects.Include(
            p => p.Id, 
            p => p.Name,
            p => p.IncludeCustomFields,
            p => p.IncludeCustomFields.CustomFields
        ));
    
   ```

3. Examine each project.
    
   The project objects used in this application are the PublishedProject type because the values are retrieved and displayed. 
    
   If you need to update data values in one or more projects, the project undergoing the update would be checked out and the application would use a DraftProject object to retrieve the values and update the project.
    
4. Accessing the ECF entries for a project
    
   Each ECF instance separates the field value from the rest of the ECF information. The field value is stored as part of a key/value pair. The rest of the information is stored in a CustomField object.
    
   Accessing ECF values in a project consists of two parts:
    
   - Cycling through the CustomFields collection
    
   - Accessing the proper entry using two constructs.
    
   Each project stores associated ECF entries in two places, a CustomFields collection that is enumerable and and the field values as part of key/value pairs. In the key/value pairs, the internalName is the key and the field value is the value. Use a dictionary to hold and access the field values. 
    
   The ECF properties, other than the field values, are stored in CustomField objects, one object per project. Use a CustomFields collection to access the ECFs associated with an individual project. 
    
5. Each project stores the associated ECFs in a collection where each ECF entry consists of a key--the internal name of the ECF--and an object that holds the value of the ECF. Transfer the collection to a dictionary to access individual entries. The declaration follows.
    
   ```cs
    Dictionary<string, object> projDict = pubProj.IncludeCustomFields.FieldValues;
    
   ```

   The value in a dictionary entry corresponds to the data type of the ECF. The object for each ECF maps to one of a variety of types. Most ECFs use simple types that fit into standard variables. The following fragment shows that minimal processing is involved for several types:
    
   ```cs
    switch (cf.FieldType)
    {
        case CustomFieldType.COST:
            decimal costValue = (decimal)oVal;
            Console.WriteLine("\tFieldType:\t{0}\n\tValue:\t{1}", cf.FieldType, 
                costValue.ToString("C"));
            break;
        case CustomFieldType.DATE:
            Console.WriteLine("\tFieldType:\t{0}\n\tValue:\t{1}", cf.FieldType, 
                oVal.ToString());
            break;
        case CustomFieldType.FINISHDATE:
            Console.WriteLine("\tFieldType:\t{0}\n\tValue:\t{1}", cf.FieldType, 
                oVal.ToString());
            break;
        case CustomFieldType.DURATION:
            Console.WriteLine("\tFieldType:\t{0}\n\tValue:\t{1}", cf.FieldType, 
                oVal.ToString());
            break;
        case CustomFieldType.FLAG:
            Console.WriteLine("\tFieldType:\t{0}\n\tValue:\t{1}", cf.FieldType, 
                oVal.ToString());
            break;
        case CustomFieldType.NUMBER:
            Console.WriteLine("\tFieldType:\t{0}\n\tValue:\t{1}", cf.FieldType, 
                oVal.ToString());
            break;
    
   ```

   The lookup table of TEXT values, however, requires additional processing. The application retrieves the appropriate lookup table from the service, and outputs the ECF instance (with single or multiple values) by traversing the lookup table. The following code fragment shows processing of TEXT ECFs, including those with simple values and those using lookup tables: 
    
   ```cs
    case CustomFieldType.TEXT:
        if (!cf.LookupTable.ServerObjectIsNull.HasValue ||
            (cf.LookupTable.ServerObjectIsNull.HasValue && 
            cf.LookupTable.ServerObjectIsNull.Value))
        { //No lookup table
            Console.WriteLine("\tFieldType:\t{0}\n\tText:\t{1}", cf.FieldType, 
                oVal.ToString());
        }
        else
        { //Lookup table
            Console.WriteLine("\tFieldType:\t{0} - using Lookup Table", cf.FieldType);
            String[] entries = (String[])oVal;
            foreach (String entry in entries)
            {
                var luEntry = projContext.LoadQuery(cf.LookupTable.Entries
                    .Where(e => e.InternalName == entry));
                projContext.ExecuteQuery();
                Console.WriteLine("\tLookup Value:\t{0}", luEntry.First().FullValue);  
            }
        }
        break;
    
   ```

   This application simply outputs the value(s); however, it is possible to get more meaning from the data value(s).
    
## ListPWACustomFields

The ListPWACustomFields method retrieves and lists the ECFs associated with projects. This method lists the ECFs registered on the PWA instance that can be associated with individual projects. The entry point for accessing the ECFs uses the CustomFields element of the project context, as in the following query request:
  
```cs
// Project ECFs
    var allECFields = 
            projContext.LoadQuery(projContext.CustomFields.Include(
            qp => qp.InternalName,
            qp => qp.Name
        ));
    projContext.ExecuteQuery();

```

The method does not check to see whether a project uses a specific ECF.
  
## See also

- [Project Development Portal](https://developer.microsoft.com/en-us/project)
- [Overview: Enterprise custom fields and lookup tables](https://support.office.com/en-us/article/overview-enterprise-custom-fields-and-lookup-tables-f99db553-0b33-4648-93c0-f6a74637d790?ui=en-us&rs=en-us&ad=us)
- [Local and Enterprise Custom Fields](https://msdn.microsoft.com/library/office/ms447495(v=office.14).aspx)
- [Add or edit enterprise custom fields in Project Server 2013](https://docs.microsoft.com/project/add-or-edit-enterprise-custom-fields-in-project-server)
    

