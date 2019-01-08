---
title: Этап 2. Инициализация главного списка | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: a1454493-1c86-46c2-ada8-d3c6fcdaf3c1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 90b7d50d6cb0a6fd8c0814d1b4bcbb631e5e8376
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53206423"
---
# <a name="step-2-initialize-the-main-list-box"></a>Этап 2. Инициализация главного списка
Чтобы объявить глобальные объекты набора записей и записи, вставьте следующий код в (Общие) (объявления) для Form1:  
  
```  
Option Explicit  
Dim grec As Record  
Dim grs As Recordset  
```  
  
 Этот код объявляет ссылок на глобальный объект для набора записей и записи объектов, которые будут использоваться позже в этом сценарии.  
  
## <a name="to-connect-to-a-url-and-populate-lstmain"></a>Чтобы подключиться к URL-адрес и заполнить lstMain  
 Вставьте следующий код в обработчик событий загрузки формы для Form1:  
  
```  
Private Sub Form_Load()  
    Set grec = New Record  
    Set grs = New Recordset  
    grec.Open "", "URL=https://servername/foldername/", , _  
        adOpenIfExists Or adCreateCollection  
    Set grs = grec.GetChildren  
    While Not grs.EOF  
        lstMain.AddItem grs(0)  
        grs.MoveNext  
    Wend  
End Sub  
```  
  
 Этот код создает экземпляр глобальных объектов набора записей и записи. Объект записи, `grec`, открыт с помощью URL-адрес, заданный как ActiveConnection. Если URL-адрес существует, он открывается; Если он еще не существует, он создается. Обратите внимание, что следует заменить "<https://servername/foldername/>" с допустимым URL-адресом из среды.  
  
 Объект Recordset, `grs`, открывается на дочерние элементы записи `grec`. Затем `lstMain` заполняется имена файлов ресурсов, которые опубликованы на URL-адрес.  
  
## <a name="see-also"></a>См. также  
 [Сценарий публикации в Интернете](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Шаг 1. Настройка проекта Visual Basic](../../../ado/guide/data/step-1-set-up-the-visual-basic-project.md)   
 [Шаг 3. Заполнение списка полей](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
