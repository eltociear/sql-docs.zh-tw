---
title: AbsolutePage、PageCount 和 PageSize 屬性範例（VB） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- PageCount property [ADO], Visual Basic example
- AbsolutePage property [ADO], Visual Basic example
- PageSize property [ADO], Visual Basic example
ms.assetid: 5aaada64-5115-4adc-8668-827348f32566
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ad832a1e0028005ff1893df43fbadcd078bc2859
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "67921858"
---
# <a name="absolutepage-pagecount-and-pagesize-properties-example-vb"></a>AbsolutePage、PageCount 和 PageSize 屬性範例（VB）
```  
'BeginAbsolutePageVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    'recordset and connection variables  
    Dim rstEmployees As ADODB.Recordset  
    Dim Cnxn As ADODB.Connection  
    Dim strCnxn As String  
    Dim strSQL As String  
        'record variables  
    Dim strMessage As String  
    Dim intPage As Integer  
    Dim intPageCount As Integer  
    Dim intRecord As Integer  
  
    'Open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    ' Open employee recordset  
    ' Use client cursor to enable AbsolutePosition property  
    Set rstEmployees = New ADODB.Recordset  
    strSQL = "employee"  
    rstEmployees.Open strSQL, strCnxn, adUseClient, adLockReadOnly, adCmdTable  
  
    ' Display names and hire dates, five records at a time  
    rstEmployees.PageSize = 5  
    intPageCount = rstEmployees.PageCount  
    For intPage = 1 To intPageCount  
        rstEmployees.AbsolutePage = intPage  
        strMessage = ""  
        For intRecord = 1 To rstEmployees.PageSize  
            strMessage = strMessage & _  
                rstEmployees!fname & " " & _  
                rstEmployees!lname & " " & _  
                rstEmployees!hire_date & vbCr  
            rstEmployees.MoveNext  
            If rstEmployees.EOF Then Exit For  
        Next intRecord  
        MsgBox strMessage  
    Next intPage  
  
    ' clean up  
    rstEmployees.Close  
    Cnxn.Close  
    Set rstEmployees = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rstEmployees Is Nothing Then  
        If rstEmployees.State = adStateOpen Then rstEmployees.Close  
    End If  
    Set rstEmployees = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndAbsolutePageVB  
```  
  
## <a name="see-also"></a>另請參閱  
 [AbsolutePage 屬性（ADO）](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [PageCount 屬性（ADO）](../../../ado/reference/ado-api/pagecount-property-ado.md)   
 [PageSize 屬性（ADO）](../../../ado/reference/ado-api/pagesize-property-ado.md)   
 [Recordset 物件 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
