---
title: CursorTypeEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CursorTypeEnum
helpviewer_keywords:
- CursorTypeEnum enumeration [ADO]
ms.assetid: ffc6e245-4471-42ae-84dd-e85bddfce983
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f6333934997c9de38b8df1dd08849886ff3dd7f2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "67933276"
---
# <a name="cursortypeenum"></a>CursorTypeEnum
指定[記錄集](../../../ado/reference/ado-api/recordset-object-ado.md)物件中使用的資料指標類型。  
  
|持續性|值|描述|  
|--------------|-----------|-----------------|  
|**adOpenDynamic**|2|使用動態資料指標。 系統會顯示其他使用者的新增、變更和刪除，而且除了書簽以外，如果提供者不支援，則會允許所有類型的移動**記錄**。|  
|**adOpenForwardOnly**|0|預設。 使用順向資料指標。 與靜態資料指標相同，不同之處在于您只能向前移動記錄。 當您只需要對**記錄集**進行一次傳遞時，這會改善效能。|  
|**adOpenKeyset**|1|使用索引鍵集資料指標。 與動態資料指標相似，不同之處在于您無法查看其他使用者所新增的記錄，但無法從您的**記錄集**存取其他使用者所刪除的記錄。 其他使用者的資料變更仍然可見。|  
|**adOpenStatic**|3|使用靜態資料指標，這是一組記錄的靜態副本，您可以用來尋找資料或產生報表。 不會顯示其他使用者所做的新增、變更或刪除。|  
|**adOpenUnspecified**|-1|未指定資料指標的類型。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 對等  
 Package： **.com. wfc. 資料**  
  
|持續性|  
|--------------|  
|AdoEnums. CursorType. DYNAMIC|  
|AdoEnums. CursorType. FORWARDONLY|  
|AdoEnums. CursorType. 索引鍵集|  
|AdoEnums. CursorType. STATIC|  
|AdoEnums. CursorType。未指定|  
  
## <a name="applies-to"></a>套用至  
 [CursorType 屬性 (ADO)](../../../ado/reference/ado-api/cursortype-property-ado.md)
