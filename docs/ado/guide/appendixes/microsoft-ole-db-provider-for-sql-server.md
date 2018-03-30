---
title: Поставщик Microsoft OLE DB для SQL Server | Документы Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [ADO], OLE DB provider for SQL Server
- OLE DB provider for SQL Server [ADO]
- SQLOLEDB [ADO]
ms.assetid: 99bc40c4-9181-4ca1-a06f-9a1a914a0b7b
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Active
ms.openlocfilehash: 69e32ae7ddb254e18d0789f22bb6471da17a0c5e
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2018
---
# <a name="microsoft-ole-db-provider-for-sql-server-overview"></a>Поставщик Microsoft OLE DB для Обзор SQL Server
Поставщик Microsoft OLE DB для SQL Server, SQLOLEDB, позволяет ADO для доступа к Microsoft SQL Server.

**Примечание:** не рекомендуется использовать этот драйвер для разработки новых приложений. Новый поставщик OLE DB называется [драйвер Microsoft OLE DB для SQL Server](../../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL) которого будет обновлена последние функции сервера Забегая вперед.

## <a name="connection-string-parameters"></a>Параметры строки соединения
 Чтобы подключиться к этому поставщику, задайте *поставщика* аргумент [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойства:

```
SQLOLEDB
```

 Это значение можно также задать или прочитать с помощью [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойство.

## <a name="typical-connection-string"></a>Обычная строка соединения
 — Строка соединения для данного поставщика:

```
"Provider=SQLOLEDB;Data Source=serverName;"
Initial Catalog=databaseName;
User ID=MyUserID;Password=MyPassword;"
```

 Строка состоит из следующих ключевых слов:

|Ключевое слово|Описание|
|-------------|-----------------|
|**Поставщик**|Указывает поставщика OLE DB для SQL Server.|
|**Источник данных** или **сервера**|Указывает имя сервера.|
|**Начальный каталог** или **базы данных**|Указывает имя базы данных на сервере.|
|**Идентификатор пользователя** или **uid**|Указывает имя пользователя (для проверки подлинности SQL Server).|
|**Пароль** или **pwd**|Задает пароль пользователя (для проверки подлинности SQL Server).|

> [!NOTE]
>  При подключении к поставщик источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = yes** или **Integrated Security = SSPI** вместо идентификатора пользователя и пароля сведения в строке подключения.

## <a name="provider-specific-connection-parameters"></a>Параметры подключения для конкретного поставщика
 Поставщик поддерживает несколько параметров подключения к конкретному поставщику помимо параметрами, определенными ADO. Как с помощью свойства соединения ADO, эти свойства от поставщика может быть задано посредством [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекцию [подключения](../../../ado/reference/ado-api/connection-object-ado.md) или могут быть заданы как часть **ConnectionString**.

|Параметр|Описание|
|---------------|-----------------|
|Trusted_Connection|Указывает режим проверки подлинности пользователя. Это может быть присвоено **Да** или **нет**. Значение по умолчанию — **нет**. Если это свойство имеет значение **Да**, SQLOLEDB использует режим проверки подлинности Microsoft Windows NT для авторизации доступа пользователя для базы данных SQL Server, указанной **расположение** и [источника данных ](../../../ado/reference/ado-api/datasource-property-ado.md) значения свойств. Если это свойство имеет значение **нет**, SQLOLEDB использует смешанный режим для авторизации доступа пользователей к базе данных SQL Server. Имя входа SQL Server и пароль указываются в **идентификатор пользователя** и **пароль** свойства.|
|Текущий язык|Указывает имя записи языка SQL Server. Указывает язык, используемый для выбора и форматирования системных сообщений. Язык должен быть установлен на сервере SQL Server, в противном случае открытия, подключение завершится с ошибкой.|
|Сетевой адрес|Указывает сетевой адрес сервера SQL Server, заданные **расположение** свойство.|
|Сетевая библиотека|Указывает имя файла сетевой библиотеки (DLL), используемый для обмена данными с SQL Server. Не должно включать путь или расширение DLL. Настройка клиента SQL Server предоставляется значение по умолчанию.|
|Использование процедуры для подготовки|Определяет, является ли SQL Server создает временные хранимые процедуры, когда команды готовы (по **Готово** свойство).|
|Автоматическое преобразование|Указывает необходимость преобразования символов OEM/ANSI. Это свойство может быть присвоено **True** или **False**. Значение по умолчанию — **True**. Если это свойство имеет значение **True**, SQLOLEDB выполняет преобразование символов OEM/ANSI, когда строки многобайтовых символов получаться или отправляемые SQL Server. Если это свойство имеет значение **False**, SQLOLEDB не будет выполнять преобразование символов OEM/ANSI Многобайтовый символ строковых данных.|
|Packet Size|Указывает размер сетевого пакета в байтах. Значение свойства размера пакета должно быть в диапазоне от 512 до 32767. Размер сетевого пакета SQLOLEDB по умолчанию — 4096.|
|Application Name|Указывает имя клиентского приложения.|
|Идентификатор рабочей станции|строка, идентифицирующая рабочую станцию.|

## <a name="command-object-usage"></a>Использование объекта Command
 SQLOLEDB принимает в качестве допустимого синтаксиса сочетание ODBC, ANSI и связанные с SQL Server Transact-SQL. Например, следующая инструкция SQL использует escape-последовательность ODBC SQL, чтобы указать строковую функцию LCASE.

```
SELECT customerid={fn LCASE(CustomerID)} FROM Customers

```

 Функция LCASE возвращает строковое выражение, в котором все символы приведены к нижнему регистру. ANSI SQL строковая функция LOWER выполнит та же операция, поэтому следующая инструкция SQL является эквивалентно представленного выше инструкции ODBC ANSI:

```
SELECT customerid=LOWER(CustomerID) FROM Customers

```

 SQLOLEDB успешно обрабатывает любую форму инструкции при указании в виде текста команды.

## <a name="stored-procedures"></a>Хранимые процедуры
 При выполнении SQL Server хранимой процедуры с помощью команды SQLOLEDB, необходимо используйте escape-последовательность вызовов ODBC процедуры в тексте команды. SQLOLEDB затем использует механизм удаленного вызова процедуры SQL Server, чтобы оптимизировать обработку команды. Например следующая инструкция ODBC SQL является более предпочтительным текстом команды над формой Transact-SQL:

## <a name="odbc-sql"></a>ODBC SQL

```
{call SalesByCategory('Produce', '1995')}

```

## <a name="transact-sql"></a>Transact-SQL

```
EXECUTE SalesByCategory 'Produce', '1995'

```

## <a name="sql-server-features"></a>Функции SQL Server
 SQL Server с ADO можно использовать XML для **команда** вводить и получать результаты в формате потока XML, а не в **записей** объектов. Дополнительные сведения см. в разделе [использование потоков для ввода команды](../../../ado/guide/data/command-streams.md) и [получение результирующих наборов в потоки](../../../ado/guide/data/retrieving-resultsets-into-streams.md).

### <a name="accessing-sqlvariant-data-using-mdac-27-mdac-28-or-windows-dac-60"></a>Доступ к данным sql_variant, с помощью MDAC 2.7, компоненты MDAC версии 2.8 или Windows DAC 6.0
 Microsoft SQL Server имеет тип данных с именем **sql_variant**. Аналогично OLE DB **DBTYPE_VARIANT**, **sql_variant** тип данных может хранить данные из нескольких разных типов. Однако существуют некоторые ключевые различия между **DBTYPE_VARIANT** и **sql_variant**. ADO также обрабатывает данные, хранящиеся в виде **sql_variant** значение иначе, чем обработка других типов данных. В следующем списке описываются проблемы, которые следует учитывать при доступе к данным SQL Server, хранящиеся в столбцах типа **sql_variant**.

-   MDAC 2.7, компоненты MDAC версии 2.8 и компоненты доступа к данным Windows (Windows DAC) 6.0, поставщик OLE DB для SQL Server поддерживает **sql_variant** типа. Поставщик OLE DB для ODBC не поддерживается.

-   **Sql_variant** точно соответствует типу **DBTYPE_VARIANT** тип данных.  **Sql_variant** тип поддерживает несколько новые подтипы не поддерживается **DBTYPE_VARIANT,** включая **GUID**, **ANSI** (Юникод) строки, и **BIGINT**. Используя подтипов, отличный от перечисленных выше будет работать правильно.

-   **Sql_variant** подтип **ЧИСЛОВОЕ** не соответствует **DBTYPE_DECIMAL** в размере.

-   Несколько преобразований типов данных приведет к типам, которые не соответствуют. Например, приведение **sql_variant** с подтипом **GUID** для **DBTYPE_VARIANT** приведет к подтипом **safearray**(байт) . Преобразование этого типа обратно в **sql_variant** приведет к новых подтипа **массива**(в байтах).

-   **Набор записей** полей, содержащих **sql_variant** данных можно использовать удаленно (маршалинг) или сохраненного, только если **sql_variant** содержит конкретных подтипов. Попытка удаленного или сохранения данных со следующими неподдерживаемый подтипы приведет к ошибке во время выполнения (Неподдерживаемое преобразование) от поставщика сохраняемости Microsoft (MSPersist): **VT_VARIANT**, **VT_RECORD**, **VT_ILLEGAL**, **VT_UNKNOWN**, **VT_BSTR**, и **VT_DISPATCH.**

-   Поставщик OLE DB для SQL Server в MDAC 2.7, компоненты MDAC версии 2.8 и Windows DAC 6.0 имеет динамическое свойство с именем **разрешить собственного варианты** , как следует из имен, позволяющее разработчикам доступ к **sql_variant** в как в собственном формате **DBTYPE_VARIANT**. Если это свойство задано, а также **записей** открывается с обработчик курсора клиента (**adUseClient**), **Recordset.Open** вызов завершится ошибкой. Если это свойство задано и **записей** открывается с серверными курсорами (**adUseServer**), **Recordset.Open** вызов будет выполнен успешно, но при доступе к столбцам типа **sql_variant** приведет к ошибке.

-   В клиентские приложения, использующие компоненты MDAC версии 2.5 **sql_variant** данные могут быть использованы с запросами Microsoft SQL Server. Однако значения **sql_variant** данных рассматриваются как строки. Таких клиентских приложений необходимо обновить до MDAC 2.7, компоненты MDAC версии 2.8 или Windows DAC 6.0.

## <a name="recordset-behavior"></a>Поведение набора записей
 SQLOLEDB нельзя использовать курсоры SQL Server для поддержки нескольких результат, сформированных несколькими командами. Если потребитель запрашивает набор записей, требующий поддержки курсора SQL Server, если текст команды, используемый приводит к возникновению ошибки более чем одного определенного набора записей в результате возникает ошибка.

 Прокручиваемые наборы записей SQLOLEDB поддерживаются курсорами SQL Server. SQL Server налагает ограничения на курсоры, чувствительные к изменениям, сделанные другими пользователями базы данных. В частности строки в некоторых курсорах не может быть упорядочен и попытке создать набор записей, используя команду, содержащую предложение SQL ORDER BY может завершиться ошибкой.

## <a name="dynamic-properties"></a>Динамические свойства
 Поставщик Microsoft OLE DB для SQL Server вставляет несколько динамических свойств в **свойства** коллекцию Неоткрытое [подключения](../../../ado/reference/ado-api/connection-object-ado.md), [записей](../../../ado/reference/ado-api/recordset-object-ado.md)и [ Команда](../../../ado/reference/ado-api/command-object-ado.md) объектов.

 Следующие таблицы являются cross-index имен ADO и OLE DB для каждого динамических свойств. Справочник программиста OLE DB указано имя свойства ADO термин «Описание». Дополнительные сведения об этих свойствах можно найти в справочнике программиста OLE DB. Найдите имя свойства OLE DB в индексе или в разделе [приложение C: OLE DB свойства](http://msdn.microsoft.com/en-us/deded3ff-f508-4e1b-b2b1-fd9afd3bd292).

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
|Максимальный размер индекса|DBPROP_MAXINDEXSIZE|
|Максимальный размер строки|DBPROP_MAXROWSIZE|
|Максимальный размер строки, включая BLOB|DBPROP_MAXROWSIZEINCLUDESBLOB|
|Максимальное число таблиц в инструкции SELECT|DBPROP_MAXTABLESINSELECT|
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
 Следующие свойства добавляются **свойства** коллекцию **записей** объекта.

|Имя свойства ADO|Имя свойства OLE DB|
|-----------------------|--------------------------|
|Порядок доступа|DBPROP_ACCESSORDER|
|Блокировка объектов хранилища|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Тип закладки|DBPROP_BOOKMARKTYPE|
|Bookmarkable|DBPROP_IROWSETLOCATE|
|Изменить вставленных строк|DBPROP_CHANGEINSERTEDROWS|
|Права доступа столбца|DBPROP_COLUMNRESTRICT|
|Столбец набор уведомлений|DBPROP_NOTIFYCOLUMNSET|
|Время ожидания команды|DBPROP_COMMANDTIMEOUT|
|Отложенные столбцы|DBPROP_DEFERRED|
|Отложенное обновление объекта хранилища|DBPROP_DELAYSTORAGEOBJECTS|
|Выборку|DBPROP_CANFETCHBACKWARDS|
|Удерживайте строк|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|Немобильные строки|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|IRowsetIdentity|DBPROP_IRowsetIdentity|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsestLocate|
|IRowsetResynch||
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
|ISupportErrorInfo|DBPROP_ISupportErrorInfo|
|Литерал закладки|DBPROP_LITERALBOOKMARKS|
|Идентификатор строки литерала|DBPROP_LITERALIDENTITY|
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
|Уведомление об изменении позиции выборки набора строк|DBPROP_NOTIFYROWSETFETCHPOSISIONCHANGE|
|Уведомления о выпуске набора строк|DBPROP_NOTIFYROWSETRELEASE|
|Прокрутка назад|DBPROP_CANSCROLLBACKWARDS|
|Серверный курсор|DBPROP_SERVERCURSOR|
|Пропустить удаленные закладки|DBPROP_BOOKMARKSKIPPED|
|Идентификатор строки строгих|DBPROP_STRONGITDENTITY|
|Уникальные строки|DBPROP_UNIQUEROWS|
|Возможность обновления|DBPROP_UPDATABILITY|
|С помощью закладок|DBPROP_BOOKMARKS|

## <a name="command-dynamic-properties"></a>Команда динамические свойства
 Следующие свойства добавляются **свойства** коллекцию **команда** объекта.

|Имя свойства ADO|Имя свойства OLE DB|
|-----------------------|--------------------------|
|Порядок доступа|DBPROP_ACCESSORDER|
|Базовый путь|SSPROP_STREAM_BASEPATH|
|Блокировка объектов хранилища|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Тип закладки|DBPROP_BOOKMARKTYPE|
|Bookmarkable|DBPROP_IROWSETLOCATE|
|Изменить вставленных строк|DBPROP_CHANGEINSERTEDROWS|
|Права доступа столбца|DBPROP_COLUMNRESTRICT|
|Столбец набор уведомлений|DBPROP_NOTIFYCOLUMNSET|
|Тип содержимого|SSPROP_STREAM_CONTENTTYPE|
|Выборка курсора Auto|SSPROP_CURSORAUTOFETCH|
|Отложенные столбцы|DBPROP_DEFERRED|
|Отложенная подготовка|SSPROP_DEFERPREPARE|
|Отложенное обновление объекта хранилища|DBPROP_DELAYSTORAGEOBJECTS|
|Выборку|DBPROP_CANFETCHBACKWARDS|
|Удерживайте строк|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|Немобильные строки|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|IRowsetIdentity|DBPROP_IRowsetIdentity|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsetLocate|
|IRowsetResynch|DBPROP_IRowsetResynch|
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
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
|Свойство Encoding выходные данные|DBPROP_OUTPUTENCODING|
|Свойство выходного потока|DBPROP_OUTPUTSTREAM|
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
|Серверный курсор|DBPROP_SERVERCURSOR|
|Данные сервера при вставке|DBPROP_SERVERDATAONINSERT|
|Пропустить удаленные закладки|DBPROP_BOOKMARKSKIP|
|Идентификатор строки строгих|DBPROP_STRONGIDENTITY|
|Возможность обновления|DBPROP_UPDATABILITY|
|С помощью закладок|DBPROP_BOOKMARKS|
|Корневой XML|SSPROP_STREAM_XMLROOT|
|XSL|SSPROP_STREAM_XSL|

 Определенные сведения о реализации и функционального сведения о SQL Server поставщик OLE DB см. в разделе [поставщик SQL Server](http://msdn.microsoft.com/en-us/adf1d6c4-5930-444a-9248-ff1979729635).

## <a name="see-also"></a>См. также
 [Свойство ConnectionString (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [свойство поставщика (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) [объекта набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
