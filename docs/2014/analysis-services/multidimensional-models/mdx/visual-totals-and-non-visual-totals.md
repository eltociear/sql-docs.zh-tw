---
title: 視覺效果總計和非視覺效果總計 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ea9d02f2-a668-4547-ade5-e3d077a2e1bd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3f110b54d1a8a057f16b5e5682adc3beb04c54f6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "66073724"
---
# <a name="visual-totals-and-non-visual-totals"></a>視覺化總計和非視覺化總計
  視覺化總計是在資料行或資料列結尾加總該資料行或資料列中之所有可見項目的總計。 這是大部分資料表顯示時的預設行為。 不過，有時候使用者只想要顯示資料表中的某些資料行，但保持整個資料列的總計，包括未顯示的資料行。 這些稱為「非視覺化總計」(`Non Visual Totals`)，因為總計來自可見和不可見的值。  
  
 下列案例示範非視覺化總計的行為。 第一個步驟示範視覺化總計的預設行為。  
  
 下列範例示範 [Adventure Works] 的查詢如何在包含產品類別目錄資料行和轉售商商務類型資料列的資料表中，取得 [Reseller Sales Amount] 數字。 請注意，在發出下列 SELECT 陳述式時，會提供產品和轉售商的總計：  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from [Adventure Works]`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 會產生下列結果：  
  
|||||||  
|-|-|-|-|-|-|  
||**所有產品**|**Accessories**|**Bikes**|**Clothing**|**元件**|  
|**所有轉銷商**|**$80450596.98**|**$571297.93**|**$66302381.56**|**$1777840.84**|**$11799076.66**|  
|**專業自行車商店**|**$6756166.18**|**$65125.48**|**$6080117.73**|**$252933.91**|**$357989.07**|  
|**增值轉銷商**|**$34967517.33**|**$175002.81**|**$30892354.33**|**$592385.71**|**$3307774.48**|  
|**式**|**$38726913.48**|**$331169.64**|**$29329909.50**|**$932521.23**|**$8133313.11**|  
  
## <a name="non-visual-on-rows-and-columns"></a>資料行和資料列上的非視覺化  
 若要只針對產品為 Accessories 和 Clothing，且轉售商為 Value Added Reseller 和 Warehouse 的資料產生資料表，但同時保留全部項目的總計，可以使用 NON VISUAL 撰寫如下：  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0,`  
  
 `{[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 1`  
  
 `from [Adventure Works])`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 會產生下列結果：  
  
|||||  
|-|-|-|-|  
||**所有產品**|**Accessories**|**Clothing**|  
|**所有轉銷商**|**$80450596.98**|**$571297.93**|**$1777840.84**|  
|**增值轉銷商**|**$34967517.33**|**$175002.81**|**$592385.71**|  
|**式**|**$38726913.48**|**$331169.64**|**$932521.23**|  
  
## <a name="non-visual-on-rows"></a>資料列上的非視覺化  
 若要產生可以視覺化總計資料行，但就資料列總計傳回所有 [Category] 的實際總計，應發出下列查詢：  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0`  
  
 `from ( Select {[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 0`  
  
 `from [Adventure Works])`  
  
 `)`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 請注意如何將 NON VISUAL 只套用到 [Category]。  
  
 上述的查詢會產生下列結果：  
  
|||||  
|-|-|-|-|  
||All Products|Accessories|Clothing|  
|All Resellers|$73,694,430.80|$506,172.45|$1,524,906.93|  
|Value Added Reseller|$34,967,517.33|$175,002.81|$592,385.71|  
|Warehouse|$38,726,913.48|$331,169.64|$932,521.23|  
  
 與前一個結果相比，您可以發現 [All Resellers] 資料列現在只總計 [Value Added Reseller] 和 [Warehouse] 的顯示值，但 [All Products] 資料行顯示所有產品 (包括未顯示產品) 的總計值。  
  
## <a name="see-also"></a>另請參閱  
 [MDX 中的重要概念 &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md)   
 [自動存在](autoexists.md)   
 [使用成員、元組和集合 &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md)   
 [MDX 查詢基本概念 &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)   
 [&#40;MDX 的基本 MDX 查詢&#41;](mdx-query-the-basic-query.md)   
 [使用查詢和交叉分析篩選器軸來限制查詢 &#40;MDX&#41;](mdx-query-and-slicer-axes-restricting-the-query.md)   
 [在查詢中建立 Cube 內容 &#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md)  
  
  
