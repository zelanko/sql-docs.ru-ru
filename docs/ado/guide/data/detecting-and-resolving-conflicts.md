---
title: Обнаружение и разрешение конфликтов | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- conflicts [ADO], detecting and resolving
- ADO, detecting and resolving conflicts
ms.assetid: b28fdd26-c1a4-40ce-a700-2b0c9d201514
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a27a8ff70a995ab24dcf762d0ada731e0de6fa92
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47625292"
---
# <a name="detecting-and-resolving-conflicts"></a>Обнаружение и разрешение конфликтов
Если вы работаете с набором записей в режиме интерпретации, это гораздо меньше вероятность проблемы параллелизма. С другой стороны, если приложение использует режим пакетного обновления, может существовать хорошее вероятность того, что пользователь изменит записи, перед сохранением изменений, внесенных другим пользователем, редактирования и той же записи. В этом случае требуется, приложение может корректно обрабатывать конфликт. Может быть нежелательным, последнего пользователя для отправки обновления на сервер «побеждает.» Или вы можете позволить последнему пользователю, чтобы определить, какие обновления больший приоритет, предоставляя ему возможность выбора из двух конфликтующих значений.  
  
 В любом случае ADO предоставляет UnderlyingValue и OriginalValue свойств объекта поля для обработки таких типов конфликтов. Эти свойства можно используйте в сочетании с методом повторной синхронизации и свойство фильтра набора записей.  
  
## <a name="remarks"></a>Примечания  
 Когда ADO обнаруживает конфликт во время пакетного обновления, предупреждения будут добавляться в коллекцию ошибок. Таким образом следует всегда проверять наличие ошибок сразу после вызова BatchUpdate и если найти их, приступить к тестированию в предположении, что вы столкнулись с конфликтом. Первым шагом является установка свойства фильтра для набора записей, равным adFilterConflictingRecords. Это ограничивает представление набора записей только те записи, участвующих в конфликте. Если свойство RecordCount равным нулю после выполнения этого шага, вы знаете, что произошла ошибка, отличные от конфликт.  
  
 При вызове BatchUpdate, ADO и поставщика создают инструкции SQL для выполнения обновлений в источнике данных. Помните, что для некоторых источников данных обладают ограничения, на которых можно использовать типы столбцов в предложении WHERE.  
  
 Затем вызывается метод повторной синхронизации для объекта Recordset с аргументом AffectRecords равным adAffectGroup и аргумент ResyncValues, равным adResyncUnderlyingValues. Повторная синхронизация метод обновляет данные в текущем объекте набора записей из базы данных. С помощью adAffectGroup, можете быть уверены, что только записи, видимым по текущему фильтру, параметр, то есть только конфликтующих записей, выполняется повторная синхронизация с базой данных. Это может усложнить значительную разницу в производительности при работе с набором больших записей. Установив аргумент ResyncValues adResyncUnderlyingValues при вызове повторной синхронизации, вы убедитесь, что свойство UnderlyingValue будет содержать значение (конфликт) из базы данных, что свойство Value будет поддерживать значением, введенным пользователем, и что свойство OriginalValue будет содержать исходное значение для поля (значение, которое было до последнего успешного вызова UpdateBatch). Затем эти значения можно использовать для разрешения конфликта программным способом или пользователь должен выбрать значение, которое будет использоваться.  
  
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
  
 Можно использовать свойство Status текущей записи или поля, чтобы определить, какого рода конфликт произошла.  
  
 Подробные сведения об обработке ошибок см. в разделе [обработка ошибок](../../../ado/guide/data/error-handling.md).  
  
## <a name="see-also"></a>См. также  
 [Пакетный режим](../../../ado/guide/data/batch-mode.md)
