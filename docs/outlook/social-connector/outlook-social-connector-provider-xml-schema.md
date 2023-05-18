---
title: "Outlook Social Connector provider XML schema"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: 5a88adf0-9265-4d49-976d-de0d93269aa9
description: "All XML that is returned by OSC providers in OSC provider extensibility methods must comply with the following OSC provider XML schema. The OSC schema is reproduced here in its entirety."
---

# Outlook Social Connector provider XML schema

All XML that is returned by OSC providers in OSC provider extensibility methods must comply with the following OSC provider XML schema. The OSC schema is reproduced here in its entirety. The current schema definition file, OutlookSocialProvider1_1.xsd, is also provided in the download for the provider templates that accompany this article. For more information, see [Outlook Social Connector 2013: Provider templates](https://code.msdn.microsoft.com/Outlook-Social-Connector-73fd8d2c). 
  
```XML
<?xml version="1.0" encoding="utf-8"?>
<!--
    XML Schema for Microsoft Outlook Social Connector Provider Extensibility 
    Copyright (c) 2009 Microsoft Corporation
    All Rights Reserved
-->
<xs:schema
    xmlns:xs="https://www.w3.org/2001/XMLSchema"
    targetNamespace="http://schemas.microsoft.com/office/outlook/2010/06/socialprovider.xsd"
    xmlns="http://schemas.microsoft.com/office/outlook/2010/06/socialprovider.xsd"
    elementFormDefault="qualified">
  <!-- Root element for the activity feed -->
  <xs:element name="activityFeed" type="activityFeedType" />
  <!-- Type definition for .\activityFeed  -->
  <xs:complexType name="activityFeedType">
    <xs:sequence>
      <!-- Network where the activity feed items originated (required) -->
      <xs:element name="network"    type="xs:string"  minOccurs="1" maxOccurs="1" />
      <!-- Container for activity feed items (required) -->
      <xs:element name="activities" type="activitiesType" minOccurs="1" maxOccurs="1" />
      <!-- Container for feed item display templates (required) -->
      <xs:element name="templates"  type="templatesType"  minOccurs="1" maxOccurs="1" />
    </xs:sequence>
  </xs:complexType>
  <!-- Type definition for .\activityFeed\activities -->
  <xs:complexType name="activitiesType">
    <xs:sequence>
      <xs:element name="activityDetails" type="activityDetailsType" minOccurs="0" maxOccurs="unbounded" />
    </xs:sequence>
  </xs:complexType>
  <!-- Type definition for .\activityFeed\activities\activityDetails element -->
  <xs:complexType name="activityDetailsType">
    <xs:sequence>
      <!-- Used to denote the user id of the user generating this activity (required) -->
      <xs:element name="ownerID" type="xs:string" minOccurs="1" maxOccurs="1" />
      <!-- Used to denote a unique string idenfitifying this activity. Used for duplicate detection (required) -->
      <xs:element name="objectID" type="xs:string" minOccurs="1" maxOccurs="1" />
      <!-- Used to denote an activity feed update template, such as a blog post or profile change (required) -->
      <xs:element name="applicationID" type="xs:unsignedLong" minOccurs="1" maxOccurs="1" />
      <!-- Used to denote the template type, such as multiple profile change types (required) -->
      <xs:element name="templateID" type="xs:unsignedLong" minOccurs="1" maxOccurs="1" />
      <!-- Date on which this feed item was published (required) -->
      <xs:element name="publishDate" type="xs:dateTime" minOccurs="1" maxOccurs="1" />
      <!-- Used for denoting a status, photo or document related activity feed item (optional) -->
      <xs:element name="type" type="activityTemplateTypeRestrictionType" minOccurs="0" maxOccurs="1" />
      <!-- Variables included with the feed item (required) -->
      <xs:element name="templateVariables" type="templateVariablesType" minOccurs="1" maxOccurs="1" />
    </xs:sequence>
  </xs:complexType>
  <!-- Type definition for .\activityFeed\activities\activityDetails\templateVariables element -->
  <xs:complexType name="templateVariablesType">
    <xs:sequence>
      <xs:element name="templateVariable" type="templateVariableType" minOccurs="0" maxOccurs="unbounded" />
    </xs:sequence>
  </xs:complexType>
  <!-- Type definition for .\activityFeed\activities\activityDetails\templateVariables\templateVariable element -->
  <xs:complexType name="templateVariableType">
    <xs:sequence>
      <!-- All activityTemplateType nodes require a Name element to identify the node
           (required for all nodes)  -->
      <xs:element name="name" type="xs:string" minOccurs="1" maxOccurs="1" />
      <!-- Used for Publisher and Entity nodes, the Id node value is a unique id of the person or entity
           (required for the Publisher and Entity nodes)  -->
      <xs:element name="id" type="xs:string" minOccurs="0" maxOccurs="1" />
      <!-- Used for Publisher and Entity nodes, the nameHint node value is the name to be displayed in
           the formatted activity  -->
      <xs:element name="nameHint" type="xs:string" minOccurs="0" maxOccurs="1" />
      <!-- Used for Publisher and Entity nodes, the emailAddress node value is the SMTP address associated
           with the person being mentioned in the feed  -->
      <xs:element name="emailAddress" type="xs:string" minOccurs="0" maxOccurs="1" />
      <!-- Used for Publisher and Entity nodes, the profileUrl node value is the URI which points to the
           user's profile page   -->
      <xs:element name="profileUrl" type="xs:string" minOccurs="0" maxOccurs="1" />
      <!-- Used for Link nodes to denote the text the link should display
           (optional for the Link node, if not specified the URI will be used as the display text)  -->
      <xs:element name="text" type="xs:string" minOccurs="0" maxOccurs="1" />
      <!-- Used for Link and Picture nodes to specify the picture location or desired link, 
           (required for the Link and Picture nodes)
           Also used by Text nodes to specify a string value for the node -->
      <xs:element name="value" type="xs:string" minOccurs="0" maxOccurs="1" />
      <!-- Used for the Picture node to denote alternate text for the picture and/or a link where
           the user is taken when they click the picture
           (both elements are optional for the Picture node) -->
      <xs:element name="altText" type="xs:string" minOccurs="0" maxOccurs="1" />
      <xs:element name="href" type="xs:anyURI" minOccurs="0" maxOccurs="1" />
      <!-- Used for the List node as a container of the simpleTemplateVariables, which contain Picture nodes
           (required for the List node)  -->
      <xs:element name="listItems" type="templateListItemsType" minOccurs="0" maxOccurs="1" />
    </xs:sequence>
    <xs:attribute name="type" type="templateTypeRestrictionType" use="required" />
  </xs:complexType>
  <xs:simpleType name="templateTypeRestrictionType">
    <xs:restriction base="xs:string">
      <!-- Denotes the publisher of the feed item -->
      <xs:enumeration value="publisherVariable" />
      <!-- Entities which are not the publisher included with the feed item -->
      <xs:enumeration value="entityVariable" />
      <!-- Links included with the feed item -->
      <xs:enumeration value="linkVariable" />
      <!-- Text included with the feed item -->
      <xs:enumeration value="textVariable" />
      <!-- Picture variables included in ListVariableItem -->
      <xs:enumeration value="pictureVariable" />
      <!-- List to hold pictures included with the feed item
           A list holds a Name node and ListItems node  -->
      <xs:enumeration value="listVariable" />
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="templateListItemsType">
    <xs:sequence>
      <!-- Lists are used to contain a series of pictures, defined as a simpleTemplateVariable
           which is enumerated as a PictureVariable -->
      <xs:element name="simpleTemplateVariable" type="simpleTemplateVariableType" minOccurs="0" maxOccurs="unbounded" />
    </xs:sequence>
  </xs:complexType>
  <xs:complexType name="simpleTemplateVariableType">
    <xs:sequence>
      <!-- The name is used to identify this variable within the feed item template (required) -->
      <xs:element name="name" type="xs:string" minOccurs="1" maxOccurs="1" />
      <!-- Used for Link nodes to denote the text the link should display
           (optional for the Link node, if not specified the URI will be used 
           as the display text) -->
      <xs:element name="text" type="xs:string" minOccurs="0" maxOccurs="1" />
      <!-- URI of the picture location (required) -->
      <xs:element name="value" type="xs:anyURI" minOccurs="0" maxOccurs="1" />
      <!-- Alternate text for the picture (optional) -->
      <xs:element name="altText" type="xs:string" minOccurs="0" maxOccurs="1" />
      <!-- The picture can be a link which is specified here (optional) -->
      <xs:element name="href" type="xs:anyURI" minOccurs="0" maxOccurs="1" />
    </xs:sequence>
    <xs:attribute name="type" type="templateSimpleTypeRestrictionType" use="required" />
  </xs:complexType>
  <xs:simpleType name="templateSimpleTypeRestrictionType">
    <xs:restriction base="xs:string">
      <!-- Links included with the feed item -->
      <xs:enumeration value="linkVariable" />
      <!-- Text included with the feed item -->
      <xs:enumeration value="textVariable" />
      <!-- Picture variables included in ListVariableItem -->
      <xs:enumeration value="pictureVariable" />
    </xs:restriction>
  </xs:simpleType>
  <!-- Type definiton for .\activityFeed\templates -->
  <xs:complexType name="templatesType">
    <xs:sequence>
      <!-- Container for template parts -->
      <xs:element name="activityTemplateContainer" type="activityTemplateContainerType" minOccurs="0" maxOccurs="unbounded" />
    </xs:sequence>
  </xs:complexType>
  <!-- Type definiton for .\activityFeed\templates\activityTemplateContainer -->
  <xs:complexType name="activityTemplateContainerType">
    <xs:sequence>
      <!-- Used to denote an activity feed update template, such as a blog post or profile change (required) -->
      <xs:element name="applicationID" type="xs:unsignedLong" minOccurs="1" maxOccurs="1" />
      <!-- Used to denote the template type, such as multiple profile change types (required) -->
      <xs:element name="templateID" type="xs:unsignedLong" minOccurs="1" maxOccurs="1" />
      <!-- Template information for displaying activity feed item (required) -->
      <xs:element name="activityTemplate" type="activityTemplateType" minOccurs="1" maxOccurs="1" />
    </xs:sequence>
  </xs:complexType>
  <!-- Type definiton for .\activityFeed\templates\activityTemplateContainer\activityTemplate -->
  <xs:complexType name="activityTemplateType">
    <xs:sequence>
      <!-- Used for denoting a status, photo or document related activity feed item (optional) -->
      <xs:element name="type" type="activityTemplateTypeRestrictionType" minOccurs="0" maxOccurs="1" />
      <!-- Title used for displaying activity feed item (required) -->
      <xs:element name="title" type="xs:string" minOccurs="1" maxOccurs="1" />
      <!-- Extra information displayed with activity feed item (optional) -->
      <xs:element name="data" type="xs:string" minOccurs="0" maxOccurs="1" />
      <!-- Icon used for displaying activity feed item (required) -->
      <xs:element name="icon" type="xs:anyURI" minOccurs="1" maxOccurs="1" />
    </xs:sequence>
  </xs:complexType>
  <!-- Type definiton for .\activityFeed\templates\activityTemplateContainer\activityTemplate\type -->
  <!-- Only status, photo and document updates are specially recognized -->
  <xs:simpleType name="activityTemplateTypeRestrictionType">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Status Update" />
      <xs:enumeration value="Photo" />
      <xs:enumeration value="Document" />
      <xs:enumeration value="Other" />
    </xs:restriction>
  </xs:simpleType>
  <!-- Type definition for Capabilities-->
  <xs:element name="capabilities">
    <xs:annotation>
      <xs:documentation xml:lang="en">
        Schema for Capabilities
      </xs:documentation>
    </xs:annotation>
    <xs:complexType>
    <xs:sequence>
      <!-- Indicates if the network supports get friends call-->
      <xs:element name="getFriends" type="xs:boolean" minOccurs="1" maxOccurs="1"/>
      <!-- Indicates if the network allows storing friends-->
      <!--(contacts) locally as Outlook contact items-->
      <xs:element name="cacheFriends" type="xs:boolean" minOccurs="1" maxOccurs="1"/>
      <!-- Indicates if the network supports follow this person call-->
      <xs:element name="followPerson" type="xs:boolean" minOccurs="1" maxOccurs="1"/>
      <!-- Indicates if the network supports do not follow this person call-->
      <xs:element name="doNotFollowPerson" type="xs:boolean" minOccurs="1" maxOccurs="1"/>
      <!-- Indicates if the network supports get activities call-->
      <xs:element name="getActivities" type="xs:boolean" minOccurs="1" maxOccurs="1"/>
      <!-- Indicates if the network supports storing activities-->
      <!-- as Outlook RSS items-->
      <xs:element name="cacheActivities" type="xs:boolean" minOccurs="1" maxOccurs="1"/>
      <!-- Indicates if the network supports dynamic lookup-->
      <!-- of Activities-->
      <xs:element name="dynamicActivitiesLookup" type="xs:boolean" minOccurs="0" maxOccurs="1"/>
      <!-- Indicates if the OSC displays network url in Acct config-->
      <xs:element name="displayUrl" type="xs:boolean" minOccurs="1" maxOccurs="1"/>
      <!-- Indicates if the OSC should use Forms Based Authentication (LogonWeb method)-->
      <xs:element name="useLogonWebAuth" type="xs:boolean" minOccurs="1" maxOccurs="1"/>
      <!-- Indicates if the OSC should hide "Click here to create an account" and-->
      <!-- "Forgot your password?" hyperlinks in the account setup dialog-->
      <xs:element name="hideHyperlinks" type="xs:boolean" minOccurs="0" maxOccurs="1"/>
      <!-- Indicates if the OSC should call the GetAutoConfiguredSession-->
      <!-- function on the ISocialSession object interface to attempt-->
      <!-- autoconfiguration of the network for the user-->
      <xs:element name="supportsAutoConfigure" type="xs:boolean" minOccurs="0" maxOccurs="1"/>
      <!-- Determines the minimum time in minutes between network contact syncs, -->
      <!-- regardless of success -->
      <xs:element name="contactSyncRestartInterval" type="xs:unsignedInt" minOccurs="0" maxOccurs="1"/>
      <!-- Indicates if the network supports dynamic lookup-->
      <!-- of Activities using hashed SMTP addresses-->
      <xs:element name="dynamicActivitiesLookupEx" type="xs:boolean" minOccurs="0" maxOccurs="1"/>
      <!-- Indicates if the network supports dynamic lookup-->
      <!-- of Contacts using hashed SMTP addresses-->
      <xs:element name="dynamicContactsLookup" type="xs:boolean" minOccurs="0" maxOccurs="1"/>
      <!-- Indicates if the OSC should call LogonCached on ISocialSession2-->
      <xs:element name="useLogonCached" type="xs:boolean" minOccurs="0" maxOccurs="1"/>
      <!-- Indicates if the OSC should hide the Remember my password check box-->
      <xs:element name="hideRememberMyPassword" type="xs:boolean" minOccurs="0" maxOccurs="1"/>
      <!-- Url opens in the default browser when user clicks create account in Acct config-->
      <xs:element name="createAccountUrl" type="xs:anyURI" minOccurs="0" maxOccurs="1"/>
      <!-- Url opens in the default browser when user clicks forgot pwd in Acct config -->
      <xs:element name="forgotPasswordUrl" type="xs:anyURI" minOccurs="0" maxOccurs="1"/>
      <!-- Indicates if the OSC should sync on-demand activities when people pane is minimized--> 
      <xs:element name="showOnDemandActivitiesWhenMinimized" type="xs:boolean" minOccurs="0" maxOccurs="1"/>
      <!-- Indicates if the OSC should sync on-demand contacts when people pane is minimized -->
      <xs:element name="showOnDemandContactsWhenMinimized" type="xs:boolean" minOccurs="0" maxOccurs="1"/>
      <!-- Indicates hashing function used to hash email addresses, ignored unless-->
      <!-- dynamicActivitiesLookupEx = true or dynamicContactsLookup = true in capabilities XML-->
      <xs:element name="hashFunction" minOccurs="0" maxOccurs="1">
        <xs:simpleType>
          <xs:restriction base="xs:string">
            <xs:pattern value="SHA1|MD5|CRC32MD5"/>
          </xs:restriction>
        </xs:simpleType>
      </xs:element>
      <!-- Indicates if the autoconfiguration settings can be changed/overridden by the user or not -->
      <xs:element name="allowChangesToAutoConfigure" type="xs:boolean" minOccurs="0" maxOccurs="1"/>
    </xs:sequence>
    </xs:complexType>
  </xs:element>
  <!-- Root element for hashedAddresses list-->
  <xs:element name="hashedAddresses">
    <xs:annotation>
      <xs:documentation xml:lang="en">
        hashedAddresses contains a collection of personAddresses elements
      </xs:documentation>
    </xs:annotation>
    <xs:complexType>
      <xs:sequence>
        <xs:element name="personAddresses" minOccurs="0" maxOccurs="unbounded" type="personAddressType">
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  <!-- Type definition for personAddressType -->
  <xs:complexType name="personAddressType">
    <xs:annotation>
      <xs:documentation xml:lang ="en">
        personAddressType represents a collection of hashedAddress elements
      </xs:documentation>
    </xs:annotation>
    <xs:sequence>
      <xs:annotation>
        <xs:documentation>
          <!-- The hashedAddress element contains the hash of an SMTP address
          The hash is computed based on the hashFunction element in capabilities XML 
          Index attribute is an integer counter for each hashedAddress  -->
        </xs:documentation>
      </xs:annotation>
      <xs:element name="hashedAddress" minOccurs="0" maxOccurs="unbounded" type="xs:string"/>
    </xs:sequence>
    <xs:attribute name="index" type="xs:int" use ="required" />
  </xs:complexType>
  <!-- Root element for friends list-->
  <xs:element name="friends">
    <xs:annotation>
      <xs:documentation xml:lang="en">
        Friends contains a collection of person elements
      </xs:documentation>
    </xs:annotation>
    <xs:complexType>
      <xs:sequence>
        <xs:element name="person" minOccurs="0" maxOccurs="unbounded" type="personType">
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  <!-- Root element for friend element-->
  <xs:element name="person" type="personType">
    <xs:annotation>
      <xs:documentation xml:lang="en">
        Top level friend element for being returned via ISocialPerson::GetDetails
      </xs:documentation>
    </xs:annotation>
  </xs:element>
  <!-- Type definition for personType -->
  <xs:complexType name="personType">
    <xs:annotation>
      <xs:documentation xml:lang="en">
        personType represents a person contact in Outlook
      </xs:documentation>
    </xs:annotation>
      <xs:sequence>
        <!-- Network User ID for this person -->
        <xs:element name="userID" type="xs:string" />
        <!-- Person first name or given name -->
        <xs:element name="firstName" minOccurs="0" type="stringType" />
        <!-- Person last name or surname-->
        <xs:element name="lastName" minOccurs="0" type="stringType" />
        <!-- Person full name -->
        <xs:element name="fullName" minOccurs="0" type="stringType" />
        <!-- Person nickname -->
        <xs:element name="nickname" minOccurs="0" type="stringType" />
        <!-- Person fileas name used for FileAs property of Contact item-->
        <xs:element name="fileAs" minOccurs="0" type="stringType" />
        <!-- Company name for the person -->
        <xs:element name="company" minOccurs="0" type="stringType" />
        <!-- Person title -->
        <xs:element name="title" minOccurs="0" type="stringType" />
        <!-- Person's anniversary date -->
        <xs:element name="anniversary" minOccurs="0" type="xs:date" />
        <!-- Person's birthday -->
        <xs:element name="birthday" minOccurs="0" type="xs:date" />
        <!-- Unique SMTP address for the person -->
        <xs:element name="emailAddress" minOccurs="0" type="xs:string" />
        <!-- Email2 SMTP address for the person -->
        <xs:element name="emailAddress2" minOccurs="0" type="xs:string" />
        <!-- Email3 SMTP address for the person -->
        <xs:element name="emailAddress3" minOccurs="0" type="xs:string" />
        <!-- Web profile page for the person -->
        <xs:element name="webProfilePage" minOccurs="0" type="xs:string" />
        <!-- Person's home phone -->
        <xs:element name="phone" minOccurs="0" type="stringType" />
        <!-- Person's cell or mobile phone -->
        <xs:element name="cell" minOccurs="0" type="stringType" />
        <!-- Person's home phone (this element is not used in OSC v1.0) -->
        <xs:element name="homePhone" minOccurs="0" type="stringType" />
        <!-- Person's work phone -->
        <xs:element name="workPhone" minOccurs="0" type="stringType" />
        <!-- Person's address -->
        <xs:element name="address" minOccurs="0" type="stringType" />
        <!-- Person's city -->
        <xs:element name="city" minOccurs="0" type="stringType" />
        <!-- Person's state/province -->
        <xs:element name="state" minOccurs="0" type="stringType" />
        <!-- Person's country/region -->
        <xs:element name="countryOrRegion" minOccurs="0" type="stringType" />
        <!-- Person's zip code -->
        <xs:element name="zip" minOccurs="0" type="stringType" />
        <!-- Person's relationship (this element is not used in OSC v1.0) -->
        <xs:element name="relationship" minOccurs="0" type="stringType" />
        <!-- Creation time of the person's profile on the network -->
        <xs:element name="creationTime" minOccurs="0" type="xs:dateTime" />
        <!-- Last modification time of person's profile on the network -->
        <xs:element name="lastModificationTime" minOccurs="0" type="xs:dateTime" />
        <!-- Expiration time of the person's profile data -->
        <xs:element name="expirationTime" minOccurs="0" type="xs:dateTime" />
        <!-- Gender for this person -->
        <xs:element name="gender" minOccurs="0">
          <xs:simpleType>
            <xs:restriction base="xs:string">
              <xs:pattern value="male|female|unspecified"/>
            </xs:restriction>
          </xs:simpleType>
        </xs:element>
        <!-- Index must equal index attribute passed to the provider in personAddresses
             Required only when friends XML is returned to ISocialSession2::GetPeopleDetails -->
        <xs:element name ="index" minOccurs="0" type="xs:int" />
        <!-- Url for the person's picture -->
        <xs:element name ="pictureUrl" minOccurs="0" type="xs:string" />
        <!-- Indicates friend status with logged-on user -->
        <xs:element name="friendStatus" minOccurs ="0">
          <xs:simpleType>
            <xs:restriction base="xs:string">
              <xs:pattern value="friend|notfriend|pending|pendingin|pendingout"/>
            </xs:restriction>
          </xs:simpleType>
        </xs:element>
        <!-- Person's business address -->
        <xs:element name="businessAddress" minOccurs="0" type="stringType" />
        <!-- Person's business city -->
        <xs:element name="businessCity" minOccurs="0" type="stringType" />
        <!-- Person's business state/province -->
        <xs:element name="businessState" minOccurs="0" type="stringType" />
        <!-- Person's business country/region -->
        <xs:element name="businessCountryOrRegion" minOccurs="0" type="stringType" />
        <!-- Person's business zip code -->
        <xs:element name="businessZip" minOccurs="0" type="stringType" />
        <!-- Person's other address -->
        <xs:element name="otherAddress" minOccurs="0" type="stringType" />
        <!-- Person's other city -->
        <xs:element name="otherCity" minOccurs="0" type="stringType" />
        <!-- Person's other state/province -->
        <xs:element name="otherState" minOccurs="0" type="stringType" />
        <!-- Person's other country/region -->
        <xs:element name="otherCountryOrRegion" minOccurs="0" type="stringType" />
        <!-- Person's other zip code -->
        <xs:element name="otherZip" minOccurs="0" type="stringType" />
        <!-- Person's personal website -->
        <xs:element name="website" minOccurs="0" type="stringType" />
        <!-- Person's  askmeabout -->
        <xs:element name="askmeabout" minOccurs="0" type="stringType" />
        <!-- Person's personal industries -->
        <xs:element name="industries" minOccurs="0" type="stringType" />
        <!-- Person's personal skills -->
        <xs:element name="skills" minOccurs="0" type="stringType" />
        <!-- Person's personal interests -->
        <xs:element name="interests" minOccurs="0" type="stringType" />
        <!-- Person's personal schools -->
        <xs:element name="schools" minOccurs="0" type="stringType" />
        <!-- Person's location -->
        <xs:element name="location" minOccurs="0" type="stringType" />
      </xs:sequence>
  </xs:complexType>
  <xs:simpleType name="stringType">
    <xs:restriction base="xs:string">
      <xs:maxLength value="1024" />
    </xs:restriction>
  </xs:simpleType>
</xs:schema>

```

## See also

- [Capabilities XML Example](capabilities-xml-example.md)  
- [Friends XML Example](friends-xml-example.md) 
- [Activity Feed XML Example](activity-feed-xml-example.md)  
- [XML for Capabilities](xml-for-capabilities.md)  
- [XML for Friends](xml-for-friends.md)  
- [XML for Activities](xml-for-activities.md)  
- [Outlook Social Connector Provider Interfaces](outlook-social-connector-provider-interfaces.md)

