---
title: 什麼是資料指標？ | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], about cursors
ms.assetid: 596eb4b6-c22f-4cde-b23f-172dd66c3161
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7d903b2a5f971d0b6c7114a9e5229bff6133d743
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "67923451"
---
# <a name="what-is-a-cursor"></a>什麼是資料指標？
關聯式資料庫中的作業會針對完整的資料列集運作。 由 SELECT 陳述式所傳回的資料列集包括所有滿足陳述式 WHERE 子句之條件的資料列。 由陳述式傳回的完整資料列稱為結果集。 應用程式（特別是互動式和線上）不一定能有效地將整個結果集當做一個單位來運作。 這些應用程式需要一個機制，一次運用一個資料列或小型資料列區塊。 資料指標就是一種結果集的擴充，提供此種機制。  
  
 資料指標是由資料指標程式庫所執行。 資料指標程式庫是一種軟體，通常會實作為資料庫系統或資料存取 API 的一部分，用來管理從資料來源傳回的資料屬性（結果集）。 這些屬性包括並行管理、結果集中的位置、傳回的資料列數目，以及您是否可以透過結果集（捲動）向前或向後移動（或兩者）。  
  
 資料指標會持續追蹤結果集中的位置，並可讓您針對結果集執行多個作業的資料列，不論是否傳回原始資料表。 換句話說，在概念上，資料指標會根據資料庫內的資料表傳回結果集。 資料指標會命名為，因為它會指出結果集中的目前位置，就像電腦螢幕上的游標指出目前的位置一樣。  
  
 請務必熟悉資料指標的概念，再繼續瞭解其在 ADO 中的用法細節。  
  
 使用資料指標，您可以：  
  
-   指定結果集中特定資料列的位置。  
  
-   根據目前的結果集位置，抓取一列或資料列區塊。  
  
-   修改結果集中目前位置的資料列中的資料。  
  
-   針對其他使用者所做的資料變更，定義不同層級的敏感度。  
  
 例如，假設有一個應用程式會向潛在購買者顯示可用產品清單。 購買者會滾動清單，以查看產品詳細資料和成本，最後選取要購買的產品。 清單的其餘部分會發生額外的滾動和選取。 就購買者而言，產品一次只會出現一個，但應用程式會使用可滾動的資料指標，在結果集上向上和向下流覽。  
  
 您可以透過各種不同的方式來使用資料指標：  
  
-   完全沒有資料列。  
  
-   包含單一資料表中的部分或所有資料列。  
  
-   包含來自邏輯聯結資料表的部分或所有資料列。  
  
-   唯讀或可更新的資料指標或欄位層級。  
  
-   作為順向或完全可滾動。  
  
-   使用位於伺服器上的資料指標索引鍵集。  
  
-   對基礎資料表所做的影響，其他應用程式（例如成員資格、排序、插入、更新和刪除）所造成。  
  
-   伺服器或用戶端上的現有。  
  
 唯讀資料指標可協助使用者流覽結果集，而讀取/寫入資料指標則可以執行個別的資料列更新。 您可以使用指向基表資料列的索引鍵集來定義複雜的資料指標。 雖然某些資料指標在正向方向是唯讀的，但其他資料指標可以來回移動，並根據其他應用程式對資料庫所做的變更，提供結果集的動態重新整理。  
  
 並非所有應用程式都需要使用資料指標來存取或更新資料。 有些查詢只是不需要使用資料指標來進行直接的資料列更新。 游標應該是您選擇用來抓取資料的最後一項技巧，然後您應該選擇可能最小的影響資料指標。 當您使用預存程式建立結果集時，無法使用 cursor edit 或 update 方法來更新結果集。  
  
## <a name="concurrency"></a>並行  
 在某些多使用者應用程式中，向終端使用者呈現的資料非常重要。 這類系統的典型範例是航空公司保留系統，其中許多使用者可能會在特定航班（也就是單一記錄）爭用相同的基座。 在這樣的情況下，應用程式設計必須處理單一記錄的並行作業。  
  
 在其他應用程式中，並行處理並不重要。 在這種情況下，在隨時保持最新資料時所需的費用無法對齊。  
  
## <a name="position"></a>位置  
 資料指標也會持續追蹤結果集內的目前位置。 將游標位置視為目前記錄的指標，類似于陣列索引指向陣列中該特定位置之值的方式。  
  
## <a name="scrollability"></a>可捲動性  
 您的應用程式所採用的資料指標類型也會影響在結果集的資料列中向前和向後移動的能力;這有時稱為捲動。 透過結果集向前*和*向後移動的能力會增加資料指標的複雜度，因此執行的成本會更高。 基於這個理由，您應該只在必要時，才要求具有這種功能的資料指標。
