---
title: MSlogreader_agents （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSlogreader_agents_TSQL
- MSlogreader_agents
dev_langs:
- TSQL
helpviewer_keywords:
- MSlogreader_agents system table
ms.assetid: 8baa3c5a-cb40-42d0-b966-00e6d55368e8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 802d2075a0146febc4521fb17b65f236533596bf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "67907304"
---
# <a name="mslogreader_agents-transact-sql"></a>MSlogreader_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSlogreader_agents**資料表會針對在本機散發者上執行的每個記錄讀取器代理程式，各包含一個資料列。 這份資料表儲存在散發資料庫中。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**號**|**int**|記錄讀取器代理程式的識別碼。|  
|**name**|**Nvarchar （100）**|記錄讀取器代理程式的名稱。|  
|**publisher_id**|**smallint**|發行者的識別碼。|  
|**publisher_db**|**sysname**|發行者資料庫的名稱。|  
|**發行集**|**sysname**|發行集的名稱。|  
|**local_job**|**bit**|指出本機散發者是否有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業。|  
|**job_id**|**binary （16）**|作業識別碼。|  
|**profile_id**|**int**|[MSagent_profiles](../../relational-databases/system-tables/msagent-profiles-transact-sql.md)資料表中的設定識別碼。|  
|**publisher_security_mode**|**smallint**|連接到發行者時，代理程式所用的安全性模式，它可以是下列項目之一：<br /><br /> ****  =  0[!INCLUDE[msCoName](../../includes/msconame-md.md)]驗證[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。<br /><br /> ****  =  1[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 驗證。|  
|**publisher_login**|**sysname**|連接到發行者時所用的登入。|  
|**publisher_password**|**Nvarchar （524）**|連接到發行者時，所用之密碼的加密值。|  
|**job_step_uid**|**uniqueidentifier**|用來啟動代理程式之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業步驟的唯一識別碼。|  
|**job_login**|**sysname**||  
|**job_password**|**Nvarchar （524）**||  
  
## <a name="see-also"></a>另請參閱  
 [複寫資料表 &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
