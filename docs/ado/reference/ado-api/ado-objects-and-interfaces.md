---
title: Объекты ADO и интерфейсы | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, objects and interfaces
- objects [ADO]
ms.assetid: d0b7e254-c89f-4406-b846-a060ef038c30
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 047e1a7a0cafee0b562edc5b3ec47f9f4dd3989d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="ado-objects-and-interfaces"></a>Объекты ADO и интерфейсы
Для представления связей между этими объектами [объектная модель ADO](../../../ado/reference/ado-api/ado-object-model.md).  
  
 Каждый объект может содержаться в соответствующей коллекции. Например [ошибка](../../../ado/reference/ado-api/error-object.md) объекта может содержаться в [ошибки](../../../ado/reference/ado-api/errors-collection-ado.md) коллекции. Дополнительные сведения см. в разделе [коллекций ADO](../../../ado/reference/ado-api/ado-collections.md) или раздел определенной коллекции.  
  
|||  
|-|-|  
|[IADOCommandConstruction](https://msdn.microsoft.com/library/windows/desktop/aa965677.aspx)|Используется для извлечения из объекта ADOCommand базовой команды OLEDB.|  
|[ADORecordConstruction](../../../ado/reference/ado-api/adorecordconstruction-interface.md)|Создает ADO **запись** объектов из поставщика OLE DB **строки** объекта в приложении C/C++.|  
|[ADORecordsetConstruction](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)|Создает ADO **записей** объектов из поставщика OLE DB **строк** объекта в приложении C/C++.|  
|[Интерфейс ADOStreamConstruction](../../../ado/reference/ado-api/adostreamconstruction-interface.md)|Создает ADO **поток** объектов из поставщика OLE DB **IStream** объекта в приложении C/C++.|  
|[Command](../../../ado/reference/ado-api/command-object-ado.md)|Определяет той или иной команды, которую планируется выполнить в источнике данных.<br /><br /> **Команда** объект не является безопасным для создания сценариев.|  
|[Соединение](../../../ado/reference/ado-api/connection-object-ado.md)|Представляет открытое соединение с источником данных.<br /><br /> **Подключения** объекта безопасные для использования.|  
|[Интерфейс IDSOShapeExtensions](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)|Возвращает объект базового источника данных OLE DB для поставщика ФИГУРЫ.|  
|[Ошибка](../../../ado/reference/ado-api/error-object.md)|Содержит сведения об ошибках доступа к данным, которые относятся к одной операции с участием поставщика.<br /><br /> **Ошибка** объект не является безопасным для создания сценариев.|  
|[Поле](../../../ado/reference/ado-api/field-object.md)|Представляет столбец данных с общим типом данных.|  
|[Параметр](../../../ado/reference/ado-api/parameter-object.md)|Представляет параметр или аргумент, связанный с **команда** объекта, основанного на параметризованный запрос или хранимую процедуру.<br /><br /> **Параметр** объект не является безопасным для создания сценариев.|  
|[Свойство](../../../ado/reference/ado-api/property-object-ado.md)|Представляет динамический характеристику объекта ADO, определенной поставщиком.|  
|[Запись](../../../ado/reference/ado-api/record-object-ado.md)|Представляет строку **записей**, каталог или файл в файловой системе. **Записи** объекта безопасные для использования.|  
|[Набор записей](../../../ado/reference/ado-api/recordset-object-ado.md)|Представляет набор записей из базовой таблицы или результаты выполнения команды. В любой момент **записей** объект ссылается только на одну запись в набор, что текущая запись.<br /><br /> **Записей** объекта безопасные для использования.|  
|[Поток](../../../ado/reference/ado-api/stream-object-ado.md)|Представляет двоичный поток данных.<br /><br /> **Поток** объекта безопасные для использования.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO коллекций](../../../ado/reference/ado-api/ado-collections.md)   
 [Динамические свойства ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [ADO перечисляемые константы](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Приложение б. ошибки ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [События ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Методы ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Объектная модель ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Свойства ADO](../../../ado/reference/ado-api/ado-properties.md)
