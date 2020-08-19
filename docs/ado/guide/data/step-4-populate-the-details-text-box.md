---
description: Шаг 4. Заполнение текстового поля сведений
title: Шаг 4. Заполнение текстового поля сведений | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: cb4273e2-c907-4a86-a621-3bf110088228
author: rothja
ms.author: jroth
ms.openlocfilehash: 59b074b3e635457f8d96060575d941e26846281d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452786"
---
# <a name="step-4-populate-the-details-text-box"></a>Шаг 4. Заполнение текстового поля сведений
Чтобы заполнить текстовое поле сведения, создайте новую подпрограмму с именем **рекфиелдс** и вставьте следующий код:  
  
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
  
 Этот код заполняет `lstDetails` поля и значения простой записи, передаваемой в `recFields` . Если ресурс является текстовым файлом, в записи ресурса открывается текстовый поток. Код определяет, является ли кодировка кодировкой ASCII, и копирует содержимое потока в `txtDetails` .  
  
## <a name="see-also"></a>См. также:  
 [Сценарий публикации в Интернете](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Шаг 3. Заполнение списка полей](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
