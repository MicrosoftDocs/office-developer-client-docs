---
title: "Work with Digital Signatures"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
 
keywords:
- digital signatures [infopath 2007],InfoPath 2007, digital signatures
 
ms.localizationpriority: medium
ms.assetid: fd13fb71-aecf-47bb-8a6b-db70bd90ceeb
description: "The object model of the Microsoft.Office.InfoPath namespace provides features for working with digital signatures programmatically."
---

# Work with Digital Signatures

The object model of the [Microsoft.Office.InfoPath](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.aspx) namespace provides features for working with digital signatures programmatically. 
  
## Digital Signature Features

The digital signatures features provided by InfoPath enable you to: 
  
- Enable signatures for the entire form, or for specific sets of data in the form that can be signed separately.
    
- Specify, for each set of data that can be signed, whether a single signature or multiple signatures are allowed and what their relationship will be. For example, you can specify whether they are parallel co-signatures or whether each new signature countersigns all the earlier signatures.
    
- Specify a message to be shown to form users as they sign the form.
    
- Insert and see a signature in the document. 
    
- View verifiable non-repudiation information that has been added to each signature for increased security. This additional information, which includes a view of the form as it was presented to each signer, is part of the signature and cannot be removed without invalidating the signature. At any time, you can recall this data by clicking on the signature in the form to display the **Verify Digital Signature** dialog box. 
    
- Take advantage of an object model for working with digital signatures. Add custom information to the signature block in fully trusted forms through the digital signature object model. 
    
## Overview of the Digital Signatures Object Model

### The Sign Event

The object model for digital signatures provides the following event.
  
|**Name**|**Description**|
|:-----|:-----|
|[Sign](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Sign.aspx) <br/> |Occurs after a set of data has been selected to sign. You can use this event to manipulate the data stored within the digital signature. For example, you can add data from a trusted timestamp server, or add a server-side countersignature of the transaction. You can also use this event to block signing if the current user is not a member of a particular group. |
   
### The SignEventArgs Object

An event handler for the [Sign](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Sign.aspx) event can work with the [SignEventArgs](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignEventArgs.aspx) event object, which provides the following properties. 
  
|**Name**|**Description**|
|:-----|:-----|
|[SignedDataBlock](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignEventArgs.SignedDataBlock.aspx) <br/> |Gets the set of data that raised the [Sign](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Sign.aspx) event. |
|[SignatureWizard](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignEventArgs.SignatureWizard.aspx) <br/> |Gets or sets whether to display the **Digital Signatures** dialog box. |
   
> [!NOTE]
> In the [Microsoft.Office.Interop.InfoPath.SemiTrust](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.aspx) managed code object model that shipped with InfoPath 2003, the [SignEvent](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.SignEvent.aspx) event object for the [OnSign](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocumentEventSink2.OnSign.aspx) event provides an **XDocument** property for accessing the **XDocument** object of the form associated with the event. This is not necessary with form templates created with InfoPath Forms Services or InfoPath using the [Microsoft.Office.InfoPath](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.aspx) object model because the object model members of the [XmlForm](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.aspx) class can be accessed in form code using the **this** (C#) or **Me** (Visual Basic) keyword. For example, to access the [Signed](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.Signed.aspx) property of the [XmlForm](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.aspx) class to determine if a form is signed, you can type either `this.Signed` or `Me.Signed.`
  
### Collections and Objects

The object model for digital signatures provides the following collections.
  
|**Name**|**Description**|
|:-----|:-----|
|[SignedDataBlockCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignedDataBlockCollection.aspx) <br/> |The collection of the [SignedDataBlock](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignedDataBlock.aspx) objects in the form template as defined at design time in InfoPath design mode. The [SignedDataBlockCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignedDataBlockCollection.aspx) collection implements properties that can be used to access the [SignedDataBlock](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignedDataBlock.aspx) objects associated with a form. The [SignedDataBlockCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignedDataBlockCollection.aspx) object associated with a form is accessible through the [SignedDataBlocks](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.SignedDataBlocks.aspx) property of the [XmlForm](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.aspx) class. |
|[SignatureCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignatureCollection.aspx) <br/> |Contains a collection of [Signature](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Signature.aspx) objects for each [SignedDataBlock](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignedDataBlock.aspx) object in the form. The [SignatureCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignatureCollection.aspx) class implements properties and a method that can be used to access a form's associated [Signature](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Signature.aspx) objects and to create a signature. The [SignatureCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignatureCollection.aspx) object associated with a [SignedDataBlock](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignedDataBlock.aspx) is accessible using the [Signatures](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignedDataBlock.Signatures.aspx) property. When you use the [CreateSignature](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignatureCollection.CreateSignature.aspx) method of the [SignatureCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignatureCollection.aspx) class, keep in mind that the signature is not written until the [Sign](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Signature.Sign.aspx) method is called on the [Signature](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Signature.aspx) object. These methods can be called only from the **Sign** event handler of a fully trusted form template. |
   
The object model for digital signatures provides the following objects.
  
|**Name**|**Description**|
|:-----|:-----|
|[SignedDataBlock](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignedDataBlock.aspx) <br/> |Represents a set of signable data in a form. The [SignedDataBlock](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignedDataBlock.aspx) object provides a number of properties and one method that can be used to programmatically interact with a set of signable data. |
|[Signature](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Signature.aspx) <br/> |Represents a digital signature that has been added to a form or set of signable data in a form. The [Signature](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Signature.aspx) object implements properties that can be used to retrieve information about the digital signature, and the [Sign](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Signature.Sign.aspx) method for writing the XML digital signature block and computing its cryptographic hash value. |
|[Certificate](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Certificate.aspx) <br/> |Represents the X.509 digital certificate that has been used to create the signature. |
   
## Working with Digital Signatures Programmatically

The object model of the [Microsoft.Office.InfoPath](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.aspx) namespace provides members for interacting with digital signatures programmatically. In particular, fully-trusted forms can add custom information to the signature block before it is committed, according to the following timeline: 
  
1. User chooses to add a digital signature to a form.
    
2. The **Digital Signatures** dialog box is displayed, the user clicks **Add**, and then selects the data to sign.
    
3. The [Sign](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Sign.aspx) event for the selected data represented by the [SignedDataBlock](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignedDataBlock.aspx) object is raised, and the [Sign()](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignedDataBlock.Sign.aspx) method of [SignedDataBlock](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignedDataBlock.aspx) object and the [CreateSignature](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignatureCollection.CreateSignature.aspx) method of the [SignatureCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignatureCollection.aspx) collection are executed. 
    
4. Any optional custom actions are executed.
    
5. The [Sign()](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Signature.Sign.aspx) method of the [Signature](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Signature.aspx) object is executed. 
    
6. The **Sign** dialog box is displayed for typing a name (or selecting a signature image), selecting a certificate to sign with, and to enter comments. 
    
7. When the **Sign** button is clicked, the signature is added to the collection of signatures for the form and the non-repudiation information is captured and saved with the signature (which can be viewed later by clicking **View Signed Form** on the **Digital Signatures** dialog box, and then clicking **See the additional signing information that was collected**).
    
The following example invokes the [Sign()](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignedDataBlock.Sign.aspx) method when the user signs the selected data and countersigns the signature with a timestamp value retrieved from a trusted timestamp service. 
  
```cs
public void FormEvents_Sign(object sender, SignEventArgs e)
{
   // Add a new Signature object to the SignedDataBlockCollection.
   Signature thisSignature = 
      e.SignedDataBlock.Signatures.CreateSignature();
   // Write the XML digital signature block and compute hash
   // for signed data.
   thisSignature.Sign();
   // Countersign the signature with a trusted timestamp.
   // Get the XML node storing the signature block.
   XPathNavigator oNodeSig = thisSignature.SignatureBlockXmlNode;
   XPathNavigator oNodeSigValue = 
      oNodeSig.SelectSingleNode(
      ".//*[local-name(.)='signatureValue']");
   // Get timestamp from a trusted timestamp service (fictitious).
   MyTrustedTimeStampService s = new MyTrustedTimeStampService();
   string strVerifiedTimeStamp = s.AddTimeStamp(oNodeSigValue.Value);
   // Add the value returned from the timestamp service to the 
   // unsigned part of the signature block.
   XPathNavigator oNodeObj = 
      oNodeSig.SelectSingleNode(".//*[local-name(.)='Object']");
   XPathNavigator oNode = oNodeObj.Clone();
   oNode.SetValue(strVerifiedTimeStamp);
   oNodeObj.MoveToParent();
   oNodeObj.AppendChild(oNode);
   e.SignatureWizard = false;
}
```

```vb
Public Sub FormEvents_Sign(ByVal sender As Object, _
   ByVal e As SignEventArgs)
   ' Add a new Signature object to the SignedDataBlockCollection.
   Dim thisSignature As Signature = 
      e.SignedDataBlock.Signatures.CreateSignature
   ' Write the XML digital signature block and compute hash
   ' for signed data.
   thisSignature.Sign()
   ' Countersign the signature with a trusted timestamp.
   ' Get the XML node storing the signature block
   Dim oNodeSig As XPathNavigator  = _
      thisSignature.SignatureBlockXmlNode
   Dim oNodeSigValue As XPathNavigator  = _
      oNodeSig.SelectSingleNode(_
      ".//*[local-name(.)='signatureValue']")
   ' Get timestamp from a trusted timestamp service (fictitious).
   Dim s As MyTrustedTimeStampService = New MyTrustedTimeStampService()
   Dim strVerifiedTimeStamp As String  = _
      s.AddTimeStamp(oNodeSigValue.Value)
   ' Add the value returned from the timestamp service to the 
   ' unsigned part of the signature block.
   Dim oNodeObj As XPathNavigator  = 
      oNodeSig.SelectSingleNode(".//*[local-name(.)='Object']")
   Dim oNode As XPathNavigator  = oNodeObj.Clone()
   oNode.SetValue(strVerifiedTimeStamp)
   oNodeObj.MoveToParent()
   oNodeObj.AppendChild(oNode)
   e.SignatureWizard = False
```


