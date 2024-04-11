---
title: "ISocialProfileAreFriendsOrColleagues"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: a0b586cd-65f6-4792-851c-4d36eaeec56d
description: "Determines whether the specified users are friends."
---

# ISocialProfile::AreFriendsOrColleagues

Determines whether the specified users are friends.
  
```cpp
HRESULT _stdcall AreFriendsOrColleagues(SAFEARRAY(BSTR) userIds, [out, retval] SAFEARRAY(VARIANT_BOOL)* results);
```

## Parameters

_userIds_
  
> [in] A structure that specifies an array of user ID values that correspond to a set of persons on the social network.
    
_results_
  
> [out] A pointer to structure that specifies an array of Boolean values, indicating whether the corresponding person in the _userIds_ array is a friend. 
    
## Remarks

For each person represented in the input array of the  _userIds_ parameter, this method sets the corresponding element in the output array of the  _results_ parameter. **true** indicates that the person is a friend, and **false** indicates that the person is not a friend. 
  
## See also

- [ISocialProfile : ISocialPerson](isocialprofileisocialperson.md)

