---
title: 設定資料指標選項（ODBC） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], options
ms.assetid: 0e72b48a-fc5a-4656-8cf5-39f57d8c1565
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 50e1a6733976dee4dc6a7d429d5940bc1a08ea84
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "73781320"
---
# <a name="set-cursor-options-odbc"></a>設定資料指標選項 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  若要設定資料指標選項，請呼叫[SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)來設定或[SQLGetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md) ，以取得控制資料指標行為的語句選項。  
  
|*Attribute*|指定|  
|-----------------|---------------|  
|SQL_ATTR_CURSOR_TYPE|順向、靜態、動態或索引鍵集驅動的資料指標類型|  
|SQL_ATTR_CONCURRENCY|唯讀、鎖定、開放式 (使用時間戳記) 或開放式 (使用值) 的並行控制選項|  
|SQL_ATTR_ROW_ARRAY_SIZE|每次提取中擷取的資料列數目|  
|SQL_ATTR_CURSOR_SENSITIVITY|顯示或不顯示其他連接對資料指標資料列所做之更新的資料指標|  
|SQL_ATTR_CURSOR_SCROLLABLE|可以前後捲動的資料指標|  
  
 這些屬性 (順向、唯讀、資料列集大小為 1) 的預設值不會使用伺服器資料指標。 若要使用伺服器資料指標，至少其中一個屬性必須設定為預設值以外的值，而且所執行的陳述式必須為單一 SELECT 陳述式或包含單一 SELECT 陳述式的預存程序。 使用伺服器資料指標時，SELECT 陳述式無法使用伺服器資料指標不支援的子句：COMPUTE、COMPUTE BY、FOR BROWSE 和 INTO。  
  
 您可以透過設定 SQL_ATTR_CURSOR_TYPE 和 SQL_ATTR_CONCURRENCY，或是設定 SQL_ATTR_CURSOR_SENSITIVITY 和 SQL_ATTR_CURSOR_SCROLLABLE，控制所使用的資料指標類型。 您不應該混合使用這兩種指定資料指標行為的方法。  
  
## <a name="example"></a>範例  
 下列範例會配置陳述式控制代碼、使用資料列版本設定開放式並行存取來設定動態資料指標類型，然後執行 SELECT。  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER)SQL_CURSOR_DYNAMIC, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CONCURRENCY, SQLPOINTER)SQL_CONCUR_ROWVER, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, SELECT au_lname FROM authors", SQL_NTS);  
```  
  
## <a name="example"></a>範例  
 下列範例會配置陳述式控制代碼、設定可捲動的感應式資料指標，然後執行 SELECT。  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
  
// Set the cursor options and execute the statement.  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SCROLLABLE, SQLPOINTER)SQL_SCROLLABLE, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SENSITIVITY, SQLPOINTER)SQL_INSENSITIVE, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, select au_lname from authors", SQL_NTS);  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行查詢 &#40;ODBC&#41;的使用說明主題](../../../relational-databases/native-client-odbc-how-to/execute-queries/executing-queries-how-to-topics-odbc.md)  
  
  
