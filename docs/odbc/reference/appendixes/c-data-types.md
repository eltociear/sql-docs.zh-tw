---
title: C 資料類型 |Microsoft Docs
ms.custom: ''
ms.date: 07/12/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], C data types
- C data types [ODBC], about C data types
- C data types [ODBC]
- C buffers [ODBC]
ms.assetid: b681d260-3dbb-47df-a616-4910d727add7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9fe4383e397c0fd06197be2ff25e6dbb876f6c0b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037776"
---
# <a name="c-data-types"></a>C 資料類型
ODBC C 資料類型表示用來在應用程式中儲存資料之 C 緩衝區的資料類型。  
  
 所有的驅動程式都必須支援所有 C 資料類型。 這是必要的，因為所有的驅動程式都必須支援其支援的 SQL 類型所能轉換的所有 C 類型，而且所有的驅動程式都至少支援一個字元的 SQL 類型。 因為字元 SQL 類型可以在所有 C 類型之間來回轉換，所以所有的驅動程式都必須支援所有 C 類型。  
  
 C 資料類型是在具有*TargetType*引數的**SQLBindCol**和**SQLGetData**函式中指定，而在**SQLBindParameter**函式中是使用*ValueType*引數來指定。 您也可以藉由呼叫**SQLSetDescField**來設定 ARD 或 APD 的 SQL_DESC_CONCISE_TYPE 欄位，或呼叫具有*類型*引數的**SQLSetDescRec** （如有需要，則為*子類型*引數），並將*DescriptorHandle*引數設定為 ARD 或 APD 的控制碼，藉此指定。  
  
 下表列出 C 資料類型的有效類型識別碼。 資料表也會列出對應于每個識別碼的 ODBC C 資料類型，以及此資料類型的定義。  
  
|C 類型識別碼|ODBC C typedef|C 類型|  
|-----------------------|--------------------|------------|  
|SQL_C_CHAR|SQLCHAR|unsigned char *|  
|SQL_C_WCHAR|SQLWCHAR|wchar_t *|  
|SQL_C_SSHORT [j]|SQLSMALLINT|short int|  
|SQL_C_USHORT [j]|SQLUSMALLINT|不帶正負號的短整數|  
|SQL_C_SLONG [j]|SQLINTEGER|long int|  
|SQL_C_ULONG [j]|SQLUINTEGER|不帶正負號的 long int|  
|SQL_C_FLOAT|SQLREAL|FLOAT|  
|SQL_C_DOUBLE|SQLDOUBLE、SQLFLOAT|double|  
|SQL_C_BIT|SQLCHAR|不帶正負號的字元|  
|SQL_C_STINYINT [j]|SQLSCHAR|signed char|  
|SQL_C_UTINYINT [j]|SQLCHAR|不帶正負號的字元|  
|SQL_C_SBIGINT|SQLBIGINT|_int64 [h]|  
|SQL_C_UBIGINT|SQLUBIGINT|不帶正負號的 _int64 [h]|  
|SQL_C_BINARY|SQLCHAR|unsigned char *|  
|SQL_C_BOOKMARK [i]|書簽|不帶正負號的 long int [d]|  
|SQL_C_VARBOOKMARK|SQLCHAR|unsigned char *|  
|所有 C 間隔資料類型|SQL_INTERVAL_STRUCT|請參閱本附錄稍後的「 [C 間隔結構](../../../odbc/reference/appendixes/c-interval-structure.md)」一節。|  
  
 **C 類型識別碼**SQL_C_TYPE_DATE [C]  
  
 **ODBC C typedef**SQL_DATE_STRUCT  
  
 **C 類型**  
  
```  
struct tagDATE_STRUCT {  
   SQLSMALLINT year;  
   SQLUSMALLINT month;  
   SQLUSMALLINT day;    
} DATE_STRUCT;[a]  
```  
  
 **C 類型識別碼**SQL_C_TYPE_TIME [C]  
  
 **ODBC C typedef**SQL_TIME_STRUCT  
  
 **C 類型**  
  
```  
struct tagTIME_STRUCT {  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
} TIME_STRUCT;[a]  
```  
  
 **C 類型識別碼**SQL_C_TYPE_TIMESTAMP [C]  
  
 **ODBC C typedef**SQL_TIMESTAMP_STRUCT  
  
 **C 類型**  
  
```  
struct tagTIMESTAMP_STRUCT {  
   SQLSMALLINT year;  
   SQLUSMALLINT month;  
   SQLUSMALLINT day;  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
   SQLUINTEGER fraction;[b]   
} TIMESTAMP_STRUCT;[a]  
```  
  
 **C 類型識別碼**SQL_C_NUMERIC  
  
 **ODBC C typedef**SQL_NUMERIC_STRUCT  
  
 **C 類型**  
  
```  
struct tagSQL_NUMERIC_STRUCT {  
   SQLCHAR precision;  
   SQLSCHAR scale;  
   SQLCHAR sign[g];  
   SQLCHAR val[SQL_MAX_NUMERIC_LEN];[e], [f]   
} SQL_NUMERIC_STRUCT;  
```  
  
 **C 類型識別碼**SQL_C_GUID  
  
 **ODBC C typedef**SQLGUID  
  
 **C 類型**  
  
```  
struct tagSQLGUID {  
   DWORD Data1;  
   WORD Data2;  
   WORD Data3;  
   BYTE Data4[8];  
} SQLGUID;[k]  
```  
  
 [a] 日期時間 C 資料類型中 year、month、day、hour、minute 和 second 欄位的值必須符合西曆的條件約束。 （請參閱本附錄稍後[的西曆條件約束](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)）。  
  
 [b] [分數] 欄位的值是一秒的 billionths 數，範圍是從0到999999999（1小於1000000000）。 例如，[分數] 欄位的值為 [500000000]、[萬分之一秒（1毫秒）] 為1000000、第二個百萬分之一秒（一微秒）為1000，而十億分之一秒（一個毫微秒）為1。  
  
 [c] In ODBC 2。*x*，C 日期、時間和時間戳記資料類型為 SQL_C_DATE、SQL_C_TIME 和 SQL_C_TIMESTAMP。  
  
 [d] ODBC 3.x*應用程式*應該使用 SQL_C_VARBOOKMARK，而不是 SQL_C_BOOKMARK。 當 ODBC*3.x 應用程式*與 odbc 2 搭配使用時。*x* *驅動程式，ODBC 3.X 驅動程式*管理員會將 SQL_C_VARBOOKMARK 對應到 SQL_C_BOOKMARK。  
  
 [e] 數位會儲存在 SQL_NUMERIC_STRUCT 結構的*val*欄位中，做為縮放整數，以位元組為單位（最大的位元組是最不重要的位元組）。 例如，數位10.001 基底10，小數位數為4，會調整為100010的整數。 因為這是以十六進位格式186AA，SQL_NUMERIC_STRUCT 中的值會是 "AA 86 01 00 00 .。。00 "，其中包含由 SQL_MAX_NUMERIC_LEN **#define**所定義的位元組數目。  
  
 如需**SQL_NUMERIC_STRUCT**的詳細資訊，請參閱[做法：使用 SQL_NUMERIC_STRUCT 抓取數值資料](retrieve-numeric-data-sql-numeric-struct-kb222831.md)。  
  
 [f] SQL_C_NUMERIC 資料類型的有效位數和小數位數位段，會 areused 應用程式的輸入，以及從驅動程式輸出到應用程式。 當驅動程式將數值寫入 SQL_NUMERIC_STRUCT 時，它會使用自己的驅動程式專屬預設值做為 [*精確度*] 欄位的值，而且會使用 [*尺規*] 欄位之應用程式描述項的 [SQL_DESC_SCALE] 欄位中的值（預設為0）。 應用程式可以藉由設定應用程式描述項的 SQL_DESC_PRECISION 和 SQL_DESC_SCALE 欄位，為有效位數和小數位數提供自己的值。  
  
 [g] 正負號欄位是1，如果是正數，則為0（如果是負數）。  
  
 [h] 部分編譯器可能不會提供 _int64。  
  
 [i] _SQL_C_BOOKMARK 已在 ODBC 3.x 中被*取代。*  
  
 [j] 已簽署和不帶正負號的類型，已在 ODBC 中取代 _SQL_C_SHORT、SQL_C_LONG 和 SQL_C_TINYINT： SQL_C_SSHORT 和 SQL_C_USHORT、SQL_C_SLONG 和 SQL_C_ULONG，以及 SQL_C_STINYINT 和 SQL_C_UTINYINT。 ODBC 3 *. x*驅動程式，應該與 odbc 2 搭配使用。*x*應用程式應該支援 SQL_C_SHORT、SQL_C_LONG 和 SQL_C_TINYINT，因為在呼叫它們時，驅動程式管理員會將它們傳遞至驅動程式。  
  
 [k] SQL_C_GUID 只能轉換成 SQL_CHAR 或 SQL_WCHAR。  
  
 本章節包含下列主題。  
  
-   [64 位元整數結構](../../../odbc/reference/appendixes/64-bit-integer-structures.md)  
  
## <a name="see-also"></a>另請參閱  
 [ODBC 中的 C 資料類型](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)
