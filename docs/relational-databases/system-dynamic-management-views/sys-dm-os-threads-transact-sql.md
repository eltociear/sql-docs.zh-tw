---
title: sys.databases dm_os_threads （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_threads_TSQL
- sys.dm_os_threads
- dm_os_threads
- sys.dm_os_threads_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_threads dynamic management view
ms.assetid: a5052701-edbf-4209-a7cb-afc9e65c41c1
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ef8eeeaaf59934d6c3307641b6c93f110ab5738f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "73982535"
---
# <a name="sysdm_os_threads-transact-sql"></a>sys.dm_os_threads (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  傳回在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序之下執行的所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 作業系統執行緒的清單。  
  
> [!NOTE]  
>  若要從[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]或[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]呼叫此，請使用**dm_pdw_nodes_os_threads**的名稱。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|thread_address|**varbinary(8)**|執行緒的記憶體位址 (主索引鍵)。|  
|started_by_sqlservr|**bit**|指出執行緒起始端。<br /><br /> 1 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已啟動執行緒。<br /><br /> 0 = 另一個元件已啟動執行緒，例如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 內的擴充預存程序。|  
|os_thread_id|**int**|作業系統指派的執行緒識別碼。|  
|status|**int**|內部狀態旗標。|  
|instruction_address|**varbinary(8)**|目前執行的指示位址。|  
|creation_time|**datetime**|建立這個執行緒的時間。|  
|kernel_time|**Bigint**|這個執行緒使用的核心時間量。|  
|usermode_time|**Bigint**|這個執行緒使用的使用者時間量。|  
|stack_base_address|**varbinary(8)**|這個執行緒之最高堆疊位址的記憶體位址。|  
|stack_end_address|**varbinary(8)**|這個執行緒之最低堆疊位址的記憶體位址。|  
|stack_bytes_committed|**int**|堆疊中已認可的位元組數。|  
|stack_bytes_used|**int**|執行緒目前使用的位元組數。|  
|affinity|**Bigint**|這個執行緒正在執行的 CPU 遮罩。 這取決於**ALTER SERVER CONFIGURATION SET 進程親和性**語句所設定的值。 若是軟相似性，可能與排程器不同。|  
|優先順序|**int**|這個執行緒的優先權值。|  
|Locale|**int**|執行緒的快取地區設定 LCID。|  
|token|**varbinary(8)**|執行緒的快取模擬 Token 控制代碼。|  
|is_impersonating|**int**|指出這個執行緒是否使用 Win32 模擬。<br /><br /> 1 = 執行緒使用不同於處理序預設值的安全性認證。 這指出執行緒模擬的實體不是建立處理序的實體。|  
|is_waiting_on_loader_lock|**int**|執行緒是否在等待載入程式鎖定的作業系統狀態。|  
|fiber_data|**varbinary(8)**|在執行緒上執行的目前 Win32 Fiber。 這只適用於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 設定為輕量型共用的情況。|  
|thread_handle|**varbinary(8)**|僅供內部使用。|  
|event_handle|**varbinary(8)**|僅供內部使用。|  
|scheduler_address|**varbinary(8)**|與這個執行緒相關聯之排程器的記憶體位址。 如需詳細資訊，請參閱[dm_os_schedulers &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md)。|  
|worker_address|**varbinary(8)**|繫結這個執行緒之工作者的記憶體位址。 如需詳細資訊，請參閱[dm_os_workers &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)。|  
|fiber_context_address|**varbinary(8)**|內部 Fiber 內容位址。 這只適用於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 設定為輕量型共用的情況。|  
|self_address|**varbinary(8)**|內部一致性指標。|  
|processor_group|**smallint**|**適用對象**：[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 及更新版本。<br /><br /> 處理器群組識別碼。|  
|pdw_node_id|**int**|**適用**于： [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 此散發所在節點的識別碼。|  
  
## <a name="permissions"></a>權限

在[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]上， `VIEW SERVER STATE`需要許可權。   
在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]高階層級上， `VIEW DATABASE STATE`需要資料庫的許可權。 在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] [標準] 和 [基本] 層上，需要**伺服器管理員**或**Azure Active Directory 系統管理員**帳戶。   

## <a name="notes-on-linux-version"></a>Linux 版本的注意事項

由於 SQL 引擎在 Linux 中的運作方式，部分資訊與 Linux 診斷資料並不相符。 例如`os_thread_id` ，不符合類似`ps` `top`或 procfs （/proc/`pid`）等工具的結果。  這是因為平臺抽象層（SQLPAL），是 SQL Server 元件與作業系統之間的一層。

## <a name="examples"></a>範例  
 在啟動時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會啟動執行緒，然後使工作者與這些執行緒產生關聯。 不過，外部元件 (例如擴充預存程序) 可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序之下啟動執行緒。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 並沒有這些執行緒的控制權。 dm_os_threads 可以提供在[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]進程中取用資源之惡意執行緒的相關資訊。  
  
 下列查詢可用來尋找正在執行不是由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 啟動之執行緒的工作者，以及執行使用的時間。  
  
> [!NOTE]
>  為求精簡，下列查詢在 `*` 陳述式中使用星號 (`SELECT`)。 您應該避免使用星號 (*)，特別是針對目錄檢視、動態管理檢視以及系統資料表值函式。 未來的[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]升級和版本可能會新增資料行，並將資料行順序變更為這些 views 和函數。 這些變更可能會中斷應用程式所預期的特定順序和資料行數目。  
  
```  
SELECT *  
  FROM sys.dm_os_threads  
  WHERE started_by_sqlservr = 0;  
```  
  
## <a name="see-also"></a>另請參閱  
  [dm_os_workers &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)   
 [SQL Server 作業系統相關的動態管理 Views &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


