---
title: Поставщик Microsoft OLE DB для SQL Server | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], OLE DB provider for SQL Server
- OLE DB provider for SQL Server [ADO]
- SQLOLEDB [ADO]
ms.assetid: 99bc40c4-9181-4ca1-a06f-9a1a914a0b7b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 98de1a3a2e03a576b84543bf3578d87e7ad6c655
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47657981"
---
# <a name="microsoft-ole-db-provider-for-sql-server-overview"></a>Поставщик Microsoft OLE DB для Обзор SQL Server
Поставщик Microsoft OLE DB для SQL Server, SQLOLEDB, позволяет ADO для доступа к Microsoft SQL Server.

**Примечание:** не рекомендуется использовать этот драйвер для разработки новых приложений. Новый поставщик OLE DB называется [драйвера Microsoft OLE DB для SQL Server](../../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL) которого будет дополняться последние функции сервера, в дальнейшем.

## <a name="connection-string-parameters"></a>Параметры строки соединения
 Чтобы подключиться к этим поставщиком, задайте *поставщика* аргумент [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойства:

```
SQLOLEDB
```

 Это значение можно также задать или прочитать с помощью [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойство.

## <a name="typical-connection-string"></a>Типичная строка подключения
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
|**Начальный каталог** или **базы данных**|Задает имя базы данных на сервере.|
|**Идентификатор пользователя** или **uid**|Указывает имя пользователя (для проверки подлинности SQL Server).|
|**Пароль** или **pwd**|Указывает пароль пользователя (для проверки подлинности SQL Server).|

> [!NOTE]
>  Если вы подключаетесь к поставщик источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = yes** или **Integrated Security = SSPI** вместо идентификатора пользователя и пароля сведения в строке подключения.

## <a name="provider-specific-connection-parameters"></a>Параметры подключения для поставщика
 Поставщик поддерживает несколько параметров подключения для поставщика, помимо определенные ADO. Как с помощью свойства соединения ADO, эти свойства от поставщика может быть переведена с помощью [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекцию [подключения](../../../ado/reference/ado-api/connection-object-ado.md) или могут быть установлены как часть **ConnectionString**.

|Параметр|Описание|
|---------------|-----------------|
|Trusted_Connection|Указывает режим проверки подлинности пользователя. Это может быть присвоено **Да** или **нет**. Значение по умолчанию — **нет**. Если это свойство имеет значение **Да**, SQLOLEDB использует режим проверки подлинности Microsoft Windows NT для авторизации доступа пользователя для базы данных SQL Server, указанной **расположение** и [источника данных ](../../../ado/reference/ado-api/datasource-property-ado.md) значения свойств. Если это свойство имеет значение **нет**, SQLOLEDB использует смешанный режим для авторизации доступа пользователя к базе данных SQL Server. Имя входа SQL Server и пароль указываются в **идентификатор пользователя** и **пароль** свойства.|
|Текущий язык|Указывает имя языка SQL Server. Указывает язык, используемый для выбора и форматирования системных сообщений. Язык должен быть установлен на сервере SQL, в противном случае открытия, произойдет сбой подключения.|
|Сетевой адрес|Указывает сетевой адрес сервера SQL Server, определяемое **расположение** свойство.|
|Сетевая библиотека|Указывает имя сетевой библиотеки (DLL), используемый для обмена данными с SQL Server. Не должно включать путь или расширение DLL. Значение по умолчанию предоставляется в конфигурации клиента SQL Server.|
|Использование процедуры для подготовки|Определяет, создает ли SQL Server временные хранимые процедуры, когда команды готовы (с **подготовленных** свойство).|
|Автоматическое преобразование|Указывает необходимость преобразования символов OEM/ANSI. Это свойство может быть присвоено **True** или **False**. Значение по умолчанию — **True**. Если это свойство имеет значение **True**, SQLOLEDB выполняет преобразование символов OEM/ANSI, когда извлеченные из строки многобайтовых символов, или отправляемые SQL Server. Если это свойство имеет значение **False**, SQLOLEDB не выполняет преобразование символов OEM/ANSI многобайтовой кодировкой символов строковых данных.|
|Packet Size|Указывает размер сетевого пакета в байтах. Значение свойства размер пакета должен быть в диапазоне от 512 до 32767. Размер сетевого пакета SQLOLEDB по умолчанию — 4096.|
|Application Name|Указывает имя клиентского приложения.|
|Идентификатор рабочей станции|строка, идентифицирующая рабочую станцию.|

## <a name="command-object-usage"></a>Использование объекта Command
 SQLOLEDB принимает сочетание ODBC, ANSI и связанные с SQL Server Transact-SQL как допустимый синтаксис. Например, следующая инструкция SQL использует escape-последовательность ODBC SQL, чтобы указать строковую функцию LCASE.

```
SELECT customerid={fn LCASE(CustomerID)} FROM Customers

```

 Функция LCASE возвращает строковое выражение, в котором все символы приведены к нижнему регистру. Строковая функция ANSI SQL LOWER выполнит та же операция, поэтому следующая инструкция SQL является эквивалентно представленного выше инструкции ODBC ANSI:

```
SELECT customerid=LOWER(CustomerID) FROM Customers

```

 SQLOLEDB успешно обрабатывает любую форму инструкции при указании в виде текста для команды.

## <a name="stored-procedures"></a>Хранимые процедуры
 При выполнении SQL Server хранимой процедуры с помощью команды SQLOLEDB, используйте escape-последовательность вызова процедуры ODBC в тексте команды. SQLOLEDB, затем использует механизм удаленного вызова процедуры из SQL Server для оптимизации обработки команд. Например следующая инструкция ODBC SQL является более предпочтительным текстом команды форме Transact-SQL:

## <a name="odbc-sql"></a>ODBC SQL

```
{call SalesByCategory('Produce', '1995')}

```

## <a name="transact-sql"></a>Transact-SQL

```
EXECUTE SalesByCategory 'Produce', '1995'

```

## <a name="sql-server-features"></a>Функции SQL Server
 С помощью SQL Server, ADO можно использовать XML для **команда** ввода и получения результатов в формате потока XML, а не в **записей** объектов. Дополнительные сведения см. в разделе [использование потоков для ввода команды](../../../ado/guide/data/command-streams.md) и [извлечение результирующих наборов в потоки](../../../ado/guide/data/retrieving-resultsets-into-streams.md).

### <a name="accessing-sqlvariant-data-using-mdac-27-mdac-28-or-windows-dac-60"></a>Доступ к данным sql_variant, с помощью MDAC 2.7, MDAC 2.8 или Windows DAC 6.0
 Microsoft SQL Server имеет тип данных, называемый **sql_variant**. Аналогичную OLE DB **DBTYPE_VARIANT**, **sql_variant** тип данных можно хранить данные из нескольких разных типов. Тем не менее, существует ряд ключевых различий между **DBTYPE_VARIANT** и **sql_variant**. ADO также обрабатывает данные, хранящиеся в виде **sql_variant** значение иначе, чем обработка других типов данных. В следующем списке описываются проблемы, которые следует учитывать при доступе к данным SQL Server, хранящиеся в столбцах типа **sql_variant**.

-   MDAC 2.7, MDAC 2.8 и компоненты доступа к данным Windows (Windows DAC) 6.0, поставщик OLE DB для SQL Server поддерживает **sql_variant** типа. Поставщик OLE DB для ODBC — нет.

-   **Sql_variant** тип полностью соответствует **DBTYPE_VARIANT** тип данных.  **Sql_variant** типа поддерживает несколько новые подтипы не поддерживается **DBTYPE_VARIANT,** включая **GUID**, **ANSI** (Юникод) строки, и **BIGINT**. С помощью подтипов, отличные от перечисленных выше будут работать правильно.

-   **Sql_variant** подтип **ЧИСЛОВЫХ** не соответствует **DBTYPE_DECIMAL** размер.

-   Несколько преобразований типов данных приведет к типам, которые не соответствуют. Например, приведение **sql_variant** с подтипом **GUID** для **DBTYPE_VARIANT** приведет к подтипом **safearray**(в байтах) . Преобразование этого типа обратно в **sql_variant** приведет к новой подтипом **массива**(в байтах).

-   **Набор записей** поля, содержащие **sql_variant** данных может быть удаленной (маршалинг) или сохраненного, только если **sql_variant** содержит определенных подтипов. Попытка удаленного или сохранение данных в службе не поддерживаются следующие подтипы приведет к ошибке времени выполнения (неподдерживаемого преобразования) от поставщика сохраняемости Microsoft (MSPersist): **VT_VARIANT**, **VT_RECORD**, **VT_ILLEGAL**, **VT_UNKNOWN**, **VT_BSTR**, и **VT_DISPATCH.**

-   Поставщик OLE DB для SQL Server в MDAC 2.7, MDAC 2.8 и Windows DAC 6.0 имеет динамическое свойство с именем **разрешить собственные варианты** , как и предполагает название, позволяющий разработчикам получать доступ к **sql_variant** в его исходной форме, в отличие от **DBTYPE_VARIANT**. Если это свойство имеет значение, а также **записей** открыт с помощью обработчик курсора клиента (**adUseClient**), **Recordset.Open** вызов завершится ошибкой. Если это свойство имеет значение и **записей** открыт с помощью серверных курсоров (**adUseServer**), **Recordset.Open** вызов будет успешным, но доступ к столбцам типа **sql_variant** приведет к ошибке.

-   В клиентские приложения, использующие компоненты MDAC версии 2.5 **sql_variant** данные, которые могут использоваться с запросами Microsoft SQL Server. Тем не менее значения **sql_variant** данных рассматриваются как строки. Таких клиентских приложений необходимо обновить до MDAC 2.7, MDAC 2.8 или Windows DAC 6.0.

## <a name="recordset-behavior"></a>Поведение набора записей
 SQLOLEDB нельзя использовать курсоры SQL Server для поддержки нескольких результат, сформированных несколькими командами. Если потребитель запрашивает набор записей, требующих поддержки курсора SQL Server, если текст команды, используемый сформирует несколько одно подмножество записей в результате возникает ошибка.

 Прокручиваемые наборы записей SQLOLEDB поддерживаются курсоры SQL Server. SQL Server налагает ограничения на курсоры, чувствительные к изменениям, сделанные другими пользователями базы данных. В частности строки в некоторых курсорах не может быть упорядочен, и попытке создать набор записей, используя команду, содержащую предложение SQL ORDER BY может завершиться ошибкой.

## <a name="dynamic-properties"></a>Динамические свойства
 Поставщик Microsoft OLE DB для SQL Server вставляет несколько динамических свойств в **свойства** коллекцию неоткрытый [подключения](../../../ado/reference/ado-api/connection-object-ado.md), [записей](../../../ado/reference/ado-api/recordset-object-ado.md)и [ Команда](../../../ado/reference/ado-api/command-object-ado.md) объектов.

 В следующих таблицах представлены cross-index имен ADO и OLE DB для каждого динамического свойства. Справочник программиста OLE DB по указано имя свойства ADO с термином «Description». Дополнительные сведения об этих свойствах можно найти в справочнике программиста OLE DB. Найдите имя свойства OLE DB в индексе или см. в разделе [приложение C: OLE DB свойства](http://msdn.microsoft.com/deded3ff-f508-4e1b-b2b1-fd9afd3bd292).

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
|Максимальный размер индекса|DBPROP_MAXINDEXSIZE|
|Максимальный размер строки|DBPROP_MAXROWSIZE|
|Максимальный размер строки, включая BLOB|DBPROP_MAXROWSIZEINCLUDESBLOB|
|Максимальное число таблиц в SELECT|DBPROP_MAXTABLESINSELECT|
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
 Следующие свойства добавляются к **свойства** коллекцию **записей** объекта.

|Имя свойства ADO|Имя свойства OLE DB|
|-----------------------|--------------------------|
|Порядок доступа|DBPROP_ACCESSORDER|
|Блокирование объектов хранилища|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Тип закладки|DBPROP_BOOKMARKTYPE|
|Bookmarkable|DBPROP_IROWSETLOCATE|
|Изменение вставленных строк|DBPROP_CHANGEINSERTEDROWS|
|Права доступа столбца|DBPROP_COLUMNRESTRICT|
|Уведомление о задании столбца|DBPROP_NOTIFYCOLUMNSET|
|Время ожидания команды|DBPROP_COMMANDTIMEOUT|
|Отложить столбца|DBPROP_DEFERRED|
|Отложенное обновление объекта хранилища|DBPROP_DELAYSTORAGEOBJECTS|
|Выборка в обратном порядке|DBPROP_CANFETCHBACKWARDS|
|Удерживайте строк|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|Фиксированные строки|DBPROP_IMMOBILEROWS|
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
|Литеральные закладки|DBPROP_LITERALBOOKMARKS|
|Литеральная Идентификация строки|DBPROP_LITERALIDENTITY|
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
|Уведомление об изменении позиции выборки набора строк|DBPROP_NOTIFYROWSETFETCHPOSISIONCHANGE|
|Уведомление о разблокировании набора строк|DBPROP_NOTIFYROWSETRELEASE|
|Обратная прокрутка|DBPROP_CANSCROLLBACKWARDS|
|Серверный курсор|DBPROP_SERVERCURSOR|
|Пропуск удаленных закладок|DBPROP_BOOKMARKSKIPPED|
|Строгая Идентификация строки|DBPROP_STRONGITDENTITY|
|Уникальные строки|DBPROP_UNIQUEROWS|
|Возможности обновления|DBPROP_UPDATABILITY|
|Использование закладок|DBPROP_BOOKMARKS|

## <a name="command-dynamic-properties"></a>Динамические свойства команды
 Следующие свойства добавляются к **свойства** коллекцию **команда** объекта.

|Имя свойства ADO|Имя свойства OLE DB|
|-----------------------|--------------------------|
|Порядок доступа|DBPROP_ACCESSORDER|
|Базовый путь|SSPROP_STREAM_BASEPATH|
|Блокирование объектов хранилища|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Тип закладки|DBPROP_BOOKMARKTYPE|
|Bookmarkable|DBPROP_IROWSETLOCATE|
|Изменение вставленных строк|DBPROP_CHANGEINSERTEDROWS|
|Права доступа столбца|DBPROP_COLUMNRESTRICT|
|Уведомление о задании столбца|DBPROP_NOTIFYCOLUMNSET|
|Тип содержимого|SSPROP_STREAM_CONTENTTYPE|
|Выборка курсора Auto|SSPROP_CURSORAUTOFETCH|
|Отложить столбца|DBPROP_DEFERRED|
|Отложенная подготовка|SSPROP_DEFERPREPARE|
|Отложенное обновление объекта хранилища|DBPROP_DELAYSTORAGEOBJECTS|
|Выборка в обратном порядке|DBPROP_CANFETCHBACKWARDS|
|Удерживайте строк|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|Фиксированные строки|DBPROP_IMMOBILEROWS|
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
|Свойство Encoding выходные данные|DBPROP_OUTPUTENCODING|
|Свойство Output Stream|DBPROP_OUTPUTSTREAM|
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
|Серверный курсор|DBPROP_SERVERCURSOR|
|Данные сервера при вставке|DBPROP_SERVERDATAONINSERT|
|Пропуск удаленных закладок|DBPROP_BOOKMARKSKIP|
|Строгая Идентификация строки|DBPROP_STRONGIDENTITY|
|Возможности обновления|DBPROP_UPDATABILITY|
|Использование закладок|DBPROP_BOOKMARKS|
|Корневой XML|SSPROP_STREAM_XMLROOT|
|XSL|SSPROP_STREAM_XSL|

 Определенные сведения о реализации и функционального сведения о Microsoft Server поставщик OLE DB SQL, см. в разделе [поставщик SQL Server](http://msdn.microsoft.com/adf1d6c4-5930-444a-9248-ff1979729635).

## <a name="see-also"></a>См. также
 [Свойство ConnectionString (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [свойство Provider (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) [объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
