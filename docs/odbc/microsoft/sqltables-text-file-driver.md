---
title: SQLTables （文字檔驅動程式） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLTables
- SQLTables function [ODBC], Text File Driver
ms.assetid: f47fd1a4-5bd8-4b2e-8ae3-e595e49f4f95
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7fcdf9cc41a55d1e529001ae7183ef9fa833363b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "67949019"
---
# <a name="sqltables-text-file-driver"></a>SQLTables (文字檔驅動程式)
> [!NOTE]  
>  本主題提供文字檔驅動程式特定的資訊。 如需此函數的一般資訊，請參閱[ODBC API 參考](../../odbc/reference/syntax/odbc-api-reference.md)底下的適當主題。  
  
|引數|註解|  
|--------------|--------------|  
|*szTableOwner*|*SzTableOwner*的唯一有效引數為 Null，因為沒有任何驅動程式支援擁有者名稱。 當*szTableOwner*設為 Null 時，就會傳回所有資料表。 TABLE_OWNER 資料行中傳回 Null。|  
|*szTableQualifier*|在 [TABLE_QUALIFIER] 資料行中， **SQLTables**會傳回目錄的路徑。|  
|*SzTableType*|"TABLE" 是唯一支援的資料表類型。<br /><br /> 使用文字驅動程式時， **SQLTables**所傳回的檔案清單是由 [ **ODBC 文字設定**] 對話方塊的 [**副檔名] 清單**框中的副檔名所決定。|
