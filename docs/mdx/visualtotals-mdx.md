---
title: VisualTotals （MDX） |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a5becd3382f07a9adc89055a253235495a7e50a8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125843"
---
# <a name="visualtotals-mdx"></a>VisualTotals (MDX)


  傳回指定集合中動態加總子成員所產生的集合，您可以選擇是否要在結果集中使用父成員名稱的模式。  
  
## <a name="syntax"></a>語法  
  
```  
  
VisualTotals(Set_Expression[,Pattern])  
```  
  
## <a name="arguments"></a>引數  
 *Set_Expression*  
 傳回集合的有效多維度運算式 (MDX) 運算式。  
  
 *Pattern*  
 集合中父成員的有效字串運算式，包含星號 (*) 做為父系名稱的替代字元。  
  
## <a name="remarks"></a>備註  
 指定的集合運算式可以指定集合，其中包含單一維度內任何層級的成員 (一般是上下階關聯性的成員)。 **VisualTotals**函數會在指定的集合中加總子成員的值，並忽略不在計算結果總計的集合中的子成員。 以階層順序排序之集合的總計是以視覺化的方式加總。 如果集合中的成員順序破壞階層，結果不是視覺化總計。 例如，VisualTotals (USA, WA, CA, Seattle) 不會將 WA 做為 Seattle 傳回，而是傳回 WA、CA 及 Seattle 的值，然後加總這些值做為 USA 的視覺化總計，Seattle 的銷售額會計算兩次。  
  
> [!NOTE]  
>  將**VisualTotals**函數套用至與量值無關或小於量值群組資料細微性的維度成員，會導致以 null 取代值。  
  
 *模式*是選擇性的，它會指定總計標籤的格式。 *模式*需要星號（*）做為父成員的替代字元，並且字串中的其餘文字會出現在與父系名稱串連的結果中。 若要顯示常值星號，請使用兩\*\*個星號（）。  
  
## <a name="examples"></a>範例  
 下列範例會根據單一指定下階 (7 月份)，傳回 2001 日曆年度第三季的視覺化總計。  
  
```  
SELECT VisualTotals  
   ({[Date].[Calendar].[Calendar Quarter].&[2001]&[3]  
      ,[Date].[Calendar].[Month].&[2001]&[7]}) ON 0  
FROM [Adventure Works]  
```  
  
 下列範例會傳回 Product 維度中 Category 屬性階層的 [All] 成員及其四個子系的其中兩個。 所傳回的 [All] 成員的 Internet Sales Amount 量值總計只是 Accessories 和 Clothing 成員的總計。 此外，也使用模式引數來指定 [All Products] 資料行的標籤。  
  
```  
SELECT  
   VisualTotals  
   ({[Product].[Category].[All Products]  
      ,[Product].[Category].[Accessories]  
      ,[Product].[Category].[Clothing]}  
      , '* - Visual Total'  
   ) ON Columns  
, [Measures].[Internet Sales Amount] ON Rows  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>另請參閱  
 [Mdx 函數參考 &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
