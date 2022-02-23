---
title: "Using Custom XSLT in InfoPath Form Templates" 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer 
ms.localizationpriority: medium
ms.assetid: 32c80bcd-a5d6-af32-38ba-9ca9ff148b99
description: "You can create most of the view elements you're likely to need in the Microsoft InfoPath form designer. If you need a custom view element that InfoPath can't create for you, however, you can manually modify the XSL Transformation (XSLT) that InfoPath uses to generate the view. To do so, extract the form into its component files by using Export Source Files on the Publish tab of the Microsoft Office Backstage, and then edit the transform in your preferred XML editor, such as Microsoft Visual Studio or Notepad."
---

# Using Custom XSLT in InfoPath Form Templates

You can create most of the view elements you're likely to need in the Microsoft InfoPath form designer. If you need a custom view element that InfoPath can't create for you, however, you can manually modify the XSL Transformation (XSLT) that InfoPath uses to generate the view. To do so, extract the form into its component files by using **Export Source Files** on the **Publish** tab of the Microsoft Office Backstage, and then edit the transform in your preferred XML editor, such as Microsoft Visual Studio or Notepad.
  
If you make changes to a view transform outside of InfoPath and then open the view in design mode and make changes, InfoPath will overwrite the changes you made manually. To keep InfoPath from overwriting the changes you make, you must place those changes in an `<xsl:template>` element in the transform and use the `xd:preserve` mode, as shown here:
  
```XML
<xsl:template match="my:field1" mode="xd:preserve"> 
   <div> 
      The value of field1 is <xsl:value-of select="."/> 
   </div> 
</xsl:template>
```

To include the template in the transformed file, use the `<xsl:apply-templates>` element with the same `xd:preserve` mode:
  
```XML
<xsl:apply-templates select="my:field1" mode="xd:preserve"/>
```

Elements and constructs defined within XSL templates with the `xd:preserve` mode will not be displayed in the InfoPath design environment. Instead, InfoPath will mark the custom section with a control labeled **Preserve Code Block** with a red border. When a user opens the form to fill it out, the custom XSL transforms are applied and the **Preserve Code Block** controls will not appear.
  