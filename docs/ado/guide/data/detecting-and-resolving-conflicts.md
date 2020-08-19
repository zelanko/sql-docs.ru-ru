---
description: Обнаружение и разрешение конфликтов
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
author: rothja
ms.author: jroth
ms.openlocfilehash: c9ab7dd72816d47b4f8a1c7aa55ba8751399e41a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453516"
---
# <a name="detecting-and-resolving-conflicts"></a>Обнаружение и разрешение конфликтов
Если вы работаете с набором записей в режиме интерпретации, проблемы с параллелизмом значительно снижаются. С другой стороны, если приложение использует обновление в пакетном режиме, то может быть хорошей шанс, что один пользователь изменит запись, прежде чем изменения, внесенные другим пользователем, редактируют ту же запись, сохраняются. В этом случае вам потребуется, чтобы приложение корректно обрабатывал конфликт. Возможно, вы хотите, чтобы последний пользователь отправлял обновление на сервер "WINS". Или, возможно, вы хотите, чтобы последний пользователь решил, какое обновление должно иметь приоритет, предоставив ему выбор между двумя конфликтующими значениями.  
  
 В любом случае ADO предоставляет свойства UnderlyingValue и OriginalValue объекта Field для решения этих типов конфликтов. Используйте эти свойства совместно с методом повторной синхронизации и свойством Filter набора записей.  
  
## <a name="remarks"></a>Комментарии  
 Когда ADO обнаруживает конфликт во время пакетного обновления, в коллекцию Errors будет добавлено предупреждение. Таким образом, следует всегда проверять наличие ошибок сразу после вызова Батчупдате, и если вы обнаружите их, начните проверку предположения, что возник конфликт. Первым шагом является установка свойства Filter для набора записей, равного Адфилтерконфликтингрекордс. Это ограничивает представление набора записей только конфликтующими записями. Если после выполнения этого шага свойство RecordCount равно нулю, то известно, что ошибка была вызвана не конфликтом.  
  
 При вызове Батчупдате ADO и поставщик создают инструкции SQL для выполнения обновлений в источнике данных. Помните, что определенные источники данных имеют ограничения на типы столбцов, которые могут использоваться в предложении WHERE.  
  
 Затем вызовите метод Resync для набора записей с набором аргументов Аффектрекордс, равным Адаффектграуп, а аргумент Ресинквалуес — равным Адресинкундерлингвалуес. Метод Resync обновляет данные в текущем объекте набора записей из базовой базы данных. Используя Адаффектграуп, вы гарантируете, что только записи, видимые с текущим параметром фильтра, то есть только конфликтующие записи, повторно синхронизируются с базой данных. Это может значительно повысить производительность при работе с большим набором записей. Установив аргумент Ресинквалуес в значение Адресинкундерлингвалуес при вызове функции повторной синхронизации, вы убедитесь, что свойство UnderlyingValue будет содержать (конфликтующее) значение из базы данных, что свойство Value будет поддерживать введенное пользователем значение, а свойство OriginalValue будет содержать исходное значение поля (значение, которое оно имело до последнего успешного вызова UpdateBatch). Затем эти значения можно использовать для устранения конфликта программным образом или для того, чтобы пользователь мог выбрать значение, которое будет использоваться.  
  
 Этот метод показан в следующем примере кода. В этом примере искусственно создается конфликт с помощью отдельного набора записей для изменения значения в базовой таблице перед вызовом UpdateBatch.  
  
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
  
 Можно использовать свойство Status текущей записи или определенного поля, чтобы определить, какой тип конфликта был вызван.  
  
 Подробные сведения об обработке ошибок см. в разделе [Обработка ошибок](../../../ado/guide/data/error-handling.md).  
  
## <a name="see-also"></a>См. также  
 [Пакетный режим](../../../ado/guide/data/batch-mode.md)
