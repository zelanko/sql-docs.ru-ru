---
title: "Распознавание и разрешение конфликтов | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- conflicts [ADO], detecting and resolving
- ADO, detecting and resolving conflicts
ms.assetid: b28fdd26-c1a4-40ce-a700-2b0c9d201514
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 23ed1396e76f0339c2fdda92501aca751d2d4559
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="detecting-and-resolving-conflicts"></a>Обнаружение и разрешение конфликтов
Если вы имеете дело с набором записей в режиме интерпретации, есть гораздо меньше вероятность проблем с параллелизмом, возникает. С другой стороны, если приложение использует пакетного режима обновления, может существовать хорошее вероятность того, что один пользователь изменит записи перед сохранением изменений, внесенных другим пользователем, редактирования и ту же запись. В этом случае требуется приложение для правильной обработки конфликтов. Он может быть нежелательным, последнего пользователя для отправки обновления на сервер «побеждает.» Или вы можете позволить последнему пользователю, чтобы решить, какие обновления следует приоритет, предоставив ему возможность выбора из двух конфликтующие значения.  
  
 В любом случае ADO предоставляет свойства UnderlyingValue и OriginalValue объект поля для обработки этих типов конфликтов. Эти свойства можно используете в сочетании с методом повторной синхронизации и свойство фильтра набора записей.  
  
## <a name="remarks"></a>Remarks  
 Когда ADO обнаруживает конфликт при пакетных обновлениях, предупреждение будет добавляться в коллекцию ошибок. Поэтому всегда следует проверять наличие ошибок сразу после вызова BatchUpdate, а если найти их, начать тестирование в предположении, что вы столкнулись с конфликтом. Первым шагом является установка свойства фильтра для набора записей, равным adFilterConflictingRecords. Это ограничивает доступ к представлению в наборе записей только те записи, которые конфликтуют. Если свойство RecordCount равна нулю после выполнения этого шага, вы знаете, что она была вызвана каким-то отличное от конфликт.  
  
 При вызове BatchUpdate ADO и поставщика Создание инструкций SQL для выполнения обновлений в источнике данных. Помните, что некоторые источники данных ограничения, на которых могут использоваться типы столбцов в предложении WHERE.  
  
 Затем вызовите метод повторной синхронизации для объекта Recordset с аргументом AffectRecords равным adAffectGroup и ResyncValues аргумента равным adResyncUnderlyingValues. Повторная синхронизация метод обновляет данные в текущем объекте набора записей из базы данных. С помощью adAffectGroup, дает гарантию того, что только записи, отображается по текущему фильтру, параметр, то есть, конфликтующих записей, синхронизируются с базой данных. Это может сделать значительную разницу в производительности при работе с большой записей. Параметр adResyncUnderlyingValues ResyncValues аргумент при вызове повторной синхронизации позволяет гарантировать, что свойство UnderlyingValue будет содержать (конфликт) значение из базы данных, что свойство Value будет поддерживать значения, введенные пользователем, и что OriginalValue свойство будет содержать исходное значение для поля (значение, которое было до внесения последнего успешного вызова UpdateBatch). Затем эти значения можно использовать для разрешения конфликта программными средствами или требовать от пользователя, выберите значение, которое будет использоваться.  
  
 Этот способ показан в следующем примере кода. Конфликт искусственно создается с помощью отдельных записей для изменения значения в базовой таблице, перед вызовом UpdateBatch.  
  
```  
'BeginConflicts  
    strConn = "Provider=SQLOLEDB;Initial Catalog=Northwind;" & _  
              "Data Source=MySQLServer;Integrated Security=SSPI;"  
  
    strSQL = "SELECT * FROM Shippers WHERE ShipperID = 2"  
  
    'Open Rs and change a value  
    Set objRs1 = New ADODB.Recordset  
    Set objRs2 = New ADODB.Recordset  
    objRs1.CursorLocation = adUseClient  
    objRs1.Open strSQL, strConn, adOpenStatic, adLockBatchOptimistic, adCmdText  
    objRs1("Phone") = "(111) 555-1111"  
  
    'Introduce a conflict at the db...  
    objRs2.Open strSQL, strConn, adOpenKeyset, adLockOptimistic, adCmdText  
    objRs2("Phone") = "(999) 555-9999"  
    objRs2.Update  
    objRs2.Close  
    Set objRs2 = Nothing  
  
    On Error Resume Next  
    objRs1.UpdateBatch  
  
    If objRs1.ActiveConnection.Errors.Count <> 0 Then  
        Dim intConflicts As Integer  
  
        intConflicts = 0  
  
        objRs1.Filter = adFilterConflictingRecords  
  
        intConflicts = objRs1.RecordCount  
  
        'Resync so we can see the UnderlyingValue and offer user a choice.  
        'This sample only displays all three values and resets to original.  
        objRs1.Resync adAffectGroup, adResyncUnderlyingValues  
  
        If intConflicts > 0 Then  
            strMsg = "A conflict occurred with updates for " & intConflicts & _  
                     " record(s)." & vbCrLf & "The values will be restored" & _  
                     " to their original values." & vbCrLf & vbCrLf  
  
            objRs1.MoveFirst  
            While Not objRs1.EOF  
              strMsg = strMsg & "SHIPPER = " & objRs1("CompanyName") & vbCrLf  
              strMsg = strMsg & "Value = " & objRs1("Phone").Value & vbCrLf  
              strMsg = strMsg & "UnderlyingValue = " & _  
                                 objRs1("Phone").UnderlyingValue & vbCrLf  
              strMsg = strMsg & "OriginalValue = " & _  
                                 objRs1("Phone").OriginalValue & vbCrLf  
              strMsg = strMsg & vbCrLf & "Original value has been restored."  
  
              MsgBox strMsg, vbOKOnly, _  
                    "Conflict " & objRs1.AbsolutePosition & _  
                    " of " & intConflicts  
  
              objRs1("Phone").Value = objRs1("Phone").OriginalValue  
              objRs1.MoveNext  
            Wend  
  
            objRs1.UpdateBatch adAffectGroup  
        Else  
            'Other error occurred. Minimal handling in this example.  
             strMsg = "Errors occurred during the update. " & _  
                        objRs1.ActiveConnection.Errors(0).Number & " " & _  
                        objRs1.ActiveConnection.Errors(0).Description  
        End If  
  
        On Error GoTo 0  
    End If  
  
    objRs1.MoveFirst  
    objRs1.Close  
    Set objRs1 = Nothing  
'EndConflicts  
```  
  
 Чтобы определить, какого рода конфликт происходит, можно использовать свойство Status текущей записи или по указанному полю.  
  
 Подробные сведения об обработке ошибок см. в разделе [обработка ошибок](../../../ado/guide/data/error-handling.md).  
  
## <a name="see-also"></a>См. также:  
 [Пакетный режим](../../../ado/guide/data/batch-mode.md)
