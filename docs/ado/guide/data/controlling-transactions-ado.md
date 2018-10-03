---
title: Управление транзакциями (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- transactions [ADO]
ms.assetid: 189240e8-3ffa-4024-81a9-c6cb5d17eee0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8059df4275a336d084144a73910cdef99abf9467
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47603624"
---
# <a name="controlling-transactions-ado"></a>Управление транзакциями (ADO)
ADO поддерживает обработку в рамках подключения с помощью транзакций **BeginTrans**, **CommitTrans**, и **RollbackTrans** методы  **Подключение** объекта. В следующем фрагменте кода показано общее представление о реализации обработки транзакций в ADO.  
  
```  
Const DS = "MySqlServer"  
Const DB = "Northwind"  
Const DP = "SQLOLEDB"  
  
Dim oConn As ADODB.Connection  
Dim oRs As ADODB.Recordset  
Dim sConn As String  
  
sConn = "Provider=" & DP & _  
          ";Data Source=" & DS & _  
          ";Initial Catalog=" & DB & _  
          ";Integrated Security=SSPI;"  
  
sSQL = "SELECT ProductID, ProductName FROM Products"  
  
Set oConn = New ADODB.Connection  
oConn.Open sConn  
  
' Create and Open the Recordset object.  
Set oRs = New ADODB.Recordset  
oRs.Open sSQL, oConn, adOpenStatic, adLockOptimistic, adCmdText  
  
If oRs.RecordCount > 1 Then  
  
    oRs.MoveFirst  
    Id1 = oRs("ProductID")  
    Name1 = oRs("ProductName")  
    oRs.MoveNext  
    Id2 = oRs("ProductID")  
    Name2 = oRs("ProductName")  
  
    q = "Switch ID's of " & Name1 & " and " & Name2 & "?"  
    If MsgBox(q, vbYesNo) = vbYes Then  
        oRs.MoveFirst  
        oRs("ProductName") = Name2  
        oRs.Update  
  
        oRs.MoveNext  
        oRs("ProductName") = Name1  
        oRs.Update  
  
        If MsgBox("Save changes?", vbYesNo) = vbYes Then  
  
        Else  
  
        End If  
    End If  
  
End If  
  
oRs.Close  
oConn.Close  
```  
  
 Здесь обработки транзакций используется для обеспечения этих двух записей будут обновляться, как одну единицу работы, и что названия двух продуктов находятся взаимозаменяемыми или вообще не изменяется.  
  
 Присоединяйтесь к обсуждению обработки транзакций см. в разделе [обновление и сохранение данных](../../../ado/guide/data/updating-and-persisting-data.md).
