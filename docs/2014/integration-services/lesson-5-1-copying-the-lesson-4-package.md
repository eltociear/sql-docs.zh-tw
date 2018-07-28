---
title: 步驟 1：複製第 4 課套件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8aa7d690-4649-4c0a-ac6f-9504637ee426
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 653782ef61866adfa1a495deca49b563f12ca110
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37176145"
---
# <a name="step-1-copying-the-lesson-4-package"></a>步驟 1：複製第 4 課的套件
  在這項工作中，您將為第 4 課所建立的 Lesson 4.dtsx 套件建立複本。 另外，您也可以將此教學課程中隨附之已完成的第 4 課套件加入至專案中，然後改為複製該套件。 在第 5 課其餘的課程中，您將使用這個新的副本。  
  
### <a name="to-copy-the-lesson-4-package"></a>複製第 4 課的套件  
  
1.  如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools 尚未開啟，請按一下 [開始]，並依序指向 [所有程式] 和 [Microsoft SQL Server 2012]，然後按一下 [SQL Server Data Tools]。  
  
2.  在 [檔案] 功能表上，依序按一下 [開啟] 和 [專案/方案]、選取 [SSIS 教學課程]、按一下 [開啟]，再按兩下 SSIS Tutorial.sln。  
  
3.  在方案總管中，以滑鼠右鍵按一下 **Lesson 4.dtsx**，然後按一下 [複製]。  
  
4.  在方案總管中，以滑鼠右鍵按一下 [SSIS 套件]，然後按一下 [貼上]。  
  
     依預設，所複製的套件稱為 Lesson 5.dtsx。  
  
5.  在方案總管中，按兩下 **Lesson 5.dtsx** 來開啟套件。  
  
6.  以滑鼠右鍵按一下 [控制流程] 索引標籤背景的任何位置，然後按一下 [屬性]。  
  
7.  在 [屬性] 視窗中，更新`Name`屬性設`Lesson 5`。  
  
8.  按一下方塊**識別碼**屬性，然後按一下下拉箭頭，，，然後按一下**\<產生新的識別碼 >**。  
  
### <a name="to-add-the-completed-lesson-4-package"></a>新增已完成的第 4 課套件  
  
1.  開啟 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools 及 SSIS 教學課程專案。  
  
2.  在方案總管中，以滑鼠右鍵按一下 [SSIS 套件]，然後按一下 [新增現有的套件]。  
  
3.  在 [新增現有套件的副本] 對話方塊的 [套件位置] 中，選取 [檔案系統]。  
  
4.  按一下瀏覽 (**…**) 按鈕、導覽至電腦上的 **Lesson 4.dtsx**，然後按一下 [開啟]。  
  
     若要下載此教學課程的所有課程封裝，請執行下列動作。  
  
    1.  導覽至 [Integration Services 產品範例](http://go.microsoft.com/fwlink/?LinkId=275027)  
  
    2.  按一下 **[下載]** 索引標籤。  
  
    3.  按一下 SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 檔案。  
  
5.  複製並貼上第 4 課套件，如上一個程序的步驟 3-8 所述。  
  
## <a name="next-task-in-lesson"></a>本課程的下一項工作  
 [步驟 2：啟用和設定套件設定](lesson-5-2-enabling-and-configuring-package-configurations.md)  
  
  