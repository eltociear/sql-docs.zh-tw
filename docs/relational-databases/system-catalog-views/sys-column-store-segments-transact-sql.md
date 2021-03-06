---
title: sys.databases column_store_segments （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 01/15/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- column_store_segments
- sys.column_store_segments_TSQL
- sys.column_store_segments
- column_store_segments_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_store_segments catalog view
ms.assetid: 1253448c-2ec9-4900-ae9f-461d6b51b2ea
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b8d476e2f21693254eac5fc4712d53ac854e74ff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68139996"
---
# <a name="syscolumn_store_segments-transact-sql"></a>sys.column_store_segments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

針對資料行存放區索引中的每個資料行區段，各傳回一個資料列。 每個資料列群組都有一個資料行區段。 例如，具有10個數據列群組和34資料行的資料表會傳回340個數據列。 
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**partition_id**|**Bigint**|指出資料分割識別碼。 在資料庫中，這是唯一的。|  
|**hobt_id**|**Bigint**|具有此資料行存放區索引之資料表的堆積或 B 型樹狀目錄索引 (hobt) 的識別碼。|  
|**column_id**|**int**|資料行存放區資料行的識別碼。|  
|**segment_id**|**int**|資料列群組的識別碼。 為了回溯相容性，即使這是資料列群組識別碼，仍會繼續呼叫資料行名稱 segment_id。 您可以使用\<hobt_id、partition_id、column_id> <segment_id> 來唯一識別區段。|  
|**版本**|**int**|資料行區段格式的版本。|  
|**encoding_type**|**int**|用於該區段的編碼類型：<br /><br /> 1 = VALUE_BASED-不含字典的非字串/二進位（與一些內部變數非常類似4）<br /><br /> 2 = VALUE_HASH_BASED-字典中具有通用值的非字串/二進位資料行<br /><br /> 3 = 具有字典中通用值的 STRING_HASH_BASED 字串/二進位資料行<br /><br /> 4 = STORE_BY_VALUE_BASED-不含字典的非字串/二進位<br /><br /> 5 = 不含字典的 STRING_STORE_BY_VALUE_BASED 字串/二進位檔<br /><br /> 所有編碼會盡可能利用位封裝和執行長度編碼。|  
|**row_count**|**int**|資料列群組中的列數。|  
|**has_nulls**|**int**|如果資料行區段具有 Null 值，則為 1。|  
|**base_id**|**Bigint**|如果正在使用編碼類型1，則為基底值識別碼。  如果未使用編碼類型1，base_id 會設定為-1。|  
|**magnitude**|**float**|如果正在使用編碼類型1，則為大小。  如果未使用編碼類型1，則會將量值設定為-1。|  
|**primary_dictionary_id**|**int**|值為0表示全域字典。 值為-1 表示沒有為此資料行建立全域字典。|  
|**secondary_dictionary_id**|**int**|非零值指向目前區段中這個資料行的本機字典（也就是資料列群組）。 值為-1 表示沒有此區段的本機字典。|  
|**min_data_id**|**Bigint**|資料行區段中的最小資料識別碼。|  
|**max_data_id**|**Bigint**|資料行區段中的最大資料識別碼。|  
|**null_value**|**Bigint**|用來表示 Null 的值。|  
|**on_disk_size**|**Bigint**|區段大小 (以位元組為單位)。|  
  
## <a name="remarks"></a>備註  
 下列查詢會傳回資料行存放區索引之區段的相關資訊。  
  
```sql  
SELECT i.name, p.object_id, p.index_id, i.type_desc,   
    COUNT(*) AS number_of_segments  
FROM sys.column_store_segments AS s   
INNER JOIN sys.partitions AS p   
    ON s.hobt_id = p.hobt_id   
INNER JOIN sys.indexes AS i   
    ON p.object_id = i.object_id  
WHERE i.type = 5 OR i.type = 6  
GROUP BY i.name, p.object_id, p.index_id, i.type_desc ;  
GO  
```  
  
## <a name="permissions"></a>權限  
 所有資料行都至少需要資料表的**VIEW DEFINITION**許可權。 除非使用者也具有**SELECT**許可權，否則下列資料行會傳回 null： has_nulls、base_id、量值、min_data_id、max_data_id 和 null_value。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的物件目錄檢視](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [查詢 SQL Server 系統目錄常見問題](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.databases &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [all_columns &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [computed_columns &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [資料行存放區索引指南](~/relational-databases/indexes/columnstore-indexes-overview.md)    
 [column_store_dictionaries &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)  
  
  

