---
title: 資料移轉設定（MySQLToSQL） |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9c396df4-5676-4f32-9c57-70d4f15f9b7a
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: c2c903ef29ab1a103bc9aa4f7b061e83ee7f2a95
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "67896376"
---
# <a name="data-migration-settings-mysqltosql"></a>資料移轉設定 (MySQLToSQL)
  
## <a name="data-migration-settings"></a>資料移轉設定  
**資料移轉設定**可讓使用者撰寫自訂查詢來進行資料移轉。  
  
-   當 [**擴充資料移轉選項**] 設定為 [**顯示**]，並且在 [專案設定] 中的設定為 [**隱藏**] 時，就可以使用此索引標籤。 如需專案遷移設定的詳細資訊，請參閱[專案設定（遷移）](https://msdn.microsoft.com/2a3cba9e-cd54-4a8b-b858-8fc4cf2580d9) 。  
  
-   自訂 SQL 語句的剖析將會在資料表節點的 [**資料移轉設定**] 索引標籤中執行。  
  
-   以下是 [**資料移轉設定**] 視覺效果中可用的兩個核取方塊：  
  
    1.  截斷 SQL Server 資料表  
  
    2.  使用自訂選取  
  
1.  **截斷 SQL Server 資料表：**  
     此選項可讓使用者清楚瞭解目標資料庫上的已遷移資料。  
  
    -   根據預設，會核取此文字方塊。  
  
    -   如果未選取此文字方塊，則會將所遷移的資料加入至目標資料庫的現有資料。  
  
2.  **使用自訂選取：**  
     此選項可讓使用者修改存在的**select**語句（**select**語句可讓使用者選取要在目標資料庫上顯示的資料）。  
  
    1.  根據預設，不會選取此文字方塊。  
  
    2.  如果已核取此文字方塊，則會允許使用者修改現有的**select**語句。  
  
有兩個按鈕出現視覺效果。：  
  
-   **適用：** 按一下 **[** 套用] 以套用已變更的設定。  
  
-   **取消：** 按一下 [**取消**]，以在進行變更之前還原存在的設定。  
  
## <a name="see-also"></a>另請參閱  
[將 MySQL 資料移轉至 SQL Server/SQL Azure](https://msdn.microsoft.com/a6a7f4d6-68aa-4a38-93bf-53eba0d7dc82)  
  
