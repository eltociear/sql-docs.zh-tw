---
title: 處理採礦結構 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], processing
ms.assetid: 4162f33e-c23f-4293-8905-271781e45fa4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 92793adcf2fd04b1dac0c26933c1d5969a31f1a5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "66083094"
---
# <a name="process-a-mining-structure"></a>處理採礦結構
  在您可以瀏覽或使用與採礦結構相關聯的採礦模型之前，必須部署 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案並處理採礦結構和採礦模型。 此外，如果您變更採礦結構或採礦模型，會提示您重新部署和處理它們。 在 **中之資料採礦設計師的** [採礦結構] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 索引標籤中處理結構時，會處理所有相關聯的模型。  
  
 您可以使用下列工具來處理採礦結構：  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   XMLA：處理命令  
  
 如需如何處理個別模型的資訊，請參閱 [處理採礦模型](process-a-mining-model.md)。  
  
### <a name="to-process-a-mining-structure-and-all-associated-mining-models-using-sql-server-data-tools"></a>若要使用 SQL Server 資料工具來處理採礦結構和所有相關聯的採礦模型  
  
1.  從 **中的** [採礦模型] **功能表項目選取** [處理採礦結構和所有模型] [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]。  
  
     如果您變更了結構，在處理模型之前，會提示您重新部署結構。 按一下 [是]  。  
  
2.  按一下 [**處理採礦結構- \<結構>** ] 對話方塊中的 [**執行**]。  
  
     隨即開啟 **[處理進度]** 對話方塊，以顯示模型處理的詳細資料。  
  
3.  在模型完成處理之後，按一下 **[處理進度]** 對話方塊中的 **[關閉]** 。  
  
4.  在 [**處理採礦結構- \<結構>** ] 對話方塊中，按一下 [**關閉**]。  
  
## <a name="see-also"></a>另請參閱  
 [採礦結構工作和使用說明](mining-structure-tasks-and-how-tos.md)  
  
  
