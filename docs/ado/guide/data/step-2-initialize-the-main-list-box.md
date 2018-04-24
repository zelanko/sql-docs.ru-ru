---
title: 'Шаг 2: Инициализируйте главном списке | Документы Microsoft'
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
ms.assetid: a1454493-1c86-46c2-ada8-d3c6fcdaf3c1
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e8272c721c2717df494db5ead86716900f44c46e
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="step-2-initialize-the-main-list-box"></a>Шаг 2: Инициализируйте главном списке
Чтобы объявить глобальные объекты набора записей и записи, вставьте следующий код (Общие) (объявления) класса Form1:  
  
```  
Option Explicit  
Dim grec As Record  
Dim grs As Recordset  
```  
  
 Этот код объявляет глобальный объект ссылки для объектов набора записей и записи, которые будут использоваться позже в этом сценарии.  
  
## <a name="to-connect-to-a-url-and-populate-lstmain"></a>Чтобы подключиться к URL-адрес и заполнить lstMain  
 Вставьте следующий код в обработчик событий загрузки формы класса Form1:  
  
```  
Private Sub Form_Load()  
    Set grec = New Record  
    Set grs = New Recordset  
    grec.Open "", "URL=http://servername/foldername/", , _  
        adOpenIfExists Or adCreateCollection  
    Set grs = grec.GetChildren  
    While Not grs.EOF  
        lstMain.AddItem grs(0)  
        grs.MoveNext  
    Wend  
End Sub  
```  
  
 Этот код создает экземпляр глобальных объектов набора записей и записи. Объект записи `grec`, открытом с URL-адрес, указанный как ActiveConnection. Если URL-адрес существует, он открыт; Если он еще не существует, он создается. Обратите внимание, что необходимо заменить «http://servername/foldername/» с допустимый URL-адрес из среды.  
  
 Объект Recordset, `grs`, открывается на дочерние записи, `grec`. Затем `lstMain` заполняется имена файлов ресурсов, которые опубликованы на URL-адрес.  
  
## <a name="see-also"></a>См. также  
 [Сценарий публикации в Интернете](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Шаг 1: Настройка проекта Visual Basic](../../../ado/guide/data/step-1-set-up-the-visual-basic-project.md)   
 [Шаг 3. Заполнение списка полей](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
