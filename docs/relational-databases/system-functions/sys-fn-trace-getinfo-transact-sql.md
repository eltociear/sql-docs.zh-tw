---
title: sys.databases fn_trace_getinfo （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_trace_getinfo
- fn_trace_getinfo_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- traces [SQL Server], status information
- status information [SQL Server], traces
- sys.fn_trace_getinfo function
- fn_trace_getinfo function
ms.assetid: 04b140fe-110a-47b8-98b5-e4c161beb6c9
author: rothja
ms.author: jroth
ms.openlocfilehash: 041f651fb34c486cebc589f119f3e5f220314dd2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68059228"
---
# <a name="sysfn_trace_getinfo-transact-sql"></a>sys.fn_trace_getinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  傳回所指定追蹤或所有現有追蹤的資訊。  
  
> **重大!** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 請改用擴充事件。    
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sys.fn_trace_getinfo ( { trace_id | NULL | 0 | DEFAULT } )  
```  
  
## <a name="arguments"></a>引數  
 *trace_id*  
 這是追蹤的識別碼。 *trace_id*為**int**。 有效的輸入是追蹤的識別碼、Null、0或 DEFAULT。 NULL、0 和 DEFAULT 是這個內容中的對等值。 請指定 NULL、0 或 DEFAULT 以傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中所有追蹤的資訊。  
  
## <a name="tables-returned"></a>傳回的資料表  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|traceid|**int**|追蹤的識別碼。|  
|屬性|**int**|追蹤的屬性：<br /><br /> 1= 追蹤選項。 如需詳細資訊， @options請參閱[sp_trace_create &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)中的。<br /><br /> 2 = 檔案名稱<br /><br /> 3 = 大小上限<br /><br /> 4 = 停止時間<br /><br /> 5 = 目前追蹤狀態。 0 = 已停止。 1 = 執行中。|  
|value|**sql_variant**|指定追蹤屬性的相關資訊。|  
  
## <a name="remarks"></a>備註  
 在傳遞特定追蹤的識別碼之後，fn_trace_getinfo 會傳回該追蹤的相關資訊。 當傳遞無效的識別碼時，這個函數會傳回空的資料列集。  
  
 fn_trace_getinfo 會對其結果集所包含的任何追蹤檔案名稱附加 .trc 副檔名。 如需定義追蹤的詳細資訊，請參閱[sp_trace_create &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)。 如需追蹤篩選器的類似資訊，請參閱[fn_trace_getfilterinfo &#40;transact-sql&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)。  
  
 如需使用追蹤預存程式的完整範例，請參閱[&#40;transact-sql&#41;建立追蹤](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)。  
  
## <a name="permissions"></a>權限  
 需要伺服器的 ALTER TRACE 權限。  
  
## <a name="examples"></a>範例  
 下列範例會傳回所有使用中追蹤的相關資訊。  
  
```  
SELECT * FROM sys.fn_trace_getinfo(0) ;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [建立追蹤 &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)   
 [sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)   
 [sp_trace_generateevent &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [fn_trace_geteventinfo &#40;Transact-sql&#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)   
 [fn_trace_gettable &#40;Transact-sql&#41;](../../relational-databases/system-functions/sys-fn-trace-gettable-transact-sql.md)  
  
  
