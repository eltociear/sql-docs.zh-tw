---
title: MSMQ 連線管理員編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msmqconnectionmanager.f1
helpviewer_keywords:
- MSMQ Connection Manager Editor
ms.assetid: ef842cb4-82da-4550-85fe-9bedbc1e77c7
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 91b448a87408a830464b50f641e6eefa8cf3f12c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "66057636"
---
# <a name="msmq-connection-manager-editor"></a>MSMQ 連線管理員編輯器
  使用 [MSMQ 連線管理員]**** 對話方塊，來指定 Message Queuing (又稱為 MSMQ) 訊息佇列的路徑。  
  
 若要深入了解 MSMQ 連線管理員，請參閱＜ [MSMQ Connection Manager](connection-manager/msmq-connection-manager.md)＞。  
  
> [!NOTE]  
>  MSMQ 連線管理員支援本機的共用和私用佇列，以及遠端的公用佇列。 但不支援遠端私用佇列。 如需使用指令碼工作的解決方案，請參閱＜ [Sending to a Remote Private Message Queue with the Script Task](control-flow/script-task.md)＞。  
  
## <a name="options"></a>選項。  
 **名稱**  
 提供唯一的名稱給工作流程中的 MSMQ 連線管理員。 提供的名稱將顯示在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師內。  
  
 **說明**  
 描述連接管理員。 最佳作法是以其用途描述連接管理員，使封裝可以自我記錄並易於維護。  
  
 **Path**  
 輸入訊息佇列的完整路徑。 路徑的格式取決於佇列的類型。  
  
|佇列類型|範例路徑|  
|----------------|-----------------|  
|公開|
  \<電腦名稱>\\<佇列名稱\>|  
|Private|
  \<電腦名稱>\Private$\\<佇列名稱\>|  
  
 您可以使用 "." 代表本機電腦。  
  
 **測驗**  
 在設定 MSMQ 連線管理員之後，請按一下 [測試]**** 來確認連接已可使用。  
  
## <a name="see-also"></a>另請參閱  
 [Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
