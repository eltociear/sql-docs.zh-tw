---
title: MSSQL_ENG014144 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014144 error
ms.assetid: fdc744d5-530e-48c4-9420-cca032fd482b
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: c43395fffe934756bb69e0d094a3e6637adcedad
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76286498"
---
# <a name="mssql_eng014144"></a>MSSQL_ENG014144
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>訊息詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|14144|  
|事件來源|MSSQLSERVER|  
|元件|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|符號名稱||  
|訊息文字|無法卸除訂閱者 '%s'。 發行集資料庫 '%s' 中有其訂閱。|  
  
## <a name="explanation"></a>說明  
 如果存在為執行個體設定的使用中訂閱，則設定為「訂閱者」的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體將無法從「訂閱者」角色中移除。  
  
## <a name="user-action"></a>使用者動作  
 在嘗試變更 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的「訂閱者」狀態之前，請先卸除所有相關聯的訂閱。  
  
1.  在「發行者」端的發行集資料庫中執行 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md) 以尋找訂閱。  
  
2.  在發行集資料庫中執行 [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md) 以卸除訂閱。  

## <a name="see-also"></a>另請參閱  
 [錯誤和事件參考 &#40;複寫&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [訂閱發行集](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
