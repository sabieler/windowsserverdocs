---
title: Bitsadmin setdescription
ms.custom: na
ms.prod: windows-server-2012
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1e46a5dd-4637-4a2e-b88f-d3f85b177db8
---
# Bitsadmin setdescription
Sets the description of the specified job.

## Syntax

```
bitsadmin /SetDescription <Job> <Description>
```

## Parameters

|Parameter|Description|
|-------------|---------------|
|Job|The job's display name or GUID|
|Description|Text used to describe the job.|

## <a name="BKMK_examples"></a>Examples
The following example retrieves the description for the job named *myDownloadJob*.

```
C:\>bitsadmin /SetDescription myDownloadJob "Music Downloads"
```

## Additional references
[Command-Line Syntax Key](../Command-Line-Syntax-Key.md)

