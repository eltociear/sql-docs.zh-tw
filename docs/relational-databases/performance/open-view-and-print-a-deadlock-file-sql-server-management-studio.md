---
title: 開啟、檢視、列印死結檔案 (SSMS)
ms.custom: seo-dt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- deadlocks [SQL Server], printing files
- deadlocks [SQL Server], opening files
- opening deadlock files
- printing deadlock files
ms.assetid: 5061b13f-2cb7-457a-b8d0-fbd437b510ab
author: julieMSFT
ms.author: jrasnick
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c305d9fd08ffcdd1c4b66d90d834c8f0fb6dead5
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "74165763"
---
# <a name="open-view-and-print-a-deadlock-file-in-sql-server-management-studio-ssms"></a>在 SQL Server Management Studio (SSMS) 開啟、檢視及列印死結檔案

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  當 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 產生死結時，您可以擷取死結資訊並將資訊儲存至檔案。 在儲存死結檔案之後，您可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中開啟檔案，再檢視或列印它。  
  
## <a name="open-and-view-a-deadlock-file"></a>開啟和檢視死結檔案  
  
1. 在  **的 [檔案]** [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 功能表上，指向 [開啟]  ，然後選取 [檔案]  。  
  
2. 在 [開啟檔案]  對話方塊中，從 [檔案類型]  方塊中選取 .xdl 檔案類型。 您現在會有一份只有死結檔案的篩選清單。  
  
## <a name="print-a-deadlock-file"></a>列印死結檔案  
  
1. 在  **的 [檔案]** [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 功能表上，指向 [開啟]  ，然後選取 [檔案]  。  
  
2. 在 [開啟檔案]  對話方塊中，從 [檔案類型]  方塊中選取 .xdl 檔案類型。 您現在會有一份只有死結檔案的篩選清單。  
  
3. 選取您要列印的死結檔案，然後選取 [開啟]  。  
  
4. 在 [檔案]  功能表上，選取 [列印]  。  
  
## <a name="see-also"></a>另請參閱  
 [儲存 Deadlock Graph &#40;SQL Server Profiler&#41;](../../relational-databases/performance/save-deadlock-graphs-sql-server-profiler.md)  
  
  
