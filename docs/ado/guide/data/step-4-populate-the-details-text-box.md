---
title: "Шаг 4: Заполнить текстовое поле сведений | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb4273e2-c907-4a86-a621-3bf110088228
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 512ad22b6529adcf065cacb219d1f0acc025c306
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="step-4-populate-the-details-text-box"></a>Шаг 4: Заполнить текстовое поле сведений
Чтобы заполнить текстовое поле сведений, создайте новый подпрограмму с именем **recFields** и вставьте следующий код:  
  
```  
Sub recFields(r As Record, l As ListBox, t As TextBox)  
    Dim f As Field  
    Dim s As Stream  
    Set s = New Stream  
    Dim str As String  
  
    For Each f In r.Fields  
        l.AddItem f.Name & ": " & f.Value  
    Next  
    t.Text = ""  
    If r!RESOURCE_CONTENTCLASS = "text/plain" Then  
        s.Open r, adModeRead, adOpenStreamFromRecord  
        str = s.ReadText(1)  
        s.Position = 0  
        If Asc(Mid(str, 1, 1)) = 63 Then '//63 = "?"  
            s.Charset = "ascii"  
            s.Type = adTypeText  
        End If  
        t.Text = s.ReadText(adReadAll)  
    End If  
End Sub  
```  
  
 Этот код заполняет поле `lstDetails` с полями и значения, передаваемый простой записи `recFields`. Если ресурс находится в текстовый файл, открывается текстовый поток из записи ресурса. Код определяет, является ли набор символов ASCII и копирует содержимое потока в `txtDetails`.  
  
## <a name="see-also"></a>См. также:  
 [Сценарий публикации в Интернете](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Шаг 3: Заполнения списка полей](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
