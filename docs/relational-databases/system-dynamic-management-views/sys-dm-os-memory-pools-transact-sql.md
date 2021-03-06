---
title: sys.databases dm_os_memory_pools （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_pools_TSQL
- dm_os_memory_pools
- dm_os_memory_pools_TSQL
- sys.dm_os_memory_pools
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_pools dynamic management view
ms.assetid: 1ef053f3-c6f3-456e-82b6-26e4bd630d46
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dbd5ce36c9d83eb6347bcba71c26c3fd71c4513d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68265742"
---
# <a name="sysdm_os_memory_pools-transact-sql"></a>sys.dm_os_memory_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中的每一個物件存放區，各傳回一個資料列。 您可以利用這份檢視，來監視快取記憶體的使用情形，並且識別不當的快取行為。  
  
> [!NOTE]  
>  若要從[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]或[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]呼叫此，請使用**dm_pdw_nodes_os_memory_pools**的名稱。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**memory_pool_address**|**varbinary(8)**|代表記憶體集區之項目的記憶體位址。 不可為 Null。|  
|**pool_id**|**int**|一組集區中某個特定集區的識別碼。 不可為 Null。|  
|**type**|**Nvarchar （60）**|物件集區的類型。 不可為 Null。 如需詳細資訊，請參閱[dm_os_memory_clerks &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)。|  
|**name**|**nvarchar(256)**|這個記憶體物件之系統指派的名稱。 不可為 Null。|  
|**max_free_entries_count**|**Bigint**|集區最多所能容納的可用項目數。 不可為 Null。|  
|**free_entries_count**|**Bigint**|目前在集區中的可用項目數。 不可為 Null。|  
|**removed_in_all_rounds_count**|**Bigint**|自  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體啟動之後，從集區移除的項目數。 不可為 Null。|  
|**pdw_node_id**|**int**|**適用**于： [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 此散發所在節點的識別碼。|  
  
## <a name="permissions"></a>權限

在[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]上， `VIEW SERVER STATE`需要許可權。   
在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]高階層級上， `VIEW DATABASE STATE`需要資料庫的許可權。 在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] [標準] 和 [基本] 層上，需要**伺服器管理員**或**Azure Active Directory 系統管理員**帳戶。   

## <a name="remarks"></a>備註  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件有時會使用一個共用集區架構，來快取異質、非靜態類型的資料。 集區架構比快取架構更簡單。 集區中所有的項目都視為相同。 集區在內部相當於記憶體 Clerk，可以取代記憶體 Clerk 使用。  
  
## <a name="see-also"></a>另請參閱  
 
  [SQL Server 作業系統相關的動態管理 Views &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


