---
title: 以檔案為基礎的驅動程式 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- file-based drivers [ODBC]
- ODBC architecture [ODBC], drivers
- drivers [ODBC], file-based drivers
ms.assetid: d92e0c5c-d176-4282-bbe1-d449e2223d50
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 803da51c8507faa47f92b295d3749f00317bc413
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "67915380"
---
# <a name="file-based-drivers"></a>以檔案為基礎的驅動程式
以檔案為基礎的驅動程式會搭配資料來源使用，例如，未提供獨立資料庫引擎供驅動程式使用的 dBASE。 這些驅動程式會直接存取實體資料，而且必須執行資料庫引擎來處理 SQL 語句。 以檔案為基礎的驅動程式中的資料庫引擎是標準做法，它會執行最低 SQL 一致性層級所定義的 ODBC SQL 子集;如需此一致性層級中的 SQL 語句清單，請參閱[附錄 C： Sql 文法](../../odbc/reference/appendixes/appendix-c-sql-grammar.md)。  
  
 比較以檔案為基礎的驅動程式和以 DBMS 為基礎的驅動程式時，因為資料庫引擎元件較難撰寫，所以不太複雜，因為沒有任何網路元件，而且功能較低，因為少數人員有寫入資料庫的時間引擎與資料庫公司所產生的功能強大。  
  
 下圖顯示以檔案為基礎的驅動程式的兩個不同設定，其中一個資料位於本機，另一個則位於網路檔案伺服器上。  
  
 ![以檔案&#45;為基礎的驅動程式的兩個配置](../../odbc/reference/media/pr06.gif "pr06")
