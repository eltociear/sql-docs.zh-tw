---
title: 還原服務主要金鑰 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- service master key [SQL Server], importing
- service master key [SQL Server], restoring
ms.assetid: 14bdbbbe-d384-4692-b670-4243d2466fe1
author: jaszymas
ms.author: jaszymas
manager: craigg
ms.openlocfilehash: 21abdf4e5781f179c8168ff02aa611bd7dffd39f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "74957156"
---
# <a name="restore-the-service-master-key"></a>還原服務主要金鑰
  此主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] ，還原 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中的服務主要金鑰。  
  
> [!WARNING]  
>  需要還原服務主要金鑰的情況不太可能發生在您身上。 萬一真的碰到了，就應該非常小心地進行。 如需詳細資訊，請參閱 [Back Up the Service Master Key](service-master-key.md)。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [限制事項](#Restrictions)  
  
     [安全性](#Security)  
  
-   [若要使用 Transact-sql 還原服務主要金鑰](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Restrictions"></a> 限制事項  
  
-   當還原服務主要金鑰時， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會解密所有已利用目前的服務主要金鑰來加密的金鑰和秘密，然後利用從備份檔案載入的服務主要金鑰來加密它們。  
  
-   如果任何一項解密失敗，還原便會失敗。 您可以利用 FORCE 選項來省略錯誤，但這個選項會使所有無法解密的資料遺失。  
  
-   重新產生加密階層是一項需要大量資源的作業。 您應該將這項作業安排在低需求時進行。  
  
> [!CAUTION]  
>  服務主要金鑰是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 加密階層的根。 服務主要金鑰會直接或間接維護樹狀結構中之所有其他金鑰的安全。 如果在強制還原作業進行期間某相依金鑰無法解密，由該金鑰維護其安全的資料便會遺失。  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> 權限  
 需要伺服器的 CONTROL SERVER 權限。  
  
##  <a name="SSMSProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-restore-the-service-master-key"></a>若要還原服務主要金鑰  
  
1.  從實體備份媒體或本機檔案系統上的目錄，擷取已備份的服務主要金鑰副本。  
  
2.  在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。  
  
3.  在標準列上，按一下 **[新增查詢]** 。  
  
4.  複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。  
  
    ```  
    -- Restores the service master key from a backup file.  
    RESTORE SERVICE MASTER KEY   
        FROM FILE = 'c:\temp_backups\keys\service_master_key'   
        DECRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';  
    GO  
    ```  
  
    > [!NOTE]  
    >  金鑰的檔案路徑和金鑰的密碼 (如果有) 不同於上方指示。 請確定兩者都是您伺服器和金鑰設定專用的。  
  
  
