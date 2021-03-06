---
title: MSmerge_contents （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_contents
- MSmerge_contents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_contents system table
ms.assetid: 8d68a61a-683f-4b20-92f9-c0a8d9ba0ad1
author: stevestein
ms.author: sstein
ms.openlocfilehash: a4be6cffcc7e4f13b88d8037b53d438d604b9650
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68089939"
---
# <a name="msmerge_contents-transact-sql"></a>MSmerge_contents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_contents**資料表會針對目前資料庫中每個已修改的資料列，各包含一個資料列，因為它已發行。 合併處理序利用這份資料表來判斷已變更的資料列。 這份資料表儲存在發行集和訂閱資料庫中。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|已發行資料表的暱稱。|  
|**rowguid**|**uniqueidentifier**|給定資料列的資料列識別碼。|  
|**代數**|**Bigint**|**Tablenick**和**rowguid**所識別的資料列產生。|  
|**partchangegen**|**Bigint**|可能變更了資料列是否屬於篩選發行集的最後一項資料變更之相關聯層代 (Generation)。|  
|**衍生**|**Varbinary （501）**|用來維護這個資料列之變更記錄的訂閱者暱稱、版本號碼組。|  
|**colvl**|**Varbinary （7489）**|資料行版本資訊。|  
|**筆**|**uniqueidentifier**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**logical_record_parent_rowguid**|**uniqueidentifier**|識別邏輯記錄中每個對應子資料列在**MSmerge_contents** （藉由**rowguid**）中的最上層父資料列。|  
|**logical_record_lineage**|**Varbinary （501）**|用來維護邏輯記錄中最上層父資料列之變更記錄的訂閱者暱稱、版本號碼組。 邏輯記錄中所有子資料列的這個值都是 NULL。|  
|**logical_relation_change_gen**|**Bigint**|造成在邏輯記錄中重新對齊的最後一項變更之相關聯層代 (Generation) 值，現有的資料列會移入或移出邏輯記錄。|  
  
## <a name="see-also"></a>另請參閱  
 [複寫資料表 &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
