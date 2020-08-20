---
description: Обзор поставщика Microsoft OLE DB для Microsoft Jet
title: Поставщик OLE DB Майкрософт для Microsoft Jet | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 822c9f6ef6aebe5e32bb37e4c89a9bb4e6d7db68
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88454076"
---
# <a name="microsoft-ole-db-provider-for-microsoft-jet-overview"></a>Обзор поставщика Microsoft OLE DB для Microsoft Jet
Поставщик OLE DB для Microsoft Jet позволяет ADO получать доступ к базам данных Microsoft Jet.

## <a name="connection-string-parameters"></a>Параметры строки соединения
 Чтобы подключиться к этому поставщику, задайте для аргумента *поставщика* свойства [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) следующее значение:

```vb
Microsoft.Jet.OLEDB.4.0
```

 При чтении свойства [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) также будет возвращена эта строка.

## <a name="typical-connection-string"></a>Типичная строка подключения
 Типичная строка подключения для этого поставщика:

```vb
"Provider=Microsoft.Jet.OLEDB.4.0;Data Source=databaseName;User ID=MyUserID;Password=MyPassword;"
```

 Строка состоит из следующих ключевых слов:

|Ключевое слово|Описание|
|-------------|-----------------|
|**Поставщик**|Указывает поставщика OLE DB для Microsoft Jet.|
|**Источник данных**|Указывает путь к базе данных и имя файла (например, `c:\Northwind.mdb` ).|
|**Идентификатор пользователя**|Указывает имя пользователя. Если это ключевое слово не указано, `admin` по умолчанию используется строка "".|
|**Пароль**|Указывает пароль пользователя. Если это ключевое слово не указано, по умолчанию используется пустая строка ("").|

> [!NOTE]
>  При подключении к поставщику источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = Yes** или **Integrated Security = SSPI** вместо сведений об идентификаторе пользователя и пароле в строке подключения.

## <a name="provider-specific-connection-parameters"></a>Параметры подключения, зависящие от поставщика
 Поставщик OLE DB для Microsoft Jet поддерживает несколько динамических свойств, зависящих от поставщика, помимо тех, которые определены в ADO. Как и в случае со всеми другими параметрами **соединения** , их можно задать с помощью коллекции **Properties** объекта **Connection** или в составе строки подключения.

 В следующей таблице перечислены эти свойства вместе с соответствующим OLE DB именем свойства в круглых скобках.

|Параметр|Описание|
|---------------|-----------------|
|Jet OLEDB: сжатие освобожденного объема пространства (DBPROP_JETOLEDB_COMPACTFREESPACESIZE)|Указывает оценку объема пространства в байтах, которое может быть освобождено путем сжатия базы данных. Это значение допустимо только после установки подключения к базе данных.|
|Jet OLEDB: Управление подключением (DBPROP_JETOLEDB_CONNECTIONCONTROL)|Указывает, могут ли пользователи подключаться к базе данных.|
|Jet OLEDB: Создание системной базы данных (DBPROP_JETOLEDB_CREATESYSTEMDATABASE)|Указывает, должна ли создаваться системная база данных при создании нового источника данных.|
|Jet OLEDB: режим блокировки базы данных (DBPROP_JETOLEDB_DATABASELOCKMODE)|Указывает режим блокировки для этой базы данных. Первый пользователь, который открывает базу данных, определяет режим, используемый при открытии базы данных.|
|Jet OLEDB: пароль базы данных (DBPROP_JETOLEDB_DATABASEPASSWORD)|Указывает пароль базы данных.|
|Jet OLEDB: не копируйте языковой стандарт в Compact (DBPROP_JETOLEDB_COMPACT_DONTCOPYLOCALE)|Указывает, должна ли Jet копировать сведения о языковых стандартах при сжатии базы данных.|
|Jet OLEDB: шифрование базы данных (DBPROP_JETOLEDB_ENCRYPTDATABASE)|Указывает, следует ли шифровать сжатую базу данных. Если это свойство не задано, сжатая база данных будет зашифрована, если исходная база данных также была зашифрована.|
|Jet OLEDB: тип подсистемы (DBPROP_JETOLEDB_ENGINE)|Указывает подсистему хранилища, используемую для доступа к текущему хранилищу данных.|
|Jet OLEDB: эксклюзивная асинхронная задержка (DBPROP_JETOLEDB_EXCLUSIVEASYNCDELAY)|Указывает максимальный интервал времени в миллисекундах, в течение которого Jet может задержать асинхронную запись на диск, когда база данных открыта в монопольном режиме.<br /><br /> Это свойство игнорируется, если **Jet OLEDB: время ожидания транзакции сброса** данных равно 0.|
|Jet OLEDB: время ожидания очистки транзакций (DBPROP_JETOLEDB_FLUSHTRANSACTIONTIMEOUT)|Указывает время ожидания, по истечении которого данные, хранящиеся в кэше для асинхронной записи, фактически записываются на диск. Этот параметр переопределяет значения для **Jet OLEDB: Shared Async Delay** и **Jet OLEDB: эксклюзивная асинхронная задержка**.|
|Jet OLEDB: глобальные групповые транзакции (DBPROP_JETOLEDB_GLOBALBULKNOTRANSACTIONS)|Указывает, являются ли транзакции с массовыми SQL транзакционными.|
|Jet OLEDB: глобальные частичные операции без операций (DBPROP_JETOLEDB_GLOBALBULKPARTIAL)|Указывает пароль, используемый для открытия базы данных.|
|Jet OLEDB: Неявная синхронизация фиксации (DBPROP_JETOLEDB_IMPLICITCOMMITSYNC)|Указывает, записываются ли изменения, внесенные во внутренние неявные транзакции, в синхронном или асинхронном режиме.|
|Jet OLEDB: задержка блокировки (DBPROP_JETOLEDB_LOCKDELAY)|Указывает количество миллисекунд ожидания перед попыткой получить блокировку после сбоя предыдущей попытки.|
|Jet OLEDB: повтор блокировки (DBPROP_JETOLEDB_LOCKRETRY)|Указывает, сколько раз попытка доступа к заблокированной странице повторяется.|
|Jet OLEDB: максимальный размер буфера (DBPROP_JETOLEDB_MAXBUFFERSIZE)|Указывает максимальный объем памяти (в килобайтах), который может использоваться модулем Jet перед тем, как начнется запись изменений на диск.|
|Jet OLEDB: максимальное число блокировок на файл (DBPROP_JETOLEDB_MAXLOCKSPERFILE)|Указывает максимальное количество блокировок, которые может разместить модуль Jet в базе данных. Значение по умолчанию — 9500.|
|Jet OLEDB: новый пароль базы данных (DBPROP_JETOLEDB_NEWDATABASEPASSWORD)|Указывает новый пароль, который необходимо задать для этой базы данных. Старый пароль хранится в **Jet OLEDB: пароль базы данных**.|
|Jet OLEDB: время ожидания команды ODBC (DBPROP_JETOLEDB_ODBCCOMMANDTIMEOUT)|Указывает число миллисекунд, по истечении которых истекает время ожидания удаленного запроса ODBC от Jet.|
|Jet OLEDB: Блокировка страниц для блокировки таблицы (DBPROP_JETOLEDB_PAGELOCKSTOTABLELOCK)|Указывает, сколько страниц должно быть заблокировано в рамках транзакции, прежде чем Jet попытается повысить блокировку до блокировки таблицы. Если это значение равно 0, блокировка не повышается.|
|Jet OLEDB: время ожидания страницы (DBPROP_JETOLEDB_PAGETIMEOUT)|Указывает время в миллисекундах, в течение которого Jet будет ожидать, не устарел ли его кэш с файлом базы данных.|
|Jet OLEDB: повторное использование страниц с длинными значениями (DBPROP_JETOLEDB_RECYCLELONGVALUEPAGES)|Указывает, должен ли модуль Jet принудительно пытаться восстановить страницы больших двоичных объектов при их освобождении.|
|Jet OLEDB: путь реестра (DBPROP_JETOLEDB_REGPATH)|Указывает раздел реестра Windows, который содержит значения для ядра СУБД Jet.|
|Jet OLEDB: сброс ISAM stats (DBPROP_JETOLEDB_RESETISAMSTATS)|Указывает, DBSCHEMA_JETOLEDB_ISAMSTATS ли **набор записей** схемы сбрасывать счетчики производительности после возврата сведений о производительности.|
|Jet OLEDB: Общая асинхронная задержка (DBPROP_JETOLEDB_SHAREDASYNCDELAY)|Указывает максимальное время в миллисекундах, в течение которого Jet может откладывать асинхронные операции записи на диск при открытии базы данных в многопользовательской режиме.|
|Jet OLEDB: системная база данных (DBPROP_JETOLEDB_SYSDBPATH)|Указывает путь и имя файла для информационного файла рабочей группы (системная база данных).|
|Jet OLEDB: режим фиксации транзакции (DBPROP_JETOLEDB_TXNCOMMITMODE)|Указывает, записывает ли Jet данные на диск синхронно или асинхронно при фиксации транзакции.|
|Jet OLEDB: Синхронизация пользовательской фиксации (DBPROP_JETOLEDB_USERCOMMITSYNC)|Указывает, записываются ли изменения, внесенные в транзакции, в синхронном или асинхронном режиме.|

## <a name="provider-specific-recordset-and-command-properties"></a>Специфические для поставщика набор записей и свойства команды
 Поставщик Jet также поддерживает несколько специфических для поставщика **наборов записей** и свойств **команд** . Доступ к этим свойствам и их настройка осуществляется с помощью коллекции **свойств** **набора записей** или объекта **команды** . В таблице перечислены имя свойства ADO и соответствующее OLE DB имя свойства в круглых скобках.

|Имя свойства|Описание|
|-------------------|-----------------|
|Jet OLEDB: групповые транзакции (DBPROP_JETOLEDB_BULKNOTRANSACTIONS)|Указывает, являются ли групповые операции SQL транзакционными. Большие операции с массовыми операциями могут завершаться ошибкой в связи с задержками ресурсов.|
|Jet OLEDB: включение курсоров FAT (DBPROP_JETOLEDB_ENABLEFATCURSOR)|Указывает, должен ли модуль Jet кэшировать несколько строк при заполнении набора записей для удаленных источников строк.|
|Jet OLEDB: размер кэша курсора FAT (DBPROP_JETOLEDB_FATCURSORMAXROWS)|Указывает количество строк для кэширования при использовании кэширования строк удаленного хранилища данных. Это значение игнорируется, если **Jet OLEDB: enable FAT** имеет значение true.|
|Jet OLEDB: несоответствие (DBPROP_JETOLEDB_INCONSISTENT)|Указывает, разрешены ли в результатах запроса непоследовательные обновления.|
|Jet OLEDB: гранулярность блокировки (DBPROP_JETOLEDB_LOCKGRANULARITY)|Указывает, открыта ли таблица с блокировкой на уровне строк.|
|Jet OLEDB: Инструкция сквозного ODBC (DBPROP_JETOLEDB_ODBCPASSTHROUGH)|Указывает, что Jet должен передать текст SQL в объект **команды** в серверную части без изменений.|
|Jet OLEDB: частичные операции без операций (DBPROP_JETOLEDB_BULKPARTIAL)|Указывает на поведение Jet при сбое операций SQL DML.|
|Jet OLEDB: сквозная операция запроса (DBPROP_JETOLEDB_PASSTHROUGHBULKOP)|Указывает, передаются ли запросы, не возвращающие **набор записей** , в источник данных.|
|Jet OLEDB: сквозная строка подключения запроса (DBPROP_JETOLEDB_ODBCPASSTHROUGHCONNECTSTRING)|Указывает строку подключения Jet, используемую для подключения к удаленному хранилищу данных. Это значение игнорируется, если не выполняется **инструкция сквозной инструкции Jet OLEDB: ODBC** .|
|Jet OLEDB: сохраненный запрос (DBPROP_JETOLEDB_STOREDQUERY)|Указывает, следует ли интерпретировать текст команды как хранимый запрос вместо команды SQL.|
|Jet OLEDB: Проверка правил в наборе (DBPROP_JETOLEDB_VALIDATEONSET)|Указывает, оцениваются ли правила проверки Jet при установке данных столбца или при фиксации изменений в базе данных.|

 По умолчанию поставщик OLE DB для Microsoft Jet открывает базы данных Microsoft Jet в режиме чтения и записи. Чтобы открыть базу данных в режиме только для чтения, установите свойство [mode](../../../ado/reference/ado-api/mode-property-ado.md) объекта **соединения** ADO в значение **адмодереад**.

## <a name="command-object-usage"></a>Использование объекта команды
 Текст команды в объекте [Command](../../../ado/reference/ado-api/command-object-ado.md) использует диалект Microsoft Jet SQL. В тексте команды можно указать запросы, возвращающие строки, запросы действий и имена таблиц. Однако хранимые процедуры не поддерживаются, и их не следует указывать.

## <a name="recordset-behavior"></a>Поведение набора записей
 Ядро СУБД Microsoft Jet не поддерживает динамические курсоры. Таким образом, поставщик OLE DB для Microsoft Jet не поддерживает тип курсора **адлоккдинамик** . При запросе динамического курсора поставщик возвращает курсор KEYSET и сбрасывает свойство [примеры CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) , чтобы указать тип возвращаемого [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) . Кроме того, если запрашивается обновляемый **набор записей** (**LockType** — **adLockOptimistic**, **адлоккбатчоптимистик**или **адлоккпессимистик**), поставщик также возвращает курсор KEYSET и сбрасывает свойство **примеры CursorType** .

## <a name="dynamic-properties"></a>Динамические свойства
 Поставщик OLE DB для Microsoft Jet вставляет несколько динамических свойств в коллекцию **свойств** неоткрытыго [соединения](../../../ado/reference/ado-api/connection-object-ado.md), [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md)и [командных](../../../ado/reference/ado-api/command-object-ado.md) объектов.

 В следующих таблицах приведены перекрестные индексы имен ADO и OLE DB для каждого динамического свойства. Ссылка на OLE DB программиста ссылается на имя свойства ADO по термину «Description». Дополнительные сведения об этих свойствах можно найти в справочнике по программисту OLE DB.

## <a name="connection-dynamic-properties"></a>Динамические свойства подключения
 Следующие свойства добавляются в коллекцию **Properties** объекта **Connection** .

|Имя свойства ADO|Имя свойства OLE DB|
|-----------------------|--------------------------|
|Активные сеансы|DBPROP_ACTIVESESSIONS|
|Прервать асинхронная|DBPROP_ASYNCTXNABORT|
|Асинхронная фиксация|DBPROP_ASYNCTNXCOMMIT|
|Уровни изоляции с автоматической фиксацией|DBPROP_SESS_AUTOCOMMITISOLEVELS|
|Расположение каталога|DBPROP_CATALOGLOCATION|
|Термин каталога|DBPROP_CATALOGTERM|
|Определение столбца|DBPROP_COLUMNDEFINITION|
|Текущий каталог|DBPROP_CURRENTCATALOG|
|Источник данных|DBPROP_INIT_DATASOURCE|
|Имя базы данных-источника|DBPROP_DATASOURCENAME|
|Потоковая модель объекта источника данных|DBPROP_DSOTHREADMODEL|
|Имя СУБД|DBPROP_DBMSNAME|
|Версия СУБД|DBPROP_DBMSVER|
|ГРУППИРОВКа по поддержке|DBPROP_GROUPBY|
|Поддержка разнородных таблиц|DBPROP_HETEROGENEOUSTABLES|
|Чувствительность идентификатора к регистру|DBPROP_IDENTIFIERCASE|
|Уровни изоляции|DBPROP_SUPPORTEDTXNISOLEVELS|
|Хранение изоляции|DBPROP_SUPPORTEDTXNISORETAIN|
|Идентификатор локали|DBPROP_INIT_LCID|
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
|Версия OLE DB|DBPROP_PROVIDEROLEDBVER|
|Поддержка объектов OLE|DBPROP_OLEOBJECTS|
|Поддержка открытых наборов строк|DBPROP_OPENROWSETSUPPORT|
|УПОРЯДОЧЕНие по столбцам в списке выбора|DBPROP_ORDERBYCOLUMNSINSELECT|
|Доступность выходного параметра|DBPROP_OUTPUTPARAMETERAVAILABILITY|
|Методы доступа для передачи по ссылке|DBPROP_BYREFACCESSORS|
|Пароль|DBPROP_AUTH_PASSWORD|
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
 Следующие свойства добавляются в коллекцию **Properties** объекта **Recordset** .

|Имя свойства ADO|Имя свойства OLE DB|
|-----------------------|--------------------------|
|Порядок доступа|DBPROP_ACCESSORDER|
|Набор строк только для добавления|DBPROP_APPENDONLY|
|Блокировка объектов хранилища|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Тип закладки|DBPROP_BOOKMARKTYPE|
|С закладками|DBPROP_IROWSETLOCATE|
|Упорядоченные закладки|DBPROP_ORDEREDBOOKMARKS|
|Кэширование отложенных столбцов|DBPROP_CACHEDEFERRED|
|Изменить вставленные строки|DBPROP_CHANGEINSERTEDROWS|
|Права доступа к столбцу|DBPROP_COLUMNRESTRICT|
|Уведомление о наборе столбцов|DBPROP_NOTIFYCOLUMNSET|
|Столбец доступен для записи|DBPROP_MAYWRITECOLUMN|
|Откладывание столбца|DBPROP_DEFERRED|
|Задержка обновлений объектов хранилища|DBPROP_DELAYSTORAGEOBJECTS|
|Получить назад|DBPROP_CANFETCHBACKWARDS|
|Удержание строк|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|ILockBytes|DBPROP_ILockBytes|
|Строки немобильных устройств|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|ировсетидентити|DBPROP_IRowsetIdentity|
|IRowsetIndex|DBPROP_IRowsetIndex|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsestLocate|
|Интерфейс irowsetresynch||
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
|Метод IStorage|DBPROP_IStorage|
|IStream|DBPROP_IStream|
|ISupportErrorInfo|DBPROP_ISupportErrorInfo|
|Литеральные закладки|DBPROP_LITERALBOOKMARKS|
|Удостоверение литеральной строки|DBPROP_LITERALIDENTITY|
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
|Быстрый перезапуск|DBPROP_QUICKRESTART|
|Повторные события|DBPROP_REENTRANTEVENTS|
|Удалить удаленные строки|DBPROP_REMOVEDELETED|
|Отчет о нескольких изменениях|DBPROP_REPORTMULTIPLECHANGES|
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
|Уведомление об изменении расположения выборки набора строк|DBPROP_NOTIFYROWSETFETCHPOSISIONCHANGE|
|Уведомление о выпуске набора строк|DBPROP_NOTIFYROWSETRELEASE|
|Прокрутка назад|DBPROP_CANSCROLLBACKWARDS|
|Пропустить удаленные закладки|DBPROP_BOOKMARKSKIPPED|
|Строгая идентификация строк|DBPROP_STRONGITDENTITY|
|Updatability|DBPROP_UPDATABILITY|
|Использование закладок|DBPROP_BOOKMARKS|

## <a name="command-dynamic-properties"></a>Динамические свойства команды
 Следующие свойства добавляются в коллекцию **Properties** объекта **Command** .

|Имя свойства ADO|Имя свойства OLE DB|
|-----------------------|--------------------------|
|Порядок доступа|DBPROP_ACCESSORDER|
|Набор строк только для добавления|DBPROP_APPENDONLY|
|Блокировка объектов хранилища|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Тип закладки|DBPROP_BOOKMARKTYPE|
|С закладками|DBPROP_IROWSETLOCATE|
|Изменить вставленные строки|DBPROP_CHANGEINSERTEDROWS|
|Права доступа к столбцу|DBPROP_COLUMNRESTRICT|
|Уведомление о наборе столбцов|DBPROP_NOTIFYCOLUMNSET|
|Откладывание столбца|DBPROP_DEFERRED|
|Задержка обновлений объектов хранилища|DBPROP_DELAYSTORAGEOBJECTS|
|Получить назад|DBPROP_CANFETCHBACKWARDS|
|Удержание строк|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|ILockBytes|DBPROP_ILockBytes|
|Строки немобильных устройств|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|ировсетидентити|DBPROP_IRowsetIdentity|
|IRowsetIndex|DBPROP_IRowsetIndex|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsetLocate|
|Интерфейс irowsetresynch||
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
|Метод IStorage|DBPROP_IStorage|
|IStream|DBPROP_IStream|
|ISupportErrorInfo|DBPROP_ISupportErrorInfo|
|Литеральные закладки|DBPROP_LITERALBOOKMARKS|
|Удостоверение литеральной строки|DBPROP_LITERALIDENTITY|
|Режим блокировки|DBPROP_LOCKMODE|
|Максимальное число открытых строк|DBPROP_MAXOPENROWS|
|Максимальное число ожидающих строк|DBPROP_MAXPENDINGROWS|
|Максимальное число строк|DBPROP_MAXROWS|
|Гранулярность уведомлений|DBPROP_NOTIFICATIONGRANULARITY|
|Этапы уведомления|DBPROP_NOTIFICATIONPHASES|
|Транзакционные объекты|DBPROP_TRANSACTEDOBJECT|
|Изменения видны другим пользователям|DBPROP_OTHERUPDATEDELETE|
|Видимые вставки других пользователей|DBPROP_OTHERINSERT|
|Видны собственные изменения|DBPROP_OWNUPDATEDELETE|
|Видны собственные вставки|DBPROP_OWNINSERT|
|Сохранить при прерывании|DBPROP_ABORTPRESERVE|
|Сохранить при фиксации|DBPROP_COMMITPRESERVE|
|Быстрый перезапуск|DBPROP_QUICKRESTART|
|Повторные события|DBPROP_REENTRANTEVENTS|
|Удалить удаленные строки|DBPROP_REMOVEDELETED|
|Отчет о нескольких изменениях|DBPROP_REPORTMULTIPLECHANGES|
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
|Данные сервера при вставке|DBPROP_SERVERDATAONINSERT|
|Пропустить удаленные закладки|DBPROP_BOOKMARKSKIP|
|Строгая идентификация строк|DBPROP_STRONGIDENTITY|
|Updatability|DBPROP_UPDATABILITY|
|Использование закладок|DBPROP_BOOKMARKS|

 Сведения о конкретных особенностях реализации и сведения о поставщике OLE DB для Microsoft Jet см. в документации по [службам Jet](https://msdn.microsoft.com/library/windows/desktop/ms722791.aspx) в OLE DB.
