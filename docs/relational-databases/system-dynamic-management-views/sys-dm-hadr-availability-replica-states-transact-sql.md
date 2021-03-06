---
title: sys.databases dm_hadr_availability_replica_states （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 10/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_hadr_availability_replica_states
- sys.dm_hadr_availability_replica_states_TSQL
- sys.dm_hadr_availability_replica_states
- dm_hadr_availability_replica_states_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_hadr_availability_replica_states dynamic management view
ms.assetid: d2e678bb-51e8-4a61-b223-5c0b8d08b8b1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 05964e0557cb08e874424af542b8fc8a57ce0835
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "67900632"
---
# <a name="sysdm_hadr_availability_replica_states-transact-sql"></a>sys.dm_hadr_availability_replica_states (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  傳回每個本機複本的資料列，並針對同一個 Always On 群組中當做本機複本的每一個遠端複本，各傳回一個資料列。 每一個資料列都包含有關給定複本狀態的資訊。  
  
> [!IMPORTANT]  
>  若要取得給定可用性群組中每個複本的相關資訊，請在裝載主要複本的伺服器實例上**dm_hadr_availability_replica_states 查詢 sys.databases** 。 在裝載可用性群組之次要複本的伺服器執行個體上查詢時，這個動態管理檢視只會傳回此可用性群組的本機資訊。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**replica_id**|**uniqueidentifier**|複本的唯一識別碼。|  
|**group_id**|**uniqueidentifier**|可用性群組的唯一識別碼。|  
|**is_local**|**bit**|複本是否為本機，下列其中一個：<br /><br /> 0 = 表示可用性群組中的遠端次要複本，該群組的主要複本是由本機伺服器執行個體所裝載。 這個值只會出現在主要複本位置。<br /><br /> 1 = 表示本機複本。 在次要複本上，這是該複本所屬之可用性群組的唯一可用值。|  
|**角色**|**tinyint**|本機[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]複本或已連接遠端複本的目前角色，下列其中一個：<br /><br /> 0 = 正在解析<br /><br /> 1 = 主要<br /><br /> 2 = 次要<br /><br /> 如需 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 角色的詳細資訊，請參閱 [Always On 可用性群組概觀 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)。|  
|**role_desc**|**Nvarchar （60）**|**角色**的描述，下列其中一個：<br /><br /> RESOLVING<br /><br /> PRIMARY<br /><br /> SECONDARY|  
|**operational_state**|**tinyint**|複本的目前操作狀態，下列其中一個：<br /><br /> 0 = 暫止容錯移轉<br /><br /> 1 = 暫止<br /><br /> 2 = 線上<br /><br /> 3 = 離線<br /><br /> 4 = 失敗<br /><br /> 5 = 失敗，無仲裁<br /><br /> NULL = 複本不是本機。<br /><br /> 如需詳細資訊，請參閱本主題稍後的[角色和操作狀態](#RolesAndOperationalStates)。|  
|**操作\_狀態\_desc**|**Nvarchar （60）**|**操作\_狀態**的描述，下列其中一個：<br /><br /> PENDING_FAILOVER<br /><br /> PENDING<br /><br /> ONLINE<br /><br /> OFFLINE<br /><br /> FAILED<br /><br /> FAILED_NO_QUORUM<br /><br /> NULL|  
|**復原\_健全狀況**|**tinyint**|[Dm_hadr_database_replica_states](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md)動態管理檢視的**資料庫狀態資料\_** 行匯總。 以下是可能的值及其描述。<br /><br /> 0：進行中。  至少有一個聯結的資料庫具有 [線上] 以外的資料庫狀態（[**資料庫\_狀態**] 不是0）。<br /><br /> 1：線上。 所有聯結的資料庫都有線上的資料庫狀態（**database_state**是0）。<br /><br /> Null： **is_local** = 0|  
|**recovery_health_desc**|**Nvarchar （60）**|**Recovery_health**的描述，下列其中一個：<br /><br /> ONLINE_IN_PROGRESS<br /><br /> ONLINE<br /><br /> NULL|  
|**同步\_處理健全狀況**|**tinyint**|反映所有聯結的可用性資料庫（也稱為*複本*）和複本的可用性模式（同步認可或非同步認可模式）之資料庫同步處理狀態（**synchronization_state**）的匯總套件。 匯總會反映複本上資料庫的最低累計狀態。 以下是可能的值及其描述。<br /><br /> 0：狀況不良。   至少有一個聯結資料庫處於 NOT SYNCHRONIZING 狀態下。<br /><br /> 1：部分狀況良好。 某些複本未處於目標同步處理狀態：同步認可複本應該已同步處理，而非同步認可複本應該正在同步處理。<br /><br /> 2：狀況良好。 所有複本都處於目標同步處理狀態：同步認可複本已同步處理，而非同步認可複本正在同步處理。|  
|**synchronization_health_desc**|**Nvarchar （60）**|**Synchronization_health**的描述，下列其中一個：<br /><br /> NOT_HEALTHY<br /><br /> PARTIALLY_HEALTHY<br /><br /> HEALTHY|  
|**connected_state**|**tinyint**|次要複本目前是否已連接到主要複本。 可能的值如下所示，以及其描述。<br /><br /> 0：已中斷連線。 可用性複本對 DISCONNECTED 狀態的回應取決於其角色：在主要複本上，如果次要複本已中斷連接，主要複本上的次要資料庫會標示為 [未同步處理]，這會等待次要複本地在次要複本上，一旦偵測到它已中斷連接，次要複本就會嘗試重新連接到主要複本。<br /><br /> 1：已連接。<br /><br /> 每個主要複本都會針對相同可用性群組中的每一個次要複本來追蹤連接狀態。 次要複本只會追蹤主要複本的連接狀態。|  
|**connected_state_desc**|**Nvarchar （60）**|**Connection_state**的描述，下列其中一個：<br /><br /> DISCONNECTED<br /><br /> CONNECTED|  
|**last_connect_error_number**|**int**|上次連接錯誤的號碼。|  
|**last_connect_error_description**|**nvarchar(1024)**|**Last_connect_error_number**訊息的文字。|  
|**last_connect_error_timestamp**|**datetime**|指出何時發生**last_connect_error_number**錯誤的日期和時間時間戳記。|  
  
##  <a name="RolesAndOperationalStates"></a>角色和操作狀態  
 角色、**角色**會反映給定可用性複本的狀態，而作業狀態（ **operational_state**）則描述複本是否準備好處理可用性複本的所有資料庫的用戶端要求。 以下是每個角色可能的操作狀態摘要： [解析]、[主要] 和 [次要]。  
  
 **解析：** 當可用性複本在解析角色中時，可能的操作狀態如下表所示。  
  
|作業狀態|描述|  
|-----------------------|-----------------|  
|PENDING_FAILOVER|正在針對可用性群組處理容錯移轉命令。|  
|OFFLINE|可用性複本的所有組態資料都已經在 WSFC 叢集和本機中繼資料中更新，但是可用性群組目前缺少主要複本。|  
|FAILED|嘗試從 WSFC 叢集中擷取資訊時發生讀取失敗。|  
|FAILED_NO_QUORUM|本機 WSFC 節點沒有仲裁。 這是推斷的狀態。|  
  
 **主要：** 當可用性複本正在執行主要角色時，它目前是主要複本。 可能的操作狀態如下表所示。  
  
|作業狀態|描述|  
|-----------------------|-----------------|  
|PENDING|這是暫時性狀態，但是如果沒有工作者可處理要求，則主要複本可能會陷在這個狀態中。|  
|ONLINE|可用性群組資源在線上，而且所有資料庫工作者執行緒都已收取。|  
|FAILED|可用性複本無法從 WSFC 叢集讀取及/或將資料寫入其中。|  
  
 **次要：** 當可用性複本正在執行次要角色時，它目前是次要複本。 可能的操作狀態如下表所示。  
  
|作業狀態|描述|  
|-----------------------|-----------------|  
|ONLINE|本機次要複本已連接到主要複本。|  
|FAILED|本機次要複本無法從 WSFC 叢集讀取及/或將資料寫入其中。|  
|NULL|在主要複本上，當資料列與次要複本有關時就會傳回這個值。|  
  
## <a name="security"></a>安全性  
  
### <a name="permissions"></a>權限  
 需要伺服器的 VIEW SERVER STATE 權限。  
  
## <a name="see-also"></a>另請參閱  
 [AlwaysOn 可用性群組概觀 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [監視可用性群組 &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)  
  
  
