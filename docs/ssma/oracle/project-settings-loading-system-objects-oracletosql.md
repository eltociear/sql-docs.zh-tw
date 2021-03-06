---
title: 專案設定（載入系統物件）（OracleToSQL） |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9418cb34-d869-4d24-95b3-6cb9db949bb0
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: a5e8feb6c083c787d877cbc5491c533b8a35d740
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68266614"
---
# <a name="project-settingsloading-system-objects-oracletosql"></a>專案設定 (載入系統物件) (OracleToSQL)
[**專案設定**] 對話方塊的 [載入系統物件] 頁面，可讓您指定 SSMA 轉換和載入的目標[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Oracle 系統物件。  
  
[載入系統物件] 窗格可在 [**專案設定**] 和 [**預設專案設定**] 對話方塊中使用：  
  
-   若要指定所有 SSMA 專案的設定，請在 [**工具**] 功能表上，選取 [**預設專案設定**]，選取 [遷移專案類型]，在左窗格底部的 [遷移] [**目標版本**] 下拉 [一般] 下方，按一下 **[一般**]，然後按一下 [**載入系統物件**]。  
  
-   若要指定目前專案的設定，請在 [**工具**] 功能表上，選取 [**專案設定**]，按一下左窗格底部的 **[一般**]，然後按一下 [**載入系統物件**]。  
  
## <a name="default-settings"></a>預設值  
轉換系統物件會耗用系統資源，而且需要一些時間。 為了改善效能，SSMA 只會選取最常使用的系統物件，如下列清單所示：  
  
-   SYS.DATABASES.DBMS_OUTPUT  
  
-   SYS.DATABASES.DBMS_PIPE  
  
-   SYS.DATABASES.DBMS_UTILITY  
  
-   SYS.DATABASES.常用  
  
-   SYS.DATABASES.UTL_FILE  
  
-   SYS.DATABASES.DBMS_LOB  
  
-   SYS.DATABASES.DBMS_SQL  
  
-   SYS.DATABASES.DBMS_SESSION  
  
如果您的 Oracle 物件參考其他系統物件，您應該選取這些物件。 如果您未選取 Oracle 資料庫物件所參考的系統物件，SSMA 會報告轉換錯誤。 如果您收到因遺漏系統物件所造成的轉換錯誤，請在此對話方塊中選取遺漏的物件。 然後您可以視需要重複轉換。  
  
