---
title: 設定參數值對話方塊 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ce9c2201-4e9a-4495-948f-b68deeaa7955
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5e5bfe3faf83b0873a8b47c348df9cfd8138dacb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "62771624"
---
# <a name="set-parameter-value-dialog-box"></a>設定參數值對話方塊
  使用 **[設定參數值]** 對話方塊來針對專案和封裝設定參數與連接管理員屬性的值。  
  
 **您想要做什麼事？**  
  
-   [開啟設定參數值對話方塊](#open_dialog)  
  
-   [設定選項](#option)  
  
##  <a name="open_dialog"></a> 開啟設定參數值對話方塊  
  
1.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，連接至 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器。  
  
     您正在連線到裝載 SSISDB 資料庫的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體。  
  
2.  在 [物件總管] 中，展開樹狀目錄以顯示 **[Integration Services 目錄]** 節點。  
  
3.  展開 **[SSISDB]** 節點。  
  
4.  以滑鼠右鍵按一下封裝或專案，再按一下 [設定]  ，然後按一下 [參數]  索引標籤或 [連線管理員]  索引標籤中的省略符號按鈕。  
  
##  <a name="option"></a> 設定選項  
 **參數**  
 列出參數名稱。  
  
 **型別**  
 列出參數值的資料類型。  
  
 **說明**  
 顯示參數的選擇性描述。  
  
 **編輯值**  
 選取此選項來編輯參數值。  
  
 **使用封裝中的預設值**  
 選取此選項可使用儲存在封裝中的預設參數值。  
  
 **使用環境變數**  
 選取此選項可使用儲存在環境中的變數值，該值是由專案或封裝所參考。 若要將環境參考加入至專案或封裝中，請使用 **[設定]** 對話方塊。 如需相關資訊，請參閱 [Configure Dialog Box](configure-dialog-box.md)。  
  
  
