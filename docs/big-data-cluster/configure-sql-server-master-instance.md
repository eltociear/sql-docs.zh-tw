---
title: 設定 SQL Server 主要執行個體
titleSuffix: Configure SQL Server master instance of Big Data Cluster
description: 設定 SQL Server 巨量資料叢集的主要執行個體
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: overview
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 205f849310ffe2f6139e76783ba7fa6ac315b214
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/31/2020
ms.locfileid: "73532355"
---
# <a name="configure-master-instance-of-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>設定 [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]的主要執行個體

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

設定 [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]的主要執行個體。

無法在部署階段為 SQL Server 主要執行個體設定伺服器組態設定。 本文描述如何設定 SQL Server edition、啟用或停用 SQL Server Agent、啟用特定追蹤旗標，或啟用/停用客戶意見反應等設定的暫時因應措施。

若要變更這些設定的任一個，請遵循下列步驟：

1. 建立包含目標設定的自訂 `mssql-custom.conf` 檔案。 下列範例會啟用 SQL 代理程式、遙測、設定 Enterprise Edition 的 PID，並啟用追蹤旗標 1204：

   ```
   [sqlagent]
   enabled=true
   
   [telemetry]
   customerfeedback=true
   userRequestedLocalAuditDirectory = /tmp/audit

   [DEFAULT]
   pid = Enterprise

   [traceflag]
   traceflag0 = 1204
   ```

1. 將 `mssql-custom.conf` 檔案複製到 `/var/opt/mssql` Pod 中 `mssql-server` 容器的 `master-0` 內。 將 `<namespaceName>` 取代為巨量資料叢集名稱。

   ```bash
   kubectl cp mssql-custom.conf master-0:/var/opt/mssql/mssql-custom.conf -c mssql-server -n <namespaceName>
   ```

1. 將 SQL Server 執行個體重新啟動。  將 `<namespaceName>` 取代為巨量資料叢集名稱。

   ```bash
   kubectl exec -it master-0  -c mssql-server -n <namespaceName>-- /bin/bash
   supervisorctl restart mssql-server
   exit
   ```

> [!IMPORTANT]
> 如果 SQL Server 的主要執行個體位於可用性群組設定中，請複製所有 `mssql-custom.conf` Pod 中的 `master` 檔案。 請注意，每次重新啟動都會導致容錯移轉，因此，請務必確定您將此活動的時間設定在停機期間。

## <a name="known-limitations"></a>已知限制

- 上述步驟需要 Kubernetes 叢集系統管理員權限
- 您無法在部署後變更巨量資料叢集 SQL Server 主要執行個體的伺服器定序。

## <a name="next-steps"></a>後續步驟

如需部署 SQL Server 巨量資料叢集的詳細資訊，請參閱[開始使用 SQL Server 巨量資料叢集](deploy-get-started.md)。