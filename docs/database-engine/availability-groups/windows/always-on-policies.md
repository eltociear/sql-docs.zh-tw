---
title: 針對可用性群組健康情況使用群組原則
description: 了解如何檢視 Always On 儀表板為提供可用性群組健全狀況相關資訊所使用的群組系統原則。
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 26bf8f71-c2b8-45ef-b3a3-372b96c9e6e3
author: rothja
ms.author: jroth
ms.openlocfilehash: 6a48450322a8552720a119ea325ed720669fe5a8
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "75245645"
---
# <a name="evaluate-health-of-the-always-on-availability-group-using-group-policies"></a>使用群組原則評估 Always On 可用性群組的健全狀況
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Always On 儀表板使用 Always On 可用性群組系統原則，來將可用性群組健全狀況的資訊提供給使用者。 它們對可用性群組操作問題的疑難排解非常有用。 這些原則可以擴充，並用來自訂 Always On 儀表板，或立即執行以報告所需的健康情況資訊。  
  
 有 14 個可用性群組的系統原則。 如需每個原則的詳細資訊，請參閱 [Always On 可用性群組 (SQL Server) 操作問題的 Always On 原則](always-on-policies-for-operational-issues-always-on-availability.md)。  
  
## <a name="view-or-evaluate-availability-groups-system-policies"></a>檢視或評估可用性群組的系統原則  
 若要在 SQL Server Management Studio (SSMS) 中檢視或執行可用性群組的系統原則，請執行以下作業：  
  
1.  在 [物件總管]  中，依序展開 [管理]  、[原則管理]  、[原則]  ，然後 [系統原則]  。  
  
2.  以滑鼠右鍵按一下其中一個原則，然後按一下 [評估]  。 如果您想要評估所選取的原則，那麼您已完成。 您可以在 [目標詳細資料]  方塊中按一下 [檢視]  ，以查看評估結果的詳細資料。  
  
3.  若要在 [選取頁面]  窗格中檢視所有可用性群組系統原則，按一下 [原則選取]  。  
  
## <a name="next-steps"></a>後續步驟  
 [Always On 健康情況模型第 2 部分：擴充健康情況模型](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/extending-the-alwayson-health-model.aspx) \(英文\)。   
  
  
