---
title: 關聯性暫存資料表
ms.custom: ''
ms.date: 04/01/2016
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- relationships staging table [Master Data Services]
- database [Master Data Services], relationships table
ms.assetid: e19b6002-67bd-4e7d-9f19-ecb455522b1a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: dff1ab73713aed3bfb635c0399028f0c9a1a8c86
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "73727904"
---
# <a name="relationship-staging-table-master-data-services"></a>關聯性暫存資料表 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  使用 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫中的關聯性暫存資料表 (stg.name_Relationship) 來依據成員之間的必要關聯性變更成員在明確階層中的位置。  
  
##  <a name="TableColumns"></a>資料表資料行  
 下表說明關聯性暫存資料表中各欄位的用途。  
  
|資料行名稱|描述|值|  
|-----------------|-----------------|-----------|  
|**ID**|自動指派的識別碼。|請勿在此欄位中輸入值。 如果尚未處理批次，這個欄位是空白。|  
|**RelationshipType**|必要<br /><br /> 所設定的關聯性類型。|可能的值為：<br /><br /> **1**:P 不用<br /><br /> **2**：同輩（位於相同層級）|  
|**ImportStatus_ID**|必要<br /><br /> 匯入程序的狀態。|可能的值為：<br /><br /> **0**，您指定以表示記錄已準備好進行預備。<br /><br /> **1**：自動指派，表示記錄的暫存進程已成功。<br /><br /> **2**：自動指派，表示記錄的暫存進程已失敗。|  
|**Batch_ID**|只有 Web 服務需要<br /><br /> 自動指派的識別碼，可用來將暫存的記錄分組。<br /><br /> 如果尚未處理批次，這個欄位是空白。|批次中的所有成員都會被指派這個識別碼，這個識別碼會顯示在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 使用者介面的 **[識別碼]** 欄中。|  
|**BatchTag**|必要項，只有 Web 服務不需要<br /><br /> 批次的唯一名稱 (最多 50 個字元)。||  
|**HierarchyName**|必要<br /><br /> 明確階層名稱。 每一個合併成員只能屬於一個階層。||  
|**ParentCode**|必要<br /><br /> 若是父子式關聯性，即為分葉子成員或合併子成員之父系的合併成員代碼。<br /><br /> 若是同層級關聯性，即為其中一個同層級的代碼。||  
|**ChildCode**|必要<br /><br /> 若是父子式關聯性，即為子系的合併成員或分葉成員代碼。<br /><br /> 若是同層級關聯性，即為其中一個同層級的代碼。||  
|**排序次序**|選用<br /><br /> 一個整數，代表此成員相對於父系底下其他成員的順序。 每個子成員都應該有一個唯一識別碼。||  
|**錯誤碼**|顯示錯誤碼。 若要查詢 **ImportStatus_ID** 為 **2**的所有記錄，請參閱 [暫存處理序錯誤 &#40;Master Data Services&#41;](../master-data-services/staging-process-errors-master-data-services.md)。||  
  
## <a name="see-also"></a>另請參閱  
 [總覽：從資料表匯入資料 &#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)   
 [查看預備 &#40;Master Data Services 時所發生的錯誤&#41;](../master-data-services/view-errors-that-occur-during-staging-master-data-services.md)   
 [暫存進程錯誤 &#40;Master Data Services&#41;](../master-data-services/staging-process-errors-master-data-services.md)  
  
  
