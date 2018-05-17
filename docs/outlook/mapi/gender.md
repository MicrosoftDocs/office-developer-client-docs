---
title: "Gender"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f60c65e3-b55f-cb68-746e-d0a8cd862d4d
description: "Last modified: July 23, 2011"
---

# Gender

  
  
**Applies to**: Outlook 
  
Specifies the possible values for the gender of a messaging user.
  
## Quick Info

```
enum Gender { 
    genderMin = 0, 
    genderUnspecified = genderMin, 
    genderFemale, 
    genderMale, 
    genderCount, 
    genderMax = genderCount - 1 
}; 

```

## Members

 _genderMin_
  
> The minimum number of different values supported for the gender.
    
 _genderUnspecified_
  
> The gender is not specified for the messaging user.
    
 _genderFemale_
  
> The messaging user is female.
    
 _genderMale_
  
> The messaging user is male.
    
 _genderCount_
  
> The number of different values supported for the gender.
    
 _genderMax_
  
> The maximum number of different values supported for the gender.
    
## See also

#### Reference

[PidTagGender Canonical Property](pidtaggender-canonical-property.md)

