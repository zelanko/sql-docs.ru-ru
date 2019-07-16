---
title: Объекты и интерфейсы ADO | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, objects and interfaces
- objects [ADO]
ms.assetid: d0b7e254-c89f-4406-b846-a060ef038c30
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e5ecc6de67defb2366bf208c38bd2de5bff643e4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67920900"
---
# <a name="ado-objects-and-interfaces"></a>Объекты и интерфейсы ADO
Связи между этими объектами, представлены в [объектная модель ADO](../../../ado/reference/ado-api/ado-object-model.md).  
  
 Каждый объект может содержаться в соответствующей коллекции. Например [ошибка](../../../ado/reference/ado-api/error-object.md) объекта может содержаться в [ошибки](../../../ado/reference/ado-api/errors-collection-ado.md) коллекции. Дополнительные сведения см. в разделе [коллекции ADO](../../../ado/reference/ado-api/ado-collections.md) или раздел определенной коллекции.  
  
|||  
|-|-|  
|[IADOCommandConstruction](https://msdn.microsoft.com/library/windows/desktop/aa965677.aspx)|Используется для извлечения из объекта ADOCommand, лежащей в основе команды OLEDB.|  
|[ADORecordConstruction](../../../ado/reference/ado-api/adorecordconstruction-interface.md)|Создает объект ADO **записи** объект из OLE DB **строки** объекта в приложении C/C++.|  
|[ADORecordsetConstruction](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)|Создает объект ADO **записей** объект из OLE DB **набора строк** объекта в приложении C/C++.|  
|[Интерфейс ADOStreamConstruction](../../../ado/reference/ado-api/adostreamconstruction-interface.md)|Создает объект ADO **Stream** объект из OLE DB **IStream** объекта в приложении C/C++.|  
|[Command](../../../ado/reference/ado-api/command-object-ado.md)|Определяет определенной команде, где вы собираетесь выполнить в источнике данных.<br /><br /> **Команда** объект не является безопасным для использования в сценариях.|  
|[Соединение](../../../ado/reference/ado-api/connection-object-ado.md)|Представляет открытое подключение к источнику данных.<br /><br /> **Подключения** объект безопасен для скриптов.|  
|[Интерфейс IDSOShapeExtensions](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)|Получает базовый объект источника данных OLE DB для поставщика ФИГУРЫ.|  
|[Ошибка](../../../ado/reference/ado-api/error-object.md)|Содержит сведения об ошибках доступа к данным, которые относятся к одной операции с участием поставщика.<br /><br /> **Ошибка** объект не является безопасным для использования в сценариях.|  
|[Поле](../../../ado/reference/ado-api/field-object.md)|Представляет столбец данных с типом данных.|  
|[Параметр](../../../ado/reference/ado-api/parameter-object.md)|Представляет параметр или аргумент, связанный с **команда** объекта на основании параметризованного запроса или хранимой процедуры.<br /><br /> **Параметр** объект не является безопасным для использования в сценариях.|  
|[Property](../../../ado/reference/ado-api/property-object-ado.md)|Представляет характеристику динамического объекта ADO, определенной поставщиком.|  
|[Запись](../../../ado/reference/ado-api/record-object-ado.md)|Представляет строку **записей**, каталог или файл в файловой системе. **Записи** объект безопасен для скриптов.|  
|[Набор записей](../../../ado/reference/ado-api/recordset-object-ado.md)|Представляет набор записей из базовой таблицы или результаты выполнения команды. В любое время **записей** объект ссылается на одну запись в наборе как текущую запись.<br /><br /> **Записей** объект безопасен для скриптов.|  
|[поток](../../../ado/reference/ado-api/stream-object-ado.md)|Представляет двоичный поток данных.<br /><br /> **Stream** объект безопасен для скриптов.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [Коллекции ADO](../../../ado/reference/ado-api/ado-collections.md)   
 [Динамические свойства ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [Перечисляемые константы ADO](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Приложение б. Ошибки ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [События ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Методы ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Объектная модель ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Свойства ADO](../../../ado/reference/ado-api/ado-properties.md)
