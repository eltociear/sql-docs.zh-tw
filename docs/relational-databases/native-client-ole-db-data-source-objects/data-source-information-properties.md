---
title: 資料來源資訊屬性 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- information properties [OLE DB]
- OLE DB data source properties [SQL Server Native Client]
ms.assetid: 7fd80e47-5bd9-41e2-a3d3-091a7c8c5f2b
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c2b186b1a91724135ca68657d094b99ba6ff3af0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "73775243"
---
# <a name="data-source-information-properties"></a>資料來源資訊屬性
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  在提供者專用的屬性集 DBPROPSET_SQLSERVERDATASOURCEINFO 中，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會定義下列資料來源資訊屬性。  
  
|屬性識別碼|描述|  
|-----------------|-----------------|  
|SSPROP_COLUMNLEVELCOLLATION|類型：VT_BOOL<br /><br /> R/W：讀取<br /><br /> 預設值：VARIANT_TRUE<br /><br /> 描述：用於判斷是否支援資料行定序。<br /><br /> VARIANT_TRUE：支援資料行層級定序。<br /><br /> VARIANT_FALSE：不支援資料行層級定序。|  
|SSPROP_UNICODELCID|類型：VT_I4 R/W：讀取<br /><br /> 描述：Unicode 地區設定識別碼。<br /><br /> 這是用於 Unicode 資料排序的地區設定。|  
|SSPROP_UNICODECOMPARISONSTYLE|類型：VT_I4 R/W：讀取<br /><br /> 描述：Unicode 比較樣式。<br /><br /> 用於 Unicode 資料排序的排序選項。|  
  
 在提供者專屬的屬性集 DBPROPSET_SQLSERVERSTREAM 中，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會定義以下額外的屬性。  
  
|屬性識別碼|描述|  
|-----------------|-----------------|  
|SSPROP_STREAM_XMLROOT|類型：VT_BSTR R/W：讀取/寫入<br /><br /> 描述：FOR XML 查詢的結果可能不是格式正確的文件。 指定此屬性時，'select ... for XML' 查詢的結果會包裝在此屬性提供的根標記中，以傳回格式正確的 XML 文件。 如果在瀏覽器中執行查詢，載入結果時，它可能會使瀏覽器顯示剖析器錯誤。 為避免這個錯誤，SQL ISAPI 支援關鍵字 ROOT。 此關鍵字會對應至 SSPROP_STREAM_XMLROOT 屬性。|  
  
## <a name="see-also"></a>另請參閱  
 [資料來源物件 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
