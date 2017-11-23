---
title: "Индекс динамических свойств ADO | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: dynamic properties [ADO], index
ms.assetid: 80d389dd-46ef-459f-b0d4-6f712fc4f32d
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.openlocfilehash: f126cc040174725ded02bd320e54a76536c0d516
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="ado-dynamic-property-index"></a>ADO динамических свойств индекса
Поставщики данных, поставщики служб и компонентов службы можно добавить все динамические свойства **свойства** коллекции Неоткрытое [подключения](../../../ado/reference/ado-api/connection-object-ado.md) и [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекты. Заданный поставщик также может вставить дополнительные свойства, при открытии этих объектов. Некоторые из этих свойств, перечислены в [динамические свойства ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md) раздела. Несколько отображаются в отдельных поставщиков в [приложение A: поставщики](../../../ado/guide/appendixes/appendix-a-providers.md) раздела.  
  
 Следующие таблицы являются cross-indexes имен ADO и OLE DB для каждой стандартной OLE DB поставщик динамических свойств. Ваш поставщики могут добавлять больше свойств, чем перечисленные здесь. Сведения о динамических свойствах поставщика можно найти в документации поставщика.  
  
 Справочник программиста OLE DB указано имя свойства ADO термин «Описание». Дополнительные сведения об этих свойствах стандартный поиск или просмотр индекса в [документации OLE DB](https://msdn.microsoft.com/library/windows/desktop/ms722784.aspx)для свойства OLE DB по его имени.  
  
## <a name="connection-dynamic-properties"></a>Динамические свойства подключения  
  
|Имя свойства ADO|Имя свойства OLE DB|  
|-----------------------|--------------------------|  
|Активные сеансы|DBPROP_ACTIVESESSIONS|  
|Прерывание Asynchable|DBPROP_ASYNCTXNABORT|  
|Asynchable фиксации|DBPROP_ASYNCTNXCOMMIT|  
|Уровни изоляции автоматической фиксации|DBPROP_SESS_AUTOCOMMITISOLEVELS|  
|Расположение каталога|DBPROP_CATALOGLOCATION|  
|Термин каталога|DBPROP_CATALOGTERM|  
|Определение столбца|DBPROP_COLUMNDEFINITION|  
|Время ожидания соединения|DBPROP_INIT_TIMEOUT|  
|Текущий каталог.|DBPROP_CURRENTCATALOG|  
|Источник данных|DBPROP_INIT_DATASOURCE|  
|Имя источника данных|DBPROP_DATASOURCENAME|  
|Потоковая модель объекта источника данных|DBPROP_DSOTHREADMODEL|  
|Имя СУБД|DBPROP_DBMSNAME|  
|Версия СУБД|DBPROP_DBMSVER|  
|Расширенные свойства|DBPROP_INIT_PROVIDERSTRING|  
|Группировать по поддержке|DBPROP_GROUPBY|  
|Поддержка разнородных таблиц|DBPROP_HETEROGENEOUSTABLES|  
|Идентификатор регистра|DBPROP_IDENTIFIERCASE|  
|Исходный каталог|DBPROP_INIT_CATALOG|  
|Уровни изоляции|DBPROP_SUPPORTEDTXNISOLEVELS|  
|Хранение изоляции|DBPROP_SUPPORTEDTXNISORETAIN|  
|Идентификатор локали|DBPROP_INIT_LCID|  
|Местоположение|DBPROP_INIT_LOCATION|  
|Максимальный размер индекса|DBPROP_MAXINDEXSIZE|  
|Максимальный размер строки|DBPROP_MAXROWSIZE|  
|Максимальный размер строки, включая BLOB|DBPROP_MAXROWSIZEINCLUDESBLOB|  
|Максимальное число таблиц в инструкции SELECT|DBPROP_MAXTABLESINSELECT|  
|Режим|DBPROP_INIT_MODE|  
|Несколько наборов параметров|DBPROP_MULTIPLEPARAMSETS|  
|Несколько результатов|DBPROP_MULTIPLERESULTS|  
|Несколько объектов хранилища|DBPROP_MULTIPLESTORAGEOBJECTS|  
|Обновление нескольких таблицы|DBPROP_MULTITABLEUPDATE|  
|Порядок сортировки значений NULL|DBPROP_NULLCOLLATION|  
|Поведение сцепление со значением NULL|DBPROP_CONCATNULLBEHAVIOR|  
|Службы OLE DB|DBPROP_INIT_OLEDBSERVICES, УСТАНОВИТЬ|  
|OLE DB версии|DBPROP_PROVIDEROLEDBVER|  
|Поддержка объекта OLE|DBPROP_OLEOBJECTS|  
|Поддержка открытых наборов строк|DBPROP_OPENROWSETSUPPORT|  
|Столбцы ORDER BY в списке выбора|DBPROP_ORDERBYCOLUMNSINSELECT|  
|Выходной параметр доступности|DBPROP_OUTPUTPARAMETERAVAILABILITY|  
|Передача по событиям Ref|DBPROP_BYREFACCESSORS|  
|Пароль|DBPROP_AUTH_PASSWORD|  
|Сохранять сведения о безопасности|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|  
|Тип сохраняемого идентификатора|DBPROP_PERSISTENTIDTYPE|  
|Подготовка поведение Abort|DBPROP_PREPAREABORTBEHAVIOR|  
|Подготовка поведение фиксации|DBPROP_PREPARECOMMITBEHAVIOR|  
|Термин для процедуры|DBPROP_PROCEDURETERM|  
|Запрос|DBPROP_INIT_PROMPT|  
|Понятное имя поставщика|DBPROP_PROVIDERFRIENDLYNAME|  
|Provider Name|DBPROP_PROVIDERFILENAME|  
|Версия поставщика|DBPROP_PROVIDERVER|  
|Источник данных только для чтения|DBPROP_DATASOURCEREADONLY|  
|Преобразования набора строк для команды|DBPROP_ROWSETCONVERSIONSONCOMMAND|  
|Термин схемы|DBPROP_SCHEMATERM|  
|Использование схемы|DBPROP_SCHEMAUSAGE|  
|Поддержка SQL|DBPROP_SQLSUPPORT|  
|Структурированного хранилища|DBPROP_STRUCTUREDSTORAGE|  
|Поддержка вложенных запросов|DBPROP_SUBQUERIES|  
|Термин таблицы|DBPROP_TABLETERM|  
|Операции DDL|DBPROP_SUPPORTEDTXNDDL|  
|Идентификатор пользователя|DBPROP_AUTH_USERID|  
|Имя пользователя|DBPROP_USERNAME|  
|Дескриптор окна|DBPROP_INIT_HWND|  
  
## <a name="recordset-dynamic-properties"></a>Свойства динамический набор записей  
 Обратите внимание, что **динамические свойства** из **записей** объекта перейдите за пределы области (становятся недоступными) при **записей** закрыт.  
  
|Имя свойства ADO|Имя свойства OLE DB|  
|-----------------------|--------------------------|  
|IAccessor|DBPROP_IACCESSOR|  
|IChapteredRowset||  
|IColumnsInfo|DBPROP_ICOLUMNSINFO|  
|IColumnsRowset|DBPROP_ICOLUMNSROWSET|  
|IConnectionPointContainer|DBPROP_ICONNECTIONPOINTCONTAINER|  
|IConvertType||  
|ILockBytes|DBPROP_ILOCKBYTES|  
|IRowset|DBPROP_IROWSET|  
|IDBAsynchStatus|DBPROP_IDBASYNCHSTATUS|  
|IParentRowset||  
|IRowsetChange|DBPROP_IROWSETCHANGE|  
|IRowsetExactScroll||  
|IRowsetFind|DBPROP_IROWSETFIND|  
|IRowsetIdentity|DBPROP_IROWSETIDENTITY|  
|IRowsetInfo|DBPROP_IROWSETINFO|  
|IRowsetLocate|DBPROP_IROWSETLOCATE|  
|IRowsetRefresh|DBPROP_IROWSETREFRESH|  
|IRowsetResynch||  
|IRowsetScroll|DBPROP_IROWSETSCROLL|  
|IRowsetUpdate|DBPROP_IROWSETUPDATE|  
|IRowsetView|DBPROP_IROWSETVIEW|  
|IRowsetIndex|DBPROP_IROWSETINDEX|  
|ISequentialStream|DBPROP_ISEQUENTIALSTREAM|  
|IStorage|DBPROP_ISTORAGE|  
|IStream|DBPROP_ISTREAM|  
|ISupportErrorInfo|DBPROP_ISUPPORTERRORINFO|  
|Порядок доступа|DBPROP_ACCESSORDER|  
|Только для добавления строк|DBPROP_APPENDONLY|  
|Обработка асинхронных набора строк|DBPROP_ROWSET_ASYNCH|  
|Автоматическое обновление ссылок|DBPROP_ADC_AUTORECALC|  
|Размер выборки фона|DBPROP_ASYNCHFETCHSIZE|  
|Приоритет фонового потока|DBPROP_ASYNCHTHREADPRIORITY|  
|Размер пакета|DBPROP_ADC_BATCHSIZE|  
|Блокировка объектов хранилища|DBPROP_BLOCKINGSTORAGEOBJECTS|  
|Тип закладки|DBPROP_BOOKMARKTYPE|  
|Bookmarkable|DBPROP_IROWSETLOCATE|  
|Упорядоченные закладки|DBPROP_ORDEREDBOOKMARKS|  
|Кэш дочерние строки|DBPROP_ADC_CACHECHILDROWS|  
|Кэш Отложенные столбцы|DBPROP_CACHEDEFERRED|  
|Изменить вставленных строк|DBPROP_CHANGEINSERTEDROWS|  
|Права доступа столбца|DBPROP_COLUMNRESTRICT|  
|Столбец набор уведомлений|DBPROP_NOTIFYCOLUMNSET|  
|Столбец для записи|DBPROP_MAYWRITECOLUMN|  
|Время ожидания команды|DBPROP_COMMANDTIMEOUT|  
|Версия подсистемы курсора|DBPROP_ADC_CEVER|  
|Отложенные столбцы|DBPROP_DEFERRED|  
|Отложенное обновление объекта хранилища|DBPROP_DELAYSTORAGEOBJECTS|  
|Выборку|DBPROP_CANFETCHBACKWARDS|  
|Операции над фильтрами|DBPROP_FILTERCOMPAREOPS|  
|Найти операции|DBPROP_FINDCOMPAREOPS|  
|Скрытые столбцы (число)|DBPROP_HIDDENCOLUMNS|  
|Удерживайте строк|DBPROP_CANHOLDROWS|  
|Немобильные строки|DBPROP_IMMOBILEROWS|  
|Размер начального выборки|DBPROP_ASYNCHPREFETCHSIZE|  
|Литерал закладки|DBPROP_LITERALBOOKMARKS|  
|Идентификатор строки литерала|DBPROP_LITERALIDENTITY|  
|Сохранения изменений состояния|DBPROP_ADC_MAINTAINCHANGESTATUS|  
|Максимальное число открытых строк|DBPROP_MAXOPENROWS|  
|Максимальное количество ожидающих строк|DBPROP_MAXPENDINGROWS|  
|Максимальное число строк|DBPROP_MAXROWS|  
|Использование памяти|DBPROP_MEMORYUSAGE|  
|Гранулярность уведомления|DBPROP_NOTIFICATIONGRANULARITY|  
|Этапы уведомлений|DBPROP_NOTIFICATIONPHASES|  
|Объекты с поддержкой транзакций|DBPROP_TRANSACTEDOBJECT|  
|Видны прочие изменения|DBPROP_OTHERUPDATEDELETE|  
|Чужих вставок видимым|DBPROP_OTHERINSERT|  
|Видны собственные изменения|DBPROP_OWNUPDATEDELETE|  
|Видны собственные операции вставки|DBPROP_OWNINSERT|  
|Сохранять при аварийном завершении|DBPROP_ABORTPRESERVE|  
|Сохранять при фиксации|DBPROP_COMMITPRESERVE|  
|Private1||  
|Быстрый перезапуск|DBPROP_QUICKRESTART|  
|Повторные входящие события|DBPROP_REENTRANTEVENTS|  
|Удаление удаленных строк|DBPROP_REMOVEDELETED|  
|Отчет несколько изменений|DBPROP_REPORTMULTIPLECHANGES|  
|Изменить имя|DBPROP_ADC_RESHAPENAME|  
|Команда синхронизации|DBPROP_ADC_CUSTOMRESYNCH|  
|Вернуть ожидающие выполнения операции вставки|DBPROP_RETURNPENDINGINSERTS|  
|Уведомление об удалении строк|DBPROP_NOTIFYROWDELETE|  
|Первым уведомлением об изменении строки|DBPROP_NOTIFYROWFIRSTCHANGE|  
|Уведомление об вставки строки|DBPROP_NOTIFYROWINSERT|  
|Привилегии строки|DBPROP_ROWRESTRICT|  
|Уведомления повторная синхронизация строк|DBPROP_NOTIFYROWRESYNCH|  
|Потоковая модель строк|DBPROP_ROWTHREADMODEL|  
|Уведомление об отмене изменений строки|DBPROP_NOTIFYROWUNDOCHANGE|  
|Уведомление об отмене удаления строки|DBPROP_NOTIFYROWUNDODELETE|  
|Уведомление об отмене вставки строки|DBPROP_NOTIFYROWUNDOINSERT|  
|Уведомление об обновлении строки|DBPROP_NOTIFYROWUPDATE|  
|Уведомление об изменении позиции выборки набора строк|DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE|  
|Уведомления о выпуске набора строк|DBPROP_NOTIFYROWSETRELEASE|  
|Прокрутка назад|DBPROP_CANSCROLLBACKWARDS|  
|Серверный курсор|DBPROP_SERVERCURSOR|  
|Пропустить удаленные закладки|DBPROP_BOOKMARKSKIPPED|  
|Идентификатор строки строгих|DBPROP_STRONGIDENTITY|  
|Уникальный каталог|DBPROP_ADC_UNIQUECATALOG|  
|Уникальные строки|DBPROP_UNIQUEROWS|  
|Уникальной схемы|DBPROP_ADC_UNIQUESCHEMA|  
|Уникальной таблицы|DBPROP_ADC_UNIQUETABLE|  
|Возможность обновления|DBPROP_UPDATABILITY|  
|Обновление критериев|DBPROP_ADC_UPDATECRITERIA|  
|Повторная синхронизация обновлений|DBPROP_ADC_UPDATERESYNC|  
|С помощью закладок|DBPROP_BOOKMARKS|