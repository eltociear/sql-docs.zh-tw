---
title: Broker:Connection 事件類別 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Broker:Connection event class
ms.assetid: d3e505f2-0a43-486f-aa92-9c8e49b2dfea
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 22cb73877dcea8fb880d4c565b809990e5ce7123
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "62664374"
---
# <a name="brokerconnection-event-class"></a>Broker:Connection 事件類別
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 產生 **Broker:Connection** 事件以報告 Service Broker 所管理的傳輸連線狀態。  
  
## <a name="brokerconnection-event-class-data-columns"></a>Broker:Connection 事件類別資料行  
  
|資料行|類型|描述|資料行編號|可篩選|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|`nvarchar`|建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體之連接的用戶端應用程式名稱。 這個資料行會填入應用程式所傳送的值，而非程式的顯示名稱。|10|是|  
|**ClientProcessID**|`int`|主機電腦指派給用戶端應用程式執行中處理序的識別碼。 如果用戶端提供處理序識別碼，這個資料行就會擴展。|9|是|  
|**DatabaseID**|`int`|由 USE *database* 陳述式所指定的資料庫識別碼，或者如果沒有針對指定執行個體發出 USE *database*陳述式，則是預設資料庫的識別碼。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]如果在追蹤中捕捉到**ServerName**資料行，而且伺服器可供使用，則會顯示資料庫的名稱。 使用**DB_ID**函數來決定資料庫的值。|3|是|  
|**錯誤**|`int`|事件中文字的訊息識別碼（以**sys.databases**表示）。 如果此事件報告錯誤，這是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤號碼。|31|否|  
|**EventClass**|`int`|擷取的事件類別類型。 
  **Broker:Connection** 永遠是 **138**。|27|否|  
|**EventSequence**|`int`|此事件的序號。|51|否|  
|**EventSubClass**|`nvarchar`|此連線的連線狀態。 對於此事件，子類別將為下列其中一個值：<br /><br /> **正在連接**。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 正在起始傳輸連接。<br /><br /> **Connected**。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已建立傳輸連接。<br /><br /> **連接失敗**。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 無法建立傳輸連接。<br /><br /> **關閉**。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 正在關閉傳輸連接。<br /><br /> **已關閉**。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已經關閉傳輸連接。<br /><br /> **接受**。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已經接受另一個執行個體的傳輸連接。<br /><br /> **傳送 IO 錯誤**。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在傳送訊息時遭遇到傳輸錯誤。<br /><br /> **接收 IO 錯誤**。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在接收訊息時遭遇到傳輸錯誤。|21|是|  
|**GUID**|`uniqueidentifier`|此連線的結束點識別碼。|54|否|  
|**名稱**|`nvarchar`|執行用戶端的電腦名稱。 這個資料行會在用戶端提供主機名稱時填入。 若要判斷主機名稱，請使用**HOST_NAME**函數。|8|是|  
|**IntegerData**|`int`|此連線已經關閉的次數|25|是|  
|**IsSystem**|`int`|指出事件是發生在系統處理序或使用者處理序。<br /><br /> 0 = 使用者<br /><br /> 1 = 系統|60|否|  
|**LoginSid**|`image`|已登入之使用者的安全性識別碼 (SID)。 伺服器上的每一個登入之 SID 是唯一的。|41|是|  
|**NTDomainName**|`nvarchar`|使用者所隸屬的 Windows 網域。|7|是|  
|**NTUserName**|`nvarchar`|擁有產生此事件之連接的使用者名稱。|6|是|  
|**ObjectName**|`nvarchar`|對話的交談控制代碼。|34|否|  
|**ServerName**|`nvarchar`|正在追蹤之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的名稱。|26|否|  
|**SPID**|`int`|由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 指派給用戶端關聯之處理序的伺服器處理序識別碼。|12|是|  
|**StartTime**|`datetime`|事件啟動的時間 (如果有的話)。|14|是|  
|**TextData**|`ntext`|與此事件相關的錯誤訊息文字。 對於未報告錯誤的事件，此欄位是空白的。 錯誤訊息有可能是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤訊息或是 Windows 錯誤訊息。|1|是|  
|**TransactionID**|`bigint`|系統指派的交易識別碼。|4|否|  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
