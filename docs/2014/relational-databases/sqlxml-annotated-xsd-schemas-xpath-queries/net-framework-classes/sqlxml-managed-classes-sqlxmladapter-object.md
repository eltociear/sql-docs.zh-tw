---
title: SqlXmlAdapter 物件（SQLXML Managed 類別） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- void Update(DataSet ds) method
- SqlXmlAdapter object
- void Fill(DataSet ds) method
- SQLXML Managed Classes, SqlXmlAdapter object
- Managed Classes [SQLXML], SqlXmlAdapter object
ms.assetid: 0a16eddf-fc26-4d92-82d4-359b5fb905d5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b339e67b07ddb4168f9922c22e620eb2fa10d85e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "66014925"
---
# <a name="sqlxmladapter-object-sqlxml-managed-classes"></a>SqlXmlAdapter 物件 (SQLXML Managed 類別)
  這個物件會提供一些方法，方便您與 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 中的資料集進行互動。 如需實用範例，請參閱[存取 .Net 環境中的 SQLXML 功能](accessing-sqlxml-functionality-in-the-net-environment.md)。  
  
 SqlXmlAdapter 物件支援下列方法：  
  
 void Fill （資料集 ds）  
 將 .NET Framework 中的資料集填滿從 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中擷取的 XML 資料。  
  
 void 更新（資料集 ds）  
 從資料集中的資料，將更新套用至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的記錄。  
  
 SqlXmlAdapter 物件支援下列函數：  
  
```  
public SqlXmlAdapter(SqlXmlCommand  cmd)   
  
public SqlXmlAdapter(  
                     string commandText,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                      )   
  
public SqlXmlAdapter(  
                     Stream commandStream,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                     )   
```  
  
## <a name="see-also"></a>另請參閱  
 [SqlXmlCommand 物件 &#40;SQLXML Managed 類別&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)   
 [SqlXmlParameter 物件 &#40;SQLXML Managed 類別&#41;](sqlxml-managed-classes-sqlxmlparameter-object.md)  
  
  
