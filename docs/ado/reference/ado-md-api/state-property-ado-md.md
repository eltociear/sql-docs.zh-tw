---
title: State 屬性（ADO MD） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- State
- Cellset::State
helpviewer_keywords:
- State property [ADO MD]
ms.assetid: 06d480ca-9eb6-4570-a45d-a73539bddd32
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0c11bb74b62d54b1e2489cba5dd7cd35ee376a41
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "67949150"
---
# <a name="state-property-ado-md"></a>State 屬性 (ADO MD)
表示集的目前狀態。  
  
## <a name="return-values"></a>傳回值  
 傳回**長**整數，表示[集](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)區分物件的目前條件，而且是唯讀的。 下列是有效的值： **adStateClosed** （0）和**adStateOpen** （1）。  
  
## <a name="remarks"></a>備註  
 若要使用[ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md)常數名稱，您的專案中必須參考 ADO 類型程式庫。 如需詳細資訊，請參閱搭配[使用 ADO 與 ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md) 。  
  
## <a name="applies-to"></a>套用至  
 [Cellset 物件 (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>另請參閱  
 [Close 方法（ADO MD）](../../../ado/reference/ado-md-api/close-method-ado-md.md)   
 [Open 方法 (ADO MD)](../../../ado/reference/ado-md-api/open-method-ado-md.md)
