---
description: Обзор службы Microsoft OLE DB Provider для Microsoft Indexing Service
title: Поставщик Microsoft OLE DB для службы индексирования (Майкрософт) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Indexing Service provider [ADO]
- providers [ADO], OLE DB provider for Microsoft Indexing service
- OLE DB provider for Microsoft Indexing service [ADO]
ms.assetid: f86a0598-5097-471b-8318-d2c859d085f2
author: rothja
ms.author: jroth
ms.openlocfilehash: b3e479ca023efb704bf496c9ffaeaca2f1b6ba15
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991045"
---
# <a name="microsoft-ole-db-provider-for-microsoft-indexing-service-overview"></a>Обзор службы Microsoft OLE DB Provider для Microsoft Indexing Service
Поставщик Microsoft OLE DB для службы индексирования Майкрософт предоставляет программный доступ только для чтения к файловой системе и веб-данным, индексированным службой индексирования Майкрософт. Приложения ADO могут выдавать SQL запросы для получения сведений о содержимом и свойствах файла.

 Поставщик бесплатен и поддерживает Юникод.

## <a name="connection-string-parameters"></a>Параметры строки соединения
 Чтобы подключиться к этому поставщику, задайте для аргумента **provider =** свойства [ConnectionString](../../reference/ado-api/connectionstring-property-ado.md) значение:

```vb
MSIDXS
```

 При чтении свойства [поставщика](../../reference/ado-api/provider-property-ado.md) также будет возвращена эта строка.

## <a name="typical-connection-string"></a>Типичная строка подключения
 Типичная строка подключения для этого поставщика:

```vb
"Provider=MSIDXS;Data Source=myCatalog;Locale Identifier=nnnn;"
```

 Строка состоит из следующих ключевых слов:

|Ключевое слово|Описание|
|-------------|-----------------|
|**Поставщик**|Указывает поставщика OLE DB для службы индексирования (Майкрософт). Обычно это единственное ключевое слово, указанное в строке подключения.|
|**Источник данных**|Указывает имя каталога службы индексирования. Если это ключевое слово не указано, используется системный каталог по умолчанию.|
|**Идентификатор локали**|Задает уникальное 32-разрядное число (например, 1033), которое указывает параметры, относящиеся к языку пользователя. Если это ключевое слово не указано, используется идентификатор локали системы по умолчанию.|

## <a name="command-text"></a>Текст команды
 Синтаксис запроса SQL службы индексирования состоит из расширений для инструкции **SELECT** sql-92 и предложений **from** и **WHERE** . Результаты запроса возвращаются с помощью OLE DB наборов строк, которые могут использоваться ADO и обрабатываются как объекты [Recordset](../../reference/ado-api/recordset-object-ado.md) .

 Можно выполнять поиск точных слов или фраз или использовать подстановочные знаки для поиска шаблонов или слов. Логика поиска может основываться на логических решениях, взвешенных условиях или относительно других слов. Можно также выполнить поиск по слову "бесплатный текст", который находит совпадения по смыслу, а не к точным словам.

 Конкретный диалект команды полностью документирован в документации по службе индексирования в языке запросов.

 Поставщик не принимает вызовы хранимых процедур или простые имена таблиц (например, свойство [CommandType](../../reference/ado-api/commandtype-property-ado.md) всегда будет **адкмдтекст**).

## <a name="recordset-behavior"></a>Поведение набора записей
 В следующих таблицах перечислены функции, доступные для объекта **набора записей** , открытого с помощью этого поставщика. Доступен только статический тип курсора (**адопенстатик**).

 Чтобы получить более подробные сведения о поведении **набора записей** для конфигурации поставщика, выполните метод [поддерживает](../../reference/ado-api/supports-method.md) и перечислите коллекцию [свойств](../../reference/ado-api/properties-collection-ado.md) **набора записей** , чтобы определить, имеются ли связанные с поставщиком динамические свойства.

 **Доступность стандартных свойств набора записей ADO:**

|Свойство|Доступность|
|--------------|------------------|
|[Примеры absolutepage](../../reference/ado-api/absolutepage-property-ado.md)|чтение/запись|
|[Примеры AbsolutePosition](../../reference/ado-api/absoluteposition-property-ado.md)|чтение/запись|
|[ActiveConnection](../../reference/ado-api/activeconnection-property-ado.md)|Только для чтения|
|[BOF](../../reference/ado-api/bof-eof-properties-ado.md)|Только для чтения|
|[Закладка](../../reference/ado-api/bookmark-property-ado.md)*|чтение/запись|
|[CacheSize](../../reference/ado-api/cachesize-property-ado.md)|чтение/запись|
|[CursorLocation](../../reference/ado-api/cursorlocation-property-ado.md)|всегда **адусесервер**|
|[Примеры CursorType](../../reference/ado-api/cursortype-property-ado.md)|всегда **адопенстатик**|
|[EditMode](../../reference/ado-api/editmode-property.md)|всегда **адедитноне**|
|[КОНЦА](../../reference/ado-api/bof-eof-properties-ado.md)|Только для чтения|
|[Filter](../../reference/ado-api/filter-property.md)|чтение/запись|
|[LockType](../../reference/ado-api/locktype-property-ado.md)|чтение/запись|
|[MarshalOptions](../../reference/ado-api/marshaloptions-property-ado.md)|недоступно|
|[MaxRecords](../../reference/ado-api/maxrecords-property-ado.md)|чтение/запись|
|[PageCount](../../reference/ado-api/pagecount-property-ado.md)|Только для чтения|
|[PageSize](../../reference/ado-api/pagesize-property-ado.md)|чтение/запись|
|[RecordCount](../../reference/ado-api/recordcount-property-ado.md)|Только для чтения|
|[Source](../../reference/ado-api/source-property-ado-recordset.md)|чтение/запись|
|[Состояние](../../reference/ado-api/state-property-ado.md)|Только для чтения|
|[Состояние](../../reference/ado-api/status-property-ado-recordset.md)|Только для чтения|

 \*Чтобы эта функция существовала в **наборе записей**, для поставщика необходимо включить закладки.

 **Доступность стандартных методов набора записей ADO:**

|Метод|Доступно?|
|------------|----------------|
|[Вызов](../../reference/ado-api/addnew-method-ado.md)|Нет|
|[Отмена](../../reference/ado-api/cancel-method-ado.md)|Да|
|[CancelBatch](../../reference/ado-api/cancelbatch-method-ado.md)|Нет|
|[CancelUpdate](../../reference/ado-api/cancelupdate-method-ado.md)|Нет|
|[Клонировать](../../reference/ado-api/clone-method-ado.md)|Да|
|[Закрыть](../../reference/ado-api/close-method-ado.md)|Да|
|[Удаление](../../reference/ado-api/delete-method-ado-recordset.md)|Нет|
|[GetRows](../../reference/ado-api/getrows-method-ado.md)|Да|
|[Перемещение](../../reference/ado-api/move-method-ado.md)|Да|
|[MoveFirst](../../reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|
|[NextRecordset](../../reference/ado-api/nextrecordset-method-ado.md)|Да|
|[Открыть](../../reference/ado-api/open-method-ado-recordset.md)|Да|
|[Повтор](../../reference/ado-api/requery-method.md)|Да|
|[Повторная синхронизация](../../reference/ado-api/resync-method.md)|Да|
|[Поддерживает](../../reference/ado-api/supports-method.md)|Да|
|[Обновление](../../reference/ado-api/update-method.md)|Нет|
|[UpdateBatch](../../reference/ado-api/updatebatch-method.md)|Нет|

 Для получения сведений о конкретной реализации и функциональных сведений о поставщике Microsoft OLE DB для службы индексирования Майкрософт обратитесь к [руководству по OLE DB](/previous-versions/windows/desktop/ms713643(v=vs.85))или посетите страницу веб-службы на веб-сайте Windows NT Server.

## <a name="see-also"></a>См. также
 Свойство [CommandType (объекты (ADO)](../../reference/ado-api/commandtype-property-ado.md) свойства [ConnectionString](../../reference/ado-api/connectionstring-property-ado.md) (ADO) свойство [поставщика](../../reference/ado-api/provider-property-ado.md) [коллекции](../../reference/ado-api/properties-collection-ado.md) (ADO) [объект Recordset](../../reference/ado-api/recordset-object-ado.md) (ADO) [поддерживает метод](../../reference/ado-api/supports-method.md)