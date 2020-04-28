---
title: Индекс динамического свойства ADO | Документация Майкрософт
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
ms.openlocfilehash: 9eb88905f56abf9c1c702f5fd73cbe61a1bcde3d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67921085"
---
# <a name="ado-dynamic-property-index"></a>Индекс динамических свойств ADO
Поставщики данных, поставщики служб и компоненты служб могут добавлять динамические свойства в коллекции **свойств** неоткрытых [соединений](../../../ado/reference/ado-api/connection-object-ado.md) и объектов [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) . Данный поставщик может также вставлять дополнительные свойства при открытии этих объектов. Некоторые из этих свойств перечислены в разделе [динамические свойства ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md) . Дополнительные сведения см. в разделе "конкретные поставщики" раздела [приложение A: поставщики](../../../ado/guide/appendixes/appendix-a-providers.md) .  
  
 Следующие таблицы являются перекрестными индексами имен ADO и OLE DB для каждого динамического свойства стандартного поставщика OLE DB. Поставщики могут добавлять больше свойств, чем указано здесь. Конкретные сведения о динамических свойствах, связанных с поставщиком, см. в документации поставщика.  
  
 Ссылка на OLE DB программиста ссылается на имя свойства ADO по термину «описание». Для получения дополнительных сведений об этих стандартных свойствах найдите или просмотрите индекс в [OLE DB документации](https://msdn.microsoft.com/library/windows/desktop/ms722784.aspx)по свойству OLE DB по его имени.  
  
## <a name="connection-dynamic-properties"></a>Динамические свойства подключения  
  
|Имя свойства ADO|Имя свойства OLE DB|  
|-----------------------|--------------------------|  
|Активные сеансы|DBPROP_ACTIVESESSIONS|  
|Прервать асинхронная|DBPROP_ASYNCTXNABORT|  
|Асинхронная фиксация|DBPROP_ASYNCTNXCOMMIT|  
|Уровни изоляции с автоматической фиксацией|DBPROP_SESS_AUTOCOMMITISOLEVELS|  
|Расположение каталога|DBPROP_CATALOGLOCATION|  
|Термин каталога|DBPROP_CATALOGTERM|  
|Определение столбца|DBPROP_COLUMNDEFINITION|  
|Время ожидания соединения|DBPROP_INIT_TIMEOUT|  
|Текущий каталог|DBPROP_CURRENTCATALOG|  
|Источник данных|DBPROP_INIT_DATASOURCE|  
|Имя базы данных-источника|DBPROP_DATASOURCENAME|  
|Потоковая модель объекта источника данных|DBPROP_DSOTHREADMODEL|  
|Имя СУБД|DBPROP_DBMSNAME|  
|Версия СУБД|DBPROP_DBMSVER|  
|Расширенные свойства|DBPROP_INIT_PROVIDERSTRING|  
|ГРУППИРОВКа по поддержке|DBPROP_GROUPBY|  
|Поддержка разнородных таблиц|DBPROP_HETEROGENEOUSTABLES|  
|Чувствительность идентификатора к регистру|DBPROP_IDENTIFIERCASE|  
|Исходный каталог|DBPROP_INIT_CATALOG|  
|Уровни изоляции|DBPROP_SUPPORTEDTXNISOLEVELS|  
|Хранение изоляции|DBPROP_SUPPORTEDTXNISORETAIN|  
|Идентификатор локали|DBPROP_INIT_LCID|  
|Расположение|DBPROP_INIT_LOCATION|  
|Максимальный размер индекса|DBPROP_MAXINDEXSIZE|  
|Максимальный размер строки|DBPROP_MAXROWSIZE|  
|Максимальный размер строки включает большой двоичный объект|DBPROP_MAXROWSIZEINCLUDESBLOB|  
|Максимальное число таблиц в SELECT|DBPROP_MAXTABLESINSELECT|  
|Режим|DBPROP_INIT_MODE|  
|Несколько наборов параметров|DBPROP_MULTIPLEPARAMSETS|  
|Множественные результаты|DBPROP_MULTIPLERESULTS|  
|Несколько объектов хранилища|DBPROP_MULTIPLESTORAGEOBJECTS|  
|Обновление нескольких таблиц|DBPROP_MULTITABLEUPDATE|  
|Порядок параметров сортировки NULL|DBPROP_NULLCOLLATION|  
|Поведение сцепления со значением NULL|DBPROP_CONCATNULLBEHAVIOR|  
|Службы OLE DB|DBPROP_INIT_OLEDBSERVICES|  
|Версия OLE DB|DBPROP_PROVIDEROLEDBVER|  
|Поддержка объектов OLE|DBPROP_OLEOBJECTS|  
|Поддержка открытых наборов строк|DBPROP_OPENROWSETSUPPORT|  
|УПОРЯДОЧЕНие по столбцам в списке выбора|DBPROP_ORDERBYCOLUMNSINSELECT|  
|Доступность выходного параметра|DBPROP_OUTPUTPARAMETERAVAILABILITY|  
|Методы доступа для передачи по ссылке|DBPROP_BYREFACCESSORS|  
|Пароль|DBPROP_AUTH_PASSWORD|  
|Сохранять сведения о безопасности|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|  
|Тип постоянного идентификатора|DBPROP_PERSISTENTIDTYPE|  
|Поведение при подготовке к прерыванию|DBPROP_PREPAREABORTBEHAVIOR|  
|Действие подготовки к фиксации|DBPROP_PREPARECOMMITBEHAVIOR|  
|Условие процедуры|DBPROP_PROCEDURETERM|  
|prompt|DBPROP_INIT_PROMPT|  
|Понятное имя поставщика|DBPROP_PROVIDERFRIENDLYNAME|  
|Provider Name|DBPROP_PROVIDERFILENAME|  
|Версия поставщика|DBPROP_PROVIDERVER|  
|Источник данных только для чтения|DBPROP_DATASOURCEREADONLY|  
|Преобразования наборов строк для команды|DBPROP_ROWSETCONVERSIONSONCOMMAND|  
|Термин схемы|DBPROP_SCHEMATERM|  
|Использование схемы|DBPROP_SCHEMAUSAGE|  
|Поддержка SQL|DBPROP_SQLSUPPORT|  
|Структурированное хранилище|DBPROP_STRUCTUREDSTORAGE|  
|Поддержка вложенных запросов|DBPROP_SUBQUERIES|  
|Термин таблицы|DBPROP_TABLETERM|  
|DDL транзакции|DBPROP_SUPPORTEDTXNDDL|  
|Идентификатор пользователя.|DBPROP_AUTH_USERID|  
|Имя пользователя|DBPROP_USERNAME|  
|Дескриптор окна|DBPROP_INIT_HWND|  
  
## <a name="recordset-dynamic-properties"></a>Динамические свойства набора записей  
 Обратите внимание, что **динамические свойства** объекта **Recordset** выходят за пределы области видимости (становятся недоступными) при закрытии **набора записей** .  
  
|Имя свойства ADO|Имя свойства OLE DB|  
|-----------------------|--------------------------|  
|IAccessor|DBPROP_IACCESSOR|  
|ичаптередровсет||  
|IColumnsInfo|DBPROP_ICOLUMNSINFO|  
|IColumnsRowset|DBPROP_ICOLUMNSROWSET|  
|IConnectionPointContainer|DBPROP_ICONNECTIONPOINTCONTAINER|  
|IConvertType||  
|ILockBytes|DBPROP_ILOCKBYTES|  
|IRowset|DBPROP_IROWSET|  
|IDBAsynchStatus|DBPROP_IDBASYNCHSTATUS|  
|ипарентровсет||  
|IRowsetChange|DBPROP_IROWSETCHANGE|  
|ировсетексактскролл||  
|IRowsetFind|DBPROP_IROWSETFIND|  
|ировсетидентити|DBPROP_IROWSETIDENTITY|  
|IRowsetInfo|DBPROP_IROWSETINFO|  
|IRowsetLocate|DBPROP_IROWSETLOCATE|  
|ировсетрефреш|DBPROP_IROWSETREFRESH|  
|Интерфейс irowsetresynch||  
|IRowsetScroll|DBPROP_IROWSETSCROLL|  
|IRowsetUpdate|DBPROP_IROWSETUPDATE|  
|ировсетвиев|DBPROP_IROWSETVIEW|  
|IRowsetIndex|DBPROP_IROWSETINDEX|  
|ISequentialStream|DBPROP_ISEQUENTIALSTREAM|  
|Метод IStorage|DBPROP_ISTORAGE|  
|IStream|DBPROP_ISTREAM|  
|ISupportErrorInfo|DBPROP_ISUPPORTERRORINFO|  
|Порядок доступа|DBPROP_ACCESSORDER|  
|Набор строк только для добавления|DBPROP_APPENDONLY|  
|Асинхронная обработка наборов строк|DBPROP_ROWSET_ASYNCH|  
|Автоматическое повторное вычисление|DBPROP_ADC_AUTORECALC|  
|Размер фоновой выборки|DBPROP_ASYNCHFETCHSIZE|  
|Приоритет фонового потока|DBPROP_ASYNCHTHREADPRIORITY|  
|Размер пакета|DBPROP_ADC_BATCHSIZE|  
|Блокировка объектов хранилища|DBPROP_BLOCKINGSTORAGEOBJECTS|  
|Тип закладки|DBPROP_BOOKMARKTYPE|  
|С закладками|DBPROP_IROWSETLOCATE|  
|Упорядоченные закладки|DBPROP_ORDEREDBOOKMARKS|  
|Дочерние строки кэша|DBPROP_ADC_CACHECHILDROWS|  
|Кэширование отложенных столбцов|DBPROP_CACHEDEFERRED|  
|Изменить вставленные строки|DBPROP_CHANGEINSERTEDROWS|  
|Права доступа к столбцу|DBPROP_COLUMNRESTRICT|  
|Уведомление о наборе столбцов|DBPROP_NOTIFYCOLUMNSET|  
|Столбец доступен для записи|DBPROP_MAYWRITECOLUMN|  
|Время ожидания команды|DBPROP_COMMANDTIMEOUT|  
|Версия обработчика курсоров|DBPROP_ADC_CEVER|  
|Откладывание столбца|DBPROP_DEFERRED|  
|Задержка обновлений объектов хранилища|DBPROP_DELAYSTORAGEOBJECTS|  
|Получить назад|DBPROP_CANFETCHBACKWARDS|  
|Операции фильтрации|DBPROP_FILTERCOMPAREOPS|  
|Поиск операций|DBPROP_FINDCOMPAREOPS|  
|Скрытые столбцы (количество)|DBPROP_HIDDENCOLUMNS|  
|Удержание строк|DBPROP_CANHOLDROWS|  
|Строки немобильных устройств|DBPROP_IMMOBILEROWS|  
|Размер начальной выборки|DBPROP_ASYNCHPREFETCHSIZE|  
|Литеральные закладки|DBPROP_LITERALBOOKMARKS|  
|Удостоверение литеральной строки|DBPROP_LITERALIDENTITY|  
|Ведение состояния изменений|DBPROP_ADC_MAINTAINCHANGESTATUS|  
|Максимальное число открытых строк|DBPROP_MAXOPENROWS|  
|Максимальное число ожидающих строк|DBPROP_MAXPENDINGROWS|  
|Максимальное число строк|DBPROP_MAXROWS|  
|Использование памяти|DBPROP_MEMORYUSAGE|  
|Гранулярность уведомлений|DBPROP_NOTIFICATIONGRANULARITY|  
|Этапы уведомления|DBPROP_NOTIFICATIONPHASES|  
|Транзакционные объекты|DBPROP_TRANSACTEDOBJECT|  
|Изменения видны другим пользователям|DBPROP_OTHERUPDATEDELETE|  
|Видимые вставки других пользователей|DBPROP_OTHERINSERT|  
|Видны собственные изменения|DBPROP_OWNUPDATEDELETE|  
|Видны собственные вставки|DBPROP_OWNINSERT|  
|Сохранить при прерывании|DBPROP_ABORTPRESERVE|  
|Сохранить при фиксации|DBPROP_COMMITPRESERVE|  
|Private1||  
|Быстрый перезапуск|DBPROP_QUICKRESTART|  
|Повторные события|DBPROP_REENTRANTEVENTS|  
|Удалить удаленные строки|DBPROP_REMOVEDELETED|  
|Отчет о нескольких изменениях|DBPROP_REPORTMULTIPLECHANGES|  
|Изменить имя формы|DBPROP_ADC_RESHAPENAME|  
|Команда повторной синхронизации|DBPROP_ADC_CUSTOMRESYNCH|  
|Возврат ожидающих вставок|DBPROP_RETURNPENDINGINSERTS|  
|Уведомление об удалении строки|DBPROP_NOTIFYROWDELETE|  
|Уведомление о первом изменении строки|DBPROP_NOTIFYROWFIRSTCHANGE|  
|Уведомление о вставке строки|DBPROP_NOTIFYROWINSERT|  
|Права доступа к строке|DBPROP_ROWRESTRICT|  
|Уведомление о повторной синхронизации строк|DBPROP_NOTIFYROWRESYNCH|  
|Потоковая модель строк|DBPROP_ROWTHREADMODEL|  
|Уведомление об отмене изменения строки|DBPROP_NOTIFYROWUNDOCHANGE|  
|Уведомление об отмене удаления строки|DBPROP_NOTIFYROWUNDODELETE|  
|Уведомление об отмене вставки строки|DBPROP_NOTIFYROWUNDOINSERT|  
|Уведомление об обновлении строки|DBPROP_NOTIFYROWUPDATE|  
|Уведомление об изменении расположения выборки набора строк|DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE|  
|Уведомление о выпуске набора строк|DBPROP_NOTIFYROWSETRELEASE|  
|Прокрутка назад|DBPROP_CANSCROLLBACKWARDS|  
|Серверный курсор|DBPROP_SERVERCURSOR|  
|Пропустить удаленные закладки|DBPROP_BOOKMARKSKIPPED|  
|Строгая идентификация строк|DBPROP_STRONGIDENTITY|  
|Уникальный каталог|DBPROP_ADC_UNIQUECATALOG|  
|Уникальные строки|DBPROP_UNIQUEROWS|  
|Уникальная схема|DBPROP_ADC_UNIQUESCHEMA|  
|уникальная таблица|DBPROP_ADC_UNIQUETABLE|  
|Updatability|DBPROP_UPDATABILITY|  
|Критерии обновления|DBPROP_ADC_UPDATECRITERIA|  
|Повторная синхронизация обновлений|DBPROP_ADC_UPDATERESYNC|  
|Использование закладок|DBPROP_BOOKMARKS|
