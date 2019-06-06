---
title: Шаг 4. Заполнение текстового поля сведений | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: cb4273e2-c907-4a86-a621-3bf110088228
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8a2d19ed59aa10ad75843df03d626f5f880462ca
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66718704"
---
# <a name="step-4-populate-the-details-text-box"></a>Шаг 4. Заполнение текстового поля сведений
Для заполнения текстового поля сведений, создайте новый подпрограмму с именем **recFields** и вставьте следующий код:  
  
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
  
 Этот код заполняет `lstDetails` с полями и значения простой записи передаваемое `recFields`. Если ресурс — это текстовый файл, открывается Stream текст из записи ресурса. Код определяет соответствие набор символов ASCII и копирует содержимое в Stream `txtDetails`.  
  
## <a name="see-also"></a>См. также  
 [Сценарий публикации в Интернете](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Шаг 3. Заполнение списка полей](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
