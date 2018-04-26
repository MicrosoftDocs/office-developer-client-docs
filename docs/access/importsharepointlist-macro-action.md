---
title: "ImportSharePointList Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm152234
  
localization_priority: Normal
ms.assetid: 6a633d7d-d81d-0e2e-6c1c-706a552c1bf2
description: "You can use the ImportSharePointList action to import or link data from a Microsoft SharePoint Foundation site."
---

# ImportSharePointList Macro Action

You can use the **ImportSharePointList** action to import or link data from a Microsoft SharePoint Foundation site. 
  
> [!NOTE]
> This action will not be allowed if the database is not trusted. For more information about enabling macros, see the links in the **See Also** section of this article. 
  
## Setting

The **ImportSharePointList** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Transfer Type** <br/> | Select the type of transfer.  <br/>  Select **Import** to copy the SharePoint Foundation data into a table in Microsoft Access. Updates to the data in Access do not affect the data in SharePoint Foundation. Likewise, updates to the data in SharePoint Foundation do not affect the data in Access.  <br/>  Select **Link** to create a linked table in Access that links to the data in SharePoint Foundation. Updates to the data in Access are reflected in SharePoint Foundation. Likewise, updates to the data in SharePoint Foundation are reflected in Access.  <br/> |
|**Site Address** <br/> |Enter the full path of the SharePoint site.  <br/> |
|**List ID** <br/> |Enter the name or GUID of the list to be transferred. Required argument.  <br/> |
|**View ID** <br/> |Enter the GUID of the view for the list you want to use. Leave this argument blank to transfer all rows and columns in the list.  <br/> |
|**Table Name** <br/> |Enter the name you want displayed for the table or linked table in Access.  <br/> |
|**Get Lookup Display Values** <br/> |Select **Yes** to transfer display values for Lookup fields instead of the ID used to perform the lookup.  <br/> |
   
## Remarks

- This action has the same effect as clicking **SharePoint List** in the **Import** group on the **External Data** tab. The arguments for the action correspond to the choices you make in the Get External Data Wizard. 
    
- To run the **ImportSharePointList** action in a VBA module, use the **TransferSharePointList** method of the **DoCmd** object. 
    
- If you specify a nonexistent list or view, no error occurs, and no data is transferred.
    
- A GUID is a unique hexadecimal identifier for a list or a view. A GUID must be entered in the following format, where each "F" is a hexadecimal number (0 through 9 or A through F).
    
  ```
  {FFFFFFFF-FFFF-FFFF-FFFF-FFFFFFFFFFFF}
  ```

    You can obtain the GUID for a list or view from the SharePoint site by using the following procedure:
    
1. Open the list in SharePoint Foundation.
    
2. If the view you want is not displayed, click the **View** drop-down arrow and then select the view you want. 
    
3. Click the **View** drop-down arrow and then select **Modify this View**.The address in the browser's address bar contains the GUIDs for both the list and the view. The GUID for the list follows **List=**, and the GUID for the view follows **View=**. However, in the address, each **{** (left brace) character is represented by the string **%7B**, each **-** (hyphen) character is represented by the string **%2D**, and each **}** (right brace) character is represented by the string **%7D**. For example: 
    
  ```
  http://MySite12/_layouts/ViewEdit.aspx?List=%7B2A82A404%2D5529%2D47DC%2DAE13%2DAC1D9BC0A84F%7D&amp;View=%7B357B4FE6%2D44CF%2D4275%2DB91F%2D46558301579B%7D
  ```

    Before you can use the GUIDs from the address as arguments in this macro action, you must replace each **%7B** string with the **{** character, replace each **%2D** string with the **-** character, and replace each **%7D** string with the **}** character. Do not include the **&amp;** (ampersand) character that follows the **%7D** string in the list GUID. 
    

