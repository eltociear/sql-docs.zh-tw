---
title: 交易 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: 3b41e33a-c1ca-4b2a-9464-312b0ed3ca89
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d54dbe8e3df6e930ebd026e638d0a21f2f88f32e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "73772562"
---
# <a name="transactions"></a>交易
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會實行本機交易支援。 取用者可以使用 Microsoft 分散式交易協調器 (MS DTC) 來使用分散式或協調的交易。 若取用者需要跨多個會話的交易控制[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，Native Client OLE DB 提供者可以聯結由 MS DTC 所起始和維護的交易。  
  
 根據預設， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會使用自動認可交易模式，其中取用者會話上的每個離散動作都是針對實例所[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]組成的完整交易。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者自動認可模式為本機，而自動認可交易絕不會跨越一個以上的會話。  
  
 Native Client OLE DB 提供者會公開**ITransactionLocal**介面，讓取用者在實例的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]單一連接上，明確地使用並隱含啟動交易。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者不支援嵌套的本機交易。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [支援本機交易](../../relational-databases/native-client-ole-db-transactions/supporting-local-transactions.md)  
  
-   [支援分散式交易](../../relational-databases/native-client-ole-db-transactions/supporting-distributed-transactions.md)  
  
-   [&#40;OLE DB 的隔離等級&#41;](../../relational-databases/native-client-ole-db-transactions/isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
