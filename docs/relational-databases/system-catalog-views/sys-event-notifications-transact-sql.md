---
title: sys.databases event_notifications （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- event_notifications_TSQL
- event_notifications
- sys.event_notifications_TSQL
- sys.event_notifications
dev_langs:
- TSQL
helpviewer_keywords:
- sys.event_notifications catalog view
ms.assetid: 136a76ee-2b35-4418-ab46-fda2d51f7d99
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 736083db5043dd8bcb9dce9f828a9191c582c872
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68048425"
---
# <a name="sysevent_notifications-transact-sql"></a>sys.event_notifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  針對每個屬於事件通知的物件，各傳回一個資料列，其中包含**sys.databases。 type** = EN。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|事件通知名稱。|  
|**object_id**|**int**|物件識別碼。 在資料庫中，這是唯一的。|  
|**parent_class**|**tinyint**|父系的類別。<br /><br /> 0 = 資料庫<br /><br /> 1 = 物件或資料行|  
|**parent_class_desc**|**Nvarchar （60）**|DATABASE<br /><br /> OBJECT_OR_COLUMN|  
|**parent_id**|**int**|父物件的非零識別碼。<br /><br /> 0 = 父類別是資料庫。|  
|**create_date**|**datetime**|建立日期。|  
|**modify_date**|**datetime**|一律等於**create_date**。|  
|**service_name**|**nvarchar(256)**|通知所送往之目標服務的名稱。|  
|**broker_instance**|**nvarchar(128)**|通知所送往的 Broker 執行個體。|  
|**principal_id**|**int**|擁有這個事件通知的資料庫主體識別碼。|  
|**creator_sid**|**Varbinary （85）**|建立事件通知之登入的 SID。<br /><br /> 如果未指定 FAN_IN 選項，便是 NULL。|  
  
## <a name="permissions"></a>權限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的物件目錄檢視](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
