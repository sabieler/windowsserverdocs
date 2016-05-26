---
title: Authorization entries should have distinct trust group names for primary servers with virtual machines that are not part of the same trust group
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: 
  - hyper-v
  - techgroup-compute
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8827a3a7-9f3c-4f51-826a-8e2ec43e01df
---
# Authorization entries should have distinct trust group names for primary servers with virtual machines that are not part of the same trust group
\[This information is preliminary and subject to change.\]

For more information about best practices and scans, see [Run Best Practices Analyzer Scans and Manage Scan Results](http://go.microsoft.com/fwlink/p/?LinkID=223177).

|||
|-|-|
|**Operating System**|[!INCLUDE[winthreshold_server_2](includes/winthreshold_server_2_md.md)]|
|**Product\/Feature**|Hyper\-V|
|**Severity**|Warning|
|**Category**|Configuration|

In the following sections, italics indicates UI text that appears in the Best Practices Analyzer tool for this issue.

## **Issue**
*The server will accept replication requests for the replica virtual machine from any of the servers in the authorization list associated with the same replication tag as the virtual machine.*

## **Impact**
*There might be privacy and security concerns with a virtual machine accepting replication from primary servers belonging to different authorization entries. This impacts the following authorization entries: \<list of authorization entries>*

## **Resolution**
*Use different tags in the authorization entries for primary servers with virtual machines that are not part of the same security group. Modify the Hyper\-V settings to configure the replication tags.*

