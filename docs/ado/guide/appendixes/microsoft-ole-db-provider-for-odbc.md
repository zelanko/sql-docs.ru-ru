---
title: "Поставщик Microsoft OLE DB для ODBC | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: H1Hack27Feb2017
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OLE DB provider for ODBC [ADO]
- providers [ADO], OLE DB provider for ODBC
ms.assetid: 2dc0372d-e74d-4d0f-9c8c-04e5a168c148
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6b3753748a9e76d24dc968983fa358b5d0050f41
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="microsoft-ole-db-provider-for-odbc-overview"></a>Поставщик Microsoft OLE DB для ODBC Обзор
Программисту ADO или служб удаленных рабочих СТОЛОВ идеальном мире бы одно данных каждый источник предоставляет интерфейс OLE DB, чтобы вызвать ADO непосредственно в источник данных. Несмотря на то, что все чаще других поставщиков базы данных реализует интерфейсы OLE DB, некоторые источники данных не еще доступны таким образом. Однако большинство систем DBMS в настоящее время доступны через ODBC.

 Драйверы ODBC доступны для каждой основной СУБД, в настоящее время, включая Microsoft SQL Server, Microsoft Access (базы данных Microsoft Jet) и Microsoft FoxPro, помимо продукты сторонних разработчиков баз данных, например Oracle.

 Поставщик Microsoft ODBC, однако позволяет ADO для подключения к любому источнику данных ODBC. Поставщик является свободнопотоковым и Юникод.

 Поставщик поддерживает транзакции, несмотря на то, что разные ядра СУБД предлагают различные виды поддержки транзакций. Например Microsoft Access поддерживает вложенные транзакции до пяти уровней вложенности.

 Это поставщик по умолчанию для ADO, и все зависящие от поставщика ADO свойства и методы поддерживаются.

## <a name="connection-string-parameters"></a>Параметры строки соединения
 Чтобы подключиться к этому поставщику, задайте **поставщика =** аргумент [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойства:

```
MSDASQL
```

 Чтение [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойство возвратит также этой строки.

## <a name="typical-connection-string"></a>Обычная строка соединения
 — Строка соединения для данного поставщика:

```
"Provider=MSDASQL;DSN=dsnName;UID=MyUserID;PWD=MyPassword;"
```

 Строка состоит из следующих ключевых слов:

|Ключевое слово|Description|
|-------------|-----------------|
|**Поставщик**|Определяет поставщик OLE DB для ODBC.|
|**ИМЯ ИСТОЧНИКА ДАННЫХ**|Указывает имя источника данных.|
|**UID**|Указывает имя пользователя.|
|**PWD**|Указывает пароль пользователя.|
|**URL-адрес**|Указывает URL-адрес к файлу или каталогу, опубликованных в веб-папке.|

 Поскольку это поставщик по умолчанию для ADO, если не указан **поставщика =** параметр в строке подключения ADO будет пытаться установить соединение с этим поставщиком.

> [!NOTE]
>  При подключении к поставщик источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = yes** или **Integrated Security = SSPI** вместо идентификатора пользователя и пароля сведения в строке подключения.

 Поставщик не поддерживает параметры конкретного соединения помимо параметрами, определенными ADO. Однако поставщик передает параметры соединения не ADO диспетчер драйверов ODBC.

 Поскольку можно опустить **поставщика** параметр, вы можете таким образом составить строки соединения ADO, идентичный строку соединения для источника данных ODBC. Использовать одинаковые имена параметров (**ДРАЙВЕРА =**, **базы данных =**, **DSN =**и так далее), значения и синтаксис, что вы бы при создании строки подключения ODBC. Можно подключиться с или без имени источника данных (DSN) или FileDSN.

## <a name="syntax-with-a-dsn-or-filedsn"></a>Синтаксис с DSN или FileDSN:

```
"[Provider=MSDASQL;] { DSN=name | FileDSN=filename } ;
[DATABASE=database;] UID=user; PWD=password"
```

## <a name="syntax-without-a-dsn-dsn-less-connection"></a>Синтаксис без DSN (соединения):

```
"[Provider=MSDASQL;] DRIVER=driver; SERVER=server;
DATABASE=database; UID=MyUserID; PWD=MyPassword"
```

## <a name="remarks"></a>Замечания
 Если вы используете **DSN** или **FileDSN**, он должен быть определен через администратор источников данных ODBC в панели управления Windows. В Microsoft Windows 2000 администратор ODBC находится в разделе Администрирование. В более ранних версиях Windows, называется значок администратора ODBC **32-разрядная версия ODBC** или просто **ODBC**.

 В качестве альтернативы для параметра **DSN**, можно указать драйвер ODBC (**ДРАЙВЕР =**), такие как «SQL Server»; имя сервера (**SERVER =**); и имя базы данных (**Базы данных =**).

 Можно также указать имя учетной записи пользователя (**UID =**) и пароль для учетной записи пользователя (**PWD =**) в параметры, относящиеся к ODBC или в стандарте определяемых ADO *пользователя* и *пароль* параметров.

 Несмотря на то что **DSN** определение уже содержит имя базы данных, можно указать ** *базы данных* параметр в дополнение к **DSN** для подключения с другой базой данных. Рекомендуется всегда включать ** *базы данных* параметр при использовании **DSN**. Это обеспечит подключение к правильной базе данных, если другой пользователь изменил параметр по умолчанию базы данных с момента последней проверки **DSN** определения.

## <a name="provider-specific-connection-properties"></a>Свойства подключения для конкретного поставщика
 Поставщик OLE DB для ODBC добавляет несколько параметров для [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекцию **подключения** объекта. Ниже перечислены эти свойства с именем соответствующего свойства OLE DB в круглые скобки.

|Имя свойства|Description|
|-------------------|-----------------|
|Доступны процедуры (KAGPROP_ACCESSIBLEPROCEDURES)|Указывает, имеет ли пользователь доступ к хранимым процедурам.|
|Доступной таблицы (KAGPROP_ACCESSIBLETABLES)|Указывает, имеет ли пользователь разрешение на выполнение инструкций SELECT к таблицам базы данных.|
|К активным операторам (KAGPROP_ACTIVESTATEMENTS)|Указывает число дескрипторов, поддерживаемых драйвером ODBC для подключения.|
|Имя драйвера (KAGPROP_DRIVERNAME)|Указывает имя файла драйвера ODBC.|
|Версия драйвера ODBC (KAGPROP_DRIVERODBCVER)|Указывает версию ODBC, который поддерживает этот драйвер.|
|Использование файла (KAGPROP_FILEUSAGE)|Указывает, как драйвер использует файл источника данных; Таблица, либо как каталог.|
|Как и предложение Escape (KAGPROP_LIKEESCAPECLAUSE)|Указывает ли драйвер поддерживает определение и использование escape-символ для (%) символ процента и символ подчеркивания (_) в предикате LIKE предложения WHERE.|
|Max столбцов на Group By (KAGPROP_MAXCOLUMNSINGROUPBY)|Указывает максимальное число столбцов, которые могут быть перечислены в предложении GROUP BY инструкции SELECT.|
|Max столбцов в индексе (KAGPROP_MAXCOLUMNSININDEX)|Указывает максимальное число столбцов, которые могут быть включены в индекс.|
|Max столбцы в Order By (KAGPROP_MAXCOLUMNSINORDERBY)|Указывает максимальное число столбцов, которые могут быть перечислены в предложении ORDER BY инструкции SELECT.|
|Max столбцы в инструкции Select (KAGPROP_MAXCOLUMNSINSELECT)|Указывает максимальное число столбцов, которые могут быть перечислены в предложение SELECT инструкции SELECT.|
|Max столбцов в таблице (KAGPROP_MAXCOLUMNSINTABLE)|Указывает максимальное количество столбцов в таблице.|
|Числовые функции (KAGPROP_NUMERICFUNCTIONS)|Указывает числовые функции, которые поддерживаются драйвером ODBC. Для получения списка имен функций и связанные значения, используемые в этой битовой маске [приложение E: скалярные функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md), в документации ODBC.|
|Возможности внешнего соединения (KAGPROP_OJCAPABILITY)|Указывает типы ВНЕШНИЕ соединения, поддерживаемых поставщиком.|
|Внешние соединения (KAGPROP_OUTERJOINS)|Указывает, поддерживает ли поставщик ВНЕШНИЕ соединения.|
|Специальные символы (KAGPROP_SPECIALCHARACTERS)|Указывает, какие символы имеют специальное значение для драйвера ODBC.|
|Хранимые процедуры (KAGPROP_PROCEDURES)|Указывает, доступны ли хранимые процедуры для использования с этот драйвер ODBC.|
|Строковые функции (KAGPROP_STRINGFUNCTIONS)|Указывает, какие строки функции поддерживаются драйвером ODBC. Для получения списка имен функций и связанные значения, используемые в этой битовой маске [приложение E: скалярные функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md), в документации ODBC.|
|Системные функции (KAGPROP_SYSTEMFUNCTIONS)|Указывает, какие системные функции поддерживаются драйвером ODBC. Для получения списка имен функций и связанные значения, используемые в этой битовой маске [приложение E: скалярные функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md), в документации ODBC.|
|Функции даты и времени, (KAGPROP_TIMEDATEFUNCTIONS)|Указывает, какие функции даты и времени поддерживаются драйвером ODBC. Для получения списка имен функций и связанные значения, используемые в этой битовой маске [приложение E: скалярные функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md), в документации ODBC.|
|Поддержка грамматики SQL (KAGPROP_ODBCSQLCONFORMANCE)|Указывает грамматику SQL, который поддерживает драйвер ODBC.|

## <a name="provider-specific-recordset-and-command-properties"></a>Набор записей поставщика и свойства команд
 Поставщик OLE DB для ODBC добавляет несколько параметров для **свойства** коллекцию **записей** и **команда** объектов. Ниже перечислены эти свойства с именем соответствующего свойства OLE DB в круглые скобки.

|Имя свойства|Description|
|-------------------|-----------------|
|Запрос на основе обновлений и удалений и вставок (KAGPROP_QUERYBASEDUPDATES)|Указывает, можно ли выполнить обновления, удаления и вставки с помощью SQL-запросов.|
|Тип параллелизма ODBC (KAGPROP_CONCURRENCY)|Указывает метод, используемый для уменьшения потенциальных проблем, вызванных двух пользователей получить доступ к данным из источника данных одновременно.|
|Большой двоичный объект специальных возможностей для курсора последовательного доступа (KAGPROP_BLOBSONFOCURSOR)|Указывает ли BLOB-ОБЪЕКТОВ **поля** возможен при использовании однонаправленный курсор.|
|Включить SQL_FLOAT SQL_DOUBLE и SQL_REAL в предложений QBU WHERE (KAGPROP_INCLUDENONEXACT)|Указывает, можно ли включать в предложение QBU WHERE SQL_FLOAT SQL_DOUBLE и SQL_REAL значения.|
|Позиция в последней строке после вставки (KAGPROP_POSITIONONNEWROW)|Показывает, что после вставки новой записи в таблице последней строки в таблице входящие в текущей строке.|
|IRowsetChangeExtInfo (KAGPROP_IROWSETCHANGEEXTINFO)|Указывает, является ли **IRowsetChange** интерфейс обеспечивает поддержку расширенных сведений.|
|Тип курсора ODBC (KAGPROP_CURSOR)|Указывает тип курсора, используемые **записей**.|
|Создать набор строк, который может быть маршалирован (KAGPROP_MARSHALLABLE)|Указывает, что драйвер ODBC создает набор записей, который может быть маршалирован|

## <a name="command-text"></a>Текст команды
 Как использовать [команда](../../../ado/reference/ado-api/command-object-ado.md) объект во многом зависит от источника данных и тип оператора запроса или команды будет принимать.

 ODBC предоставляет особый синтаксис для вызова хранимых процедур. Для [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) свойство **команда** объекта, *CommandText* аргумент **Execute** метод [ Подключение](../../../ado/reference/ado-api/connection-object-ado.md) объекта, или *источника* аргумент **откройте** метод [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) объект передает строки со следующим синтаксисом:

```
"{ [ ? = ] call procedure [ ( ? [, ? [ , … ]] ) ] }"
```

 Каждый **?** ссылается на объект в [параметры](../../../ado/reference/ado-api/parameters-collection-ado.md) коллекции. Первый **?** ссылки на **параметры**(0), Далее **?** ссылки на **параметры**(1), и т. д.

 Ссылки на параметры являются необязательными и зависят от структуры хранимой процедуры. Если необходимо вызвать хранимую процедуру, которая определяет без параметров, строки будет выглядеть следующим образом:

```
"{ call procedure }"
```

 Если у вас есть два параметра запроса, строка будет выглядеть так:

```
"{ call procedure ( ?, ? ) }"
```

 Если хранимая процедура возвращает значение, возвращаемое значение будет считаться другого параметра. Если у вас есть без параметров запроса, но возвращаемое значение, строка будет выглядеть так:

```
"{ ? = call procedure }"
```

 Наконец Если возвращаемое значение и двух параметров запроса, строка будет выглядеть так:

```
"{ ? = call procedure ( ?, ? ) }"
```

## <a name="recordset-behavior"></a>Поведение набора записей
 В следующих таблицах перечислены стандартные методы ADO и свойства, предоставляемые **записей** открыть объект с этим поставщиком.

 Для получения дополнительных сведений о **записей** поведение конфигурации поставщика, запустите [поддерживает](../../../ado/reference/ado-api/supports-method.md) метод и перечисление **свойства** коллекцию **Записей** для определения того, присутствуют ли динамические свойства от поставщика.

 Доступность Стандартная ADO **записей** свойства:

|Свойство|ForwardOnly|Динамический|Keyset|Статические|
|--------------|-----------------|-------------|------------|------------|
|[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|недоступно|недоступно|чтение/запись|чтение/запись|
|[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|недоступно|недоступно|чтение/запись|чтение/запись|
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|только для чтения|только для чтения|только для чтения|только для чтения|
|[Закладка](../../../ado/reference/ado-api/bookmark-property-ado.md)|недоступно|недоступно|чтение/запись|чтение/запись|
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|только для чтения|только для чтения|только для чтения|только для чтения|
|[Filter](../../../ado/reference/ado-api/filter-property.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|чтение/запись|недоступно|только для чтения|только для чтения|
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|чтение/запись|недоступно|только для чтения|только для чтения|
|[Source](../../../ado/reference/ado-api/source-property-ado-recordset.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[Состояние](../../../ado/reference/ado-api/state-property-ado.md)|только для чтения|только для чтения|только для чтения|только для чтения|
|[Состояние](../../../ado/reference/ado-api/status-property-ado-recordset.md)|только для чтения|только для чтения|только для чтения|только для чтения|

 [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) и [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) свойства доступны только для записи, при использовании ADO версии 1.0 поставщик Microsoft OLE DB для ODBC.

 Доступность Стандартная ADO **записей** методов:

|Метод|ForwardOnly|Динамический|Keyset|Статические|
|------------|-----------------|-------------|------------|------------|
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|Да|Да|Да|Да|
|[Отмена](../../../ado/reference/ado-api/cancel-method-ado.md)|Да|Да|Да|Да|
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|Да|Да|Да|Да|
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|Да|Да|Да|Да|
|[Клон](../../../ado/reference/ado-api/clone-method-ado.md)|Нет|Нет|Да|Да|
|[Закрыть](../../../ado/reference/ado-api/close-method-ado.md)|Да|Да|Да|Да|
|[Delete](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|Да|Да|Да|Да|
|[Получение строк](../../../ado/reference/ado-api/getrows-method-ado.md)|Да|Да|Да|Да|
|[Переместить](../../../ado/reference/ado-api/move-method-ado.md)|Да|Да|Да|Да|
|[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|Да|Да|Да|
|[MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Нет|Да|Да|Да|
|[MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|Да|Да|Да|
|[MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Нет|Да|Да|Да|
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)*|Да|Да|Да|Да|
|[Открытие](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Да|Да|Да|Да|
|[Повторный запрос](../../../ado/reference/ado-api/requery-method.md)|Да|Да|Да|Да|
|[Повторная синхронизация](../../../ado/reference/ado-api/resync-method.md)|Нет|Нет|Да|Да|
|[Поддерживает](../../../ado/reference/ado-api/supports-method.md)|Да|Да|Да|Да|
|[Update](../../../ado/reference/ado-api/update-method.md)|Да|Да|Да|Да|
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|Да|Да|Да|Да|

 * Не поддерживается для баз данных Microsoft Access.

## <a name="dynamic-properties"></a>Динамические свойства
 Поставщик Microsoft OLE DB для ODBC вставляет несколько динамических свойств в **свойства** коллекцию Неоткрытое [подключения](../../../ado/reference/ado-api/connection-object-ado.md), [записей](../../../ado/reference/ado-api/recordset-object-ado.md)и [Команда](../../../ado/reference/ado-api/command-object-ado.md) объектов.

 Следующие таблицы являются cross-index имен ADO и OLE DB для каждого динамических свойств. Справочник программиста OLE DB указано имя свойства ADO термин «Описание». Дополнительные сведения об этих свойствах можно найти в справочнике программиста OLE DB. Найдите имя свойства OLE DB в индексе или в разделе [приложение C: OLE DB свойства](http://msdn.microsoft.com/en-us/deded3ff-f508-4e1b-b2b1-fd9afd3bd292).

## <a name="connection-dynamic-properties"></a>Динамические свойства подключения
 Следующие свойства добавляются **подключения** объекта **свойства** коллекции.

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
|Пароль|DBPROP_AUTH_PASSWORD|
|Передача по событиям Ref|DBPROP_BYREFACCESSORS|
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
 Следующие свойства добавляются **записей** объекта **свойства** коллекции.

|Имя свойства ADO|Имя свойства OLE DB|
|-----------------------|--------------------------|
|Порядок доступа|DBPROP_ACCESSORDER|
|Блокировка объектов хранилища|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Тип закладки|DBPROP_BOOKMARKTYPE|
|Bookmarkable|DBPROP_IROWSETLOCATE|
|Изменить вставленных строк|DBPROP_CHANGEINSERTEDROWS|
|Права доступа столбца|DBPROP_COLUMNRESTRICT|
|Столбец набор уведомлений|DBPROP_NOTIFYCOLUMNSET|
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
|IRowsetResynch||
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
|Уникальные строки|DBPROP_UNIQUEROWS|
|Возможность обновления|DBPROP_UPDATABILITY|
|С помощью закладок|DBPROP_BOOKMARKS|

## <a name="command-dynamic-properties"></a>Команда динамические свойства
 Следующие свойства добавляются **команда** объекта **свойства** коллекции.

|Имя свойства ADO|Имя свойства OLE DB|
|-----------------------|--------------------------|
|Порядок доступа|DBPROP_ACCESSORDER|
|Блокировка объектов хранилища|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Тип закладки|DBPROP_BOOKMARKTYPE|
|Bookmarkable|DBPROP_IROWSETLOCATE|
|Изменить вставленных строк|DBPROP_CHANGEINSERTEDROWS|
|Права доступа столбца|DBPROP_COLUMNRESTRICT|
|Столбец набор уведомлений|DBPROP_NOTIFYCOLUMNSET|
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
|IRowsetResynch||
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
|Пропустить удаленные закладки|DBPROP_BOOKMARKSKIP|
|Идентификатор строки строгих|DBPROP_STRONGIDENTITY|
|Возможность обновления|DBPROP_UPDATABILITY|
|С помощью закладок|DBPROP_BOOKMARKS|

 Дополнительные сведения о реализации и функциональной сведения о поставщике Microsoft OLE DB для ODBC см. в разделе [Справочник программиста OLE DB](http://msdn.microsoft.com/en-us/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8) или перейдите на сайт веб-центра разработчиков хранения и доступа к данным в библиотеке MSDN.

## <a name="see-also"></a>См. также:
 [Команды объекта (ADO)](../../../ado/reference/ado-api/command-object-ado.md) [свойства CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md) [объект соединения (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) [свойство ConnectionString (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [выполнение Метод (команда ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md) [Open-метод (набора записей ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md) [коллекцию параметров (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md) [коллекции свойств (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) [Свойство поставщика (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) [объекта набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [поддерживает метод](../../../ado/reference/ado-api/supports-method.md)

