---
title: SQL Server 的 Wait Statistics 物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Wait Statistics object
- SQLServer:Wait Statistics
ms.assetid: cb7f917d-4291-4115-9b78-ee7692ebbb2d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 28e7ee81273d47e285b9903575bdc40ccededbb5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "63151024"
---
# <a name="sql-server-wait-statistics-object"></a>SQL Server 的 Wait Statistics 物件
  **SQLServer:Wait Statistics** 效能物件包含效能計數器，可報告等候狀態的詳細資訊。  
  
 下表列出 Wait Statistics 物件包含的計數器。  
  
|SQL Server Wait Statistics 計數器|描述|  
|-----------------------------------------|-----------------|  
|**Lock waits**|正在等候鎖定的處理序統計資料。|  
|**Log buffer waits**|等候記錄緩衝區變為可用的處理序統計資料。|  
|**Log write waits**|等候寫入記錄緩衝區的處理序統計資料。|  
|**Memory grant queue waits**|等候記憶體授權變為可用的處理序統計資料。|  
|**Network IO waits**|有關等候網路 I/O 的統計資料。|  
|**Non-Page latch waits**|有關非頁面閂鎖的統計資料。|  
|**Page IO latch waits**|有關頁面 I/O 閂鎖的統計資料。|  
|**Page latch waits**|有關頁面閂鎖的統計資料，不包括 I/O 閂鎖。|  
|**Thread-safe memory objects waits**|等候安全執行緒記憶體配置器的處理序統計資料。|  
|**Transaction ownership waits**|有關同步存取交易的處理序統計資料。|  
|**Wait for the worker**|有關等候工作者變為可用的處理序統計資料。|  
|**Workspace synchronization waits**|有關同步存取工作空間的處理序統計資料。|  
  
 物件中的每個計數器均包含下列執行個體：  
  
|Item|描述|  
|----------|-----------------|  
|**Average wait time (ms)**|所選取等候類型的平均等候時間。|  
|**Cumulative wait time (ms) per second**|所選取等候類型的每秒彙總等候時間。|  
|**Waits in progress**|目前正在等候其下類型的處理序數目。|  
|**Waits started per second**|所選取等候類型的每秒開始等候數目。|  
  
## <a name="see-also"></a>另請參閱  
 [監視資源使用狀況 &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md)  
  
  
