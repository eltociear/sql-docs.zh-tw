---
title: 資料列取樣轉換編輯器（取樣頁面） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.ROWSAMPLINGTRANSFORMATION.COLUMNS.F1
- sql12.dts.designer.rowsamplingtransformation.f1
helpviewer_keywords:
- Row Sampling Transformation Editor
ms.assetid: 544c7709-6de0-4c08-bda3-759985be9a05
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 30163b4d65ac6a732efb3f7c67a018f433a42ac0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "66056451"
---
# <a name="row-sampling-transformation-editor-sampling-page"></a>資料列取樣轉換編輯器 (取樣頁面)
  使用 **[資料列取樣轉換編輯器]** 對話方塊，即可將輸入的一部分分割為指定資料列數目的取樣。 這個轉換會將輸入分成兩個不同的輸出。  
  
 若要深入了解資料列取樣轉換，請參閱＜ [Row Sampling Transformation](data-flow/transformations/row-sampling-transformation.md)＞。  
  
## <a name="options"></a>選項。  
 **資料列數目**  
 指定輸入中的資料列數目作為取樣。  
  
 此屬性的值可以使用屬性運算式指定。  
  
 **取樣輸出名稱**  
 提供包含取樣資料列之輸出的唯一名稱。 提供的名稱將顯示在 SSIS 設計師內。  
  
 **未選取的輸出名稱**  
 提供輸出的唯一名稱，其中包含從取樣排除的資料列。 提供的名稱將顯示在 SSIS 設計師內。  
  
 **使用下列隨機種子**  
 指定轉換用來建立取樣之隨機號碼產生器的取樣種子。 只建議用於開發和測試。 如果未指定隨機種子，則轉換會使用 Microsoft Windows 滴答計數作為種子。  
  
## <a name="see-also"></a>另請參閱  
 [Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [百分比取樣轉換](data-flow/transformations/percentage-sampling-transformation.md)  
  
  
