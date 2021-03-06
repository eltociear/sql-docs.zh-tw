---
title: 插入（DMX） |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 210ab8c5750fdcb38bcbca324d77eecd926042d1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68892719"
---
# <a name="insert-into-dmx"></a>INSERT INTO (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  處理指定的資料採礦物件。 如需有關處理採礦模型和採礦結構的詳細資訊，請參閱[&#40;資料採礦&#41;的處理需求和考慮](https://docs.microsoft.com/analysis-services/data-mining/processing-requirements-and-considerations-data-mining)。  
  
 如果指定採礦結構，則陳述式會處理採礦結構及其所有相關聯的採礦模型。 如果指定採礦模型，陳述式就只會處理採礦模型。  
  
## <a name="syntax"></a>語法  
  
```  
  
INSERT INTO [MINING MODEL]|[MINING STRUCTURE] <model>|<structure> (<mapped model columns>) <source data query>  
INSERT INTO [MINING MODEL]|[MINING STRUCTURE] <model>|<structure>.COLUMN_VALUES (<mapped model columns>) <source data query>  
```  
  
## <a name="arguments"></a>引數  
 *model*  
 模型識別碼。  
  
 *表示*  
 結構識別碼。  
  
 *對應的模型資料行*  
 資料行識別碼與巢狀識別碼的逗號分隔清單。  
  
 *來源資料查詢*  
 提供者自訂格式中的來源查詢。  
  
## <a name="remarks"></a>備註  
 如果您未指定 [**採礦模型**] 或 [**採礦結構**]， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]會根據名稱來搜尋物件類型，並處理正確的物件。 如果伺服器包含具有相同名稱的採礦結構與採礦模型，就會傳回錯誤。  
  
 藉由使用第二個語法形式，插入*\<物件>*。COLUMN_VALUES，您可以將資料直接插入模型資料行，而不需要定型模型。 這種方法以精簡、已排序的方式提供模型的資料行資料，當您處理包含階層或已排序資料行的資料集時很有用。  
  
 如果您使用 [**插入至**] 與 [採礦模型] 或 [採礦結構]， \<並保留 [對應的\<模型資料行]> 和 [來源資料] 查詢> 引數，則語句的行為就像**ProcessDefault**，使用已經存在的系結。 如果繫結不存在，陳述式就會傳回錯誤。 如需有關**ProcessDefault**的詳細資訊，請參閱[處理選項和設定 &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-options-and-settings-analysis-services)。 下列範例會顯示語法：  
  
```  
INSERT INTO [MINING MODEL] <model>  
```  
  
 如果您指定 [**採礦模型**] 並提供對應的資料行和來源資料查詢，則會處理模型和相關聯的結構。  
  
 下表會根據物件的狀態，提供不同陳述式格式之結果的描述。  
  
|引數|物件的狀態|結果|  
|---------------|----------------------|------------|  
|插入至採礦模型*\<模型>*|處理採礦結構。|處理採礦模型。|  
||不處理採礦結構。|處理採礦模型與採礦結構。|  
||採礦結構包含其他的採礦模型。|處理失敗。 您必須重新處理結構與相關聯的採礦模型。|  
|插入至採礦結構*\<結構>*|處理或不處理採礦結構。|處理採礦結構與相關聯的採礦模型。|  
|插入包含來源查詢的「採礦模型*\<模型>* 」<br /><br /> 或<br /><br /> 插入包含來源查詢的採礦結構*\<結構>*|結構或模型早已包含內容。|處理失敗。 在執行此作業之前，您必須先清除物件，方法是使用[DELETE &#40;DMX&#41;](../dmx/delete-dmx.md)。|  
  
## <a name="mapped-model-columns"></a>對應的模型資料行  
 藉由使用\<對應的模型資料行> 專案，您可以將資料來源中的資料行對應至您的採礦模型中的資料行。 對應\<的模型資料行> 元素具有下列格式：  
  
```  
<column identifier> | SKIP | <table identifier> (<column identifier> | SKIP), ...  
```  
  
 藉由使用**SKIP**，您可以排除某些必須存在於來源查詢中的資料行，但不存在於此採礦模型中的資料行。 當您對於輸入資料列集中包含的資料行沒有任何控制權時，SKIP 將會非常實用。 如果您正在撰寫自己的 OPENQUERY，比較好的作法是省略 SELECT 資料行清單中的資料行，而不是使用 SKIP。  
  
 當需要輸入資料列集來執行聯結時，SKIP 也非常實用，但是採礦結構不會使用此資料行。 這個處理的典型範例就是採礦結構及包含巢狀資料表的採礦模型。 此結構的輸入資料列集將會有一個用來透過 SHAPE 子句建立階層式資料列集的外部索引鍵資料行，但是此模型中幾乎都不會使用此外部索引鍵資料行。  
  
 SKIP 的語法要求您在沒有對應採礦結構資料行的輸入資料列集中的個別資料行位置插入 SKIP。 例如，在底下的巢狀資料表範例中，必須在 APPEND 子句中選取 OrderNumber，好讓它可以在 RELATE 子句中用來指定聯結；但是，您不想要將 OrderNumber 資料插入採礦結構的巢狀資料表內。 因此，此範例會在 INSERT INTO 引數中使用 SKIP 關鍵字，而不是 OrderNumber。  
  
## <a name="source-data-query"></a>來源資料查詢  
 \<來源資料查詢> 元素可以包含下列資料來源類型：  
  
-   **OPENQUERY**  
  
-   **OPENROWSET**  
  
-   **多邊形**  
  
-   傳回資料列集的任何 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 查詢  
  
 如需資料來源類型的詳細資訊，請參閱[&#60;來源資料查詢&#62;](../dmx/source-data-query.md)。  
  
## <a name="basic-example"></a>基本範例  
 下列範例會根據**** [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]資料庫中的目標郵寄資料，使用 OPENQUERY 來定型貝氏貝氏機率分類模型。  
  
```  
INSERT INTO NBSample (CustomerKey, Gender, [Number Cars Owned],  
    [Bike Buyer])  
OPENQUERY([AdventureWorksDW2012],'Select CustomerKey, Gender, [NumberCarsOwned], [BikeBuyer]   
FROM [vTargetMail]')  
```  
  
## <a name="nested-table-example"></a>巢狀資料表範例  
 下列範例會使用**SHAPE**來訓練包含一個嵌套資料表的關聯性採礦模型。 請注意，第一個行會包含**SKIP**取代 OrderNumber，這在**SHAPE_APPEND**語句中是必要的，但不會在此模型中使用。  
  
```  
INSERT INTO MyAssociationModel  
    ([OrderNumber],[Models] (SKIP, [Model])  
    )  
SHAPE {  
    OPENQUERY([AdventureWorksDW2012],'SELECT OrderNumber  
    FROM vAssocSeqOrders ORDER BY OrderNumber')  
} APPEND (  
    {OPENQUERY([AdventureWorksDW2012],'SELECT OrderNumber, model FROM   
    dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')}  
  RELATE OrderNumber to OrderNumber)   
AS [Models]  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料採礦延伸模組 &#40;DMX&#41; 資料定義語句](../dmx/dmx-statements-data-definition.md)   
 [資料採礦延伸模組 &#40;DMX&#41; 資料動作陳述式](../dmx/dmx-statements-data-manipulation.md)   
 [資料採礦延伸模組 &#40;DMX&#41; 語句參考](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
