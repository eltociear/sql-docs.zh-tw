---
title: 運算子（MDX 語法） |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5067793ae0f5533a889973e18f7b300914df9092
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68892108"
---
# <a name="operators-mdx-syntax"></a>運算子 (MDX 語法)


  在多維度運算式 (MDX) 中，您可以使用運算子來執行以下動作：  
  
-   變更資料，永久性或暫時性皆可。  
  
-   搜尋符合指定條件的值或物件。  
  
-   實作值或運算式之間的決策。  
  
-   在開始或認可交易之前，或是執行特定的陳述式之前，測試特定條件。  
  
 MDX 支援下表中列出的運算子：  
  
|若要執行此種類型的運算|使用|  
|---------------------------------------|---------|  
|將某值指派到變數，或使用別名來關聯結果集資料行。|[指派運算子](../mdx/assignment-operators.md)|  
|加法、減法、乘法、除法。|[算術運算子](../mdx/arithmetic-operators.md)|  
|測試條件的真實性，例如 AND、OR、NOT 或 XOR。|[位元運算子](../mdx/bitwise-operators.md)|  
|針對另一個值或運算式來比較某值。|[比較運算子](../mdx/comparison-operators.md)|  
|永久或暫時將兩個字串結合成一個字串。|[串連運算子](../mdx/concatenation-operators.md)|  
|永久或暫時將兩個集合運算式結合成單一集合。|[集合運算子](../mdx/set-operators.md)|  
|在一個運算元上執行運算。|[一元運算子](../mdx/unary-operators.md)|  
  
> [!NOTE]  
>  在查詢中，只要看得見 Cube 中與某些類型運算子並用的資料，任何人都可以執行運算。 但是，您必須要有適當的權限，才能順利地變更資料。  
  
 使用多個運算子時，MDX 評估運算子的順序很重要。 同樣地，運算子的使用者可能必須將一個資料類型轉換成另一個資料類型，才能評估運算子。  
  
## <a name="evaluating-complex-expressions"></a>評估複雜的運算式  
 您可以使用運算子來結合數個較小的運算式，來建立一個運算式。 在這些複雜運算式中，MDX 會根據所使用的運算子優先順序定義來評估運算子[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]。 MDX 會先執行優先順序較高的運算子，之後才會執行優先順序較低的運算子。  
  
### <a name="understanding-operator-precedence"></a>了解運算子優先順序  
 以下清單會顯示運算子優先順序，從最高顯示到最低。 位於同一行的運算子會有相同的優先順序，而且除非利用括號強制執行，否則會由左至右進行評估。  
  
-   IS  
  
-   AS  
  
-   DISTINCT  
  
-   :  
  
-   ^  
  
-   /, *  
  
-   +、 -  
  
-   EXISTING  
  
-   <>、>=、=、 \<=、>、<  
  
-   NOT  
  
-   AND  
  
-   XOR  
  
-   OR  
  
 如需 MDX 中運算子的詳細資訊，請參閱 mdx[運算子參考 &#40;mdx&#41;](../mdx/mdx-operator-reference-mdx.md)。  
  
### <a name="determining-results"></a>決定結果  
 當您將簡單的運算式組合成複雜的運算式時，結合了資料類型優先順序規則的運算子規則，即可決定結果值的資料類型。  
  
 如果結果是字元或 Unicode 值， 結合運算子的規則與定序優先順序的規則，就可以決定結果的定序。 如需定序的詳細資訊，請參閱[&#40;Analysis Services&#41;的語言和](https://docs.microsoft.com/analysis-services/languages-and-collations-analysis-services)定序。  
  
 另外也有一些規則，根據簡單運算式的有效位數、小數位數與長度，決定結果的有效位數、小數位數與長度。  
  
## <a name="converting-data-types"></a>轉換資料類型  
 在需要不同類型的運算式中使用物件時，MDX 會隱含地將那個物件轉換成不同的類型。 下表定義了每個物件的轉換規則。  
  
|原始類型|所需類型|轉換|  
|-------------------|-----------------|----------------|  
|層級|設定|\<層級>。成員|  
|階層|成員|\<階層>. defaultmember|  
|成員|Tuple|（\<成員>）|  
|Tuple|成員|\<元組> 專案（0）|  
|Tuple|純量|\<元組> 值|  
  
## <a name="see-also"></a>另請參閱  
 [Mdx 運算子參考 &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Mdx 語法元素 &#40;MDX&#41;](../mdx/mdx-syntax-elements-mdx.md)  
  
  
