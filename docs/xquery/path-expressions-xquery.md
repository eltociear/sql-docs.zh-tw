---
title: 路徑運算式（XQuery） |Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- axis step [XQuery]
- path expressions [XQuery]
- expressions [XQuery], path
ms.assetid: b93fa36c-bf69-46b9-b137-f597d66fd0c0
author: rothja
ms.author: jroth
ms.openlocfilehash: 9be2fb8752f27164e0e6dbc59e499f4b048d8979
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "67946396"
---
# <a name="path-expressions-xquery"></a>路徑運算式 (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  XQuery 路徑運算式會找出文件中的節點，例如元素、屬性及文字節點。 路徑運算式的結果永遠發生在文件順序中，在結果時序中沒有重複的節點。 在指定的路徑中，您可以使用未縮寫或縮寫的語法。 下列資訊是著重在未縮寫的語法中。 本主題稍後將說明縮寫語法。  
  
> [!NOTE]  
>  因為本主題中的範例查詢是針對**ProductModel**資料表中的**xml**類型資料行**CatalogDescription**和**指示**所指定，所以您應該熟悉儲存在這些資料行中的 xml 檔的內容和結構。  
  
 路徑運算式可以是相對或絕對。 下列是這兩種路徑的描述：  
  
-   相對路徑運算式是由一或多步所組成，並以一或兩個斜線分隔 (/ 或 //)。 例如，`child::Features` 是相對路徑運算式，其中 `Child` 只參考內容節點的子節點。 這是目前所處理的節點。 運算式會抓取內容\<節點之元素節點子系的功能>。  
  
-   以一或兩個斜線開頭的絕對路徑運算式，後面接著選擇性的相對路徑。 例如，運算式中的開頭斜線 `/child::ProductDescription`，表示它是絕對路徑運算式。 由於運算式開頭的斜線會傳回內容節點的檔根節點，因此運算式會傳回檔根目錄的所有\<ProductDescription> 元素節點子系。  
  
     如果絕對路線是以單一斜線開頭，它後面可能會或可能不會接著相對路徑。 如果只指定單一斜線，運算式會傳回內容節點的根節點。 對於 XML 資料類型，這是文件節點。  
  
 典型的路徑運算式是由數步所組成。 例如，絕對路徑運算式`/child::ProductDescription/child::Summary`包含以斜線分隔的兩個步驟。  
  
-   第一個步驟會抓取\<檔根目錄的 ProductDescription> 元素節點子系。  
  
-   第二個步驟會\<針對每個抓取的\<ProductDescription> 元素節點，抓取摘要> 元素節點子系，而後者會成為內容節點。  
  
 路徑運算式中的一步可以是一個軸步或一般步。  
  
## <a name="axis-step"></a>軸步  
 路徑運算式中的軸步包含下列部份。  
  
 [相交](../xquery/path-expressions-specifying-axis.md)  
 定義移動的方向。 路徑運算式中的軸步是從內容節點開始，並導覽回軸中所指定的可到達方向之節點。  
  
 [節點測試](../xquery/path-expressions-specifying-node-test.md)  
 指定要選取的節點類型或節點名稱。  
  
 零或多個選擇性述詞  
 選擇一些節點並捨棄其他以篩選它們。  
  
 下列範例會在路徑運算式中使用**axisstep** ：  
  
-   絕對路徑運算式 `/child::ProductDescription` 只包含一個步驟。 它指定一個軸 (`child`) 及一個節點測試 (`ProductDescription`)。  
  
-   相對路徑運算式 `child::ProductDescription/child::Features` 包含以斜線分隔的兩步。 兩步都指定子軸。 ProductDescription 與 Features 都是節點測試。  
  
-   相對路徑運算式`child::root/child::Location[attribute::LocationID=10]`包含以斜線分隔的兩個步驟。 第一步指定一個軸 (`child`) 及一個節點測試 (`root`)。 第二步指定一個軸步的所有三個元件：一個軸 (子系)、節點測試 (`Location`) 以及述詞 (`[attribute::LocationID=10]`)。  
  
 如需軸步驟之元件的詳細資訊，請參閱在[路徑運算式步驟中指定軸](../xquery/path-expressions-specifying-axis.md)、[在路徑運算式步驟中指定節點測試](../xquery/path-expressions-specifying-node-test.md)和在[路徑運算式步驟中指定述](../xquery/path-expressions-specifying-predicates.md)詞。  
  
## <a name="general-step"></a>一般步  
 一般步只是一個必須評估為節點序列的運算式。  
  
 在 SQL Server 中的 XQuery 實作支援路徑運算式中做為第一步的一般步。 下列是使用一般步的路徑運算式範例。  
  
```  
(/a, /b)/c  
id(/a/b)  
```  
  
 如需 id 函式的詳細資訊，請參閱[Id 函數 &#40;XQuery&#41;](../xquery/functions-on-sequences-id.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [指定路徑運算式步驟中的軸](../xquery/path-expressions-specifying-axis.md)  
 描述在路徑運算式中使用軸步。  
  
 [指定路徑運算式步驟中的節點測試](../xquery/path-expressions-specifying-node-test.md)  
 描述在路徑運算式中使用節點測試。  
  
 [在路徑運算式步驟中指定述詞](../xquery/path-expressions-specifying-predicates.md)  
 描述在路徑運算式中使用述詞。  
  
 [在路徑運算式中使用縮寫語法](../xquery/path-expressions-using-abbreviated-syntax.md)  
 描述在路徑運算式中使用縮寫語法。  
  
  
