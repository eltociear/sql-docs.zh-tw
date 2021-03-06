---
title: sp_help_log_shipping_primary_database （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_log_shipping_primary_database_TSQL
- sp_help_log_shipping_primary_database
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_log_shipping_primary_database
ms.assetid: e711b01c-ef29-4eb6-a016-0e647e337818
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9559a882da12c3e2a7a48a0aaa656a554633aa6f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "67937919"
---
# <a name="sp_help_log_shipping_primary_database-transact-sql"></a>sp_help_log_shipping_primary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  擷取主要資料庫設定。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_help_log_shipping_primary_database  
[ @database = ] 'database' OR  
[ @primary_id = ] 'primary_id'  
```  
  
## <a name="arguments"></a>引數  
`[ @database = ] 'database'`這是記錄傳送主資料庫的名稱。 *資料庫*是**sysname**，沒有預設值，而且不能是 Null。  
  
`[ @primary_id = ] 'primary_id'`記錄傳送設定之主資料庫的識別碼。 *primary_id*是**uniqueidentifier** ，不能是 Null。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|描述|  
|-----------------|-----------------|  
|**primary_id**|記錄傳送組態之主要資料庫的識別碼。|  
|**primary_database**|記錄傳送組態中之主要資料庫的名稱。|  
|**backup_directory**|用於儲存主要伺服器之交易記錄備份檔的目錄。|  
|**backup_share**|備份目錄的網路或 UNC 路徑。|  
|**backup_retention_period**|在刪除記錄備份檔之前，將它保留在備份目錄中的時間長度 (以分鐘為單位)。|  
|**backup_compression**|指出記錄傳送設定是否使用[備份壓縮](../../relational-databases/backup-restore/backup-compression-sql-server.md)。<br /><br /> **0** = 已停用。 永遠不會壓縮記錄備份。<br /><br /> **1** = 已啟用。 一定會壓縮記錄備份。<br /><br /> **2** = 使用 View 的設定，[或設定備份壓縮預設伺服器設定選項](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)。 這是預設值。<br /><br /> 只有 [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (或更新版本) 才支援備份壓縮。 在其他版本中，此值一定是 2。|  
|**backup_job_id**|與主要伺服器上之備份作業相關聯的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業識別碼。|  
|**monitor_server**|在記錄傳送組態中，用於做為監視伺服器之 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體的名稱。|  
|**monitor_server_security_mode**|用於連接到監視伺服器的安全性模式。<br /><br /> 1 = [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 驗證。<br /><br /> 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]驗證。|  
|**backup_threshold**|在產生警示之前，備份作業之間所能經歷的時間 (以分鐘為單位)。|  
|**threshold_alert**|當超出備份臨界值時，所產生的警示。|  
|**threshold_alert_enabled**|決定是否啟用備份臨界值警示。<br /><br /> **1** = 已啟用。<br /><br /> **0** = 已停用。|  
|**last_backup_file**|最近之交易記錄備份的絕對路徑。|  
|**last_backup_date**|最後一項記錄備份作業的日期和時間。|  
|**last_backup_date_utc**|在主要資料庫中，前一個交易記錄備份作業的日期和時間 (以國際標準時間 (UTC) 為單位)。|  
|**history_retention_period**|給定主要資料庫的記錄傳送記錄，在刪除之前所保留的時間 (以分鐘為單位)。|  
  
## <a name="remarks"></a>備註  
 **sp_help_log_shipping_primary_database**必須從主伺服器的**master**資料庫中執行。  
  
## <a name="permissions"></a>權限  
 只有**系統管理員（sysadmin** ）固定伺服器角色的成員，才能夠執行此程式。  
  
## <a name="examples"></a>範例  
 這個範例說明如何使用**sp_help_log_shipping_primary_database**來抓取資料庫[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]的主資料庫設定。  
  
```  
EXEC master.dbo.sp_help_log_shipping_primary_database @database=N'AdventureWorks2012';  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [關於記錄傳送 &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
