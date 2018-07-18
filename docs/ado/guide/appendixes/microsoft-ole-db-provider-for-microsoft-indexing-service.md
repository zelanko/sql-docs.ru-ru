---
title: Поставщик Microsoft OLE DB для службы индексирования Microsoft | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Indexing Service provider [ADO]
- providers [ADO], OLE DB provider for Microsoft Indexing service
- OLE DB provider for Microsoft Indexing service [ADO]
ms.assetid: f86a0598-5097-471b-8318-d2c859d085f2
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b789802f6a8d565119450183889d238d2e3f498e
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35271313"
---
# <a name="microsoft-ole-db-provider-for-microsoft-indexing-service-overview"></a>Поставщик Microsoft OLE DB для индексирования Обзор службы Microsoft
Поставщик Microsoft OLE DB для службы индексирования Microsoft предоставляет программный доступ только для чтения к файловая система и веб-данных службой индексирования Microsoft. Приложения ADO могут выдавать запросы SQL для извлечения содержимого и файл сведений.

 Поставщик является свободнопотоковым и Юникод.

## <a name="connection-string-parameters"></a>Параметры строки соединения
 Чтобы подключиться к этому поставщику, задайте **поставщика =** аргумент [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойства:

```
MSIDXS
```

 Чтение [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойство возвратит также этой строки.

## <a name="typical-connection-string"></a>Обычная строка соединения
 — Строка соединения для данного поставщика:

```
"Provider=MSIDXS;Data Source=myCatalog;Locale Identifier=nnnn;"
```

 Строка состоит из следующих ключевых слов:

|Ключевое слово|Описание|
|-------------|-----------------|
|**Поставщик**|Указывает поставщика OLE DB для службы индексирования Microsoft. Как правило, это указано в строке соединения только ключевое слово.|
|**Источник данных**|Задает имя каталога службы индексирования. Если это ключевое слово не указан, используется системный каталог по умолчанию.|
|**Идентификатор локали**|Указывает уникальный 32-разрядное число (например, 1033), указывающее параметры, связанные с языком пользователя. Если это ключевое слово не указан, используется код языка системы по умолчанию.|

## <a name="command-text"></a>Текст команды
 Синтаксис запроса SQL службы индексирования состоит из расширений SQL-92 для **ВЫБЕРИТЕ** инструкции и его **FROM** и **ГДЕ** предложения. Результаты запроса возвращаются через наборы строк OLE DB, который может использоваться с ADO и управлять как [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объектов.

 Можно выполнить поиск точного слова или фразы или использовать подстановочные знаки для поиска шаблонов или основам слов. Логика поиска могут основываться на логические решения, взвешенных выражений или близости от других слов. Кроме того, можно выполнить поиск с «произвольный текст», который находит соответствий на основании значения, а не точного слова.

 Диалект конкретной команды полностью описаны в документации по службе индексирования языки запросов.

 Поставщик не поддерживает вызовы хранимых процедур и имена простую таблицу (например, [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) всегда будет иметь свойство **adCmdText**).

## <a name="recordset-behavior"></a>Поведение набора записей
 В следующих таблицах перечислены функции, доступные на **записей** открыть объект с этим поставщиком. Только тип статического курсора (**adOpenStatic**) доступен.

 Для получения дополнительных сведений о **записей** поведение конфигурации поставщика, запустите [поддерживает](../../../ado/reference/ado-api/supports-method.md) метод и перечисление [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекцию **Записей** для определения того, присутствуют ли динамические свойства от поставщика.

 **Доступность стандартных свойств набора записей ADO:**

|Свойство|Доступность|
|--------------|------------------|
|[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|чтение/запись|
|[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|чтение/запись|
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|только для чтения|
|[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|только для чтения|
|[Закладка](../../../ado/reference/ado-api/bookmark-property-ado.md)*|чтение/запись|
|[cacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|чтение/запись|
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|всегда **adUseServer**|
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|всегда **adOpenStatic**|
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|всегда **как таковые**|
|[КОНЕЦ ФАЙЛА](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|только для чтения|
|[Фильтр](../../../ado/reference/ado-api/filter-property.md)|чтение/запись|
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|чтение/запись|
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|недоступно|
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|чтение/запись|
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|только для чтения|
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|чтение/запись|
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|только для чтения|
|[Source](../../../ado/reference/ado-api/source-property-ado-recordset.md)|чтение/запись|
|[Состояние](../../../ado/reference/ado-api/state-property-ado.md)|только для чтения|
|[Состояние](../../../ado/reference/ado-api/status-property-ado-recordset.md)|только для чтения|

 \*Закладки должна быть включена на поставщика в этой функции на существует **записей**.

 **Доступность стандартных методов набора записей ADO:**

|Метод|Доступны?|
|------------|----------------|
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|Нет|
|[Отмена](../../../ado/reference/ado-api/cancel-method-ado.md)|Да|
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|Нет|
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|Нет|
|[Клон](../../../ado/reference/ado-api/clone-method-ado.md)|Да|
|[Закрыть](../../../ado/reference/ado-api/close-method-ado.md)|Да|
|[Удаление](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|Нет|
|[Получение строк](../../../ado/reference/ado-api/getrows-method-ado.md)|Да|
|[Переместить](../../../ado/reference/ado-api/move-method-ado.md)|Да|
|[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)|Да|
|[Открытие](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Да|
|[Повторный запрос](../../../ado/reference/ado-api/requery-method.md)|Да|
|[Повторная синхронизация](../../../ado/reference/ado-api/resync-method.md)|Да|
|[Поддерживает](../../../ado/reference/ado-api/supports-method.md)|Да|
|[Update](../../../ado/reference/ado-api/update-method.md)|Нет|
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|Нет|

 Особенности реализации и функционального сведения о поставщик Microsoft OLE DB для службы индексирования Microsoft, обратитесь к [Руководство программиста OLE DB](https://msdn.microsoft.com/library/windows/desktop/ms713643.aspx), или посетите веб-сайт веб-службы веб-сервера Windows NT веб-узел.

## <a name="see-also"></a>См. также
 [Свойство CommandType (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md) [свойство ConnectionString (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [коллекции свойств (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) [свойство поставщика (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) [ Объект набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [поддерживает метод](../../../ado/reference/ado-api/supports-method.md)
