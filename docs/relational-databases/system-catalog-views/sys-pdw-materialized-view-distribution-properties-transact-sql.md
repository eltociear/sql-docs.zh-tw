---
title: sys.databases pdw_materialized_view_distribution_properties （Transact-sql）
ms.custom: seo-dt-2019
ms.date: 07/03/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d62b0e25-3226-4f87-a10a-b3a0d9555e19
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 5dca3564e8e2ccc83f0968d42c636112880f6e56
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401678"
---
# <a name="syspdw_materialized_view_distribution_properties-transact-sql-preview"></a>sys.databases pdw_materialized_view_distribution_properties （Transact-sql）（預覽）

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

顯示散發資訊具體化視圖。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------| 
|object_id|**int**|已指定三個屬性之具體化視圖的識別碼。| 
|distribution_policy |**tinyint**|2 = 雜湊</br>4 = ROUND_ROBIN|  
|distribution_policy_desc |**Nvarchar （60）**|HASH、ROUND_ROBIN|  
 
## <a name="permissions"></a>權限

需要 VIEW DATABASE STATE 權限。
 
## <a name="see-also"></a>另請參閱

[建立具體化 VIEW 做為 SELECT &#40;Transact-sql&#41;](/sql/t-sql/statements/create-materialized-view-as-select-transact-sql?view=azure-sqldw-latest)   
[ALTER 具體化 VIEW &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-materialized-view-transact-sql?view=azure-sqldw-latest)   
[說明 &#40;Transact-sql&#41;](/sql/t-sql/queries/explain-transact-sql?view=azure-sqldw-latest)   
[pdw_materialized_view_mappings &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-mappings-transact-sql?view=azure-sqldw-latest)   
[DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-pdw-showmaterializedviewoverhead-transact-sql?view=azure-sqldw-latest)   
[SQL 資料倉儲和平行處理資料倉儲目錄檢視](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
[Azure SQL 資料倉儲中支援的系統檢視](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-system-views)   
[Azure SQL 資料倉儲中支援的 T-SQL 陳述式](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-statements)
