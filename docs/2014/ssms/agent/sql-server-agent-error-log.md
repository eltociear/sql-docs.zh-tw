---
title: SQL Server Agent 錯誤記錄檔 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- messages [SQL Server], SQL Server Agent
- errors [SQL Server], logs
- SQL Server Agent, errors
ms.assetid: 0b2d6e6e-cd2d-4b8b-9fa2-2bbd2fc0da41
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1dfa6926d86fce5006e458b3738a28a8b5f467d0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "63267384"
---
# <a name="sql-server-agent-error-log"></a>SQL Server Agent 錯誤記錄檔
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Agent 預設會建立記錄警告和錯誤的錯誤記錄檔。 記錄檔中會顯示下列警告和錯誤：  
  
-   提供有關潛在問題的警告訊息，例如「作業 \<*作業名稱*> 已於執行時刪除」。  
  
-   通常需要系統管理員介入的錯誤訊息，例如「無法啟動郵件工作階段」。 錯誤訊息可以藉由 **net send**來傳送給特定的使用者或電腦。  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 至多可以維護九個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 錯誤記錄檔。 每個已封存之記錄檔的副檔名都會指出記錄檔的相對存在時間。 例如，.1 的副檔名表示它是最近新封存的錯誤記錄檔，而 .9 的副檔名則表示是最早封存的錯誤記錄檔。  
  
 因為執行追蹤訊息會填滿 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 錯誤記錄檔，所以在預設情況下，並不會寫入錯誤記錄檔。 當錯誤記錄檔滿了，會降低您選取與分析更困難錯誤的能力。 因為記錄檔會增加伺服器的處理負擔，請務必仔細考慮將執行追蹤訊息擷取到錯誤記錄檔是否值得。 一般而言，最好只有在為一個特定問題進行偵錯時，您才擷取所有的訊息。  
  
 當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 停止時，您可以修改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 錯誤記錄檔的位置。 您無法開啟空的錯誤記錄檔。 您可以隨時循環使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 記錄檔，無須停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent。  
  
 **若要查看 SQL Server Agent 的錯誤記錄檔**  
  
-   [查看 SQL Server Agent 錯誤記錄檔 &#40;SQL Server Management Studio&#41;](view-sql-server-agent-error-log-sql-server-management-studio.md) 
  
 **若要重新命名 SQL Server Agent 錯誤記錄檔**  
  
-   [重新命名 SQL Server Agent 錯誤記錄檔 &#40;SQL Server Management Studio&#41;](rename-a-sql-server-agent-error-log-sql-server-management-studio.md)  
  
 **傳送 SQL Server Agent 錯誤訊息**  
  
-   [傳送 SQL Server Agent 錯誤訊息](send-sql-server-agent-error-messages.md)  
  
 **若要將執行追蹤訊息寫入 SQL Server Agent 錯誤記錄檔**  
  
-   [將執行追蹤訊息寫入 SQL Server Agent 錯誤記錄檔 &#40;SQL Server Management Studio&#41;](write-execution-trace-messages-to-sql-server-agent-log-ssms.md)  
  
  
