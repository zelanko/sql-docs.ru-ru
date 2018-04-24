---
title: 'Шаг 3: Заполнения списка полей | Документы Microsoft'
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 315c32dc-aeb1-4629-b30e-87b44e8f84d1
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b7f82e92cc9293781992eccdbb04a46f8ac788fa
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="step-3-populate-the-fields-list-box"></a>Шаг 3: Заполнения списка полей
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
  
 Этот код объявляет и создает локальные объекты набора записей и записи, `rec` и `rs`соответственно.  
  
 Строка, соответствующая ресурсов, выбранных в `lstMain` становится текущей строке `grs`. Затем снят список сведений и `rec` открывается с текущей строке `grs` как источник.  
  
 Если ресурс является записи коллекции, в соответствии с [RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md), локальный набор записей `rs` открывается на дочерние элементы rec. Затем `lstDetails` заполняется значениями из строки `rs`.  
  
 Если ресурс является запись простой `recFields` вызывается. Дополнительные сведения о `recFields`, см. следующий шаг.  
  
 Код не реализуется в том случае, если ресурс структурированный документ.  
  
## <a name="see-also"></a>См. также  
 [Сценарий публикации в Интернете](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Шаг 2: Инициализируйте главном списке](../../../ado/guide/data/step-2-initialize-the-main-list-box.md)   
 [Шаг 4. Заполнение текстового поля сведений](../../../ado/guide/data/step-4-populate-the-details-text-box.md)
