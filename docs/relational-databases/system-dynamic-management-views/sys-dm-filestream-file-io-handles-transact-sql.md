---
title: sys.databases dm_filestream_file_io_handles （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_filestream_file_io_handles
- sys.dm_filestream_file_io_handles
- dm_filestream_file_io_handles_TSQL
- sys.dm_filestream_file_io_handles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_filestream_file_io_handle catalog view
ms.assetid: e59632f4-3292-419f-9217-ca375749f1a5
author: stevestein
ms.author: sstein
ms.openlocfilehash: a96bcedaa3922ebb0691ac949f9eb15ed28336b3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68103303"
---
# <a name="sysdm_filestream_file_io_handles-transact-sql"></a>sys.dm_filestream_file_io_handles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  顯示命名空間擁有者 (NSO) 所知道的檔案控制代碼。 此視圖會顯示使用**OpenSqlFilestream**的 Filestream 控制碼。  
  
|資料行|類型|描述|  
|------------|----------|-----------------|  
|**handle_context_address**|**varbinary(8)**|顯示與用戶端控制碼相關聯之內部 NSO 結構的位址。 可為 Null。|  
|**creation_request_id**|**int**|從用來建立此控制代碼的 REQ_PRE_CREATE I/O 要求顯示欄位。 不可為 Null。|  
|**creation_irp_id**|**int**|從用來建立此控制代碼的 REQ_PRE_CREATE I/O 要求顯示欄位。 不可為 Null|  
|**handle_id**|**int**|顯示驅動程式指派給此控制代碼的唯一識別碼。 不可為 Null。|  
|**creation_client_thread_id**|**varbinary(8)**|從用來建立此控制代碼的 REQ_PRE_CREATE I/O 要求顯示欄位。 可為 Null。|  
|**creation_client_process_id**|**varbinary(8)**|從用來建立此控制代碼的 REQ_PRE_CREATE I/O 要求顯示欄位。 可為 Null。|  
|**filestream_transaction_id**|**Varbinary （128）**|顯示與給定控制代碼相關聯之交易的識別碼。 這是**get_filestream_transaction_coNtext**函數所傳回的值。 使用此欄位來聯結至 [ **sys.databases] dm_filestream_file_io_requests**視圖。 可為 Null。|  
|**access_type**|**Nvarchar （60）**|不可為 Null。|  
|**logical_path**|**nvarchar(256)**|顯示此控制代碼開啟之檔案的邏輯路徑名稱。 這是所傳回的相同路徑名稱 **。** **Varbinary**（**Max**） filestream 的 PathName 方法。 可為 Null。|  
|**physical_path**|**nvarchar(256)**|顯示檔案的實際 NTFS 路徑名稱。 這是所傳回的相同路徑名稱 **。** **Varbinary**（**Max**） filestream 的 .physicalpathname 方法。 它是透過追蹤旗標 5556 啟用。 可為 Null。|  
  
## <a name="permissions"></a>權限  
 需要伺服器的 VIEW SERVER STATE 權限。  
  
## <a name="see-also"></a>另請參閱  
 [Filestream 和 FileTable 動態管理檢視 &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)  
  
  
