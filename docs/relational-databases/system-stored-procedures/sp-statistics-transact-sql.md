---
title: sp_statistics （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_statistics_TSQL
- sp_statistics
dev_langs:
- TSQL
helpviewer_keywords:
- sp_statistics
ms.assetid: 0bb6495f-258a-47ec-9f74-fd16671d23b8
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b4e3e25dbab53f31e354dcff537b6bfb9a6b433d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68032744"
---
# <a name="sp_statistics-transact-sql"></a>sp_statistics (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  傳回指定資料表或索引檢視的所有索引和統計資料的清單。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_statistics [ @table_name = ] 'table_name'    
     [ , [ @table_owner = ] 'owner' ]   
     [ , [ @table_qualifier = ] 'qualifier' ]   
     [ , [ @index_name = ] 'index_name' ]   
     [ , [ @is_unique = ] 'is_unique' ]  
     [ , [ @accuracy = ] 'accuracy' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @table_name = ] 'table_name'`指定用來傳回目錄資訊的資料表。 *table_name*是**sysname**，沒有預設值。 不支援萬用字元的模式比對。  
  
`[ @table_owner = ] 'owner'`這是用來傳回目錄資訊之資料表的資料表擁有者名稱。 *table_owner*是**sysname**，預設值是 Null。 不支援萬用字元的模式比對。 如果未指定*owner* ，則會套用基礎 DBMS 的預設資料表可見度規則。  
  
 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，如果目前使用者擁有一份含指定名稱的資料表，就會傳回這份資料表的索引。 如果未指定*owner* ，且目前使用者並未擁有具有指定*名稱*的資料表，這個程式就會尋找資料庫擁有者所擁有之指定*名稱*的資料表。 如果資料表存在，就會傳回這份資料表的索引。  
  
`[ @table_qualifier = ] 'qualifier'`這是資料表限定詞的名稱。 *限定詞*是**sysname**，預設值是 Null。 各種 DBMS 產品都支援三部分的資料表命名（辨識_符號_**。**_擁有_者 **。**_名稱_）。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，這個參數代表資料庫名稱。 在某些產品中，它代表資料表之資料庫環境的伺服器名稱。  
  
`[ @index_name = ] 'index_name'`這是索引名稱。 *index_name*是**sysname**，預設值是%。 支援萬用字元的模式比對。  
  
`[ @is_unique = ] 'is_unique'`這是指是否只傳回唯一索引（如果是**Y**）。 *is_unique*是**char （1）**，預設值是**N**。  
  
`[ @accuracy = ] 'accuracy'`這是統計資料的基數和頁面精確度的層級。 *精確度*是**char （1）**，預設值是**Q**。指定**E**以確保統計資料會更新，使基數和分頁正確。  
  
 值**E** （SQL_ENSURE）會要求驅動程式無條件地取出統計資料。  
  
 值**Q** （SQL_QUICK）會要求驅動程式只在伺服器可供使用時，才取出基數和頁面。 在這個情況下，驅動程式無法確保這些值是否為最新的。 撰寫成 Open Group 標準的應用程式，永遠會透過 ODBC 3.x 相容的驅動程式取得 SQL_QUICK 行為。  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**TABLE_QUALIFIER**|**sysname**|資料表限定詞名稱。 這個資料行可以是 NULL。|  
|**TABLE_OWNER**|**sysname**|資料表擁有者名稱。 這個資料行一律會傳回值。|  
|**TABLE_NAME**|**sysname**|資料表名稱。 這個資料行一律會傳回值。|  
|**NON_UNIQUE**|**smallint**|NOT NULL。<br /><br /> 0 = 唯一<br /><br /> 1 = 不是唯一|  
|**INDEX_QUALIFIER**|**sysname**|索引擁有者名稱。 部分 DBMS 產品允許資料表擁有者以外的使用者建立索引。 在[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，這個資料行一律與**TABLE_NAME**相同。|  
|**INDEX_NAME**|**sysname**|這是索引的名稱。 這個資料行一律會傳回值。|  
|**TYPE**|**smallint**|這個資料行一律會傳回值：<br /><br /> 0 = 資料表的統計資料<br /><br /> 1 = 叢集<br /><br /> 2 = 雜湊<br /><br /> 3 = 非叢集|  
|**SEQ_IN_INDEX**|**smallint**|索引內資料行的位置。|  
|**COLUMN_NAME**|**sysname**|傳回**TABLE_NAME**之每個資料行的資料行名稱。 這個資料行一律會傳回值。|  
|**定序**|**char （1）**|定序中使用的順序。 可為以下項目：<br /><br /> A = 遞增<br /><br /> D = 遞減<br /><br /> NULL = 不適用|  
|**基數**|**int**|資料表中的資料列數，或索引中的唯一值數目。|  
|**頁面**|**int**|用來儲存索引或資料表的頁數。|  
|**FILTER_CONDITION**|**Varchar（128**|
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不會傳回值。|  
  
## <a name="return-code-values"></a>傳回碼值  
 None  
  
## <a name="remarks"></a>備註  
 結果集中的索引會依資料行**NON_UNIQUE**、**類型**、 **INDEX_NAME**和**SEQ_IN_INDEX**以遞增順序顯示。  
  
 叢集化的索引類型會參考依照索引順序來儲存資料表資料的索引。 這對應[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]于叢集索引。  
  
 雜湊的索引類型接受完全相符或範圍搜尋，但模式比對搜尋不會使用索引。  
  
 **sp_statistics**相當於 ODBC 中的**SQLStatistics** 。 傳回的結果會依**NON_UNIQUE**、**類型**、 **INDEX_QUALIFIER**、 **INDEX_NAME**和**SEQ_IN_INDEX**排序。 如需詳細資訊，請參閱[ODBC API 參考](https://go.microsoft.com/fwlink/?LinkId=68323)。  
  
## <a name="permissions"></a>權限  
 需要結構描述的 SELECT 權限。  
  
## <a name="example-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>範例： [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]和[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 下列範例會傳回資料表的`DimEmployee`相關資訊。  
  
```  
-- Uses AdventureWorks  
  
EXEC sp_statistics DimEmployee;  
```  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的目錄預存程式](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

