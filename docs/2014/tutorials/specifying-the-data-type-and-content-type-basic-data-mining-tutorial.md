---
title: 指定資料類型和內容類型（基本資料採礦教學課程） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 72484d27-3ef1-4f16-813c-2f43231fc2da
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 583a6fda2dbb4698405a3d69f33955531b3c1c10
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "62720052"
---
# <a name="specifying-the-data-type-and-content-type-basic-data-mining-tutorial"></a>指定資料類型和內容類型 (基本資料採礦教學課程)
  現在您已經選取用來建立結構及定型模型的資料行，請針對精靈所設定的預設資料類型和內容類型進行任何必要的變更。  
  
#### <a name="review-and-modify-content-type-and-data-type-for-each-column"></a>檢閱及修改每一個資料行的內容類型和資料類型  
  
1.  在 [**指定欄位的內容和資料類型**] 頁面上 **，按一下 [** 偵測] 來執行演算法，以決定每個資料行的預設資料和內容類型。  
  
2.  檢查 [**內容類型**] 和 [**資料類型**] 欄中的專案，並在必要時加以變更，以確定設定與下表所列的相同。  
  
     此精靈通常會偵測這些數字並指派適當的數值資料類型，但是在許多情況下，您可能想要將數字當做文字處理。 例如， **GeographyKey**應該當做文字來處理，因為它不適合在此識別碼上執行數學運算。  
  
    |資料行|內容類型|資料類型|  
    |------------|------------------|---------------|  
    |**位址 Line1**|**Discrete**|**文字**|  
    |**位址 Line2**|**Discrete**|**文字**|  
    |**存在**|**連續**|**Long**|  
    |**Bike Buyer**|**Discrete**|**Long**|  
    |**Commute Distance**|**Discrete**|**文字**|  
    |**CustomerKey**|**索引鍵**|**Long**|  
    |**DateLastPurchase**|**連續**|**日期**|  
    |**電子郵件地址**|**Discrete**|**文字**|  
    |**English Education**|**Discrete**|**文字**|  
    |**English Occupation**|**Discrete**|**文字**|  
    |**名字**|**Discrete**|**文字**|  
    |**性別**|**Discrete**|**文字**|  
    |**Geography Key**|**Discrete**|**文字**|  
    |**房屋擁有者旗標**|**Discrete**|**文字**|  
    |**姓氏**|**Discrete**|**文字**|  
    |**Marital Status**|**Discrete**|**文字**|  
    |**擁有的 Cars 數**|**Discrete**|**Long**|  
    |**在家中的子女數**|**Discrete**|**Long**|  
    |**區域**|**Discrete**|**文字**|  
    |**Total Children**|**Discrete**|**Long**|  
    |**年收入**|**連續**|**兩**|  
  
3.  按 [下一步]  。  
  
## <a name="next-task-in-lesson"></a>本課程的下一項工作  
 [為結構指定測試資料集 &#40;基本資料採礦教學課程&#41;](../../2014/tutorials/specifying-a-testing-data-set-for-the-structure-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>本課程的前一項工作  
 [建立目標郵寄採礦模型結構 &#40;基本資料採礦教學課程&#41;](../../2014/tutorials/creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>另請參閱  
 [&#40;資料採礦&#41;的內容類型](../../2014/analysis-services/data-mining/content-types-data-mining.md)   
 [資料類型 &#40;資料採礦&#41;](../../2014/analysis-services/data-mining/data-types-data-mining.md)  
  
  
