---
title: sys.databases sp_rda_reconcile_columns （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_reconcile_columns
- sys.sp_rda_reconcile_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_columns stored procedure
ms.assetid: 60d9cc4e-1828-450b-9d88-5b8485800d73
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7ad2fd6c51f5b5463e4e4c10745b2ff245bd691d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083667"
---
# <a name="syssp_rda_reconcile_columns-transact-sql"></a>sys.databases sp_rda_reconcile_columns （Transact-sql）
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  將遠端 Azure 資料表中的資料行調節為已啟用延展功能的 SQL Server 資料表中的資料行。  
    
  **sp_rda_reconcile_columns**會將資料行加入已啟用 Stretch 的 SQL Server 資料表中，但不在遠端資料表中的遠端資料表。 這些資料行可能是您不小心從遠端資料表中刪除的資料行。 不過， **sp_rda_reconcile_columns**不會刪除遠端資料表中的資料行，但該資料表不存在於 SQL Server 資料表中。
  
  > [!IMPORTANT]
  > 當 **sp_rda_reconcile_columns** 重新建立您不小心從遠端資料表中刪除的資料行時，它不會還原先前存在於已刪除資料行中的資料。
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>語法  
  
```  
  
sp_rda_reconcile_columns @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>引數  
 \@objname = '*\@objname*'  
 已啟用延展功能之 SQL Server 資料表的名稱。  
  
## <a name="return-code-values"></a>傳回碼值  
 0（成功）或 >0 （失敗）  
  
## <a name="permissions"></a>權限  
 需要 db_owner 許可權。  
   
## <a name="remarks"></a>備註  
 如果遠端 Azure 資料表中有些資料行已不再存在於已啟用延展功能的 SQL Server 資料表中，這些額外的資料行並不會影響 Stretch Database 的正常運作。 您也可以手動移除額外的資料行。  
  
## <a name="example"></a>範例  
 若要協調遠端 Azure 資料表中的資料行，請執行下列語句。  
  
```sql  
EXEC sp_rda_reconcile_columns @objname = N'StretchEnabledTableName';  
```  
  
  
