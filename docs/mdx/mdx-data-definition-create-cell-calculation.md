---
title: CREATE CELL CALCULATION 語句（MDX） |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 7ba563c848179e8cf3dc12f64d2b3c4233955159
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68892158"
---
# <a name="mdx-data-definition---create-cell-calculation"></a>MDX 資料定義 - CREATE CELL CALCULATION


  在 Cube 內指定的 Tuple 集合上，建立評估多維度運算式 (MDX) 運算式的計算。  
  
## <a name="syntax"></a>語法  
  
```  
  
[WITH <CELL CALCULATION clause> Calculation_Name  
   [,WITH <CELL CALCULATION clause> Calculation_Name...n]  
CREATE CELL CALCULATION CURRENTCUBE | Cube_Name.Calculation_Name   
  
<CELL CALCULATION clause> ::=  
   FOR Set_Expression AS 'MDX_Expression'   
      [ [ CONDITION = 'Logical_Expression' ]   
    | [ DISABLED = { TRUE | FALSE } ]   
    | [ DESCRIPTION =String ]   
    | [ CALCULATION_PASS_NUMBER = Integer]   
    | [ CALCULATION_PASS_DEPTH = Integer]   
    | [ SOLVE_ORDER = Integer]   
    | [ Calculation_Name= Scalar_Expression ], ...n]  
```  
  
## <a name="arguments"></a>引數  
 *Cube_Name*  
 提供 Cube 名稱的有效字串。  
  
 *Calculation_Name*  
 提供資料格計算名稱的有效字串。  
  
 *Set_Expression*  
 傳回集合的有效 MDX 運算式。  
  
 *String*  
 有效的字串值。  
  
 *MDX_Expression*  
 有效的 MDX 運算式。  
  
 *Logical_Expression*  
 有效的 MDX 邏輯運算式。  
  
 *介於*  
 有效的整數值。  
  
 *Calculation_Name*  
 提供資料格計算屬性名稱的有效字串。  
  
 *Scalar_Expression*  
 有效的 MDX 純量運算式。  
  
## <a name="remarks"></a>備註  
 在自訂積存公式或導出成員的情況下，使用導出資料格，用戶端應用程式就可以指定特定資料格集的積存值，而非整個資料格集的積存值。 例如，可以指定由 `{[Canada],[Time].[2000]}` 定義的集合內，任何資料格都可以包含由公式定義的值。 此集合以外的其他資料格，則會正常進行運算。  
  
> [!NOTE]  
>  為了回溯相容性，會將 `{*(<comment> | <whitespace> | <newline>)}` 的巴克斯格式 (Backus-Naur Form，BNF) 剖析為 `{*}`。  
  
## <a name="see-also"></a>另請參閱  
 [建立會話範圍匯出資料格](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-cell-calculations-session-scoped-calculated-cells)   
 [建立查詢範圍的資料格計算 &#40;MDX&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-cell-calculations-query-scoped-cell-calculations)   
 [在 mdx 中建立資料格計算 &#40;MDX&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-cell-calculations-build-cell-calculations)   
 [使用資料格屬性 &#40;MDX&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-cell-properties-using-cell-properties)   
 [FORMAT_STRING &#40;MDX 的內容&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents)   
 [FORE_COLOR 和 BACK_COLOR 內容 &#40;MDX&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents)   
 [Mdx 資料定義語句 &#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
