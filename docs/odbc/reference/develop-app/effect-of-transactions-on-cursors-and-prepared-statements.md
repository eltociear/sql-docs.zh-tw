---
title: 交易對資料指標和已備妥語句的影響 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- committing transactions [ODBC]
- transactions [ODBC], rolling back
- cursors [ODBC], transaction commits or roll backs
- prepared statements [ODBC]
- transactions [ODBC], cursors
ms.assetid: 523e22a2-7b53-4c25-97c1-ef0284aec76e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 83b693922d08f7298d0c5282fe2c7d1c20149d5b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046877"
---
# <a name="effect-of-transactions-on-cursors-and-prepared-statements"></a>對資料指標和已備妥陳述式的交易影響
認可或回復交易對資料指標和存取計畫會有下列影響：  
  
-   所有資料指標都會關閉，而且會刪除該連接上備妥之語句的存取計畫。  
  
-   所有資料指標都會關閉，而且該連接上備妥之語句的存取計畫會保持不變。  
  
-   所有資料指標都會保持開啟，而該連接上備妥之語句的存取計畫會保持不變。  
  
 例如，假設資料來源展現此清單中的第一個行為，這是最嚴格的行為。 現在假設應用程式會執行下列動作：  
  
1.  將認可模式設定為手動認可。  
  
2.  在語句1上建立銷售訂單的結果集。  
  
3.  當使用者反白顯示該順序時，在語句2的銷售訂單中，建立各行的結果集。  
  
4.  當使用者更新一行時，會呼叫**SQLExecute**來執行已在語句3上準備的定點更新語句。  
  
5.  呼叫**SQLEndTran**來認可定位的 update 語句。  
  
 因為資料來源的行為，在步驟5中呼叫**SQLEndTran**會使其關閉語句1和2上的資料指標，並在所有語句上刪除存取計畫。 應用程式必須重新加入語句1和2，以重新建立結果集，並 reprepare 語句3上的語句。  
  
 在自動認可模式中， **SQLEndTran**認可交易以外的函數：  
  
-   **SQLExecute**或**SQLExecDirect**在上述範例中，在步驟4中對**SQLExecute**的呼叫會認可交易。 這會導致資料來源關閉語句1和2上的資料指標，並在該連接上的所有語句上刪除存取計畫。  
  
-   在上述範例中的**SQLBulkOperations**或**SQLSetPos** ，假設在步驟4中，應用程式會使用語句2上的 SQL_UPDATE 選項呼叫**SQLSetPos** ，而不是在語句3上執行定位的 UPDATE 語句。 這會認可交易，並使資料來源關閉語句1和2上的資料指標，並捨棄該連接上的所有存取計畫。  
  
-   **SQLCloseCursor**在上述範例中，假設當使用者反白顯示不同的銷售訂單時，應用程式會先在語句2上呼叫**SQLCloseCursor** ，再建立新銷售訂單的行結果。 **SQLCloseCursor**的呼叫會認可建立程式列結果集的**SELECT**語句，並使資料來源在語句1上關閉游標，然後捨棄該連接上的所有存取計畫。  
  
 應用程式（尤其是以螢幕為基礎的應用程式，使用者在其中滾動結果集和更新或刪除資料列）必須小心撰寫此行為的程式碼。  
  
 若要判斷資料來源在認可或回復交易時的行為，應用程式會使用 SQL_CURSOR_COMMIT_BEHAVIOR 和 SQL_CURSOR_ROLLBACK_BEHAVIOR 選項來呼叫**SQLGetInfo** 。
