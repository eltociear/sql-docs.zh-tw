---
title: syspolicy_system_health_state （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syspolicy_system_health_state_TSQL
- syspolicy_system_health_state
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_system_health_state view
ms.assetid: 00815106-9fe4-481d-a9e1-a256101887f4
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 47701075fd3c650870f2ce81b021fe7c8910b26e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68110898"
---
# <a name="syspolicy_system_health_state-transact-sql"></a>syspolicy_system_health_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  針對每一個以原則為基礎的管理原則和目標查詢運算式組合各顯示一個資料列。 使用 syspolicy_system_health_state 檢視表可透過程式設計方式檢查伺服器的原則健全狀態。 下表描述 syspolicy_system_health_state 檢視表中的資料行。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|health_state_id|**Bigint**|原則健全狀態記錄的識別碼。|  
|policy_id|**int**|原則的識別碼。|  
|last_run_date|**datetime**|上次執行此原則的日期和時間。|  
|target_query_expression_with_id|**Nvarchar （400）**|目標運算式 (具有指派給識別變數的值)，可針對評估的原則定義目標。|  
|target_query_expression|**nvarchar(max)**|運算式，可針對評估的原則定義目標。|  
|結果|**bit**|這個目標與此原則有關的健全狀態：<br /><br /> 0 = 失敗<br /><br /> 1 = 成功|  
  
## <a name="remarks"></a>備註  
 syspolicy_system_health_state 檢視表會顯示每一個使用中 (已啟用) 原則之目標查詢運算式的最近健全狀態。 
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [物件總管] 和 [物件總管詳細資料] 頁面會從這個檢視表彙總原則健全狀態，以顯示關鍵健全狀態。  
  
## <a name="permissions"></a>權限  
 需要 msdb 資料庫中 PolicyAdministratorRole 角色的成員資格。  
  
## <a name="see-also"></a>另請參閱  
 [使用原則式管理來管理伺服器](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [以原則為基礎的管理檢視 &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
