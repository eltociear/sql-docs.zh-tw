---
title: 專案設定（轉換）（MySQLToSQL） |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 7ad5fe44-6445-4ba8-a457-5af792631f11
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 7a8ad0b6c4c1e836a3eacca1f497d7ed229dbfc4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "67908874"
---
# <a name="project-settings-conversion-mysqltosql"></a>專案設定 (轉換) (MySQLToSQL)
[**專案設定**] 對話方塊的 [轉換] 頁面包含自訂 SSMA 如何將 MySQL 語法轉換成 SQL SERVER 或 SQL Azure 語法的設定。  
  
[轉換] 窗格可在 [**專案設定**] 和 [**預設專案設定**] 對話方塊中取得。  
  
-   使用 [**預設專案設定**] 對話方塊，即可設定所有專案的設定選項。 若要存取轉換設定，請在 [**工具**] 功能表上，選取 [**預設專案設定**]，從 [**遷移目標版本**] 下拉式/changed 選取 [需要查看設定] 的 [遷移專案類型]，按一下左窗格底部的 **[一般**]，然後選取 [**轉換**]。  
  
-   若要指定目前專案的設定，請在 [**工具**] 功能表上按一下 [**專案設定**]，然後按一下左窗格底部的 **[一般**]，再按一下 [**轉換**]。  
  
## <a name="options"></a>選項。  
  
### <a name="collate-clause"></a>Collate 子句  
  
|||  
|-|-|  
|**詞彙**|**[定義]**|  
|**明確的 COLLATE 子句轉換**|Explicit COLLATE 子句轉換選項指定如何在 MySQL 程式碼中轉換明確的 COLLATE 子句。 可能的選項： [略過] 和 [標示警告]/[產生錯誤]<br /><br />**預設模式**：忽略並以警告標記<br /><br />**開放式模式**：忽略並以警告標記<br /><br />**Full 模式**：忽略並以警告標記|  
  
### <a name="column-constraints"></a>資料行條件約束  
  
|||  
|-|-|  
|**詞彙**|**[定義]**|  
|**為列舉資料類型的資料行產生條件約束**|在 SQL Server 或 SQL Azure 資料表中，為列舉資料類型的資料行產生條件約束（如果它不存在於 MySQL 資料表中）。 如果是，列舉資料類型的所有已轉換資料行都會伴隨著控制值的 CHECK 條件約束。<br /><br />**預設模式**：否<br /><br />**開放式模式**：否<br /><br />**完整模式**：是|  
|**為 SET 資料類型的資料行產生條件約束**|在 SQL Server 或 SQL Azure 資料表中，針對 SET 資料類型的資料行產生條件約束（如果它不存在於 MySQL 資料表中）。 如果是，則 SET 資料類型的所有已轉換資料行都會伴隨著控制值的 CHECK 條件約束。<br /><br />**預設模式**：否<br /><br />**開放式模式**：否<br /><br />**完整模式**：是|  
|**針對不帶正負號的數值資料類型資料行產生條件約束**|將非負數值的檢查新增至不帶正負號數值資料類型的資料行。<br /><br />**預設模式**：否<br /><br />**開放式模式**：否<br /><br />**完整模式**：是|  
|**針對 YEAR 資料類型資料行產生條件約束**|在 SQL Server 或 SQL Azure 資料表中的 YEAR 資料類型資料行產生條件約束（如果它不存在於 MySQL 資料表中）。 如果是，YEAR 資料類型的所有已轉換資料行都會伴隨著控制值的 CHECK 條件約束。<br /><br />**預設模式**：否<br /><br />**開放式模式**：否<br /><br />**完整模式**：是|  
  
### <a name="data-types"></a>資料類型  
  
|||  
|-|-|  
|**詞彙**|**[定義]**|  
|**列舉資料類型轉換**|指定如何將 MySQL 列舉資料類型轉換成 NVARCHAR 或轉換成數值<br /><br />**預設模式**：轉換成 NVARCHAR<br /><br />**開放式模式**：轉換成 NVARCHAR<br /><br />**完整模式**：轉換成 NVARCHAR|  
|**設定資料類型轉換**|指定 MySQL SET 資料類型應如何轉換，轉換成 NVARCHAR （L）/Convert to BINARY （L）<br /><br />**預設模式**：轉換成 NVARCHAR （L）<br /><br />**開放式模式**：轉換成 NVARCHAR （L）<br /><br />**完整模式**：轉換成 NVARCHAR （L）|  
  
### <a name="generic"></a>泛型  
  
|||  
|-|-|  
|**詞彙**|**[定義]**|  
|**INSERT 和 REPLACE 中沒有預設值的資料行**|如果為 [是]，則所有參考使用 MyISAM 和 InnoDb 以外預存引擎之資料表的語句，都應該標記為警告轉換訊息。<br /><br />**預設模式**：加入至資料行清單<br /><br />**開放式模式**：加入至資料行清單<br /><br />**完整模式**：加入至資料行清單|  
|**除數為零的轉換產生**|指定是否要模擬 MySQL 而不 ERROR_FOR_DIVISION_BY_ZERO 行為。<br /><br />**預設模式**：錯誤<br /><br />**開放式模式**：錯誤<br /><br />**完整模式**： Null|  
|**IN 運算子**|指定如何在操作員中轉換 MySQL。<br /><br />**預設模式**：一律轉換成 IN<br /><br />**開放式模式**：一律轉換成 IN<br /><br />**完整模式**：視需要展開|  
|**MySQL 函數轉換**|指定如何轉換 MySQL 標準功能。<br /><br />**預設模式**：開放式<br /><br />**開放式模式**：開放式<br /><br />**完整模式**：精確|  
|**不支援的儲存引擎**|如果為 [是]，則所有參考使用 MyISAM 和 InnoDb 以外預存引擎之資料表的語句，都應該標記為警告轉換訊息。<br /><br />**預設模式**：否<br /><br />**開放式模式**：否<br /><br />**完整模式**：是|  
|**隱藏 ROWID 輔助資料行產生**|如果是，則禁止在目標資料表上建立 ROWD 輔助資料行。 可能會影響某些結構的遷移。<br /><br />**預設模式**：否<br /><br />**開放式模式**：否<br /><br />**完整模式**：否|  
|**截斷語句轉換**|指定如何轉換截斷語句。<br /><br />**預設模式**：截斷<br /><br />**開放式模式**：截斷<br /><br />**完整模式**：截斷|  
  
### <a name="misc"></a>其他  
  
|||  
|-|-|  
|**詞彙**|**[定義]**|  
|**預設架構對應**|指定如何將 MySQL 資料庫對應至 SQL Server 架構。<br /><br />**預設模式**：資料庫到資料庫<br /><br />**開放式模式**：資料庫到資料庫<br /><br />**完整模式**：資料庫到資料庫|  
  
### <a name="procedures-and-functions"></a>程序及函數  
  
|||  
|-|-|  
|**詞彙**|**[定義]**|  
|**預設函數轉換**|指定函數預設是否應該轉換成 T-sql 函數或預存程式。<br /><br />**預設模式**：轉換成函式<br /><br />**開放式模式**：轉換成函式<br /><br />**完整模式**：轉換成函式|  
|**產生 SET XACT_ABORT 于**|指定是否必須在轉換的程式或觸發程式的開頭加入 XACT_ABORT ON 設定。<br /><br />**預設模式**：是<br /><br />**開放式模式**：是<br /><br />**完整模式**：是|  
|**產生 SET NOCOUNT ON**|指定是否必須在轉換的程式或觸發程式的開頭加入 SET NOCOUNT ON。<br /><br />**預設模式**：是<br /><br />**開放式模式**：是<br /><br />**完整模式**：是|  
  
### <a name="spatial-data-types"></a>空間資料類型  
  
|||  
|-|-|  
|**詞彙**|**[定義]**|  
|**空間索引的預設周框方塊 {XMAX&#124;XMIN&#124;YMAX&#124;YMIN}**|為空間索引中使用的周框方塊，定義 {XMAX&#124;XMIN&#124;YMAX&#124;YMIN} 參數的預設值。<br /><br />**預設模式**<br /><br />XMAX：100<br /><br />XMIN：0<br /><br />YMAX：100<br /><br />YMIN：0<br /><br />**開放式模式**<br /><br />XMAX：100<br /><br />XMIN：0<br /><br />YMAX：100<br /><br />YMIN：0<br /><br />**完整模式**<br /><br />XMAX：100<br /><br />XMIN：0<br /><br />YMAX：100<br /><br />YMIN：0|  
|**空間索引的預設方格密度**|為空間索引中使用的格線密度定義 LEVEL_1、LEVEL_2、LEVEL_3 和 LEVEL_4 的預設值。<br /><br />**預設模式**<br /><br />LEVEL_1：預設值<br /><br />LEVEL_2：預設值<br /><br />LEVEL_3：預設值<br /><br />LEVEL_4：預設值<br /><br />**開放式模式**<br /><br />LEVEL_1：預設值<br /><br />LEVEL_2：預設值<br /><br />LEVEL_3：預設值<br /><br />LEVEL_4：預設值<br /><br />**完整模式**<br /><br />LEVEL_1：預設值<br /><br />LEVEL_2：預設值<br /><br />LEVEL_3：預設值<br /><br />LEVEL_4：預設值|  
  
### <a name="transactions"></a>交易  
  
|||  
|-|-|  
|**詞彙**|**[定義]**|  
|**非交易式資料表**|指定不支援交易之資料表的所有參考是否都應該標記為警告轉換訊息。<br /><br />**預設模式**：否<br /><br />**開放式模式**：否<br /><br />**完整模式**：是|  
|**交易隔離等級**|指定新交易應使用的交易隔離等級。<br /><br />**預設模式**：預設值<br /><br />**開放式模式**：預設值<br /><br />**完整模式**：可重複讀取|  
  
### <a name="value-control"></a>值控制項  
  
|||  
|-|-|  
|**詞彙**|**[定義]**|  
|**字元轉換為數值**|指定如何處理從字元資料類型到數值資料類型的隱含和明確轉換。<br /><br />**預設模式**：開放式<br /><br />**開放式模式**：開放式<br /><br />**完整模式**：精確|  
|**控制不帶正負號的數值**|控制將值指派給不帶正負號的數值變數和參數。<br /><br />**預設模式**：否<br /><br />**開放式模式**：否<br /><br />**完整模式**：是|  
|**控制不帶正負號的減法**|修改插入不帶正負號 datatype 之資料表資料行的負值。<br /><br />**預設模式**：轉換 ' as-is '<br /><br />**開放式模式**：轉換 ' as-is '<br /><br />**Full 模式**：具有警告的標記|  
|**Binary 資料類型的轉換**|指定如何處理二進位資料類型的隱含和明確轉換。<br /><br />**預設模式**：開放式<br /><br />**開放式模式**：開放式<br /><br />**完整模式**：精確|  
|**轉換成日期/時間資料類型**|指定如何處理隱含和明確轉換至日期/時間資料類型。<br /><br />**預設模式**：模擬 MySQL 格式<br /><br />**開放式模式**：使用 SQL Server 格式<br /><br />**完整模式**：模擬 MySQL 格式|  
|**精確度超過38的數值常值**|指定如何轉換有效位數超過38的數值常值。<br /><br />**預設模式**：盡可能四捨五入<br /><br />**開放式模式**：可能的話，舍入<br /><br />**完整模式**：盡可能四捨五入|  
|**零-不是 Null 的資料行**|指定如何處理指派，而不是零日期、零日期或無效日期/時間值的非 Null 資料行。<br /><br />**預設模式**： GETDATE （）<br /><br />**開放式模式**： GETDATE （）<br /><br />**Full 模式**： GETDATE （）|  
  
## <a name="see-also"></a>另請參閱  
[&#40;MySQLToSQL&#41;的使用者介面參考](../../ssma/mysql/user-interface-reference-mysqltosql.md)  
  
