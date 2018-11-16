---
title: Поставщик Microsoft OLE DB для службы индексирования Microsoft | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Indexing Service provider [ADO]
- providers [ADO], OLE DB provider for Microsoft Indexing service
- OLE DB provider for Microsoft Indexing service [ADO]
ms.assetid: f86a0598-5097-471b-8318-d2c859d085f2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1b4dfa4771fa60286e054270cb644c72cabe8e40
ms.sourcegitcommit: 96b2355d54dfad259826e88bdff91cc9344e16f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2018
ms.locfileid: "51350358"
---
# <a name="microsoft-ole-db-provider-for-microsoft-indexing-service-overview"></a>Поставщик Microsoft OLE DB для индексирования Общие сведения о службе Microsoft
Поставщик Microsoft OLE DB для службы индексирования Microsoft предоставляет программный доступ только для чтения к файловая система и веб-данных, службой индексирования Microsoft. Приложения ADO можно выполнять запросы SQL для извлечения содержимого и файл сведений.

 Поставщик является свободнопотоковым и Юникод.

## <a name="connection-string-parameters"></a>Параметры строки соединения
 Чтобы подключиться к этим поставщиком, задайте **поставщика =** аргумент [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойства:

```vb
MSIDXS
```

 Чтение [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойство возвратит также эту строку.

## <a name="typical-connection-string"></a>Типичная строка подключения
 — Строка соединения для данного поставщика:

```vb
"Provider=MSIDXS;Data Source=myCatalog;Locale Identifier=nnnn;"
```

 Строка состоит из следующих ключевых слов:

|Ключевое слово|Описание|
|-------------|-----------------|
|**Поставщик**|Указывает поставщика OLE DB для службы индексирования Microsoft. Как правило, это единственное ключевое слово, указанный в строке подключения.|
|**Источник данных**|Указывает имя каталога службы индексирования. Если это ключевое слово не указан, используется системный каталог по умолчанию.|
|**Идентификатор локали**|Число уникальных 32-разрядных (например, 1033), указывающее параметры, связанные с языком пользователя. Если это ключевое слово не указан, используется идентификатор языкового стандарта системы по умолчанию.|

## <a name="command-text"></a>Текст команды
 Синтаксис запроса SQL службы индексирования состоит из расширений SQL-92 **ВЫБЕРИТЕ** инструкции и его **FROM** и **ГДЕ** предложения. Результаты запроса возвращаются через наборы строк OLE DB, который может использоваться с ADO и управляются как [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объектов.

 Можно искать нужные слова или фразы, или используйте подстановочные знаки для поиска шаблонов или основам слов. Логика поиска может основываться на логические решения, рядом с другими словами или взвешенных выражений. Кроме того, можно выполнять поиск по «произвольного текста», который находит совпадений, в зависимости от значения, а не нужные слова.

 Диалект определенной команде полностью описаны в языки запросов для документации по службе индексирования.

 Поставщик не поддерживает вызовы хранимых процедур и простую таблицу имена (например, [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) свойство будет всегда **adCmdText**).

## <a name="recordset-behavior"></a>Поведение набора записей
 В следующих таблицах перечислены функции, доступные в **записей** открыть объект с этим поставщиком. Только тип статического курсора (**adOpenStatic**) доступен.

 Более подробные сведения о **записей** поведение поставщика конфигурации, запустите [поддерживает](../../../ado/reference/ado-api/supports-method.md) метод и перечисление [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекцию **Записей** чтобы определить, присутствует ли динамические свойства от поставщика.

 **Доступность стандартных свойств набора записей ADO.**

|Свойство|Доступность|
|--------------|------------------|
|[Примеры AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|чтение/запись|
|[Примеры AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|чтение/запись|
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|только для чтения|
|[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|только для чтения|
|[Закладка](../../../ado/reference/ado-api/bookmark-property-ado.md)*|чтение/запись|
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|чтение/запись|
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|всегда **adUseServer**|
|[Примеры CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|всегда **adOpenStatic**|
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

 \*Закладки должно быть включено поставщика в этой функции существует во **записей**.

 **Доступность стандартных методов набора записей ADO.**

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
|[Requery](../../../ado/reference/ado-api/requery-method.md)|Да|
|[Повторная синхронизация](../../../ado/reference/ado-api/resync-method.md)|Да|
|[Поддерживает](../../../ado/reference/ado-api/supports-method.md)|Да|
|[Update](../../../ado/reference/ado-api/update-method.md)|Нет|
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|Нет|

 Определенные сведения о реализации и функционального сведения о поставщике Microsoft OLE DB для службы индексирования Microsoft, обратитесь к [Руководство программиста OLE DB](https://msdn.microsoft.com/library/windows/desktop/ms713643.aspx), или на странице веб-службы веб-сервера Windows NT веб-узел.

## <a name="see-also"></a>См. также
 [Свойство CommandType (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md) [свойство ConnectionString (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) [свойство Provider (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) [ Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [поддерживает метод](../../../ado/reference/ado-api/supports-method.md)
