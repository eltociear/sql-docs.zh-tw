---
title: sys.databases dm_os_sys_memory （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_sys_memory
- sys.dm_os_sys_memory_TSQL
- sys.dm_os_sys_memory
- dm_os_sys_memory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_sys_memory dynamic management view
ms.assetid: 1ca58814-1caa-44c1-b307-ff0bdcbbef62
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4ca8b0f6e700e97c5cbc33964cc450ad54ea1a7e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "67899708"
---
# <a name="sysdm_os_sys_memory-transact-sql"></a>sys.dm_os_sys_memory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  從作業系統傳回記憶體資訊。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 受限於 (回應) 作業系統層級的外部記憶體條件以及基礎硬體的實體限制。 判斷整體系統狀態是評估 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記憶體使用量的重要部分。  
  
> [!NOTE]  
>  若要從[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]或[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]呼叫此，請使用**dm_pdw_nodes_os_sys_memory**的名稱。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**total_physical_memory_kb**|**Bigint**|可供作業系統使用之實體記憶體的大小總計 (以 KB 為單位)。|  
|**available_physical_memory_kb**|**Bigint**|可用實體記憶體的大小 (以 KB 為單位)。|  
|**total_page_file_kb**|**Bigint**|由作業系統回報之認可限制的大小 (以 KB 為單位)。|  
|**available_page_file_kb**|**Bigint**|未使用之分頁檔的總容量 (以 KB 為單位)。|  
|**system_cache_kb**|**Bigint**|系統快取記憶體的總容量 (以 KB 為單位)。|  
|**kernel_paged_pool_kb**|**Bigint**|分頁核心集區的總容量 (以 KB 為單位)。|  
|**kernel_nonpaged_pool_kb**|**Bigint**|未分頁核心集區的總容量 (以 KB 為單位)。|  
|**system_high_memory_signal_state**|**bit**|系統記憶體資源充足通知的狀態。 值為 1 表示 Windows 已經設定了記憶體充足的訊號。 如需詳細資訊，請參閱 MSDN library 中的[CreateMemoryResourceNotification](https://go.microsoft.com/fwlink/?LinkId=82427) 。|  
|**system_low_memory_signal_state**|**bit**|系統記憶體資源不足通知的狀態。 值為 1 表示 Windows 已經設定了記憶體不足的訊號。 如需詳細資訊，請參閱 MSDN library 中的[CreateMemoryResourceNotification](https://go.microsoft.com/fwlink/?LinkId=82427) 。|  
|**system_memory_state_desc**|**nvarchar(256)**|記憶體狀態的描述。 請參閱下表。|  
|**pdw_node_id**|**int**|**適用**于： [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 此散發所在節點的識別碼。|  
  
|條件|值|  
|---------------|-----------|  
|system_high_memory_signal_state = 1<br /><br /> 和<br /><br /> system_low_memory_signal_state = 0|可用的實體記憶體充足|  
|system_high_memory_signal_state = 0<br /><br /> 和<br /><br /> system_low_memory_signal_state = 1|可用的實體記憶體不足|  
|system_high_memory_signal_state = 0<br /><br /> 和<br /><br /> system_low_memory_signal_state = 0|實體記憶體使用量穩定|  
|system_high_memory_signal_state = 1<br /><br /> 和<br /><br /> system_low_memory_signal_state = 1|實體記憶體狀態正在轉換<br /><br /> 充足和不足的訊號不應該同時開啟。 不過，作業系統層級的快速變更可能會導致這兩個值看似對某個使用者模式應用程式同時開啟。 兩個訊號同時開啟的現象將解譯成轉換狀態。|  
  
## <a name="permissions"></a>權限  
 需要伺服器的 VIEW SERVER STATE 權限。  
  
## <a name="see-also"></a>另請參閱  
 [動態管理檢視與函數 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server 作業系統相關的動態管理 Views &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


