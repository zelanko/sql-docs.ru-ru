---
title: Индекс динамических свойств ADO | Документация Майкрософт
ms.prod: sql
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- dynamic properties [ADO], index
ms.assetid: 80d389dd-46ef-459f-b0d4-6f712fc4f32d
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8dd1263d19972124166e1e11d91c8370fc3a9ff0
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66696733"
---
# <a name="ado-dynamic-property-index"></a>Индекс динамических свойств ADO
Поставщики данных, поставщиков служб и компонентов службы можно добавить все динамические свойства **свойства** коллекции неоткрытый [подключения](../../../ado/reference/ado-api/connection-object-ado.md) и [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекты. Данного поставщика также может добавить дополнительные свойства, при открытии этих объектов. Некоторые из этих свойств, перечислены в [динамические свойства ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md) раздел. Сведения отображаются в категории определенными поставщиками в [приложении a. Поставщики](../../../ado/guide/appendixes/appendix-a-providers.md) раздел.  
  
 В следующих таблицах представлены cross-indexes имен для каждого стандартный OLE DB поставщика динамические свойства ADO и OLE DB. Ваши поставщики могут добавлять больше свойств, чем перечисленные ниже. Сведения о динамических свойствах конкретного поставщика см. в документации поставщика.  
  
 Справочник программиста OLE DB по указано имя свойства ADO с термином «Description». Дополнительные сведения об этих свойствах стандартный поиск или просмотр индекса в [документации OLE DB](https://msdn.microsoft.com/library/windows/desktop/ms722784.aspx)свойства OLE DB по его имени.  
  
## <a name="connection-dynamic-properties"></a>Динамические свойства подключения  
  
|Имя свойства ADO|Имя свойства OLE DB|  
|-----------------------|--------------------------|  
|Активные сеансы|DBPROP_ACTIVESESSIONS|  
|Асинхронное прерывание работы|DBPROP_ASYNCTXNABORT|  
|Асинхронная фиксация|DBPROP_ASYNCTNXCOMMIT|  
|Уровни изоляции автофиксации|DBPROP_SESS_AUTOCOMMITISOLEVELS|  
|Расположение каталога|DBPROP_CATALOGLOCATION|  
|Термин каталога|DBPROP_CATALOGTERM|  
|Определение столбца|DBPROP_COLUMNDEFINITION|  
|Время ожидания соединения|DBPROP_INIT_TIMEOUT|  
|Текущий каталог|DBPROP_CURRENTCATALOG|  
|Источник данных|DBPROP_INIT_DATASOURCE|  
|Имя источника данных|DBPROP_DATASOURCENAME|  
|Потоковая модель объекта источника данных|DBPROP_DSOTHREADMODEL|  
|Имя СУБД|DBPROP_DBMSNAME|  
|Версия СУБД|DBPROP_DBMSVER|  
|Расширенные свойства|DBPROP_INIT_PROVIDERSTRING|  
|Поддержка оператора GROUP BY|DBPROP_GROUPBY|  
|Поддержка гетерогенных таблиц|DBPROP_HETEROGENEOUSTABLES|  
|Чувствительность идентификатора к регистру|DBPROP_IDENTIFIERCASE|  
|Исходный каталог|DBPROP_INIT_CATALOG|  
|Уровни изоляции|DBPROP_SUPPORTEDTXNISOLEVELS|  
|Сохранение изоляции|DBPROP_SUPPORTEDTXNISORETAIN|  
|Идентификатор локали|DBPROP_INIT_LCID|  
|Местоположение|DBPROP_INIT_LOCATION|  
|Максимальный размер индекса|DBPROP_MAXINDEXSIZE|  
|Максимальный размер строки|DBPROP_MAXROWSIZE|  
|Максимальный размер строки, включая BLOB|DBPROP_MAXROWSIZEINCLUDESBLOB|  
|Максимальное число таблиц в SELECT|DBPROP_MAXTABLESINSELECT|  
|Режим|DBPROP_INIT_MODE|  
|Несколько наборов параметров|DBPROP_MULTIPLEPARAMSETS|  
|Множественные результаты|DBPROP_MULTIPLERESULTS|  
|Несколько объектов хранилища|DBPROP_MULTIPLESTORAGEOBJECTS|  
|Многотабличное обновление|DBPROP_MULTITABLEUPDATE|  
|Порядок сортировки NULL|DBPROP_NULLCOLLATION|  
|Поведение при конкатенации с NULL|DBPROP_CONCATNULLBEHAVIOR|  
|Службы OLE DB|DBPROP_INIT_OLEDBSERVICES|  
|Версия OLE DB|DBPROP_PROVIDEROLEDBVER|  
|Поддержка объектов OLE|DBPROP_OLEOBJECTS|  
|Поддержка открытия наборов данных|DBPROP_OPENROWSETSUPPORT|  
|Столбцы ORDER BY в списке выбора|DBPROP_ORDERBYCOLUMNSINSELECT|  
|Доступность параметра вывода|DBPROP_OUTPUTPARAMETERAVAILABILITY|  
|Передавать по указанные методы|DBPROP_BYREFACCESSORS|  
|Пароль|DBPROP_AUTH_PASSWORD|  
|Сохранять сведения о безопасности|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|  
|Тип постоянного ИД|DBPROP_PERSISTENTIDTYPE|  
|При подготовке прерывания работы|DBPROP_PREPAREABORTBEHAVIOR|  
|Поведение при подготовке фиксации|DBPROP_PREPARECOMMITBEHAVIOR|  
|Термин процедуры|DBPROP_PROCEDURETERM|  
|Запрос|DBPROP_INIT_PROMPT|  
|Понятное имя поставщика|DBPROP_PROVIDERFRIENDLYNAME|  
|Provider Name|DBPROP_PROVIDERFILENAME|  
|Версия поставщика|DBPROP_PROVIDERVER|  
|Источник данных только для чтения|DBPROP_DATASOURCEREADONLY|  
|Преобразования набора строк по команде|DBPROP_ROWSETCONVERSIONSONCOMMAND|  
|Термин схемы|DBPROP_SCHEMATERM|  
|Использование схемы|DBPROP_SCHEMAUSAGE|  
|Поддержка SQL|DBPROP_SQLSUPPORT|  
|Структурированное хранилище|DBPROP_STRUCTUREDSTORAGE|  
|Поддержка подзапросов|DBPROP_SUBQUERIES|  
|Термин таблицы|DBPROP_TABLETERM|  
|DDL транзакций|DBPROP_SUPPORTEDTXNDDL|  
|Идентификатор пользователя|DBPROP_AUTH_USERID|  
|Имя пользователя|DBPROP_USERNAME|  
|Дескриптор окна|DBPROP_INIT_HWND|  
  
## <a name="recordset-dynamic-properties"></a>Динамические свойства набора записей  
 Обратите внимание, что **динамические свойства** из **записей** объекта перейдите за пределы области действия (становятся недоступными) при **записей** закрыт.  
  
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
|Асинхронная обработка набора строк|DBPROP_ROWSET_ASYNCH|  
|Автоматическое повторное вычисление|DBPROP_ADC_AUTORECALC|  
|Размер выборки в фоновом режиме|DBPROP_ASYNCHFETCHSIZE|  
|Приоритет фонового потока|DBPROP_ASYNCHTHREADPRIORITY|  
|Размер пакета|DBPROP_ADC_BATCHSIZE|  
|Блокирование объектов хранилища|DBPROP_BLOCKINGSTORAGEOBJECTS|  
|Тип закладки|DBPROP_BOOKMARKTYPE|  
|Bookmarkable|DBPROP_IROWSETLOCATE|  
|Закладки упорядочены|DBPROP_ORDEREDBOOKMARKS|  
|Кэш дочерних строк|DBPROP_ADC_CACHECHILDROWS|  
|Кэш отложенного столбцов|DBPROP_CACHEDEFERRED|  
|Изменение вставленных строк|DBPROP_CHANGEINSERTEDROWS|  
|Права доступа столбца|DBPROP_COLUMNRESTRICT|  
|Уведомление о задании столбца|DBPROP_NOTIFYCOLUMNSET|  
|Столбец для записи|DBPROP_MAYWRITECOLUMN|  
|Время ожидания команды|DBPROP_COMMANDTIMEOUT|  
|Версия подсистемы курсора|DBPROP_ADC_CEVER|  
|Отложить столбца|DBPROP_DEFERRED|  
|Отложенное обновление объекта хранилища|DBPROP_DELAYSTORAGEOBJECTS|  
|Выборка в обратном порядке|DBPROP_CANFETCHBACKWARDS|  
|Операции фильтрации|DBPROP_FILTERCOMPAREOPS|  
|Операции по поиску|DBPROP_FINDCOMPAREOPS|  
|Скрытые столбцы (количество)|DBPROP_HIDDENCOLUMNS|  
|Удерживайте строк|DBPROP_CANHOLDROWS|  
|Фиксированные строки|DBPROP_IMMOBILEROWS|  
|Размер начального выборки|DBPROP_ASYNCHPREFETCHSIZE|  
|Литеральные закладки|DBPROP_LITERALBOOKMARKS|  
|Литеральная Идентификация строки|DBPROP_LITERALIDENTITY|  
|Поддерживать изменение состояния|DBPROP_ADC_MAINTAINCHANGESTATUS|  
|Максимальное число открытых строк|DBPROP_MAXOPENROWS|  
|Максимальное число ожидающих строк|DBPROP_MAXPENDINGROWS|  
|Максимальное число строк|DBPROP_MAXROWS|  
|Использование памяти|DBPROP_MEMORYUSAGE|  
|Уровень детализации уведомления|DBPROP_NOTIFICATIONGRANULARITY|  
|Этапы уведомлений|DBPROP_NOTIFICATIONPHASES|  
|Обработано объектов транзакций|DBPROP_TRANSACTEDOBJECT|  
|Видны прочие изменения|DBPROP_OTHERUPDATEDELETE|  
|Других пользователей видимость строк, вставленных|DBPROP_OTHERINSERT|  
|Видимость собственных изменений|DBPROP_OWNUPDATEDELETE|  
|Видимость собственных операций вставки|DBPROP_OWNINSERT|  
|Сохранение при прерывании работы|DBPROP_ABORTPRESERVE|  
|Сохранение при фиксации|DBPROP_COMMITPRESERVE|  
|Private1||  
|Быстрый перезапуск|DBPROP_QUICKRESTART|  
|События с повторным входом|DBPROP_REENTRANTEVENTS|  
|Уничтожение удаленных строк|DBPROP_REMOVEDELETED|  
|Отчет о множественных изменениях|DBPROP_REPORTMULTIPLECHANGES|  
|Изменить имя|DBPROP_ADC_RESHAPENAME|  
|Команда синхронизации|DBPROP_ADC_CUSTOMRESYNCH|  
|Возврат ожидающих операций вставки|DBPROP_RETURNPENDINGINSERTS|  
|Уведомление об удалении строки|DBPROP_NOTIFYROWDELETE|  
|Уведомление о первом изменении строки|DBPROP_NOTIFYROWFIRSTCHANGE|  
|Уведомление о вставке строки|DBPROP_NOTIFYROWINSERT|  
|Права строки|DBPROP_ROWRESTRICT|  
|Уведомление о повторной синхронизации строки|DBPROP_NOTIFYROWRESYNCH|  
|Потоковая модель строки|DBPROP_ROWTHREADMODEL|  
|Уведомление об отмене изменений строки|DBPROP_NOTIFYROWUNDOCHANGE|  
|Уведомление об отмене удаления строки|DBPROP_NOTIFYROWUNDODELETE|  
|Уведомление об отмене вставки строки|DBPROP_NOTIFYROWUNDOINSERT|  
|Уведомление об обновлении строки|DBPROP_NOTIFYROWUPDATE|  
|Уведомление об изменении позиции выборки набора строк|DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE|  
|Уведомление о разблокировании набора строк|DBPROP_NOTIFYROWSETRELEASE|  
|Обратная прокрутка|DBPROP_CANSCROLLBACKWARDS|  
|Серверный курсор|DBPROP_SERVERCURSOR|  
|Пропуск удаленных закладок|DBPROP_BOOKMARKSKIPPED|  
|Строгая Идентификация строки|DBPROP_STRONGIDENTITY|  
|Уникальный каталог|DBPROP_ADC_UNIQUECATALOG|  
|Уникальные строки|DBPROP_UNIQUEROWS|  
|Уникальной схемы|DBPROP_ADC_UNIQUESCHEMA|  
|уникальная таблица|DBPROP_ADC_UNIQUETABLE|  
|Возможности обновления|DBPROP_UPDATABILITY|  
|Обновления условиям|DBPROP_ADC_UPDATECRITERIA|  
|Повторная синхронизация обновления|DBPROP_ADC_UPDATERESYNC|  
|Использование закладок|DBPROP_BOOKMARKS|
