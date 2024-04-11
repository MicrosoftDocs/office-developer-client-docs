---
title: "Gender"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: f60c65e3-b55f-cb68-746e-d0a8cd862d4d
---

# Gender

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies the possible values for the gender of a messaging user.
  
## Quick info

```cpp
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



[PidTagGender Canonical Property](pidtaggender-canonical-property.md)

