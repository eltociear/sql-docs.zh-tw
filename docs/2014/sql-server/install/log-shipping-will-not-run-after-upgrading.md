---
title: 升級之後，將不會執行記錄傳送 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server]
ms.assetid: 6727cb7d-ac01-4972-a730-dbb7cdc29705
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 952a47eaa2028819908ef7e93326c31a289a0cc2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "66093977"
---
# <a name="log-shipping-will-not-run-after-upgrading"></a>升級之後，不會執行記錄傳送
  Upgrade Advisor 偵測到您正在使用記錄傳送。 
  [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 記錄傳送與 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中的記錄傳送不相容，也不能直接升級。 請在升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 之後，使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或預存程序重新設定記錄傳送。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Agent 記錄傳送作業類別目錄會導致升級失敗](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md)   
 [升級會將 SQL Server Agent 的使用者 Proxy 帳戶變更為暫時的 UpgradedProxyAccount](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)   
 [資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新的&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
