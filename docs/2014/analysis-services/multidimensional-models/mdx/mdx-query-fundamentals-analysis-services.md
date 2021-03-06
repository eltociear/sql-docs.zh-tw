---
title: MDX 查詢基本概念（Analysis Services） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- statements [MDX]
- Multidimensional Expressions [Analysis Services], statements
- Multidimensional Expressions [Analysis Services], queries
- MDX [Analysis Services], statements
- MDX queries [Analysis Services]
- MDX [Analysis Services], queries
- queries [MDX]
ms.assetid: a560383b-bb58-472e-95f5-65d03d8ea08b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 42c4d8581374c9805c28ce577249995427fd5c7e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "66073884"
---
# <a name="mdx-query-fundamentals-analysis-services"></a>MDX 查詢基礎觀念 (Analysis Services)
  您可以使用多維度運算式 (MDX) 查詢多維度物件 (例如 Cube)，然後傳回包含 Cube 資料的多維度資料格集。 這個主題以及子主題將提供對 MDX 查詢的概觀。  
  
 以下主題描述 MDX 查詢與其產生的資料格集，並提供有關基本 MDX 語法更詳細的資訊。  
  
> [!NOTE]  
>  如需 MDX 查詢和計算相關效能問題的詳細資訊，請參閱《 [SQL Server 2005 Analysis Services 效能指南》](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide)中的「撰寫有效率的 MDX」一節。  
  
## <a name="in-this-section"></a>本節內容  
  
|主題|描述|  
|-----------|-----------------|  
|[&#40;MDX 的基本 MDX 查詢&#41;](mdx-query-the-basic-query.md)|提供 MDX SELECT 陳述式的基本語法資訊。|  
|[使用查詢和交叉分析篩選器軸來限制查詢 &#40;MDX&#41;](mdx-query-and-slicer-axes-restricting-the-query.md)|描述什麼是查詢及 Slicer 軸，以及如何指定它們。|  
|[在查詢中建立 Cube 內容 &#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md)|描述 MDX SELECT 陳述式中 FROM 子句的目的。|  
|[在 mdx 中建立命名集 &#40;MDX&#41;](mdx-named-sets-building-named-sets.md)|描述 MDX 中命名集的用途，以及在 MDX 查詢中建立和使用它們所需的技巧。|  
|[在 MDX 中建立匯出成員 &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md)|提供有關 MDX 中導出成員的資訊，包括在 MDX 運算式中建立和使用它們所需的技巧。|  
|[在 mdx 中建立資料格計算 &#40;MDX&#41;](../../multidimensional-models-olap-logical-cube-objects/calculations.md)|詳述建立與使用導出資料格的程序。|  
|[&#40;MDX&#41;建立和使用屬性值](../../creating-and-using-property-values-mdx.md)|詳述建立和使用維度、層級、成員及資料格屬性的程序。|  
|[&#40;MDX&#41;運算元據](mdx-data-manipulation-manipulating-data.md)|描述使用鑽研及積存功能操作資料背後的基本知識，還會描述 MDX 中的行程順序及解決順序。|  
|[修改資料 &#40;MDX&#41;](mdx-data-modification-modifying-data.md)|描述如何使用回寫，暫時或永久地變更多維度資料。|  
|[使用 &#40;MDX&#41;的變數和參數](using-variables-and-parameters-mdx.md)|描述如何在 MDX 查詢中使用變數和參數。|  
  
## <a name="see-also"></a>另請參閱  
 [&#40;MDX&#41; 參考的多維度運算式](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
