---
title: "Getting ready to release an OSC provider"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: a7d28349-3121-49ae-ad28-043789e2d205
description: "This section suggests tests you can do before you release your Outlook Social Connector (OSC) provider."
---

# Getting ready to release an OSC provider

This section suggests tests you can do before you release your Outlook Social Connector (OSC) provider. You can start referring to the topics in this section and carry out some of these tests during your development and testing phases, but you should have completed these tests by the time you release. 

These tests verify the basic functionality of your implementation of the OSC provider interfaces with respect to the capabilities you specify for the OSC provider. Also, even though the OSC is a feature shared by multiple Office client applications, these tests use Outlook as the client to test the fundamental functionality. You should determine whether other tests are necessary for features specific to your provider.
  
## In this section

- [Testing Deployment](testing-deployment.md): Describes scenarios you should test for around installing and uninstalling an OSC provider.
    
- [Testing Capabilities, Authentication, and Configuration](testing-capabilities-authentication-and-configuration.md): Describes tests for getting capabilities, and scenarios around configuring an account and authenticating a user for a social network.
    
- [Testing Following and Stop-Following Persons](testing-following-and-stop-following-persons.md): Describes scenarios to test the OSC provider's ability to add a person as a friend, or to remove a friend from the social network. 
    
- [Testing Friends](testing-friends.md): Describes tests and scenarios to verify that the OSC provider appropriately returns data of friends and non-friends, where applicable, depending on the synchronization mode that the provider supports.
    
- [Testing Activities](testing-activities.md): Describes tests and scenarios to verify that the OSC provider appropriately returns activities of friends and non-friends, where applicable, depending on the synchronization mode that the provider supports.
    
## Reference

- [Outlook Social Connector Provider Reference](outlook-social-connector-provider-reference-0.md)
  
## Related sections

- [OSC Sample Templates](osc-sample-templates.md)
  
- [OSC Typical Calling Sequences](osc-typical-calling-sequences.md)
  
- [Developing a Provider with the OSC XML Schema](developing-a-provider-with-the-osc-xml-schema.md)
  
- [Debugging a Provider](debugging-a-provider.md)
  
- [Deploying a Provider](deploying-a-provider.md)
  

