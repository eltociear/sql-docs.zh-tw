---
title: 'Record （Visual C++ #import 的語法索引） |Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
dev_langs:
- C++
helpviewer_keywords:
- 'Record collection [ADO], Visual C++ syntax index with #import'
ms.assetid: ba6dd186-9552-4b6c-960b-3ee6cd589afd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f39e5802e08fd47f5442cd7d394b6589ce56c597
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "67917349"
---
# <a name="record-visual-c-syntax-index-with-import"></a>Record （使用 #import Visual C++ 語法索引）
## <a name="methods"></a>方法  
  
```  
HRESULT Cancel( );  
  
HRESULT Close( );  
  
_bstr_t CopyRecord( _bstr_t Source, _bstr_t Destination,  
    _bstr_t     UserName, _bstr_t Password, enum CopyRecordOptionsEnum  
    Options,     VARIANT_BOOL Async );  
  
HRESULT DeleteRecord( _bstr_t Source, VARIANT_BOOL Async );  
  
_RecordsetPtr GetChildren( );  
  
_bstr_t MoveRecord( _bstr_t Source, _bstr_t Destination,  
    _bstr_t     UserName, _bstr_t Password, enum MoveRecordOptionsEnum  
    Options,     VARIANT_BOOL Async );  
  
HRESULT Open( const _variant_t & Source, const _variant_t  
&     ActiveConnection, enum ConnectModeEnum Mode, enum  
    RecordCreateOptionsEnum CreateOptions, enum RecordOpenOptionsEnum  
    Options, _bstr_t UserName, _bstr_t Password );  
```  
  
## <a name="properties"></a>屬性  
  
```  
_variant_t GetActiveConnection( );  
void PutActiveConnection( _bstr_t pvar );  
void PutRefActiveConnection( struct _Connection * pvar );  
  
FieldsPtr GetFields( );  
__declspec(property(get=GetFields)) FieldsPtr Fields;  
  
enum ConnectModeEnum GetMode( );  
void PutMode( enum ConnectModeEnum pMode );  
__declspec(property(get=GetMode,put=PutMode)) enum ConnectModeEnum Mode;  
  
_bstr_t GetParentURL( );  
__declspec(property(get=GetParentURL)) _bstr_t ParentURL;  
  
enum RecordTypeEnum GetRecordType( );  
__declspec(property(get=GetRecordType)) enum RecordTypeEnum  
    RecordType;  
  
_variant_t GetSource( );  
void PutSource( _bstr_t pvar );  
void PutRefSource( IDispatch * pvar );  
  
enum ObjectStateEnum GetState( );  
__declspec(property(get=GetState)) enum ObjectStateEnum State;  
```  
  
## <a name="see-also"></a>另請參閱  
 [Record 物件 (ADO)](../../../ado/reference/ado-api/record-object-ado.md)
