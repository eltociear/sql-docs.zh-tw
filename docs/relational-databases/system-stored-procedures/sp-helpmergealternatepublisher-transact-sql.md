---
title: sp_helpmergealternatepublisher （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergealternatepublisher_TSQL
- sp_helpmergealternatepublisher
helpviewer_keywords:
- sp_helpmergealternatepublisher
ms.assetid: a96e365f-5967-4580-9d79-5bacf2d12211
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6875e745cc05735b9f116c2d4afa5e5218defb99
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68122397"
---
# <a name="sp_helpmergealternatepublisher-transact-sql"></a>sp_helpmergealternatepublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  傳回啟用為合併式發行集的替代發行者之所有伺服器的清單。 這個預存程序執行於訂閱資料庫的訂閱者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_helpmergealternatepublisher [ @publisher = ] 'publisher', [ @publisher_db = ] 'publisher_db', [ @publication = ] 'publication'  
```  
  
## <a name="arguments"></a>引數  
`[ @publisher = ] 'publisher'`這是替代發行者的名稱。*publisher*是**sysname**，沒有預設值。  
  
`[ @publisher_db = ] 'publisher_db'`這是發行集資料庫的名稱。*publisher_db*是**sysname**，沒有預設值。  
  
`[ @publication = ] 'publication'`這是發行集的名稱。*發行*集是**sysname**，沒有預設值。  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**alternate_publisher**|**sysname**|替代發行者的名稱。|  
|**alternate_publisher_db**|**sysname**|發行集資料庫的名稱。|  
|**alternate_publication**|**sysname**|發行集的名稱。|  
|**alternate_distributor**|**sysname**|散發者的名稱。|  
|**friendly_name**|**nvarchar(255)**|替代發行者的描述。|  
|**後**|**bit**|指定伺服器是否為替代發行者。 **1**指定將發行者啟用為替代發行者。 **0**指定未啟用。|  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功）或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_helpmergealternatepublisher**用於合併式複寫中。  
  
 在每個合併工作階段期間，系統會查詢發行者和訂閱者來分別找出它們的替代發行者清單。 合併處理序會加入或卸除替代發行者清單中的項目，結果是在訂閱者端和發行者端都相符的替代發行者清單。  
  
## <a name="permissions"></a>權限  
 只有發行集之發行集存取清單的成員，才可以執行**sp_helpmergealternatepublisher**。  
  
## <a name="see-also"></a>另請參閱  
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
