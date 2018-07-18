---
title: 'При создании экземпляра события ADO: ADO и WFC | Документы Microsoft'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9ee4be21-657b-407a-afa4-0b27a6b096ce
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6aa227f5ca6b6246d61e183c03d6217ebaa70bac
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35270813"
---
# <a name="ado-event-instantiation-ado-and-wfc"></a>При создании экземпляра события ADO: ADO и WFC
ADO ввода для Windows Foundation Classes (ADO и WFC) основана на модели событий ADO и предоставляет упрощенный интерфейс программирования. В общем случае ADO/WFC перехватывает события ADO, объединяет параметры события в классе событий и затем вызывает обработчик события.  
  
### <a name="to-use-ado-events-in-adowfc"></a>Использовать ADO события в ADO или WFC  
  
1.  Определите обработчик событий для обработки события. Например, если требуется обработать **ConnectComplete** события в **ConnectionEvent** семейства, могут использовать этот пример кода:  
  
    ```  
    public void onConnectComplete(Object sender,ConnectionEvent e)  
    {  
        System.out.println("onConnectComplete:" + e);  
    }  
    ```  
  
2.  Определите объект обработчика, представляющий обработчик событий. Объект-обработчик должен иметь тип данных **ConnectEventHandler** для события типа **ConnectionEvent**, тип данных или **RecordsetEventHandler** для события типа  **RecordsetEvent**. Например, код следующие действия для вашего **ConnectComplete** обработчик событий:  
  
    ```  
    ConnectionEventHandler handler =   
        new ConnectionEventHandler(this, "onConnectComplete");  
    ```  
  
     Первый аргумент **ConnectionEventHandler** конструктор — это ссылка на класс, содержащий обработчик событий с именем в качестве второго аргумента.  
  
3.  Добавьте обработчик событий в список обработчиков, предназначенные для обработки конкретного типа событий. Например, используйте метод с именем **addOn** *EventName*(*обработчик*).  
  
4.  ADO/WFC внутренне реализует все обработчики событий ADO. Таким образом, событие вызвано **подключения** или **записей** перехватывает операцию с помощью ADO и WFC обработчика событий.  
  
     Обработчик событий ADO/WFC передает ADO **ConnectionEvent** параметры в экземпляре ADO/WFC **ConnectionEvent** класса или ADO **RecordsetEvent** параметров в экземпляр ADO/WFC **RecordsetEvent** класса. Эти классы ADO/WFC консолидировать параметры события ADO; Таким образом, каждый класс ADO/WFC содержит один элемент данных для каждого параметра, уникальный в ADO **ConnectionEvent** или **RecordsetEvent** методы.  
  
5.  ADO/WFC вызывает обработчик событий с ADO/WFC объект события. Например ваш **onConnectComplete** обработчик имеет подпись следующим образом:  
  
    ```  
    public void onConnectComplete(Object sender,ConnectionEvent e)  
    ```  
  
     Первый аргумент — тип объекта, который отправил событие ([подключения](../../../ado/reference/ado-api/connection-object-ado.md) или [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md)), а второй аргумент — это объект ADO или WFC событий (**ConnectionEvent** или **RecordsetEvent**).  
  
     Подпись обработчика событий проще, чем при возникновении события ADO. Однако по-прежнему необходимо понимать модель событий ADO параметры применяются к событию, а также способы реагирования.  
  
6.  Возврат из обработчика событий в ADO или WFC обработчик для события ADO. ADO/WFC копирование нужные элементы данных события ADO/WFC обратно в параметрах события ADO, и возвращает обработчик событий ADO.  
  
7.  По окончании обработки, удалить обработчик из списка ADO/WFC обработчиков событий. Например, используйте метод с именем **removeOn** *EventName*(*обработчик*).  
  
## <a name="see-also"></a>См. также  
 [Сводка обработчик событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [ADO - WFC синтаксис индекса](../../../ado/reference/ado-api/ado-wfc-syntax-index.md)   
 [Параметры события](../../../ado/guide/data/event-parameters.md)   
 [Как работают обработчики событий](../../../ado/guide/data/how-event-handlers-work-together.md)   
 [Типы событий](../../../ado/guide/data/types-of-events.md)
