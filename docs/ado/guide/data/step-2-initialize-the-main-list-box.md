---
title: Шаг 2. Инициализация главного окна списка | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: a1454493-1c86-46c2-ada8-d3c6fcdaf3c1
author: rothja
ms.author: jroth
ms.openlocfilehash: c6aaf4d87e4e01e6f32e1d681d93e5a2291c3999
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760820"
---
# <a name="step-2-initialize-the-main-list-box"></a>Шаг 2. Инициализация главного списка
Для объявления глобальных записей и объектов Recordset вставьте следующий код в (Общие) (объявления) для Form1:  
  
```  
Option Explicit  
Dim grec As Record  
Dim grs As Recordset  
```  
  
 Этот код объявляет ссылки на глобальные объекты для записей и объектов набора записей, которые будут использоваться далее в этом сценарии.  
  
## <a name="to-connect-to-a-url-and-populate-lstmain"></a>Подключение к URL-адресу и заполнение Лстмаин  
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
  
 Этот код создает экземпляры глобальной записи и объектов набора записей. Объект Record `grec` открыт с URL-адресом, указанным в качестве ActiveConnection. Если URL-адрес существует, он открывается; Если он еще не существует, он будет создан. Обратите внимание, что необходимо заменить " <https://servername/foldername/> " допустимым URL-адресом из вашей среды.  
  
 Объект набора записей, `grs` , открывается на дочерних элементах записи, `grec` . Затем `lstMain` заполняются имена файлов ресурсов, опубликованных по URL-адресу.  
  
## <a name="see-also"></a>См. также  
 [Сценарий публикации в Интернете](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Шаг 1. Настройка проекта Visual Basic](../../../ado/guide/data/step-1-set-up-the-visual-basic-project.md)   
 [Шаг 3. Заполнение списка полей](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
