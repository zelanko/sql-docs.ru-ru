---
title: Поставщик OLE DB Майкрософт для SQL Server | Документация Майкрософт
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
ms.openlocfilehash: bd28ece0e82c4551409920c876d54fbd7dc501ff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67926617"
---
# <a name="microsoft-ole-db-provider-for-sql-server-overview"></a>Обзор поставщика OLE DB Майкрософт для SQL Server
Поставщик OLE DB Майкрософт для SQL Server, SQLOLEDB предоставляет ADO доступ к Microsoft SQL Server.

> [!IMPORTANT]
> Поставщик OLE DB Майкрософт для SQL Server (SQLOLEDB) остается устаревшим и не рекомендуется использовать его для новых задач разработки. Вместо этого используйте новый драйвер [Microsoft OLE DB для SQL Server](../../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL), который будет обновлен с самыми последними серверными компонентами.

## <a name="connection-string-parameters"></a>Параметры строки подключения
 Чтобы подключиться к поставщику, задайте для аргумента *поставщика* в качестве значения свойства [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) значение:

```vb
SQLOLEDB
```

 Это значение также может быть задано или считано с помощью свойства [provider](../../../ado/reference/ado-api/provider-property-ado.md) .

## <a name="typical-connection-string"></a>Типичная строка подключения
 Типичная строка подключения для этого поставщика:

```vb
"Provider=SQLOLEDB;Data Source=serverName;"
Initial Catalog=databaseName;
User ID=MyUserID;Password=MyPassword;"
```

 Строка состоит из следующих ключевых слов:

|Ключевое слово|Description|
|-------------|-----------------|
|**Поставщик**|Указывает поставщика OLE DB для SQL Server.|
|**Источник данных** или **сервер**|Указывает имя сервера.|
|**Исходный каталог** или **база данных**|Указывает имя базы данных на сервере.|
|**Идентификатор пользователя** или **UID**|Указывает имя пользователя (для проверки подлинности SQL Server).|
|**Password** или **PWD**|Указывает пароль пользователя (для SQL Server проверки подлинности).|

> [!NOTE]
>  При подключении к поставщику источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = Yes** или **Integrated Security = SSPI** вместо сведений об идентификаторе пользователя и пароле в строке подключения.

## <a name="provider-specific-connection-parameters"></a>Параметры подключения, зависящие от поставщика
 Поставщик поддерживает несколько параметров соединения, зависящих от поставщика, помимо тех, которые определены в ADO. Как и в случае со свойствами соединения ADO, эти свойства, зависящие от поставщика, могут быть заданы через коллекцию [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) [соединения](../../../ado/reference/ado-api/connection-object-ado.md) или могут быть заданы как часть **ConnectionString**.

|Параметр|Description|
|---------------|-----------------|
|Trusted_Connection|Указывает режим проверки подлинности пользователя. Для этого свойства можно задать значение **Да** или **нет**. Значение по умолчанию — **No**. Если для этого свойства задано значение **Да**, SQLOLEDB использует режим проверки подлинности Microsoft Windows NT для авторизации доступа пользователей к SQL Server базе данных, указанной значениями свойств **Location** и [DataSource](../../../ado/reference/ado-api/datasource-property-ado.md) . Если это свойство имеет значение **нет**, SQLOLEDB использует смешанный режим для авторизации доступа пользователей к базе данных SQL Server. Имя входа и пароль SQL Server указаны в свойствах **идентификатора пользователя** и **пароля** .|
|Текущий язык|Указывает SQL Server имя языка. Указывает язык, используемый для выбора и форматирования системных сообщений. Язык должен быть установлен на SQL Server, иначе открытие подключения завершится ошибкой.|
|Сетевой адрес|Указывает сетевой адрес SQL Server, заданный свойством **Location** .|
|Network Library|Указывает имя сетевой библиотеки (DLL), используемой для связи с SQL Server. Не должно включать путь или расширение DLL. Значение по умолчанию предоставляется конфигурацией клиента SQL Server.|
|Использовать процедуру для подготовки|Определяет, создает ли SQL Server временные хранимые процедуры при подготовке команд ( **подготовленным** свойством).|
|Автоматическое преобразование|Указывает, преобразуются ли символы OEM/ANSI. Этому свойству можно присвоить значение **true** или **false**. Значение по умолчанию ― **True**. Если это свойство имеет значение **true**, SQLOLEDB выполняет преобразование символов OEM/ANSI, когда многобайтовые символьные строки извлекаются из SQL Server или отправляются в него. Если для этого свойства задано значение **false**, SQLOLEDB не выполняет преобразование символов OEM/ANSI в многобайтовой символьной строке данных.|
|Packet Size|Указывает размер сетевого пакета в байтах. Значение свойства "размер пакета" должно находиться в диапазоне от 512 до 32767. Размер сетевого пакета SQLOLEDB по умолчанию — 4096.|
|Имя приложения|Указывает имя клиентского приложения.|
|Идентификатор рабочей станции|строка, идентифицирующая рабочую станцию.|

## <a name="command-object-usage"></a>Использование объекта команды
 SQLOLEDB принимает в качестве допустимого синтаксиса амалгам, характерный для ODBC, ANSI и SQL Server языка Transact-SQL. Например, следующая инструкция SQL использует escape-последовательность ODBC SQL, чтобы указать строковую функцию LCASE.

```sql
SELECT customerid={fn LCASE(CustomerID)} FROM Customers

```

 Функция LCASE возвращает строковое выражение, в котором все символы приведены к нижнему регистру. Функция String SQL в ANSI LOWER выполняет ту же операцию, поэтому следующая инструкция SQL является эквивалентом приведенной выше инструкции ODBC в кодировке ANSI.

```sql
SELECT customerid=LOWER(CustomerID) FROM Customers

```

 SQLOLEDB успешно обрабатывает любую форму инструкции, если она указана в качестве текста для команды.

## <a name="stored-procedures"></a>Хранимые процедуры
 При выполнении SQL Server хранимой процедуры с помощью команды SQLOLEDB используйте escape-последовательность вызова процедуры ODBC в тексте команды. Затем служба SQLOLEDB использует механизм удаленного вызова процедур SQL Server для оптимизации обработки команд. Например, следующая инструкция ODBC SQL является предпочтительным текстом команды в форме Transact-SQL:

## <a name="odbc-sql"></a>ODBC SQL

```vb
{call SalesByCategory('Produce', '1995')}

```

## <a name="transact-sql"></a>Transact-SQL

```sql
EXECUTE SalesByCategory 'Produce', '1995'

```

## <a name="sql-server-features"></a>SQL Server функции
 При использовании SQL Server ADO может использовать XML для ввода **команды** и получать результаты в формате XML-потока, а не в объектах **набора записей** . Дополнительные сведения см. в разделе [Использование потоков для ввода команды](../../../ado/guide/data/command-streams.md) и [получение результирующих наборов в потоках](../../../ado/guide/data/retrieving-resultsets-into-streams.md).

### <a name="accessing-sql_variant-data-using-mdac-27-mdac-28-or-windows-dac-60"></a>Доступ к данным sql_variant с помощью MDAC 2,7, MDAC 2,8 или Windows DAC 6,0
 Microsoft SQL Server имеет тип данных с именем **sql_variant**. Как и **DBTYPE_VARIANT**OLE DB, тип данных **sql_variant** может хранить данные нескольких разных типов. Однако между **DBTYPE_VARIANT** и **sql_variant**существует несколько ключевых различий. ADO также обрабатывает данные, хранящиеся в виде **sql_variant** , иначе, чем они обрабатывают другие типы данных. В следующем списке описываются проблемы, которые следует учитывать при доступе к SQL Server данным, хранящимся в столбцах типа **sql_variant**.

-   В MDAC 2,7, MDAC 2,8 и компонентах доступа к данным Windows (Windows DAC) 6,0 поставщик OLE DB для SQL Server поддерживает тип **sql_variant** . Поставщик OLE DB для ODBC не поддерживает.

-   Тип **sql_variant** не в точности соответствует типу данных **DBTYPE_VARIANT** .  Тип **sql_variant** поддерживает несколько новых подтипов, которые не поддерживаются **DBTYPE_VARIANT,** включая **GUID**, строки **ANSI** (не в Юникоде) и **bigint**. Использование подтипов, отличных от перечисленных выше, будет работать правильно.

-   **Числовое** значение подтипа **sql_variant** не соответствует размеру **DBTYPE_DECIMAL** .

-   Множественные приведение типов данных приведет к несовпадению типов. Например, при преобразовании **sql_variant** с подтипом **GUID** в **DBTYPE_VARIANT** приведет к подтипу **SAFEARRAY**(bytes). Преобразование этого типа обратно в **sql_variant** приведет к созданию нового подтипа **массива**(байт).

-   Поля **набора записей** , содержащие данные **sql_variant** , могут быть удаленными (упакованными) или материализованными, только если **sql_variant** содержит конкретные подтипы. Попытка удаленного или сохранения данных со следующими неподдерживаемыми подтипами приведет к ошибке во время выполнения (неподдерживаемое преобразование) от поставщика сохраняемости (Майкрософт) (Мсперсист): **VT_VARIANT**, **VT_RECORD**, **VT_ILLEGAL**, **VT_UNKNOWN**, **VT_BSTR**и **VT_DISPATCH.**

-   Поставщик OLE DB для SQL Server в MDAC 2,7, MDAC 2,8 и Windows DAC 6,0 имеет динамическое свойство с именем **Разрешить собственные варианты** , которые, как предполагается в названии, позволяют разработчикам получить доступ к **sql_variant** в собственной форме, а не **DBTYPE_VARIANT**. Если это свойство установлено и **набор записей** открыт с помощью обработчика курсора клиента (**адусеклиент**), вызов **Recordset. Open** завершится ошибкой. Если это свойство задано и **набор записей** открыт с серверными курсорами (**адусесервер**), вызов **Recordset. Open** будет выполнен, но при доступе к столбцам типа **sql_variant** будет возникать ошибка.

-   В клиентских приложениях, использующих MDAC 2,5, **sql_variant** данные могут использоваться с запросами Microsoft SQL Server. Однако значения **sql_variant** данных обрабатываются как строки. Такие клиентские приложения должны быть обновлены до MDAC 2,7, MDAC 2,8 или Windows DAC 6,0.

## <a name="recordset-behavior"></a>Поведение набора записей
 SQLOLEDB не может использовать SQL Server курсоры для поддержки нескольких результатов, созданных многими командами. Если потребитель запрашивает набор записей, который требует SQL Server поддержки курсора, возникает ошибка, если используемый текст команды создает в качестве результата больше одного набора записей.

 Доступные для прокрутки наборы записей SQLOLEDB поддерживаются SQL Server курсорами. SQL Server накладывает ограничения на курсоры, которые чувствительны к изменениям, внесенным другими пользователями базы данных. В частности, строки в некоторых курсорах не могут быть упорядочены, и попытка создать набор записей с помощью команды, содержащей предложение SQL ORDER BY, может завершиться ошибкой.

## <a name="dynamic-properties"></a>Динамические свойства
 Поставщик OLE DB Майкрософт для SQL Server вставляет несколько динамических свойств в коллекцию **свойств** неоткрытыго [соединения](../../../ado/reference/ado-api/connection-object-ado.md), [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md)и [командных](../../../ado/reference/ado-api/command-object-ado.md) объектов.

 В следующих таблицах приведены перекрестные индексы имен ADO и OLE DB для каждого динамического свойства. Ссылка на OLE DB программиста ссылается на имя свойства ADO по термину «описание». Дополнительные сведения об этих свойствах можно найти в справочнике по программисту OLE DB. Найдите имя свойства OLE DB в индексе или см. [приложение в: OLE DB свойства](https://msdn.microsoft.com/deded3ff-f508-4e1b-b2b1-fd9afd3bd292).

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
|Время ожидания соединения|DBPROP_INIT_TIMEOUT|
|Текущий каталог|DBPROP_CURRENTCATALOG|
|источник данных|DBPROP_INIT_DATASOURCE|
|Имя источника данных|DBPROP_DATASOURCENAME|
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
|Максимальный размер индекса|DBPROP_MAXINDEXSIZE|
|Максимальный размер строки|DBPROP_MAXROWSIZE|
|Максимальный размер строки включает большой двоичный объект|DBPROP_MAXROWSIZEINCLUDESBLOB|
|Максимальное число таблиц в SELECT|DBPROP_MAXTABLESINSELECT|
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
|Сохранять сведения о безопасности|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|
|Тип постоянного идентификатора|DBPROP_PERSISTENTIDTYPE|
|Поведение при подготовке к прерыванию|DBPROP_PREPAREABORTBEHAVIOR|
|Действие подготовки к фиксации|DBPROP_PREPARECOMMITBEHAVIOR|
|Условие процедуры|DBPROP_PROCEDURETERM|
|Prompt|DBPROP_INIT_PROMPT|
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
|Маркер окна|DBPROP_INIT_HWND|

## <a name="recordset-dynamic-properties"></a>Динамические свойства набора записей
 Следующие свойства добавляются в коллекцию **Properties** объекта **Recordset** .

|Имя свойства ADO|Имя свойства OLE DB|
|-----------------------|--------------------------|
|Порядок доступа|DBPROP_ACCESSORDER|
|Блокировка объектов хранилища|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Тип закладки|DBPROP_BOOKMARKTYPE|
|С закладками|DBPROP_IROWSETLOCATE|
|Изменить вставленные строки|DBPROP_CHANGEINSERTEDROWS|
|Права доступа к столбцу|DBPROP_COLUMNRESTRICT|
|Уведомление о наборе столбцов|DBPROP_NOTIFYCOLUMNSET|
|Время ожидания команды|DBPROP_COMMANDTIMEOUT|
|Откладывание столбца|DBPROP_DEFERRED|
|Задержка обновлений объектов хранилища|DBPROP_DELAYSTORAGEOBJECTS|
|Получить назад|DBPROP_CANFETCHBACKWARDS|
|Удержание строк|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|Строки немобильных устройств|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|ировсетидентити|DBPROP_IRowsetIdentity|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsestLocate|
|Интерфейс irowsetresynch||
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
|ISupportErrorInfo|DBPROP_ISupportErrorInfo|
|Литеральные закладки|DBPROP_LITERALBOOKMARKS|
|Удостоверение литеральной строки|DBPROP_LITERALIDENTITY|
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
|Уведомление об изменении расположения выборки набора строк|DBPROP_NOTIFYROWSETFETCHPOSISIONCHANGE|
|Уведомление о выпуске набора строк|DBPROP_NOTIFYROWSETRELEASE|
|Прокрутка назад|DBPROP_CANSCROLLBACKWARDS|
|Серверный курсор|DBPROP_SERVERCURSOR|
|Пропустить удаленные закладки|DBPROP_BOOKMARKSKIPPED|
|Строгая идентификация строк|DBPROP_STRONGITDENTITY|
|Уникальные строки|DBPROP_UNIQUEROWS|
|Updatability|DBPROP_UPDATABILITY|
|Использование закладок|DBPROP_BOOKMARKS|

## <a name="command-dynamic-properties"></a>Динамические свойства команды
 Следующие свойства добавляются в коллекцию **Properties** объекта **Command** .

|Имя свойства ADO|Имя свойства OLE DB|
|-----------------------|--------------------------|
|Порядок доступа|DBPROP_ACCESSORDER|
|Базовый путь|SSPROP_STREAM_BASEPATH|
|Блокировка объектов хранилища|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Тип закладки|DBPROP_BOOKMARKTYPE|
|С закладками|DBPROP_IROWSETLOCATE|
|Изменить вставленные строки|DBPROP_CHANGEINSERTEDROWS|
|Права доступа к столбцу|DBPROP_COLUMNRESTRICT|
|Уведомление о наборе столбцов|DBPROP_NOTIFYCOLUMNSET|
|Тип содержимого|SSPROP_STREAM_CONTENTTYPE|
|Автоматическая выборка курсора|SSPROP_CURSORAUTOFETCH|
|Откладывание столбца|DBPROP_DEFERRED|
|Отложенная подготовка|SSPROP_DEFERPREPARE|
|Задержка обновлений объектов хранилища|DBPROP_DELAYSTORAGEOBJECTS|
|Получить назад|DBPROP_CANFETCHBACKWARDS|
|Удержание строк|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|Строки немобильных устройств|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|ировсетидентити|DBPROP_IRowsetIdentity|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsetLocate|
|Интерфейс irowsetresynch|DBPROP_IRowsetResynch|
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
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
|Свойство кодирования вывода|DBPROP_OUTPUTENCODING|
|Свойство потока вывода|DBPROP_OUTPUTSTREAM|
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
|Серверный курсор|DBPROP_SERVERCURSOR|
|Данные сервера при вставке|DBPROP_SERVERDATAONINSERT|
|Пропустить удаленные закладки|DBPROP_BOOKMARKSKIP|
|Строгая идентификация строк|DBPROP_STRONGIDENTITY|
|Updatability|DBPROP_UPDATABILITY|
|Использование закладок|DBPROP_BOOKMARKS|
|Корень XML|SSPROP_STREAM_XMLROOT|
|XSL|SSPROP_STREAM_XSL|

 Сведения о конкретной реализации и сведения о функциональных возMicrosoft SQL Serverии OLE DB поставщика см. в разделе [поставщик SQL Server](https://msdn.microsoft.com/adf1d6c4-5930-444a-9248-ff1979729635).

## <a name="see-also"></a>См. также:
 Property ( [ADO) свойство](../../../ado/reference/ado-api/connectionstring-property-ado.md) [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) (ADO) [объект Recordset Object (](../../../ado/reference/ado-api/recordset-object-ado.md) ADO)
