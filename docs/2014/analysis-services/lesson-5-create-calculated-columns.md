---
title: 第6課：建立計算結果欄 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d126766a-5699-4e9f-8213-8c7eea0fc14e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 58ba761f3e32f13ddcf81dc9875057195298c705
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "66078554"
---
# <a name="lesson-6-create-calculated-columns"></a>第 6 課：建立導出資料行
  在這一課，您將在模型中新增導出資料行來建立新資料。 導出資料行是以已存在模型中的資料為基礎。 如需詳細資訊，請參閱[導出資料行 &#40;SSAS 表格式&#41;](tabular-models/ssas-calculated-columns.md)。  
  
 您將在三個不同資料表中建立五個新的導出資料行。 每個工作的步驟稍有不同。 這是為了說明有幾種方式可以建立新的資料行、重新命名，以及將它們放在資料表中的不同位置。  
  
 這堂課的預估完成時間：**15 分鐘**  
  
## <a name="prerequisites"></a>Prerequisites  
 本主題是表格式模型教學課程的一部分，請依序完成。 在執行本課中的工作之前，您應已完成上一課：[第 5 課：建立關聯性](lesson-4-create-relationships.md)。  
  
## <a name="create-calculated-columns"></a>建立導出資料行  
  
#### <a name="create-a-month-calendar-calculated-column-in-the-date-table"></a>在日期資料表中建立 Month Calendar 導出資料行  
  
1.  在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中，按一下 [模型]**** 功能表，然後指向 [模型檢視]****，再按一下 [資料檢視]****。  
  
     只有在資料檢視中使用模型設計師，才能建立計算結果欄。  
  
2.  在模型設計師中，按一下 [Date]**** 資料表 (索引標籤)。  
  
3.  以滑鼠右鍵按一下 [**日曆季**] 資料行，然後按一下 [**插入資料行**]。  
  
     名為**CalculatedColumn1**的新資料行會插入 [**日曆季**] 資料行的左側。  
  
4.  在資料表上方的公式列中，輸入下列公式。 「自動完成」會協助您輸入資料行和資料表的完整名稱，並列出可用的函式。  
  
     `=RIGHT(" " & FORMAT([Month],"#0"), 2) & " - " & [Month Name]`  
  
     完成建立公式時，按 ENTER。  
  
     接著，計算結果欄的所有資料列就會填入值。 如果您在資料表中向下捲動，根據每個資料列中的資料，您會看到各資料列在此資料行中會有不同的值。  
  
    > [!NOTE]  
    >  如果您收到錯誤，請確認公式中的資料行名稱與您在[第 3 課：重新命名資料行](rename-columns.md)中變更的資料行名稱相符。  
  
5.  將此資料行`Month Calendar`重新命名為。  
  
 Month Calendar 導出資料行會提供可排序的月份名稱。  
  
#### <a name="create-a-day-of-week-calculated-column-in-the-date-table"></a>在日期資料表中建立 Day of Week 導出資料行  
  
1.  在 [日期]**** 資料表仍為使用中狀態時，按一下 [資料行]**** 功能表，然後按一下 [加入資料行]****。  
  
     新的資料行就會加入資料表的最右側。  
  
2.  在公式列中，輸入下列公式︰  
  
     `=RIGHT(" " & FORMAT([Day Number Of Week],"#0"), 2) & " - " & [Day Name]`  
  
     完成建立公式時，按 ENTER。  
  
3.  將資料行重新`Day of Week`命名為。  
  
4.  按一下欄位標題，然後將資料行拖曳到 [Day Name]**** 資料行和 [Day of Month]**** 資料行之間。  
  
    > [!TIP]  
    >  移動資料表中的資料行可讓您更輕鬆地瀏覽。  
  
 [Day of Week] 導出資料行會提供可排序的星期日期名稱。  
  
#### <a name="create-a-product-subcategory-name-calculated-column-in-the-product-table"></a>在產品資料表中建立 Product Subcategory Name 導出資料行  
  
1.  在模型設計師中，選取 [產品]**** 資料表。  
  
2.  捲動到資料表的最右側。 請注意，最右邊的資料行名為 **[新增資料行]** \(斜體)，請按一下資料行標題。  
  
3.  在公式列中，輸入下列公式。  
  
     `=RELATED('Product Subcategory'[Product Subcategory Name])`  
  
     完成建立公式時，按 ENTER。  
  
4.  將資料行重新`Product Subcategory Name`命名為。  
  
 [Product Subcategory Name] 導出資料行可用來在 [產品] 資料表中建立階層，其中包括來自 [產品子類別目錄] 資料表中 [Product Subcategory Name] 資料行的資料。 階層不可跨越多個資料表。 您稍後將在第 7 課中建立階層。  
  
#### <a name="create-a-product-category-name-calculated-column-in-the-product-table"></a>在產品資料表中建立 Product Category Name 導出資料行  
  
1.  在 [產品]**** 資料表仍為使用中狀態時，按一下 [資料行]**** 功能表，然後按一下 [加入資料行]****。  
  
2.  在公式列中，輸入下列公式︰  
  
     `=RELATED('Product Category'[Product Category Name])`  
  
     完成建立公式時，按 ENTER。  
  
3.  將資料行重新`Product Category Name`命名為。  
  
 [Product Category Name] 導出資料行可用來在 [產品] 資料表中建立階層，其中包括來自 [產品類別目錄] 資料表中 [Product Category Name] 資料行的資料。 階層不可跨越多個資料表。  
  
#### <a name="create-a-margin-calculated-column-in-the-internet-sales-table"></a>在網際網路銷售資料表中建立 Margin 導出資料行  
  
1.  在模型設計師中，選取 [網際網路銷售]**** 資料表。  
  
2.  加入新資料行。  
  
3.  在公式列中，輸入下列公式︰  
  
     `=[Sales Amount]-[Total Product Cost]`  
  
     完成建立公式時，按 ENTER。  
  
4.  將資料行重新`Margin`命名為。  
  
5.  將這個資料行拖曳至 [Sales Amount]**** 資料行和 [Tax Amt]**** 資料行之間。  
  
 [Margin] 導出資料行可用來分析每個 (產品) 資料列的利率。  
  
## <a name="next-step"></a>後續步驟  
 若要繼續進行這一課，請前往下一課：[第 7 課：建立量值](lesson-6-create-measures.md)。  
  
  
