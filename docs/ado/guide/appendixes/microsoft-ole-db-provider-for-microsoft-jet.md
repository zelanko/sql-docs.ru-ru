---
title: "Поставщик Microsoft OLE DB для Microsoft Jet | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Jet provider for OLE DB [ADO]
- providers [ADO], OLE DB provider for Microsoft Jet
- OLE DB provider for Microsoft Jet [ADO]
ms.assetid: fd956da1-5203-40af-aa7e-fc13a6c6581f
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 8a09ad6fb1af544e98f1b7875d1e04c396e46e60
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="microsoft-ole-db-provider-for-microsoft-jet-overview"></a>Поставщик Microsoft OLE DB для Microsoft Jet Обзор
Поставщик OLE DB для Microsoft Jet позволяет ADO для доступа к базам данных Microsoft Jet.

## <a name="connection-string-parameters"></a>Параметры строки соединения
 Чтобы подключиться к этому поставщику, задайте *поставщика* аргумент [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) следующее:

```
Microsoft.Jet.OLEDB.4.0
```

 Чтение [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойство возвратит этой строки.

## <a name="typical-connection-string"></a>Обычная строка соединения
 — Строка соединения для данного поставщика:

```
"Provider=Microsoft.Jet.OLEDB.4.0;Data Source=databaseName;User ID=MyUserID;Password=MyPassword;"
```

 Строка состоит из следующих ключевых слов:

|Ключевое слово|Description|
|-------------|-----------------|
|**Поставщик**|Указывает поставщика OLE DB для Microsoft Jet.|
|**Источник данных**|Указывает путь и имя базы данных (например, `c:\Northwind.mdb`).|
|**Идентификатор пользователя**|Указывает имя пользователя. Если это ключевое слово не указан, строка «`admin`», используется по умолчанию.|
|**Пароль**|Указывает пароль пользователя. Если это ключевое слово не указан, пустая строка ("»), используется по умолчанию.|

> [!NOTE]
>  При подключении к поставщик источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = yes** или **Integrated Security = SSPI** вместо идентификатора пользователя и пароля сведения в строке подключения.

## <a name="provider-specific-connection-parameters"></a>Параметры подключения для конкретного поставщика
 Поставщик OLE DB для Microsoft Jet поддерживает несколько динамических свойств поставщика помимо тех, которые определены в ADO. Как и все другие **подключения** параметров, их можно задать с помощью **свойства** коллекцию **подключения** объект или как часть строки соединения.

 Ниже перечислены эти свойства, вместе с соответствующим именем свойства OLE DB в круглые скобки.

|Параметр|Description|
|---------------|-----------------|
|Сумма освобожденное место OLEDB:Compact Jet (DBPROP_JETOLEDB_COMPACTFREESPACESIZE)|Указывает приблизительное количество места, в байтах, которые могут быть освобождены при сжатии базы данных. Это значение допустимо только после установления подключения к базе данных.|
|Элемент управления OLEDB:Connection Jet (DBPROP_JETOLEDB_CONNECTIONCONTROL)|Указывает, могут ли пользователи подключаться к базе данных.|
|Jet OLEDB: Создание системной базы данных (DBPROP_JETOLEDB_CREATESYSTEMDATABASE)|Указывает, следует ли создавать системную базу данных при создании нового источника данных.|
|Режим блокировки OLEDB:Database Jet (DBPROP_JETOLEDB_DATABASELOCKMODE)|Указывает режим блокировки для этой базы данных. Первый пользователь для открытия базы данных определяет режим, используемый при открытом базы данных.|
|Пароль OLEDB:Database Jet (DBPROP_JETOLEDB_DATABASEPASSWORD)|Указывает пароль базы данных.|
|Jet OLEDB: не копировать языковой стандарт Compact (DBPROP_JETOLEDB_COMPACT_DONTCOPYLOCALE)|Указывает, следует ли Jet скопировать сведения о языке при сжатии базы данных.|
|Jet OLEDB: шифрование базы данных (DBPROP_JETOLEDB_ENCRYPTDATABASE)|Указывает, нужно ли шифровать сжатой базы данных. Если это свойство не задано, будут зашифрованы сжатой базы данных, если исходная база данных также был зашифрован.|
|Тип OLEDB:Engine Jet (DBPROP_JETOLEDB_ENGINE)|Указывает подсистеме хранилища, используемый для доступа к текущего хранилища данных.|
|Асинхронная задержка OLEDB:Exclusive Jet (DBPROP_JETOLEDB_EXCLUSIVEASYNCDELAY)|Указывает максимальную продолжительность времени, в миллисекундах, которое Jet может задержать асинхронные операции записи на диск, когда база данных открыта в монопольном режиме.<br /><br /> Это свойство игнорируется, если **время ожидания транзакции Jet OLEDB:Flush** имеет значение 0.|
|Время ожидания транзакции OLEDB:Flush Jet (DBPROP_JETOLEDB_FLUSHTRANSACTIONTIMEOUT)|Указывает время ожидания, прежде чем данные, хранящиеся в кэше для асинхронной записи фактически записанных на диск. Этот параметр переопределяет значения для **Jet OLEDB: асинхронная задержка общих** и **Jet OLEDB:Exclusive асинхронная задержка**.|
|Jet OLEDB: глобальные массовые транзакции (DBPROP_JETOLEDB_GLOBALBULKNOTRANSACTIONS)|Указывает, является ли SQL массовые транзакции остаются активными.|
|Jet OLEDB: глобальные массового частичных Ops (DBPROP_JETOLEDB_GLOBALBULKPARTIAL)|Указывает пароль, используемый для открытия базы данных.|
|Jet OLEDB: неявное фиксации синхронизации (DBPROP_JETOLEDB_IMPLICITCOMMITSYNC)|Указывает, записываются ли изменения, внесенные в внутренней неявные транзакции в режиме синхронной или асинхронной.|
|Задержка OLEDB:Lock Jet (DBPROP_JETOLEDB_LOCKDELAY)|Указывает количество миллисекунд для ожидания запроса блокировки после предыдущей попытки.|
|Повторите попытку OLEDB:Lock Jet (DBPROP_JETOLEDB_LOCKRETRY)|Указывает, сколько раз повторяется попытка получить доступ к блокированной страницы.|
|Размер буфера OLEDB:Max Jet (DBPROP_JETOLEDB_MAXBUFFERSIZE)|Указывает максимальный размер памяти, в килобайтах, Jet используется прежде, чем начнется запись изменений на диск.|
|Jet OLEDB:Max блокировок на файл (DBPROP_JETOLEDB_MAXLOCKSPERFILE)|Указывает максимальное число блокировок, которые Jet можно поместить в базе данных. Значение по умолчанию — 9500.|
|Jet OLEDB: новый пароль базы данных (DBPROP_JETOLEDB_NEWDATABASEPASSWORD)|Указывает новый пароль должен быть задан для этой базы данных. Старый пароль хранится в **OLEDB:Database пароль Jet**.|
|Время ожидания команды Jet OLEDB:ODBC (DBPROP_JETOLEDB_ODBCCOMMANDTIMEOUT)|Указывает, что количество миллисекунд до удаленного запроса ODBC из Jet выдаст ошибку времени ожидания.|
|Jet OLEDB:Page блокировки для блокировки таблицы (DBPROP_JETOLEDB_PAGELOCKSTOTABLELOCK)|Указывает, сколько страниц должна быть заблокирована в рамках транзакции, перед попыткой Jet повысить уровень блокировки до блокировки таблицы. Если это значение равно 0, блокировка никогда не преобразуется.|
|Время ожидания OLEDB:Page Jet (DBPROP_JETOLEDB_PAGETIMEOUT)|Указывает количество миллисекунд ожидания перед проверкой ли своего кэша устарела с файлом базы данных Jet.|
|Страницы табличное долго Jet OLEDB:Recycle (DBPROP_JETOLEDB_RECYCLELONGVALUEPAGES)|Указывает, является ли Jet агрессивно пытаться освободить большой двоичный объект страницы, если их освобождения.|
|Путь OLEDB:Registry Jet (DBPROP_JETOLEDB_REGPATH)|Указывает раздел реестра Windows, содержащий значения для базы данных Jet.|
|Статистика ISAM OLEDB:Reset Jet (DBPROP_JETOLEDB_RESETISAMSTATS)|Указывает ли схема **записей** DBSCHEMA_JETOLEDB_ISAMSTATS должна сбросить его счетчики производительности после возврата сведений о производительности.|
|Jet OLEDB: общие асинхронная задержка (DBPROP_JETOLEDB_SHAREDASYNCDELAY)|Указывает максимальное время в миллисекундах, Jet может задержать асинхронные операции записи на диск, когда база данных открыта в многопользовательском режиме.|
|База данных Jet OLEDB: системная (DBPROP_JETOLEDB_SYSDBPATH)|Указывает путь и имя файла для файла рабочей группы (системной базы данных).|
|Режим фиксации OLEDB:Transaction Jet (DBPROP_JETOLEDB_TXNCOMMITMODE)|Указывает, является ли Jet записывает данные на диск, синхронно или асинхронно при фиксации транзакции.|
|Jet OLEDB:User фиксации синхронизации (DBPROP_JETOLEDB_USERCOMMITSYNC)|Указывает, записываются ли изменения, внесенные в транзакции в режиме синхронной или асинхронной.|

## <a name="provider-specific-recordset-and-command-properties"></a>Набор записей поставщика и свойства команд
 Поставщик Jet также поддерживает несколько поставщика **записей** и **команда** свойства. Эти свойства осуществляется доступ и задать с помощью **свойства** коллекцию **записей** или **команда** объекта. В таблице перечислены имя свойства ADO и OLE DB название в круглые скобки.

|Имя свойства|Description|
|-------------------|-----------------|
|Транзакции OLEDB:Bulk Jet (DBPROP_JETOLEDB_BULKNOTRANSACTIONS)|Указывает ли в рамках транзакции SQL массовых операций. Проведения массовых операций может завершиться ошибкой, если в рамках транзакции, из-за задержки ресурсов.|
|Курсоры Fat OLEDB:Enable Jet (DBPROP_JETOLEDB_ENABLEFATCURSOR)|Указывает, следует ли Jet кэшировать несколько строк при заполнении набора записей для источника удаленных строк.|
|Размер кэша OLEDB:Fat курсора Jet (DBPROP_JETOLEDB_FATCURSORMAXROWS)|Указывает количество строк для кэша, при использовании кэширования строки данных удаленного хранилища. Это значение игнорируется, если **Fat курсоры Jet OLEDB:Enable** имеет значение True.|
|Jet OLEDB: несогласованные (DBPROP_JETOLEDB_INCONSISTENT)|Указывает, разрешает ли результаты запроса несогласованных обновлений.|
|Jet OLEDB: блокировки гранулярности (DBPROP_JETOLEDB_LOCKGRANULARITY)|Указывает, является ли таблица открывается в использовании блокировки на уровне строк.|
|Инструкция сквозной OLEDB:ODBC Jet (DBPROP_JETOLEDB_ODBCPASSTHROUGH)|Указывает, что Jet должен передаваться в текст SQL **команда** объекта серверной части без изменений.|
|Jet OLEDB:Partial массового Ops (DBPROP_JETOLEDB_BULKPARTIAL)|Указывает поведение Jet, при сбое операции SQL DML.|
|Jet OLEDB:Pass через запрос Bulk-Op (DBPROP_JETOLEDB_PASSTHROUGHBULKOP)|Указывает, является ли запросы, на которых не возвращают **записей** передаются без изменений в источнике данных.|
|Строка (DBPROP_JETOLEDB_ODBCPASSTHROUGHCONNECTSTRING) подключения Jet OLEDB:Pass посредством запроса|Указывает Jet строка соединения, использованная для подключения к удаленному хранилищу данных. Это значение игнорируется, если **Jet OLEDB:ODBC сквозной инструкции** имеет значение True.|
|Jet OLEDB: хранимых запросов (DBPROP_JETOLEDB_STOREDQUERY)|Указывает, является ли текст команды должны интерпретироваться как хранимый запрос вместо команды SQL.|
|Jet OLEDB: Проверьте правила на наборе (DBPROP_JETOLEDB_VALIDATEONSET)|Указывает, вычисляются ли правила проверки для Jet при задать столбец данных или изменения будут зафиксированы в базе данных.|

 По умолчанию поставщик OLE DB для Microsoft Jet открывается баз данных Microsoft Jet в режиме чтения и записи. Чтобы открыть базу данных в режиме только для чтения, задайте [режим](../../../ado/reference/ado-api/mode-property-ado.md) свойство ADO **подключения** объект **adModeRead**.

## <a name="command-object-usage"></a>Использование объекта Command
 Текст в команды [команда](../../../ado/reference/ado-api/command-object-ado.md) объект использует диалект Microsoft Jet SQL. Можно указать возвращающей строки запросов, запросов и имен таблиц в тексте команды; Однако хранимые процедуры не поддерживаются и не должны быть указаны.

## <a name="recordset-behavior"></a>Поведение набора записей
 Базы данных Microsoft Jet не поддерживает динамические курсоры. Таким образом, поставщик OLE DB для Microsoft Jet не поддерживает **adLockDynamic** тип курсора. При запросе динамического курсора, поставщик возвращает курсор набора ключей и Сброс [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) свойство, указывающее тип [записей](../../../ado/reference/ado-api/recordset-object-ado.md) возвращается. Далее, если обновляемый **записей** запрашивается (**LockType** — **adLockOptimistic**, **adLockBatchOptimistic**, или **adLockPessimistic**) поставщик также вернет курсор набора ключей и Сброс **CursorType** свойство.

## <a name="dynamic-properties"></a>Динамические свойства
 Поставщик OLE DB для Microsoft Jet вставляет несколько динамических свойств в **свойства** коллекцию Неоткрытое [подключения](../../../ado/reference/ado-api/connection-object-ado.md), [записей](../../../ado/reference/ado-api/recordset-object-ado.md)и [Команда](../../../ado/reference/ado-api/command-object-ado.md) объектов.

 Следующие таблицы являются cross-index имен ADO и OLE DB для каждого динамических свойств. Справочник программиста OLE DB указано имя свойства ADO термин «Описание». Дополнительные сведения об этих свойствах можно найти в справочнике программиста OLE DB.

## <a name="connection-dynamic-properties"></a>Динамические свойства подключения
 Следующие свойства добавляются **свойства** коллекцию **подключения** объекта.

|Имя свойства ADO|Имя свойства OLE DB|
|-----------------------|--------------------------|
|Активные сеансы|DBPROP_ACTIVESESSIONS|
|Прерывание Asynchable|DBPROP_ASYNCTXNABORT|
|Asynchable фиксации|DBPROP_ASYNCTNXCOMMIT|
|Уровни изоляции автоматической фиксации|DBPROP_SESS_AUTOCOMMITISOLEVELS|
|Расположение каталога|DBPROP_CATALOGLOCATION|
|Термин каталога|DBPROP_CATALOGTERM|
|Определение столбца|DBPROP_COLUMNDEFINITION|
|Текущий каталог.|DBPROP_CURRENTCATALOG|
|Источник данных|DBPROP_INIT_DATASOURCE|
|Имя источника данных|DBPROP_DATASOURCENAME|
|Потоковая модель объекта источника данных|DBPROP_DSOTHREADMODEL|
|Имя СУБД|DBPROP_DBMSNAME|
|Версия СУБД|DBPROP_DBMSVER|
|Группировать по поддержке|DBPROP_GROUPBY|
|Поддержка разнородных таблиц|DBPROP_HETEROGENEOUSTABLES|
|Идентификатор регистра|DBPROP_IDENTIFIERCASE|
|Уровни изоляции|DBPROP_SUPPORTEDTXNISOLEVELS|
|Хранение изоляции|DBPROP_SUPPORTEDTXNISORETAIN|
|Идентификатор локали|DBPROP_INIT_LCID|
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
|OLE DB версии|DBPROP_PROVIDEROLEDBVER|
|Поддержка объекта OLE|DBPROP_OLEOBJECTS|
|Поддержка открытых наборов строк|DBPROP_OPENROWSETSUPPORT|
|Столбцы ORDER BY в списке выбора|DBPROP_ORDERBYCOLUMNSINSELECT|
|Выходной параметр доступности|DBPROP_OUTPUTPARAMETERAVAILABILITY|
|Передача по событиям Ref|DBPROP_BYREFACCESSORS|
|Пароль|DBPROP_AUTH_PASSWORD|
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
 Следующие свойства добавляются **свойства** коллекцию **записей** объекта.

|Имя свойства ADO|Имя свойства OLE DB|
|-----------------------|--------------------------|
|Порядок доступа|DBPROP_ACCESSORDER|
|Только для добавления строк|DBPROP_APPENDONLY|
|Блокировка объектов хранилища|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Тип закладки|DBPROP_BOOKMARKTYPE|
|Bookmarkable|DBPROP_IROWSETLOCATE|
|Упорядоченные закладки|DBPROP_ORDEREDBOOKMARKS|
|Кэш Отложенные столбцы|DBPROP_CACHEDEFERRED|
|Изменить вставленных строк|DBPROP_CHANGEINSERTEDROWS|
|Права доступа столбца|DBPROP_COLUMNRESTRICT|
|Столбец набор уведомлений|DBPROP_NOTIFYCOLUMNSET|
|Столбец для записи|DBPROP_MAYWRITECOLUMN|
|Отложенные столбцы|DBPROP_DEFERRED|
|Отложенное обновление объекта хранилища|DBPROP_DELAYSTORAGEOBJECTS|
|Выборку|DBPROP_CANFETCHBACKWARDS|
|Удерживайте строк|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|ILockBytes|DBPROP_ILockBytes|
|Немобильные строки|DBPROP_IMMOBILEROWS|
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
|Литерал закладки|DBPROP_LITERALBOOKMARKS|
|Идентификатор строки литерала|DBPROP_LITERALIDENTITY|
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
|Быстрый перезапуск|DBPROP_QUICKRESTART|
|Повторные входящие события|DBPROP_REENTRANTEVENTS|
|Удаление удаленных строк|DBPROP_REMOVEDELETED|
|Отчет несколько изменений|DBPROP_REPORTMULTIPLECHANGES|
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
|Уведомление об изменении позиции выборки набора строк|DBPROP_NOTIFYROWSETFETCHPOSISIONCHANGE|
|Уведомления о выпуске набора строк|DBPROP_NOTIFYROWSETRELEASE|
|Прокрутка назад|DBPROP_CANSCROLLBACKWARDS|
|Пропустить удаленные закладки|DBPROP_BOOKMARKSKIPPED|
|Идентификатор строки строгих|DBPROP_STRONGITDENTITY|
|Возможность обновления|DBPROP_UPDATABILITY|
|С помощью закладок|DBPROP_BOOKMARKS|

## <a name="command-dynamic-properties"></a>Команда динамические свойства
 Следующие свойства добавляются **свойства** коллекцию **команда** объекта.

|Имя свойства ADO|Имя свойства OLE DB|
|-----------------------|--------------------------|
|Порядок доступа|DBPROP_ACCESSORDER|
|Только для добавления строк|DBPROP_APPENDONLY|
|Блокировка объектов хранилища|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Тип закладки|DBPROP_BOOKMARKTYPE|
|Bookmarkable|DBPROP_IROWSETLOCATE|
|Изменить вставленных строк|DBPROP_CHANGEINSERTEDROWS|
|Права доступа столбца|DBPROP_COLUMNRESTRICT|
|Столбец набор уведомлений|DBPROP_NOTIFYCOLUMNSET|
|Отложенные столбцы|DBPROP_DEFERRED|
|Отложенное обновление объекта хранилища|DBPROP_DELAYSTORAGEOBJECTS|
|Выборку|DBPROP_CANFETCHBACKWARDS|
|Удерживайте строк|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|ILockBytes|DBPROP_ILockBytes|
|Немобильные строки|DBPROP_IMMOBILEROWS|
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
|Литерал закладки|DBPROP_LITERALBOOKMARKS|
|Идентификатор строки литерала|DBPROP_LITERALIDENTITY|
|Режим блокировки|DBPROP_LOCKMODE|
|Максимальное число открытых строк|DBPROP_MAXOPENROWS|
|Максимальное количество ожидающих строк|DBPROP_MAXPENDINGROWS|
|Максимальное число строк|DBPROP_MAXROWS|
|Гранулярность уведомления|DBPROP_NOTIFICATIONGRANULARITY|
|Этапы уведомлений|DBPROP_NOTIFICATIONPHASES|
|Объекты с поддержкой транзакций|DBPROP_TRANSACTEDOBJECT|
|Видны прочие изменения|DBPROP_OTHERUPDATEDELETE|
|Чужих вставок видимым|DBPROP_OTHERINSERT|
|Видны собственные изменения|DBPROP_OWNUPDATEDELETE|
|Видны собственные операции вставки|DBPROP_OWNINSERT|
|Сохранять при аварийном завершении|DBPROP_ABORTPRESERVE|
|Сохранять при фиксации|DBPROP_COMMITPRESERVE|
|Быстрый перезапуск|DBPROP_QUICKRESTART|
|Повторные входящие события|DBPROP_REENTRANTEVENTS|
|Удаление удаленных строк|DBPROP_REMOVEDELETED|
|Отчет несколько изменений|DBPROP_REPORTMULTIPLECHANGES|
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
|Данные сервера при вставке|DBPROP_SERVERDATAONINSERT|
|Пропустить удаленные закладки|DBPROP_BOOKMARKSKIP|
|Идентификатор строки строгих|DBPROP_STRONGIDENTITY|
|Возможность обновления|DBPROP_UPDATABILITY|
|С помощью закладок|DBPROP_BOOKMARKS|

 Определенные сведения о реализации и функциональной сведения о поставщике OLE DB для Microsoft Jet см. в разделе [поставщик Jet](https://msdn.microsoft.com/library/windows/desktop/ms722791.aspx) в документации по OLE DB.
