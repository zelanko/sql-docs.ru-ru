---
title: Редактор источника OData (страница «соединение») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- Sql12.dts.designer.odatasource.connection.f1
ms.assetid: 20bcd347-4547-4fad-b182-9571030101df
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0e36c0a3449566db9a2acee360243c77ee548f92
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66057318"
---
# <a name="odata-source-editor-connection-page"></a>Редактор источника OData (страница «Подключение»)
  Страница **Диспетчер соединений** диалогового окна **Редактор источника OData** служит для выбора диспетчера соединений OData для источника. На этой странице также можно задать путь к коллекции или ресурсу, а также параметры запроса, чтобы указать, какие данные нужно получить из источника OData. Дополнительные сведения об источнике OData см. в разделе [OData Source](data-flow/odata-source.md).  
  
## <a name="static-options"></a>Статические параметры  
 **Диспетчер соединений OData**  
 Выберите из списка существующий диспетчер соединений или создайте новое соединение, нажав кнопку **Создать**.  
  
 **Создать**  
 Создайте новый диспетчер соединений с помощью диалогового окна **Редактор диспетчера соединений OData** .  
  
 **Использование пути к коллекции или ресурсу**  
 Укажите метод выбора данных из источника.  
  
|Параметр|Описание|  
|------------|-----------------|  
|Коллекция|Извлечение данных из источника OData с помощью имени коллекции.|  
|Путь к ресурсу|Извлечение данных из источника OData с помощью пути к ресурсу.|  
  
 **Параметры запроса**  
 Укажите параметры запроса.  Например: $top=5  
  
 **URL-адрес канала**  
 Отображает доступный только для чтения URL-адрес канала на основе параметров, выбранных в этом диалоговом окне.  
  
 **Предварительный просмотр**  
 Предварительный просмотр результатов в диалоговом окне **Предварительный просмотр** . В окне**Предварительный просмотр** может отображаться до 20 строк.  
  
## <a name="dynamic-options"></a>Динамические параметры  
  
### <a name="use-collection-or-resource-path--collection"></a>Использование пути к коллекции или ресурсу = коллекция  
 **Коллекция**  
 Выберите коллекцию из раскрывающегося списка.  
  
### <a name="use-collection-or-resource-path--resource-path"></a>Использование пути к коллекции или ресурсу = путь к ресурсу  
 **Resource path**  
 Введите путь к ресурсу. Пример: Employees  
  
## <a name="see-also"></a>См. также  
 [Редактор источника OData (страница "Столбцы")](../../2014/integration-services/odata-source-editor-columns-page.md)   
 [Редактор источника OData (страница "Вывод ошибок")](../../2014/integration-services/odata-source-editor-error-output-page.md)   
 [OData Connection Manager](connection-manager/odata-connection-manager.md)  
  
  
