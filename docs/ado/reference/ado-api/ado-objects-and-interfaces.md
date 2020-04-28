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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67920900"
---
# <a name="ado-objects-and-interfaces"></a>Объекты и интерфейсы ADO
Связи между этими объектами представлены в [объектной модели ADO](../../../ado/reference/ado-api/ado-object-model.md).  
  
 Каждый объект может содержаться в соответствующей коллекции. Например, объект [ошибки](../../../ado/reference/ado-api/error-object.md) может содержаться в коллекции [Errors](../../../ado/reference/ado-api/errors-collection-ado.md) . Дополнительные сведения см. в разделе [коллекции ADO](../../../ado/reference/ado-api/ado-collections.md) или сведения о конкретной коллекции.  
  
|||  
|-|-|  
|[иадокоммандконструктион](https://msdn.microsoft.com/library/windows/desktop/aa965677.aspx)|Используется для получения базовой команды OLEDB из объекта Адокомманд.|  
|[адорекордконструктион](../../../ado/reference/ado-api/adorecordconstruction-interface.md)|Конструирует объект **записи** ADO из объекта **строки** OLE DB в приложении C/C++.|  
|[адорекордсетконструктион](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)|Конструирует объект **набора записей** ADO из объекта OLE DB **набора строк** в приложении C/C++.|  
|[Интерфейс ADOStreamConstruction](../../../ado/reference/ado-api/adostreamconstruction-interface.md)|Конструирует объект **потока** ADO из OLE DBного объекта **IStream** в приложении C/C++.|  
|[Command](../../../ado/reference/ado-api/command-object-ado.md)|Определяет конкретную команду, которую необходимо выполнить для источника данных.<br /><br /> Объект **Command** не является надежным для сценариев.|  
|[Соединен](../../../ado/reference/ado-api/connection-object-ado.md)|Представляет открытое подключение к источнику данных.<br /><br /> Объект **соединения** является надежным для сценариев.|  
|[Интерфейс IDSOShapeExtensions](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)|Возвращает базовый объект источника данных OLEDB для поставщика фигур.|  
|[Error](../../../ado/reference/ado-api/error-object.md)|Содержит сведения об ошибках доступа к данным, относящихся к одной операции, включающей в себя поставщик.<br /><br /> Объект **Error** не является надежным для скриптов.|  
|[Поле](../../../ado/reference/ado-api/field-object.md)|Представляет столбец данных с общим типом данных.|  
|[Параметр](../../../ado/reference/ado-api/parameter-object.md)|Представляет параметр или аргумент, связанный с объектом **Command** на основе параметризованного запроса или хранимой процедуры.<br /><br /> Объект **параметра** не является надежным для скриптов.|  
|[Свойство](../../../ado/reference/ado-api/property-object-ado.md)|Представляет динамическую характеристику объекта ADO, определяемого поставщиком.|  
|[Записать](../../../ado/reference/ado-api/record-object-ado.md)|Представляет строку **набора записей**или каталога или файла в файловой системе. Объект **Record** является надежным для сценариев.|  
|[набор записей](../../../ado/reference/ado-api/recordset-object-ado.md)|Представляет набор записей из базовой таблицы или результаты выполненной команды. В любой момент времени объект **Recordset** ссылается только на одну запись в наборе в качестве текущей записи.<br /><br /> Объект **набора записей** является надежным для сценариев.|  
|[Поток](../../../ado/reference/ado-api/stream-object-ado.md)|Представляет двоичный поток данных.<br /><br /> Объект **потока** является надежным для скриптов.|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [Коллекции ADO](../../../ado/reference/ado-api/ado-collections.md)   
 [Динамические свойства ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [Перечислимые константы ADO](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Приложение б. ошибки ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [События ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Методы ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Объектная модель ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Свойства ADO](../../../ado/reference/ado-api/ado-properties.md)
