---
title: 專案設定（遷移）（SybaseToSQL） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 82f8857f-7ab1-4738-ab6e-b1e95ea94924
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: baa268431f9741e3dfe016476abdf051f8f54a09
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68028710"
---
# <a name="project-settings-migration-sybasetosql"></a>專案設定 (移轉) (SybaseToSQL)
[**專案設定**] 對話方塊的 [遷移] 頁面包含自訂 SSMA 如何將資料從 Sybase 自我調整伺服器企業（ASE） [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]遷移至的設定。  
  
[**專案設定**] 和 [**預設專案設定**] 對話方塊都有 [遷移] 窗格。  
  
-   若要指定所有 SSMA 專案的設定，請在 [**工具**] 功能表上，選取 [**預設專案設定**]，選取 [遷移專案類型]，在左窗格底部按一下 **[一般**]，從 [**遷移目標版本**] 下拉式選/changed，然後按一下 [**遷移**]。  
  
-   若要指定目前專案的設定，請在 [**工具**] 功能表上，選取 [**專案設定**]，按一下左窗格底部的 **[一般**]，然後按一下 [**遷移**]。  
  
## <a name="date-correction-options"></a>日期更正選項  
  
|詞彙|定義|  
|--------|--------------|  
|**取代不支援的日期**|指定 SSMA 是否應更正早于最早[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]日期**時間**的日期（1753年1月）。<br /><br />若要保留目前的日期值，請選取 [**不執行任何動作**]。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]將不會在日期時間資料行中接受01年 1753 1 月1日之前的日期。 如果您使用較舊的日期，您必須將日期時間值轉換成字元值。<br /><br />若要將在1753年1月01之前的日期轉換成 Null，請選取 [**以 Null 取代**]<br /><br />若要以支援的日期取代1753年1月之前的日期，請選取 [**取代為最接近的支援日期**]。<br /><br />**預設模式**：不執行任何動作<br /><br />**開放式模式**：不執行任何動作<br /><br />**完整模式**：取代為最接近的支援日期|  
  
## <a name="migration-engine"></a>遷移引擎  
  
|詞彙|定義|  
|--------|--------------|  
|**遷移引擎**|指定資料移轉期間所使用的資料庫引擎。 用戶端資料移轉指的是 SSMA 用戶端從來源抓取資料，並將該資料大量插入 SQL Server。 伺服器端資料移轉指的是在 SQL Server box 上執行的 SSMA 資料移轉引擎（大量複製程式），作為 SQL 代理程式作業，從來源抓取資料並直接插入 SQL Server，因此可避免額外的用戶端躍點（較佳的效能）。<br /><br />**預設模式**：用戶端資料移轉引擎<br /><br />**開放式模式**：用戶端資料移轉引擎<br /><br />**完整模式**：用戶端資料移轉引擎|  
  
> [!IMPORTANT]  
> 當 [**遷移引擎**] 選項設定為 [**伺服器端資料移轉引擎**] 時，會顯示新的專案設定選項 [**使用32位伺服器端資料移轉引擎**]。 它會指定是否使用32位或64位大量複製程式（BCP）公用程式來遷移資料。  
  
## <a name="miscellaneous-options"></a>其他選項  
  
|詞彙|定義|  
|--------|--------------|  
|**批次大小**|指定資料移轉期間使用的批次大小。<br /><br />**預設模式**：10000<br /><br />**開放式模式**：10000<br /><br />**完整模式**：10000|  
|**檢查條件約束**|指定當 SSMA 將資料插入 SQL Server 資料表時，是否應檢查條件約束。<br /><br />**預設模式**： False<br /><br />**開放式模式**： False<br /><br />**完整模式**： False|  
|**資料移轉超時**|指定資料移轉期間使用的超時時間<br /><br />**預設模式**：15<br /><br />**開放式模式**：15<br /><br />**完整模式**：15|  
|**擴充資料移轉選項**|在個別的 [詳細資料] 索引標籤中顯示每個資料表的額外資料移轉選項。<br /><br />**預設模式**：隱藏<br /><br />**開放式模式**：隱藏<br /><br />**完整模式**：隱藏|  
|**引發觸發程式**|指定 SSMA 是否應該在將資料加入 SQL Server 資料表時，引發插入觸發程式。<br /><br />**預設模式**： False<br /><br />**開放式模式**： False<br /><br />**完整模式**： False|  
|**保留身分識別**|指定 SSMA 將資料新增至 SQL Server 時，是否保留 Sybase 識別值。 值為 False 會導致目的地指派識別值。<br /><br />**預設模式**： True<br /><br />**開放式模式**： True<br /><br />**完整模式**： True|  
|**保留 null**|指定 SSMA 將資料新增至 SQL Server 時，是否在來源資料中保留 null 值，而不論 SQL Server 中指定的預設值為何。<br /><br />**預設模式**： True<br /><br />**開放式模式**： True<br /><br />**完整模式**： True|  
|**發生錯誤時**|發生錯誤時停止資料移轉。 它有三個選項：<br /><br />**停止遷移：** 停止資料移轉作業<br /><br />**繼續進行下一個資料表：** 停止對目前資料表的資料移轉，並繼續進行下一個工作<br /><br />**繼續進行下一個批次：** 停止對目前批次的資料移轉，並繼續進行下一個<br /><br />**預設模式**：繼續進行下一個批次<br /><br />**開放式模式**：繼續進行下一個批次<br /><br />**完整模式**：繼續進行下一個批次|  
|**數位的四捨五入小數部分**|指定在遷移至整數類型期間，是否要修剪十進位和數值資料的小數部分，如果小數部分不是簡單的則顯示錯誤訊息<br /><br />**預設模式**：否<br /><br />**開放式模式**：否<br /><br />**完整模式**：否|  
|**Sybase Unicode 位元組序**|指定 Sybase Unicode 字串的 endian 類型。 您可以針對此特定設定來設定下列選項：<br /><br />位元組由大到小<br /><br />位元組由大到小<br /><br />**預設模式**：小位元組序<br /><br />**開放式模式**：小位元組序<br /><br />**完整模式**：位元組由大到小|  
|**表鎖**|指定 SSMA 是否會在資料移轉期間將資料加入資料表時，鎖定資料表。 取得大量複製作業期間的大量更新鎖定。 如果值為 False，就會在資料列層級設定鎖定。<br /><br />**預設模式**： True<br /><br />**開放式模式**： True<br /><br />**完整模式**： True|  
|**使用資料指標**|如果已設定此選項，則會使用資料指標從源資料庫中取出資料。<br /><br />**預設模式**： False<br /><br />**開放式模式**： False<br /><br />**完整模式**： False|  
  
## <a name="parallel-data-migration"></a>平行資料移轉  
  
|詞彙|定義|  
|--------|--------------|  
|**平行資料移轉模式**|指定用來分叉執行緒以啟用平行資料移轉的模式。 在 Auto 模式中，SSMA 會選擇分叉的執行緒數目（預設為10），以遷移資料。 在自訂模式中，使用者可以指定分叉到遷移資料的執行緒數目（最小值為1，最大值為100）。 目前，只有用戶端資料移轉引擎支援平行資料移轉。<br /><br />**預設模式**：自動<br /><br />**開放式模式**：自動<br /><br />**完整模式**：自動|  
  
> [!IMPORTANT]  
> 當 [**平行資料移轉模式]** 選項設定為 [**自訂**] 時，會顯示新的專案設定選項 [**執行緒計數**]。 它會指定用於資料移轉的執行緒數目。  
  
