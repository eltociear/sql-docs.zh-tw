---
title: 管理 Oracle 資料表空間 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], managing tablespaces
- tablespaces [SQL Server replication]
ms.assetid: b8ea6c3b-01d6-4efc-bbfb-03b264530bbd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9a6bf22c7649646506b65628f556b52fead23375
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "63022291"
---
# <a name="manage-oracle-tablespaces"></a>管理 Oracle 資料表空間
  資料表空間是資料庫儲存體的單位，大致相當於中[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的檔案群組。 資料表空間允許在個別群組中儲存和管理資料庫物件。 如需詳細資訊，請參閱 Oracle 文件集。  
  
 將資料表設定為 Oracle 發行集的一部分，您可以在儲存複寫記錄資訊時選擇性地指定使用現有的 Oracle 資料表空間。 如果未指定，則複寫物件的資料表空間為與複寫管理使用者結構描述相關的預設資料表空間，該複寫管理使用者結構描述在設定「發行者」時設定。  
  
 **若要為發行項記錄資料表指定資料表空間**：  
  
-   在 **[發行項屬性]** 對話方塊中指定資料表空間。 如需有關存取這個對話方塊的詳細資訊，請參閱＜ [View and Modify Publication Properties](../publish/view-and-modify-publication-properties.md)＞。  
  
-   使用 [sp_changearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)。 若要使用 **sp_changearticle**，請指定下列項目：  
  
    -   參數**@publisher**的 Oracle 發行者名稱。  
  
    -   參數**@publication**的 Oracle 發行集名稱。  
  
    -   參數**@article**的發行項名稱。  
  
    -   參數**@property**的 ' 資料表空間 ' 值。  
  
    -   參數**@value**的資料表空間名稱。  
  
## <a name="see-also"></a>另請參閱  
 [設定 Oracle 發行者](configure-an-oracle-publisher.md)   
 [在 Oracle 發行者上建立的物件](objects-created-on-the-oracle-publisher.md)  
  
  
