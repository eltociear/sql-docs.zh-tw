---
title: sys.databases dm_resource_governor_external_resource_pool_affinity （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 11/13/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_external_resource_pool_affinity
- sys.dm_resource_governor_external_resource_pool_affinity_TSQL
- dm_resource_governor_external_resource_pool_affinity
- dm_resource_governor_external_resource_pool_affinity_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_resource_governor_external_resource_pool_affinity
- dm_resource_governor_external_resource_pool_affinity
ms.assetid: e32fac49-5161-47c0-8540-af3fe730c00c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 02ec95d318825c1759067455b62f3dae6a86c184
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053334"
---
# <a name="sysdm_resource_governor_external_resource_pool_affinity-transact-sql"></a>sys.databases dm_resource_governor_external_resource_pool_affinity （Transact-sql）
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
**適用于：** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)]和[!INCLUDE[sssql17-md](../../includes/sssql17-md.md)][!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

傳回關於目前外部資源集區設定的 CPU 親和性資訊。
  
|資料行名稱|資料類型|描述|
|----------------|---------------|-----------------|
|pool_id|**int**|外部資源集區的識別碼。 不可為 Null。|
|processor_group|**smallint**|Windows 邏輯處理器群組的 ID。 不可為 Null。|
|cpu_mask|**Bigint**|二進位遮罩，代表與此集區相關聯的 Cpu。 不可為 Null。|
  
## <a name="remarks"></a>備註

使用的親和性`AUTO`建立的集區不會出現在此視圖中，因為它們沒有相似性。 如需詳細資訊，請參閱[建立外部資源集區 &#40;transact-sql&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)和[ALTER external Resource pool &#40;transact-sql&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)語句。

## <a name="permissions"></a>權限

需要 `VIEW SERVER STATE` 權限。

## <a name="see-also"></a>另請參閱

[SQL Server 中機器學習服務的資源管理](../../advanced-analytics/r/resource-governance-for-r-services.md)

[dm_resource_governor_resource_pool_affinity &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md)

[外部指令碼已啟用伺服器組態選項](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)

[ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)
