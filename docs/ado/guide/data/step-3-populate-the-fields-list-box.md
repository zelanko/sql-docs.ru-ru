---
title: Шаг 3. Заполнение поля списка полей | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 315c32dc-aeb1-4629-b30e-87b44e8f84d1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9d7f351b90030e755dde8ad13905ef4533eff08e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67924053"
---
# <a name="step-3-populate-the-fields-list-box"></a>Шаг 3. Заполнение списка полей
Чтобы заполнить поле списка поля, вставьте следующий код в обработчик событий Click `lstMain`:  
  
```  
Private Sub lstMain_Click()  
    Dim rec As Record  
    Dim rs As Recordset  
    Set rec = New Record  
    Set rs = New Recordset  
    grs.MoveFirst  
    grs.Move lstMain.ListIndex  
    lstDetails.Clear  
    rec.Open grs  
    Select Case rec.RecordType  
        Case adCollectionRecord:  
            Set rs = rec.GetChildren  
            While Not rs.EOF  
                lstDetails.AddItem rs(0)  
                rs.MoveNext  
            Wend  
        Case adSimpleRecord:  
            recFields rec, lstDetails, txtDetails  
  
        Case adStructDoc:  
    End Select  
  
End Sub  
```  
  
 Этот код объявляет и создает экземпляры локальных записей и объектов Recordset `rec` и `rs`соответственно.  
  
 Строка, соответствующая ресурсу, выбранному в `lstMain` , становится текущей строкой. `grs` Затем список сведений удаляется и `rec` открывается с текущей строкой в `grs` качестве источника.  
  
 Если ресурс является записью коллекции, как указано в [RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md), локальный набор записей `rs` открывается на дочерних элементах REC. Затем `lstDetails` заполняется значениями из строк `rs`.  
  
 Если ресурс является простой записью, `recFields` вызывается. Дополнительные сведения о `recFields`см. в следующем шаге.  
  
 Если ресурс является структурированным документом, код не реализуется.  
  
## <a name="see-also"></a>См. также:  
 [Сценарий публикации в Интернете](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Шаг 2. Инициализация основного списка](../../../ado/guide/data/step-2-initialize-the-main-list-box.md)   
 [Шаг 4. Заполнение текстового поля сведений](../../../ado/guide/data/step-4-populate-the-details-text-box.md)
