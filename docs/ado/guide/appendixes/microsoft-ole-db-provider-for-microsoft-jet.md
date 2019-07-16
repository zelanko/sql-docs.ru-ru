---
title: Поставщик Microsoft OLE DB для Jet (Майкрософт) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Jet provider for OLE DB [ADO]
- providers [ADO], OLE DB provider for Microsoft Jet
- OLE DB provider for Microsoft Jet [ADO]
ms.assetid: fd956da1-5203-40af-aa7e-fc13a6c6581f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 69d88aebe25f6cfa5490cce736c05780b87eee6e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67926647"
---
# <a name="microsoft-ole-db-provider-for-microsoft-jet-overview"></a>Поставщик Microsoft OLE DB для Jet (Майкрософт) Обзор
Поставщик OLE DB для Jet (Майкрософт) позволяет ADO для доступа к базам данных Microsoft Jet.

## <a name="connection-string-parameters"></a>Параметры строки соединения
 Чтобы подключиться к этим поставщиком, задайте *поставщика* аргумент [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) следующие свойства:

```vb
Microsoft.Jet.OLEDB.4.0
```

 Чтение [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойство вернет эту строку.

## <a name="typical-connection-string"></a>Типичная строка подключения
 — Строка соединения для данного поставщика:

```vb
"Provider=Microsoft.Jet.OLEDB.4.0;Data Source=databaseName;User ID=MyUserID;Password=MyPassword;"
```

 Строка состоит из следующих ключевых слов:

|Ключевое слово|Описание|
|-------------|-----------------|
|**Поставщик**|Указывает поставщика OLE DB для Jet (Майкрософт).|
|**Источник данных**|Указывает путь и имя базы данных (например, `c:\Northwind.mdb`).|
|**Идентификатор пользователя**|Указывает имя пользователя. Если это ключевое слово не указан, строка "`admin`«, используется по умолчанию.|
|**Пароль**|Указывает пароль пользователя. Если это ключевое слово не указан, пустая строка ("»), используется по умолчанию.|

> [!NOTE]
>  Если вы подключаетесь к поставщик источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = yes** или **Integrated Security = SSPI** вместо идентификатора пользователя и пароля сведения в строке подключения.

## <a name="provider-specific-connection-parameters"></a>Параметры подключения для поставщика
 Поставщик OLE DB для Jet (Майкрософт) поддерживает несколько динамических свойств поставщика помимо тех, которые определяются с ADO. Как и в случае со всеми другими **подключения** параметров, их можно задать с помощью **свойства** коллекцию **подключения** объекта или как часть строки подключения.

 Ниже перечислены эти свойства, а также имя соответствующего свойства OLE DB в круглые скобки.

|Параметр|Описание|
|---------------|-----------------|
|Сумма освобожденное место OLEDB:Compact Jet (DBPROP_JETOLEDB_COMPACTFREESPACESIZE)|Указывает приблизительное количество места, в байтах, которые могут быть освобождены при сжатии базы данных. Это значение допустимо только в случае, после установления подключения к базе данных.|
|Элемент управления OLEDB:Connection Jet (DBPROP_JETOLEDB_CONNECTIONCONTROL)|Указывает, могут ли пользователи подключаться к базе данных.|
|Jet OLEDB: Создание базы данных системы (DBPROP_JETOLEDB_CREATESYSTEMDATABASE)|Указывает, должен ли быть создан системную базу данных при создании нового источника данных.|
|Режим блокировки Jet OLEDB: Database (DBPROP_JETOLEDB_DATABASELOCKMODE)|Указывает режим блокировки для этой базы данных. Первый пользователь для открытия базы данных определяет режим, используемый при открытом базы данных.|
|Jet OLEDB: Database Password (DBPROP_JETOLEDB_DATABASEPASSWORD)|Указывает пароль базы данных.|
|Jet OLEDB: не копируйте языковой стандарт в Compact (DBPROP_JETOLEDB_COMPACT_DONTCOPYLOCALE)|Указывает, следует ли Jet копирование информации о языковом стандарте при сжатии базы данных.|
|Jet OLEDB: шифрование базы данных (DBPROP_JETOLEDB_ENCRYPTDATABASE)|Указывает, следует ли шифровать сжатой базы данных. Если это свойство не задано, будут зашифрованы сжатой базы данных, если исходная база данных также был зашифрован.|
|Тип OLEDB:Engine Jet (DBPROP_JETOLEDB_ENGINE)|Указывает подсистему хранилища, используемую для доступа к текущего хранилища данных.|
|Задержка Async OLEDB:Exclusive Jet (DBPROP_JETOLEDB_EXCLUSIVEASYNCDELAY)|Указывает максимальный период времени, в миллисекундах, которое Jet могут вызвать задержку асинхронные операции записи на диск, когда база данных открыта в монопольном режиме.<br /><br /> Это свойство игнорируется, если **время ожидания транзакций OLEDB:Flush Jet** имеет значение 0.|
|Время ожидания транзакций OLEDB:Flush Jet (DBPROP_JETOLEDB_FLUSHTRANSACTIONTIMEOUT)|Указывает время ожидания, прежде чем данные, хранящиеся в кэше для асинхронной записи фактически записанных на диск. Этот параметр переопределяет значения **Jet OLEDB: общие задержки Async** и **Jet OLEDB:Exclusive асинхронная задержка**.|
|Jet OLEDB: глобальный массовые транзакции (DBPROP_JETOLEDB_GLOBALBULKNOTRANSACTIONS)|Указывает, является ли SQL массовые транзакции остаются активными, несмотря.|
|Jet OLEDB: глобальный частичного массового Ops (DBPROP_JETOLEDB_GLOBALBULKPARTIAL)|Указывает пароль, используемый для открытия базы данных.|
|Jet OLEDB: неявное фиксации синхронизации (DBPROP_JETOLEDB_IMPLICITCOMMITSYNC)|Указывает, записываются ли изменения, внесенные в внутренней неявные транзакции в режиме синхронной или асинхронной.|
|Задержка OLEDB:Lock Jet (DBPROP_JETOLEDB_LOCKDELAY)|Указывает количество миллисекунд ожидания, прежде чем пытаться получить блокировку, после сбоя предыдущей попытки.|
|Повторных попыток OLEDB:Lock Jet (DBPROP_JETOLEDB_LOCKRETRY)|Показывает, сколько раз повторяется попытка получить доступ к блокированной страницы.|
|Размер буфера OLEDB:Max Jet (DBPROP_JETOLEDB_MAXBUFFERSIZE)|Указывает максимальный размер памяти, в килобайтах, Jet используется прежде чем начнется запись изменений на диск.|
|Jet OLEDB:Max блокировок на файл (DBPROP_JETOLEDB_MAXLOCKSPERFILE)|Указывает максимальное число блокировок, которые Jet можно разместить в базе данных. Значение по умолчанию — 9500.|
|Jet OLEDB: новый пароль базы данных (DBPROP_JETOLEDB_NEWDATABASEPASSWORD)|Указывает новый пароль, который нужно задать для этой базы данных. Старый пароль хранится в **Jet OLEDB: Database Password**.|
|Время ожидания команды Jet OLEDB:ODBC (DBPROP_JETOLEDB_ODBCCOMMANDTIMEOUT)|Указывает, что количество миллисекунд до удаленного запроса ODBC из Jet выдаст ошибку времени ожидания.|
|Jet OLEDB:Page блокировки для блокировки таблицы (DBPROP_JETOLEDB_PAGELOCKSTOTABLELOCK)|Указывает, сколько страниц должен быть заблокирован в рамках транзакции, перед попыткой Jet для повышения уровня блокировки, чтобы блокировку таблицы. Если это значение равно 0, никогда не повышается до блокировки.|
|Время ожидания OLEDB:Page Jet (DBPROP_JETOLEDB_PAGETIMEOUT)|Указывает количество миллисекунд ожидания перед проверкой ли кэш устарел с файлом базы данных Jet.|
|Страницы табличное долго Jet OLEDB:Recycle (DBPROP_JETOLEDB_RECYCLELONGVALUEPAGES)|Указывает ли Jet агрессивно пытаться освободить страницы BLOB-ОБЪЕКТОВ при их освобождения.|
|Путь OLEDB:Registry Jet (DBPROP_JETOLEDB_REGPATH)|Указывает раздел реестра Windows, который содержит значения для базы данных Jet.|
|Статистика ISAM OLEDB:Reset Jet (DBPROP_JETOLEDB_RESETISAMSTATS)|Указывает ли схема **записей** DBSCHEMA_JETOLEDB_ISAMSTATS необходимо сбросить его счетчики производительности, после возвращения сведений о производительности.|
|Jet OLEDB: общие задержки Async (DBPROP_JETOLEDB_SHAREDASYNCDELAY)|Указывает максимальное время в миллисекундах, Jet могут вызвать задержку асинхронные операции записи на диск, когда база данных открыта в многопользовательском режиме.|
|База данных Jet OLEDB: системная (DBPROP_JETOLEDB_SYSDBPATH)|Указывает путь к файлу и имя файла рабочей группы (системной базы данных).|
|Режим фиксации OLEDB:Transaction Jet (DBPROP_JETOLEDB_TXNCOMMITMODE)|Указывает ли Jet записывает данные на диск, синхронно или асинхронно при фиксации транзакции.|
|Jet OLEDB:User фиксации синхронизации (DBPROP_JETOLEDB_USERCOMMITSYNC)|Указывает, записываются ли изменения, внесенные в транзакциях в синхронный или асинхронный режим.|

## <a name="provider-specific-recordset-and-command-properties"></a>Набор записей поставщика и свойства команды
 Поставщик Jet также поддерживает несколько поставщика **записей** и **команда** свойства. Эти свойства осуществляется доступ и задать с помощью **свойства** коллекцию **записей** или **команда** объекта. В таблице, имя свойства ADO и OLE DB название в круглые скобки.

|Имя свойства|Описание|
|-------------------|-----------------|
|Транзакциях СУБД Jet OLEDB:Bulk (DBPROP_JETOLEDB_BULKNOTRANSACTIONS)|Указывает, являются ли SQL массовых операций в рамках транзакции. Больших массовых операций может завершиться ошибкой, если в рамках транзакции, из-за задержки ресурсов.|
|Курсоры Fat OLEDB:Enable Jet (DBPROP_JETOLEDB_ENABLEFATCURSOR)|Указывает, следует ли Jet кэшировать несколько строк при заполнении набора записей для удаленных строк источников.|
|Размер кэша курсор OLEDB:Fat Jet (DBPROP_JETOLEDB_FATCURSORMAXROWS)|Указывает количество строк для кэша, при использовании кэширования строки данных удаленного хранилища. Это значение игнорируется, если **Fat курсоры Jet OLEDB:Enable** имеет значение True.|
|Jet OLEDB: несогласованные (DBPROP_JETOLEDB_INCONSISTENT)|Указывает, разрешает ли результаты запроса несогласованных обновлений.|
|Jet OLEDB: блокировки гранулярности (DBPROP_JETOLEDB_LOCKGRANULARITY)|Указывает, открыт ли таблицы с помощью блокировки уровня строк.|
|Инструкция сквозной OLEDB:ODBC Jet (DBPROP_JETOLEDB_ODBCPASSTHROUGH)|Указывает, что Jet должен передаваться в текст SQL **команда** объекта к серверной части без изменений.|
|Jet OLEDB:Partial массового Ops (DBPROP_JETOLEDB_BULKPARTIAL)|Указывает поведение Jet, когда происходит сбой операции SQL DML.|
|Jet OLEDB:Pass через запрос Bulk-Op (DBPROP_JETOLEDB_PASSTHROUGHBULKOP)|Указывает, является ли запросы, не возвращают **записей** передаются без изменений в источник данных.|
|Строка (DBPROP_JETOLEDB_ODBCPASSTHROUGHCONNECTSTRING) подключения OLEDB:Pass Jet посредством запроса|Указывает Jet строка соединения, использованная для подключения к удаленном хранилище данных. Это значение игнорируется, если **Jet OLEDB:ODBC сквозной инструкции** имеет значение True.|
|Jet OLEDB: хранимых запросов (DBPROP_JETOLEDB_STOREDQUERY)|Указывает, следует ли интерпретировать как хранимого запроса, а не команду SQL текст команды.|
|Jet OLEDB: проверить правила в наборе (DBPROP_JETOLEDB_VALIDATEONSET)|Указывает, вычисляются ли правила проверки Jet при имеет значение данных столбца или изменения фиксируются в базе данных.|

 По умолчанию поставщик OLE DB для Jet (Майкрософт) открывается баз данных Microsoft Jet в режиме чтения/записи. Чтобы открыть базу данных в режиме только для чтения, задайте [режим](../../../ado/reference/ado-api/mode-property-ado.md) свойство ADO **подключения** объект **adModeRead**.

## <a name="command-object-usage"></a>Использование объекта Command
 Текст в команды [команда](../../../ado/reference/ado-api/command-object-ado.md) объект использует разновидность языка Microsoft Jet SQL. Можно указать запросы, возвращающие строки, запросы и имена таблиц в тексте команды; Тем не менее хранимые процедуры не поддерживаются и указывать не нужно.

## <a name="recordset-behavior"></a>Поведение набора записей
 Базы данных Microsoft Jet не поддерживает динамические курсоры. Таким образом, поставщик OLE DB для Jet (Майкрософт) не поддерживает **adLockDynamic** тип курсора. При запросе динамический курсор, поставщик возвращает курсор набора ключей и сбросить [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) свойство, указывающее тип [записей](../../../ado/reference/ado-api/recordset-object-ado.md) возвращается. Кроме того, если обновляемый **записей** запрашивается (**LockType** — **adLockOptimistic**, **adLockBatchOptimistic**, или **adLockPessimistic**) поставщик также вернет в курсор keyset и сбросить **CursorType** свойство.

## <a name="dynamic-properties"></a>Динамические свойства
 Поставщик OLE DB для Jet (Майкрософт) вставляет несколько динамических свойств в **свойства** коллекцию неоткрытый [подключения](../../../ado/reference/ado-api/connection-object-ado.md), [записей](../../../ado/reference/ado-api/recordset-object-ado.md)и [Команда](../../../ado/reference/ado-api/command-object-ado.md) объектов.

 В следующих таблицах представлены cross-index имен ADO и OLE DB для каждого динамического свойства. Справочник программиста OLE DB по указано имя свойства ADO с термином «Description». Дополнительные сведения об этих свойствах можно найти в справочнике программиста OLE DB.

## <a name="connection-dynamic-properties"></a>Динамические свойства подключения
 Следующие свойства добавляются к **свойства** коллекцию **подключения** объекта.

|Имя свойства ADO|Имя свойства OLE DB|
|-----------------------|--------------------------|
|Активные сеансы|DBPROP_ACTIVESESSIONS|
|Асинхронное прерывание работы|DBPROP_ASYNCTXNABORT|
|Асинхронная фиксация|DBPROP_ASYNCTNXCOMMIT|
|Уровни изоляции автофиксации|DBPROP_SESS_AUTOCOMMITISOLEVELS|
|Расположение каталога|DBPROP_CATALOGLOCATION|
|Термин каталога|DBPROP_CATALOGTERM|
|Определение столбца|DBPROP_COLUMNDEFINITION|
|Текущий каталог|DBPROP_CURRENTCATALOG|
|Источник данных|DBPROP_INIT_DATASOURCE|
|Имя источника данных|DBPROP_DATASOURCENAME|
|Потоковая модель объекта источника данных|DBPROP_DSOTHREADMODEL|
|Имя СУБД|DBPROP_DBMSNAME|
|Версия СУБД|DBPROP_DBMSVER|
|Поддержка оператора GROUP BY|DBPROP_GROUPBY|
|Поддержка гетерогенных таблиц|DBPROP_HETEROGENEOUSTABLES|
|Чувствительность идентификатора к регистру|DBPROP_IDENTIFIERCASE|
|Уровни изоляции|DBPROP_SUPPORTEDTXNISOLEVELS|
|Сохранение изоляции|DBPROP_SUPPORTEDTXNISORETAIN|
|Идентификатор локали|DBPROP_INIT_LCID|
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
|Версия OLE DB|DBPROP_PROVIDEROLEDBVER|
|Поддержка объектов OLE|DBPROP_OLEOBJECTS|
|Поддержка открытия наборов данных|DBPROP_OPENROWSETSUPPORT|
|Столбцы ORDER BY в списке выбора|DBPROP_ORDERBYCOLUMNSINSELECT|
|Доступность параметра вывода|DBPROP_OUTPUTPARAMETERAVAILABILITY|
|Передавать по указанные методы|DBPROP_BYREFACCESSORS|
|Пароль|DBPROP_AUTH_PASSWORD|
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
 Следующие свойства добавляются к **свойства** коллекцию **записей** объекта.

|Имя свойства ADO|Имя свойства OLE DB|
|-----------------------|--------------------------|
|Порядок доступа|DBPROP_ACCESSORDER|
|Только для добавления строк|DBPROP_APPENDONLY|
|Блокирование объектов хранилища|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Тип закладки|DBPROP_BOOKMARKTYPE|
|Bookmarkable|DBPROP_IROWSETLOCATE|
|Закладки упорядочены|DBPROP_ORDEREDBOOKMARKS|
|Кэш отложенного столбцов|DBPROP_CACHEDEFERRED|
|Изменение вставленных строк|DBPROP_CHANGEINSERTEDROWS|
|Права доступа столбца|DBPROP_COLUMNRESTRICT|
|Уведомление о задании столбца|DBPROP_NOTIFYCOLUMNSET|
|Столбец для записи|DBPROP_MAYWRITECOLUMN|
|Отложить столбца|DBPROP_DEFERRED|
|Отложенное обновление объекта хранилища|DBPROP_DELAYSTORAGEOBJECTS|
|Выборка в обратном порядке|DBPROP_CANFETCHBACKWARDS|
|Удерживайте строк|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|ILockBytes|DBPROP_ILockBytes|
|Фиксированные строки|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|IRowsetIdentity|DBPROP_IRowsetIdentity|
|IRowsetIndex|DBPROP_IRowsetIndex|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsestLocate|
|IRowsetResynch||
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
|IStorage|DBPROP_IStorage|
|IStream|DBPROP_IStream|
|ISupportErrorInfo|DBPROP_ISupportErrorInfo|
|Литеральные закладки|DBPROP_LITERALBOOKMARKS|
|Литеральная Идентификация строки|DBPROP_LITERALIDENTITY|
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
|Быстрый перезапуск|DBPROP_QUICKRESTART|
|События с повторным входом|DBPROP_REENTRANTEVENTS|
|Уничтожение удаленных строк|DBPROP_REMOVEDELETED|
|Отчет о множественных изменениях|DBPROP_REPORTMULTIPLECHANGES|
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
|Уведомление об изменении позиции выборки набора строк|DBPROP_NOTIFYROWSETFETCHPOSISIONCHANGE|
|Уведомление о разблокировании набора строк|DBPROP_NOTIFYROWSETRELEASE|
|Обратная прокрутка|DBPROP_CANSCROLLBACKWARDS|
|Пропуск удаленных закладок|DBPROP_BOOKMARKSKIPPED|
|Строгая Идентификация строки|DBPROP_STRONGITDENTITY|
|Возможности обновления|DBPROP_UPDATABILITY|
|Использование закладок|DBPROP_BOOKMARKS|

## <a name="command-dynamic-properties"></a>Динамические свойства команды
 Следующие свойства добавляются к **свойства** коллекцию **команда** объекта.

|Имя свойства ADO|Имя свойства OLE DB|
|-----------------------|--------------------------|
|Порядок доступа|DBPROP_ACCESSORDER|
|Только для добавления строк|DBPROP_APPENDONLY|
|Блокирование объектов хранилища|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Тип закладки|DBPROP_BOOKMARKTYPE|
|Bookmarkable|DBPROP_IROWSETLOCATE|
|Изменение вставленных строк|DBPROP_CHANGEINSERTEDROWS|
|Права доступа столбца|DBPROP_COLUMNRESTRICT|
|Уведомление о задании столбца|DBPROP_NOTIFYCOLUMNSET|
|Отложить столбца|DBPROP_DEFERRED|
|Отложенное обновление объекта хранилища|DBPROP_DELAYSTORAGEOBJECTS|
|Выборка в обратном порядке|DBPROP_CANFETCHBACKWARDS|
|Удерживайте строк|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|ILockBytes|DBPROP_ILockBytes|
|Фиксированные строки|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|IRowsetIdentity|DBPROP_IRowsetIdentity|
|IRowsetIndex|DBPROP_IRowsetIndex|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsetLocate|
|IRowsetResynch||
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
|IStorage|DBPROP_IStorage|
|IStream|DBPROP_IStream|
|ISupportErrorInfo|DBPROP_ISupportErrorInfo|
|Литеральные закладки|DBPROP_LITERALBOOKMARKS|
|Литеральная Идентификация строки|DBPROP_LITERALIDENTITY|
|Режим блокировки|DBPROP_LOCKMODE|
|Максимальное число открытых строк|DBPROP_MAXOPENROWS|
|Максимальное число ожидающих строк|DBPROP_MAXPENDINGROWS|
|Максимальное число строк|DBPROP_MAXROWS|
|Уровень детализации уведомления|DBPROP_NOTIFICATIONGRANULARITY|
|Этапы уведомлений|DBPROP_NOTIFICATIONPHASES|
|Обработано объектов транзакций|DBPROP_TRANSACTEDOBJECT|
|Видны прочие изменения|DBPROP_OTHERUPDATEDELETE|
|Других пользователей видимость строк, вставленных|DBPROP_OTHERINSERT|
|Видимость собственных изменений|DBPROP_OWNUPDATEDELETE|
|Видимость собственных операций вставки|DBPROP_OWNINSERT|
|Сохранение при прерывании работы|DBPROP_ABORTPRESERVE|
|Сохранение при фиксации|DBPROP_COMMITPRESERVE|
|Быстрый перезапуск|DBPROP_QUICKRESTART|
|События с повторным входом|DBPROP_REENTRANTEVENTS|
|Уничтожение удаленных строк|DBPROP_REMOVEDELETED|
|Отчет о множественных изменениях|DBPROP_REPORTMULTIPLECHANGES|
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
|Данные сервера при вставке|DBPROP_SERVERDATAONINSERT|
|Пропуск удаленных закладок|DBPROP_BOOKMARKSKIP|
|Строгая Идентификация строки|DBPROP_STRONGIDENTITY|
|Возможности обновления|DBPROP_UPDATABILITY|
|Использование закладок|DBPROP_BOOKMARKS|

 Определенные сведения о реализации и функционального сведения о поставщике OLE DB для Jet (Майкрософт), см. в разделе [поставщик Jet](https://msdn.microsoft.com/library/windows/desktop/ms722791.aspx) в документации по OLE DB.
