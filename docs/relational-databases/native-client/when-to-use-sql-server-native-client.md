---
title: 使用 SQL Server Native Client 的時機 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- SQLNCLI, about SQL Server Native Client
- data access [SQL Server Native Client], about SQL Server Native Client
ms.assetid: 08f18b36-209d-4cf7-9623-ebc61859a91d
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3b8d956d8e27a9511e5f9d6cb2ee555110210760
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "73759465"
---
# <a name="when-to-use-sql-server-native-client"></a>使用 SQL Server Native Client 的時機
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 是用來存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫資料的一種技術。  如需不同資料存取技術的討論內容，請參閱 [Data Access Technologies Road Map](https://go.microsoft.com/fwlink/?LinkID=179186) (資料存取技術藍圖)  
  
 決定是否要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 當做應用程式的資料存取技術時，您應該考慮許多因素。  
  
 對於新的應用程式而言，如果您正在使用 Microsoft Visual C# 或 Visual Basic 等 Managed 程式語言，而且需要存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的新功能，則應該使用 .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (屬於 .NET Framework 的一部分)。  
  
 如果您正在開發以 COM 為基礎的應用程式，而且需要存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所導入的新功能，則應該使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client。 如果您不需要存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的新功能，可以繼續使用 Windows Data Access Components (WDAC)。  
  
 對於現有的 OLE DB 和 ODBC 應用程式而言，主要的問題在於您是否需要存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的新功能。 如果您有一個不需要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之新功能的完整應用程式，就可以繼續使用 WDAC。 但是，如果您需要存取這些新功能（例如[xml 資料類型](../../t-sql/xml/xml-transact-sql.md)），您應該使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client。  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 和 MDAC 都可使用資料列版本設定來支援讀取認可的交易隔離，但是只有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 可支援快照集交易隔離  (在程式設計的詞彙中，含有資料列版本設定的讀取認可交易隔離與讀取認可的交易相同)。  
  
 如需 Native Client 與 MDAC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之間差異的詳細資訊，請參閱將[應用程式更新為從 MDAC SQL Server Native Client](../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Native Client 程式設計](../../relational-databases/native-client/sql-server-native-client-programming.md)   
 [ODBC 的使用說明主題](../../relational-databases/native-client-odbc-how-to/odbc-how-to-topics.md)   
 [OLE DB 的使用說明主題](../../relational-databases/native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  
