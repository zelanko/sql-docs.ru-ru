---
title: Шаг 3. Заполнение списка полей | Документация Майкрософт
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
manager: jroth
ms.openlocfilehash: f69ab97a522e148d8027042ff7e2c6b09a690424
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66704827"
---
# <a name="step-3-populate-the-fields-list-box"></a>Шаг 3. Заполнение списка полей
Для заполнения списка полей, вставьте следующий код в обработчик событий нажатия `lstMain`:  
  
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
  
 Этот код объявляет и создает локальные объекты набора записей и записи, `rec` и `rs`, соответственно.  
  
 Строка, соответствующая ресурса, выбранного в `lstMain` становится текущей строке `grs`. Затем очищается поле со списком сведения и `rec` открыт с помощью текущей строке `grs` как источник.  
  
 Если ресурс — это запись коллекции, в соответствии с [RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md), локальный набор записей `rs` открывается на дочерние элементы rec. Затем `lstDetails` заполняется значениями из строки `rs`.  
  
 Если ресурс является запись простой `recFields` вызывается. Дополнительные сведения о `recFields`, см. следующий шаг.  
  
 Код не реализуется в том случае, если ресурс структурированного документа.  
  
## <a name="see-also"></a>См. также  
 [Сценарий публикации в Интернете](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Шаг 2. Инициализация главного списка](../../../ado/guide/data/step-2-initialize-the-main-list-box.md)   
 [Шаг 4. Заполнение текстового поля сведений](../../../ado/guide/data/step-4-populate-the-details-text-box.md)
