---
title: 強制目標伺服器輪詢主要伺服器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- forcing master server polling
- polling master servers [SQL Server]
- master servers [SQL Server], polling
- target servers [SQL Server], polling the master server
ms.assetid: f1189a47-5ac3-45e2-9c5f-847810672279
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7e9580839c18ed40a6163ab933ce40276bc413ab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "63044053"
---
# <a name="force-a-target-server-to-poll-the-master-server"></a>強制目標伺服器輪詢主要伺服器
  此主題描述如何強制目標伺服器輪詢主要伺服器。 目標伺服器必須是主要伺服器上已註冊的伺服器。  
  
 作業是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 執行的一系列指定動作。 多重伺服器作業是一個主要伺服器執行於一或多個目標伺服器上的作業。 每一個目標伺服器可以同時執行相同作業的一個執行個體。 每個目標伺服器會定期輪詢主要伺服器、下載任何指派到目標伺服器的新作業之副本，然後中斷連接。 目標伺服器會先在本機執行作業，然後再重新連接到主要伺服器，以便上傳作業結果的狀態。  
  
> [!NOTE]  
>  如果當目標伺服器嘗試上傳作業狀態時無法存取主要伺服器，作業狀態會被多工緩衝處理，直到可以存取主要伺服器為止。  
  
-   **開始之前：**  [限制](#Restrictions)事項、[安全性](#Security)  
  
-   **若要強制目標伺服器輪詢主伺服器，請使用：**  [SQL Server Management Studio](#SSMS)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Restrictions"></a> 限制事項  
 目標伺服器必須是主要伺服器上已註冊的伺服器。 您必須從主要伺服器執行本主題中提供的指示。  
  
###  <a name="Security"></a> Security  
 如需詳細資訊，請參閱＜ [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) ＞和＜ [Choose the Right SQL Server Agent Service Account for Multiserver Environments](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)＞。  
  
##  <a name="SSMS"></a> 使用 SQL Server Management Studio  
 **強制目標伺服器輪詢主伺服器**  
  
1.  在 **[物件總管]** 中展開主要伺服器。  
  
2.  在 [SQL Server Agent]****，再指向 [多伺服器管理]****，然後按一下 [管理目標伺服器]****。  
  
3.  按一下目標伺服器，然後按一下 **[強制輪詢]**。  
  
  
