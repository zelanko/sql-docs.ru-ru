---
title: 'Создание экземпляра события ADO: ADO и WFC | Документация Майкрософт'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 9ee4be21-657b-407a-afa4-0b27a6b096ce
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 1a4bb76e9172458c26e59dc366e8a321a548f34e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66702603"
---
# <a name="ado-event-instantiation-ado-and-wfc"></a>Создание экземпляра события ADO: ADO и WFC
ADO ввода для Windows Foundation Classes (ADO и WFC) основан на модели событий ADO и предоставляет упрощенный интерфейс программирования. Как правило ADO и WFC перехватывает события ADO, объединяет параметры события в классе событий, а затем вызывает обработчик событий.  
  
### <a name="to-use-ado-events-in-adowfc"></a>Использовать ADO события в ADO и WFC  
  
1.  Определите обработчик событий для обработки события. Например, если вы хотите обрабатывать **ConnectComplete** событие в **ConnectionEvent** семейства, можно использовать этот код:  
  
    ```  
    public void onConnectComplete(Object sender,ConnectionEvent e)  
    {  
        System.out.println("onConnectComplete:" + e);  
    }  
    ```  
  
2.  Определите объект обработчика для представления Ваш обработчик событий. Объект-обработчик должен иметь тип данных **ConnectEventHandler** для события типа **ConnectionEvent**, тип данных или **RecordsetEventHandler** для события типа  **RecordsetEvent**. Например, код следующие действия для вашей **ConnectComplete** обработчик событий:  
  
    ```  
    ConnectionEventHandler handler =   
        new ConnectionEventHandler(this, "onConnectComplete");  
    ```  
  
     Первый аргумент **ConnectionEventHandler** конструктор — это ссылка на класс, содержащий обработчик событий с именем в качестве второго аргумента.  
  
3.  Добавьте обработчик событий в список обработчиков, предназначенные для обработки определенного типа события. Например, используйте метод с именем **addOn** *EventName*(*обработчик*).  
  
4.  ADO и WFC внутренне реализует все обработчики событий ADO. Таким образом, событие из-за **подключения** или **записей** операции перехватывается обработчиком событий ADO и WFC.  
  
     Обработчик событий ADO и WFC передает ADO **ConnectionEvent** параметров в экземпляре ADO и WFC **ConnectionEvent** класса или ADO **RecordsetEvent** параметров в экземпляр ADO и WFC **RecordsetEvent** класса. Эти классы ADO и WFC консолидировать параметры событий ADO; Таким образом, каждый класс ADO и WFC содержит один элемент данных для каждого параметра, уникальный в ADO **ConnectionEvent** или **RecordsetEvent** методы.  
  
5.  ADO и WFC затем вызывает обработчик событий с объектом событий ADO и WFC. Например ваш **onConnectComplete** обработчика имеет подпись, следующим образом:  
  
    ```  
    public void onConnectComplete(Object sender,ConnectionEvent e)  
    ```  
  
     Первым аргументом является тип объекта, отправляющий событие ([подключения](../../../ado/reference/ado-api/connection-object-ado.md) или [записей](../../../ado/reference/ado-api/recordset-object-ado.md)), и второй аргумент — объект события ADO и WFC (**ConnectionEvent** или **RecordsetEvent**).  
  
     Подпись обработчика событий проще, чем события ADO. Тем не менее по-прежнему необходимо понимать модели событий ADO знать параметры применяются к событию, а также способы реагирования.  
  
6.  Возвращает из обработчика событий в ADO и WFC обработчик для события ADO. ADO и WFC копирование нужные элементы данных события ADO и WFC обратно в параметры событий ADO, и возвращает обработчик событий ADO.  
  
7.  По завершении обработки, удалите обработчик из списка обработчиков событий ADO и WFC. Например, используйте метод с именем **removeOn** *EventName*(*обработчик*).  
  
## <a name="see-also"></a>См. также  
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [ADO — индекс синтаксиса WFC](../../../ado/reference/ado-api/ado-wfc-syntax-index.md)   
 [Параметры события](../../../ado/guide/data/event-parameters.md)   
 [Совместная работа обработчиков событий](../../../ado/guide/data/how-event-handlers-work-together.md)   
 [Типы событий](../../../ado/guide/data/types-of-events.md)
