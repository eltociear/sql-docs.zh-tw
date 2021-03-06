---
title: SQL 目的地編輯器（連線管理員頁面） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdestadapter.connection.f1
helpviewer_keywords:
- SQL Server Destination Editor
ms.assetid: 423e1654-54af-47c6-ab6f-98670534557d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d3bffc98a14c1a8bc672e9f15a4bad8b6f5a7dbe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "66055413"
---
# <a name="sql-destination-editor-connection-manager-page"></a>SQL 目的地編輯器 (連接管理員頁面)
  使用 **[SQL 目的地編輯器]** 對話方塊的 **[連接管理員]** 頁面，即可指定資料來源資訊並預覽結果。 目的地[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]會將資料載入資料庫中的[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]資料表或 views。  
  
 若要深入了解 SQL Server 目的地，請參閱＜ [SQL Server Destination](data-flow/sql-server-destination.md)＞。  
  
## <a name="options"></a>選項。  
 **OLE DB 連線管理員**  
 從清單中選取現有的連接，或按一下 [新增]**** 來建立新的連接。  
  
 **新增**  
 使用 [設定 OLE DB 連接管理員]**** 對話方塊來建立新的連接。  
  
 **使用資料表或視圖**  
 從清單中選取現有的資料表或檢視，或按一下 [新增]**** 來建立新的連接。  
  
 **新增**  
 使用 [建立資料表]**** 對話方塊建立新的資料表。  
  
> [!NOTE]  
>  當您按一下****[新增[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ] 時，會根據連接的資料來源產生預設的 CREATE TABLE 語句。 這個預設 CREATE TABLE 陳述式將不會包含 FILESTREAM 屬性，即使來源資料表包含有宣告 FILESTREAM 屬性的資料行亦然。 若要執行具有 FILESTREAM 屬性的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 元件，請先在目的地資料庫上實作 FILESTREAM 儲存體。 然後在 **[建立資料表]** 對話方塊中，將 FILESTREAM 屬性加入至 CREATE TABLE 陳述式。 如需詳細資訊，請參閱[二進位大型物件 &#40;Blob&#41; 資料 &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md)。  
  
 **預覽**  
 使用 [預覽查詢結果]**** 對話方塊來預覽結果。 預覽最多可顯示 200 個資料列。  
  
## <a name="see-also"></a>另請參閱  
 [Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [[SQL 目的地編輯器 &#40;對應] 頁面&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md)   
 [[SQL 目的地編輯器] &#40;[Advanced] 頁面&#41;](../../2014/integration-services/sql-destination-editor-advanced-page.md)   
 [使用 SQL Server 目的地來大量載入資料](data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  
