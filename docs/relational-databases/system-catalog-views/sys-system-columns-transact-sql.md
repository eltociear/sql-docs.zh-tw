---
title: sys.databases system_columns （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- system_columns_TSQL
- system_columns
- sys.system_columns
- sys.system_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.system_columns catalog view
ms.assetid: 4ab1d48a-d57a-4e76-a08c-9627eeaf4588
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cdb28d10d04c21f0d377777b41c332eb20d1ee9c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "73981910"
---
# <a name="syssystem_columns-transact-sql"></a>sys.system_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  針對有資料行的每個系統物件資料行，各包含一個資料列。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|這個資料行所屬的物件識別碼。|  
|**name**|**sysname**|資料行的名稱。 在物件中，這是唯一的。|  
|**column_id**|**int**|資料行的識別碼。 在物件中，這是唯一的。<br /><br /> 資料行識別碼不一定會循序排列。|  
|**system_type_id**|**tinyint**|資料行的系統類型識別碼|  
|**user_type_id**|**int**|使用者所定義的資料行類型識別碼。<br /><br /> 若要傳回類型的名稱，請在此資料行上加入[sys.databases](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)目錄檢視。|  
|**max_length**|**smallint**|資料行的長度上限 (以位元組為單位)。<br /><br /> -1 = 資料行資料類型是**Varchar （max）**、 **Nvarchar （max）**、 **Varbinary （max）** 或**xml**。<br /><br /> 若為**文字**資料行， **max_length**值會是16，或**sp_tableoption** ' text in row ' 所設定的值。|  
|**有效位數**|**tinyint**|如果是以數值為基礎，便是資料行的有效位數；否則，便是 0。|  
|**尺度**|**tinyint**|如果是以數值為基礎，便是資料行的小數位數；否則，便是 0。|  
|**collation_name**|**sysname**|如果是以字元為基礎，便是資料行的定序名稱；否則，便是 NULL。|  
|**is_nullable**|**bit**|1 = 資料行可為 Null。|  
|**is_ansi_padded**|**bit**|1 = 如果是字元、二進位或變數，則資料行會使用 ANSI_PADDING ON 行為。<br /><br /> 0 = 資料行不是字元、二進位或變數。|  
|**is_rowguidcol**|**bit**|1 = 資料行是已宣告的 ROWGUIDCOL。|  
|**is_identity**|**bit**|1 = 資料行有識別值。|  
|**is_computed**|**bit**|1 = 資料行是一個計算資料行。|  
|**is_filestream**|**bit**|1 = 宣告資料行使用檔案資料流儲存體。|  
|**is_replicated**|**bit**|1 = 資料行已被複寫。|  
|**is_non_sql_subscribed**|**bit**|1 = 資料行有非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的訂閱者。|  
|**is_merge_published**|**bit**|1 = 資料行已經合併發行。|  
|**is_dts_replicated**|**bit**|1 = 資料行是利用 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 加以複寫。|  
|**is_xml_document**|**bit**|1 = 內容是完整的 XML 文件集。<br /><br /> 0 = 內容是檔片段，或者資料行資料類型不是**xml**。|  
|**xml_collection_id**|**int**|如果資料行資料類型是**xml** ，而且 xml 為類型，則為非零。 這個值是包含資料行的驗證 XML 結構描述命名空間之集合的識別碼。<br /><br /> 0 = 沒有 XML 結構描述集合。|  
|**default_object_id**|**int**|預設物件的識別碼，不論其是否為獨立的[sys.databases sp_bindefault](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md)，或是內嵌的資料行層級預設條件約束。 內嵌資料行層級預設物件的**parent_object_id**資料行，就是對資料表本身的參考。 如果沒有預設值，便是 0。|  
|**rule_object_id**|**int**|使用 sys.databases 系結至資料行之獨立規則的識別碼**sp_bindrule**。<br /><br /> 0 = 沒有獨立規則。<br /><br /> 如需資料行層級的檢查條件約束，請參閱[check_constraints &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md)。|  
|is_sparse|**bit**|1 = 資料行是疏鬆資料行。 如需詳細資訊，請參閱 [使用疏鬆資料行](../../relational-databases/tables/use-sparse-columns.md)。|  
|is_column_set|**bit**|1 = 資料行是資料行集。 如需詳細資訊，請參閱 [使用資料行集](../../relational-databases/tables/use-column-sets.md)。|  
|generated_always_type|**tinyint**|代表資料行類型的數值：<br /><br /> 0 = NOT_APPLICABLE<br /><br /> 1 = AS_ROW_START<br /><br /> 2 = AS_ROW_END|  
|generated_always_type_desc|**Nvarchar （60）**|資料行類型的文字描述：<br /><br /> NOT_APPLICABLE<br /><br /> AS_ROW_START<br /><br /> AS_ROW_END<br /><br /> **適用對象**：[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 及更新版本。|  
  
## <a name="permissions"></a>權限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的物件目錄檢視](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [查詢 SQL Server 系統目錄常見問題](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.databases &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [all_columns &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [computed_columns &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)  
  
  
