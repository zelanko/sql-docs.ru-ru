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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8ad89d806f8a6774cb0fe2de056e30fd274a517c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924088"
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
  
 Этот код создает экземпляры глобальной записи и объектов набора записей. Объект `grec`Record открыт с URL-адресом, указанным в качестве ActiveConnection. Если URL-адрес существует, он открывается; Если он еще не существует, он будет создан. Обратите внимание, что необходимо<https://servername/foldername/>заменить "" допустимым URL-адресом из вашей среды.  
  
 Объект набора записей, `grs`, открывается на дочерних элементах записи, `grec`. Затем `lstMain` заполняются имена файлов ресурсов, опубликованных по URL-адресу.  
  
## <a name="see-also"></a>См. также:  
 [Сценарий публикации в Интернете](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Шаг 1. Настройка проекта Visual Basic](../../../ado/guide/data/step-1-set-up-the-visual-basic-project.md)   
 [Шаг 3. Заполнение списка полей](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
