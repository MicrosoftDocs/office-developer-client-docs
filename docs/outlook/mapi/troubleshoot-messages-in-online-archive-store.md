---
title: Troubleshoot an application that can't open messages in the online archive store
description: Learn how to troubleshoot an application that can't open messages in the online archive store.
manager: lindalu
ms.date: 10/09/2025
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
---

# Troubleshoot an application that can't open messages in the online archive store

This article provides troubleshooting guidance for developers whose MAPI-based applications encounter issues when accessing messages in Office 365's [auto-expanding archive](/purview/autoexpanding-archiving).

## Symptoms

You have an in-house application that uses MAPI to access the auto-expanding archive in Office 365. The application first opens the online archive store, and then opens a message in the store. However, you can no longer use the same app to open other messages in the online archive store. For some messages, you receive the `MAPI_E_NO_SUPPORT (0x80040102)` error message.

## Cause

When the main archive reaches its transition threshold, additional storage space is provisioned for the auxiliary archive. The messages that don’t open are the messages that moved to the auxiliary archive. This failure occurs because the hierarchy server can’t find the messages after they’re moved.

## Workaround

To work around this issue, modify your in-house application to do the following:

1. Open the online archive store.
1. Open the folder containing the target message.
1. Then, open the message.
