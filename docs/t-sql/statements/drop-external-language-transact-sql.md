---
title: DROP EXTERNAL LANGUAGE (Transact-SQL) - SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 08/08/2019
ms.prod: sql
ms.technology: language-extensions
ms.topic: language-reference
author: nelgson
ms.author: negust
ms.reviewer: dphansen
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3767bec1807b68df3eb3f82287a5c871d653a286
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "68892978"
---
# <a name="drop-external-library-transact-sql"></a>DROP EXTERNAL LIBRARY (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

刪除現有的外部語言。

## <a name="syntax"></a>語法

```text
DROP EXTERNAL LANGUAGE <language_name>
```

### <a name="arguments"></a>引數

**language_name**

語言是資料庫範圍的物件。 語言名稱在資料庫內必須是唯一的。

## <a name="permissions"></a>權限

若要刪除語言，則需要 ALTER ANY EXTERNAL LANGUAGE 權限。 根據預設，任何資料庫擁有者或物件的擁有者，也可刪除外部語言。

> [!NOTE]
> 請注意，移除外部語言之前，您需要移除參考外部語言的外部程式庫。

### <a name="return-values"></a>傳回值

如果陳述式執行成功，會傳回參考訊息。

## <a name="remarks"></a>備註

需要先刪除指定語言的所有外部程式庫，才能刪除外部語言。

## <a name="examples"></a>範例

建立外部語言 **Java**：

```sql
CREATE EXTERNAL LANGUAGE Java 
FROM (CONTENT = N'<path-to-zip>', FILE_NAME = 'javaextension.dll');
GO
```

置放外部語言：

```sql
DROP EXTERNAL LANGUAGE Java;
```

## <a name="see-also"></a>另請參閱

[CREATE EXTERNAL LANGUAGE (Transact-SQL)](create-external-language-transact-sql.md)  
[ALTER EXTERNAL LANGUAGE (Transact-SQL)](alter-external-language-transact-sql.md)  
[sys.external_languages](../../relational-databases/system-catalog-views/sys-external-languages-transact-sql.md)  
[sys.external_language_files](../../relational-databases/system-catalog-views/sys-external-language-files-transact-sql.md)  
