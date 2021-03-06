---
title: 第9課：建立觀點 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 55b0f0d0-1cdf-4876-9c3d-d0c848be3f5d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bd395e605bfde9d34ed0dc4f16060812464efb56
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "66078246"
---
# <a name="lesson-9-create-perspectives"></a>第 9 課：建立檢視方塊
  在這一課，您將建立一個 [網際網路銷售] 檢視方塊。 檢視方塊會定義可檢視的模型子集，以提供聚焦、商務特有或應用程式特有的觀點。 使用者使用檢視方塊連接到模型時，只會將那些模型物件 (資料表、資料行、量值、階層和 KPI) 視為該檢視方塊中定義的欄位。  
  
 您在本課中所建立的網際網路銷售額檢視方塊將不包含 Customer 資料表物件。 當您建立從檢視中排除某些物件的檢視方塊時，該物件仍然存在於模型中；不過，不會顯示在報告用戶端欄位清單中。 計算結果欄和量值不管是否包含在檢視方塊中，仍然可以從排除的物件資料計算。  
  
 本課程的目的在於說明如何建立檢視方塊，以及熟悉表格式模型撰寫工具。 如果您之後展開此模型納入其他資料表，可以建立其他檢視方塊來定義不同的模型視點，例如存貨和銷售人員。  
  
 如需詳細資訊，請參閱[檢視方塊 &#40;SSAS 表格式&#41;](tabular-models/perspectives-ssas-tabular.md)。  
  
 這堂課的預估完成時間：**5 分鐘**  
  
## <a name="prerequisites"></a>Prerequisites  
 本主題是表格式模型教學課程的一部分，請依序完成。 在執行本課中的工作之前，您應已完成上一課：[第 8 課：建立關鍵效能指標](lesson-7-create-key-performance-indicators.md)。  
  
## <a name="create-perspectives"></a>建立檢視方塊  
  
#### <a name="to-create-an-internet-sales-perspective"></a>建立網際網路銷售檢視方塊  
  
1.  在模型設計師中，按一下 [**模型**] 功能表，然後按一下 [**透視圖**]。  
  
2.  在 [檢視方塊]**** 對話方塊中，按一下 [新增檢視方塊]****。  
  
3.  若要重新命名此觀點，請按兩下**新的 [觀點 1** ] 資料行標題`Internet Sales`，然後輸入。  
  
4.  在 [**欄位**] 中，選取下列資料表**日期**、**地理位置**、**產品**、**產品類別目錄**、 `Internet Sales`**產品子類別**目錄和。  
  
     請注意，您從此檢視方塊中排除了 Customer 資料表及其所有資料行。 稍後，您將在第 12 課中使用 [在 Excel 中進行分析] 功能測試此檢視方塊。 Excel 樞紐分析表欄位清單將包含 Customer 資料表之外的每個資料表。  
  
5.  驗證您所做的選擇，確定未核取 [Customer]**** 資料表，然後按一下 [確定]****  
  
## <a name="next-steps"></a>後續步驟  
 若要繼續進行本教學課程，請前往下一課：[第 10 課：建立階層](lesson-9-create-hierarchies.md)。  
  
  
