---
title: "Digitally Signing Data in InfoPath Forms"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
 
 
ms.localizationpriority: medium
ms.assetid: 7b396d9f-9a47-3170-367f-5d1f0144f927
description: "A digital signature is an electronic, encryption-based, secure stamp of authentication on a macro or document. A valid digital signature confirms that the data originated from the signer and has not been altered since it was signed. When documents or certain data in the documents are signed, the signature is computed and added to the document. This way, the signatures will always travel with the signed data."
---

# Digitally Signing Data in InfoPath Forms

A digital signature is an electronic, encryption-based, secure stamp of authentication on a macro or document. A valid digital signature confirms that the data originated from the signer and has not been altered since it was signed. When documents or certain data in the documents are signed, the signature is computed and added to the document. This way, the signatures will always travel with the signed data.
  
In order to sign data, users need to request a certificate from a certificate authority, and then use it to create digital signatures. The certificate authority will manage the life cycle of the certificates and keys (public or private) needed to encrypt data and create the signature.
  
Subsequent users of the document will have to verify existing signatures, and according to the result of the verification, may add their own contribution and sign. For accurate verification results, the verifier must trust the certificate authority who issued the certificate that was used to originally sign the document.
  
XML digital signatures are designed for transactions that involve XML documents and data. The power of XML signatures stays in the ability to sign only specific data in an XML document.
  
## Types of Digital Signatures in InfoPath Forms

Microsoft InfoPath implements digital signatures to help secure data in InfoPath forms. Two kinds of digital signatures are featured in InfoPath:
  
- Digital signatures that ensure the data integrity and authenticity of the form template (.xsn file)
    
- Digital signatures that ensure the integrity, authenticity, and support for non-repudiation related to data in XML forms
    
Whereas the first category of signatures is targeting the form template (.xsn file), the second category targets the actual user-entered data in InfoPath form files (.xml files), where the form designer can enable users to create digital signatures for the whole form or for sections of the form. There are fundamental differences between a signed template and a signed form. Although this document will have some references to signed templates (as an alternative way to create a form that will run as fully trusted), it does not provide details about this kind of signing. For more information about how to sign form templates, see [Deploying Signed InfoPath Form Templates](deploying-signed-infopath-form-templates.md) The focus in this topic is using signed InfoPath XML forms. Digital signatures created by InfoPath to sign data in XML forms comply with W3C XML Digital Signatures specifications. 
  
## Digital Signatures Features

InfoPath offers an extended digital signatures feature, with template developers being able to design flexible forms that enable digital signatures either for the whole form or for specific data in the form. Whereas digitally signing the whole form will always create counter-signatures for the form as an entity, signing parts of InfoPath forms enables more flexibility in choosing the kind of relationship between signatures added to the same set of data: there can be co-signatures, counter-signatures, or only one signature allowed.
  
With the signature, InfoPath will also add by default some non-repudiation information to identify the data users have seen in the current view, as well as the time and other environment settings as they were set when the signature was created. The non-repudiation information can be customized, but only the data in default non-repudiation nodes will be displayed in the non-repudiation dialog.
  
In order to add a signature, users have to select the set of data that will be signed. The set of data that can be signed is defined by the form template designer and used to sign the data when filling out the form. For each signature, users will have to follow a digital signature wizard for selecting the set of signable data, selecting a certificate, adding comments, and approving and committing the signature to the form.
  
When a user rests the mouse over a control that contains signed data, InfoPath displays a visual indication that the data is signed and cannot be changed. Form template designers can choose to have the signatures displayed in the view with the signed data so that users can take advantage of easy access to the non-repudiation information.
  
## Programmatic Support for Digital Signatures

The InfoPath object model includes support for digital signatures, which enables developers programmatic access to the sets of signable data are defined in the form through the [SignedDataBlockCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignedDataBlockCollection.aspx) class, to the signatures assigned to each set of signed data through the [SignatureCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignatureCollection.aspx) class, and to the certificate that is used to create a signature through the [Certificate](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Certificate.aspx) class. Additionally, the [Sign](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormEvents.Sign.aspx) event handler is customizable in fully trusted forms, offering support for advanced processing of digital signatures in InfoPath forms. 
  
## Interoperability

The infrastructure for digital signatures in InfoPath was designed by using the digital signatures support in MSXML5 so that InfoPath digital signatures have full interoperability with MSXML5 digital signatures.
  
Signed InfoPath forms and digital signatures created by InfoPath will also provide full interoperability with digital signatures created by using the Microsoft .NET Framework (starting with version 1.1). Signatures created by InfoPath can be verified by applications that use .NET Framework signature verification classes. Signatures created for data hosted in InfoPath forms by applications designed using .NET Framework digital signatures classes are successfully verified by InfoPath's digital signatures mechanism.
  
## See also



[Work with Digital Signatures](how-to-work-with-digital-signatures.md)

