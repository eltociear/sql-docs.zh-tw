---
title: 使用範本設定資源管理員 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, templates
ms.assetid: f342dec2-d1d6-483e-b44e-98eb7d168b5e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3da27154a824433d214dc495bf7f236ff104274f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68198935"
---
# <a name="configure-resource-governor-using-a-template"></a>使用範本來設定資源管理員
  您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]所提供的範本來設定資源管理員。  
  
-   **開始之前：**  [許可權](#Permissions)  
  
-   **若要建立工作負載群組，請使用：**  [範本](#ConfRGTemplate)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
 使用下列步驟即可開啟和修改建立資源集區與集區之工作負載群組的範本。 此外，這個範本可讓您建立使用者定義的分類函數，以便將新的連接路由傳送至預設群組或您所建立的工作負載群組。  
  
###  <a name="Permissions"></a> 權限  
 範本中的資源管理員 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式需要 CONTROL SERVER 權限。  
  
##  <a name="ConfRGTemplate"></a>使用範本設定 Resource Governor  
 **若要使用中的範本來設定資源管理員[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的 [檢視] **** 功能表上，按一下 [範本總管] ****。  
  
2.  在 [範本總管]**** 中，展開 [Resource Governor]****，然後按兩下 [設定 Resource Governor]****。  
  
3.  在 **[連接到 Database Engine]** 中，輸入必要資訊，然後按一下 **[確定]**。 此時，[查詢編輯器] 就會提供 Configure Resource Governor.sql 範本。 您可以使用此範本來建立並設定資源集區、工作負載群組和分類函數。  
  
4.  若要變更範本中的值，請按下 CTRL+SHIFT+M。 在 **[指定範本參數的值]** 視窗中，輸入您想要使用的值。  
  
5.  若要儲存您對範本所做的變更，請按一下 **[確定]**。  
  
6.  若要執行查詢，請按一下 **[執行]**。  
  
## <a name="see-also"></a>另請參閱  
 [Resource Governor](resource-governor.md)   
 [啟用 Resource Governor](enable-resource-governor.md)   
 [Resource Governor 資源集區](resource-governor-resource-pool.md)   
 [Resource Governor 工作負載群組](resource-governor-workload-group.md)   
 [Resource Governor 分類函數](resource-governor-classifier-function.md)   
 [View Resource Governor 屬性](view-resource-governor-properties.md)   
 [建立資源集區 &#40;Transact-sql&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql)   
 [建立工作負載群組 &#40;Transact-sql&#41;](/sql/t-sql/statements/create-workload-group-transact-sql)   
 [CREATE FUNCTION &#40;Transact-sql&#41;](/sql/t-sql/statements/create-function-transact-sql)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
