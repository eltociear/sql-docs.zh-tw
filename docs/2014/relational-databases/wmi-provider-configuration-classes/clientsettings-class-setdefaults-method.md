---
title: SetDefaults 方法（ClientSettings 類別） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDefaults Method (ClientSettings Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: 056508f3-a5c8-467c-a196-dc1ef1f5178f
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: ce71d591dc8f72e6826f7bcd96628fb1898fd7bd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "63242945"
---
# <a name="setdefaults-method-clientsettings-class"></a>SetDefaults 方法 (ClientSettings 類別)
  使用覆寫現有資料的選項，設定[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]用戶端實例的所有預設值。  
  
## <a name="syntax"></a>語法  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a>組件  
 *目標*  
 代表 `ClientSettings` 用戶端執行個體的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件。  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|*OverwriteAll*|指定是否要覆寫 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端執行個體上之現有值的布林值。 
  `true` 表示要覆寫現有的資料，`false` 表示不覆寫現有的資料。|  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 
  `uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。  
  
## <a name="remarks"></a>備註  
  
