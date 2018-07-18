---
title: Поставщик Microsoft OLE DB для ODBC | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB provider for ODBC [ADO]
- providers [ADO], OLE DB provider for ODBC
ms.assetid: 2dc0372d-e74d-4d0f-9c8c-04e5a168c148
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 16a13b9051bafa40ed61d1aecce6f5b47cf4a8f3
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2018
ms.locfileid: "38982166"
---
# <a name="microsoft-ole-db-provider-for-odbc-overview"></a>Поставщик Microsoft OLE DB для ODBC-Обзор
Для использования программистами ADO или служб удаленных рабочих СТОЛОВ идеальном мире бы один, в котором каждый источник предоставляет интерфейс OLE DB таким образом, ADO может вызывать непосредственно в источнике данных. Несмотря на то, что все чаще других поставщиков базы данных при реализации интерфейсов OLE DB, некоторые источники данных не еще доступны таким образом. Однако большинство систем СУБД, в настоящее время может осуществляться через ODBC.

 Драйверы ODBC доступны для каждой основной СУБД, в настоящее время, включая Microsoft SQL Server, Microsoft Access (ядро СУБД Microsoft Jet) и Microsoft FoxPro, помимо продукты сторонних разработчиков базы данных, например Oracle.

 Поставщик ODBC Microsoft, однако позволяет ADO для подключения к любому источнику данных ODBC. Поставщик является свободнопотоковым и Юникод.

 Поставщик поддерживает транзакции, несмотря на то, что разные ядра СУБД предлагают различные виды поддержки транзакций. Например Microsoft Access поддерживает вложенные транзакции до пяти уровней вложенности.

 Это поставщик по умолчанию для ADO и поддерживаются все зависящие от поставщика ADO свойства и методы.

## <a name="connection-string-parameters"></a>Параметры строки соединения
 Чтобы подключиться к этим поставщиком, задайте **поставщика =** аргумент [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойства:

```
MSDASQL
```

 Чтение [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойство возвратит также эту строку.

## <a name="typical-connection-string"></a>Типичная строка подключения
 — Строка соединения для данного поставщика:

```
"Provider=MSDASQL;DSN=dsnName;UID=MyUserID;PWD=MyPassword;"
```

 Строка состоит из следующих ключевых слов:

|Ключевое слово|Описание|
|-------------|-----------------|
|**Поставщик**|Определяет поставщика OLE DB для ODBC.|
|**DSN**|Указывает имя источника данных.|
|**UID**|Указывает имя пользователя.|
|**PWD**|Указывает пароль пользователя.|
|**URL-адрес**|Указывает URL-адрес файла или каталога, опубликованной в веб-папки.|

 Так как это поставщика по умолчанию для ADO, если опустить **поставщика =** параметр из строки подключения ADO будет пытаться установить подключение к этим поставщиком.

> [!NOTE]
>  Если вы подключаетесь к поставщик источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = yes** или **Integrated Security = SSPI** вместо идентификатора пользователя и пароля сведения в строке подключения.

 Поставщик не поддерживает все параметры подключения, помимо определенные ADO. Тем не менее Поставщик передает параметры соединения не ADO диспетчер драйверов ODBC.

 Поскольку можно опустить **поставщика** параметр, можно таким образом создавать строки соединения ADO, идентичный строки подключения ODBC для одного источника данных. Использовать одинаковые имена параметров (**ДРАЙВЕР =**, **базы данных =**, **DSN =**, и так далее), значения и синтаксис, что вы бы при создании строки подключения ODBC. Вы можете подключиться с или без имени источника данных (DSN) или FileDSN.

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

## <a name="remarks"></a>Примечания
 Если вы используете **DSN** или **FileDSN**, он должен быть определен через администратор источников данных ODBC на панели управления Windows. В Microsoft Windows 2000 администратор ODBC находится в разделе Администрирование. В более ранних версиях Windows, называется значок администратор ODBC **32-разрядная версия ODBC** или просто **ODBC**.

 Как альтернативу параметр **DSN**, можно указать драйвер ODBC (**ДРАЙВЕР =**), такие как «SQL Server»; имя сервера (**SERVER =**); и имя базы данных (**Базы данных =**).

 Можно также указать имя учетной записи пользователя (**UID =**) и пароль для учетной записи пользователя (**PWD =**) в параметры, относящиеся к ODBC или в стандарте определяемые ADO *пользователя* и *пароль* параметров.

 Несмотря на то что **DSN** определение уже содержит имя базы данных, можно указать *a* *базы данных* параметр в дополнение к **DSN** для подключения с другой базой данных. Рекомендуется всегда включать *базы* *данных* параметр при использовании **DSN**. Это обеспечит подключения к нужной базе данных, если другой пользователь изменил параметр базы данных по умолчанию, так как Последняя проверка **DSN** определения.

## <a name="provider-specific-connection-properties"></a>Свойства подключения для поставщика
 Поставщик OLE DB для ODBC добавляет несколько свойств, чтобы [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекцию **подключения** объекта. Ниже перечислены эти свойства с именем соответствующего свойства OLE DB в круглые скобки.

|Имя свойства|Описание|
|-------------------|-----------------|
|Доступны процедуры (KAGPROP_ACCESSIBLEPROCEDURES)|Указывает, имеет ли пользователь доступ к хранимой процедуры.|
|Доступной таблицы (KAGPROP_ACCESSIBLETABLES)|Указывает, имеет ли пользователь разрешение на выполнение инструкций SELECT к таблицам базы данных.|
|Активных инструкций (KAGPROP_ACTIVESTATEMENTS)|Указывает число дескрипторов, которые поддерживает драйвер ODBC для подключения.|
|Имя драйвера (KAGPROP_DRIVERNAME)|Указывает имя файла драйвера ODBC.|
|Версия драйвера ODBC (KAGPROP_DRIVERODBCVER)|Указывает версию ODBC, который поддерживает этот драйвер.|
|Использование файла (KAGPROP_FILEUSAGE)|Указывает, как драйвер обрабатывает файл в источнике данных; как таблицу или каталогом.|
|Как и предложение Escape (KAGPROP_LIKEESCAPECLAUSE)|Указывает ли драйвер поддерживает определение и использование escape-символа для символ процента (%) и символом подчеркивания (_) в предикате LIKE предложения WHERE.|
|Максимальное количество столбцов в Group By (KAGPROP_MAXCOLUMNSINGROUPBY)|Указывает максимальное число столбцов, которые могут быть перечислены в предложении GROUP BY инструкции SELECT.|
|Максимальное количество столбцов в индексе (KAGPROP_MAXCOLUMNSININDEX)|Указывает максимальное число столбцов, которые могут быть включены в индекс.|
|Максимальное количество столбцов в Order By (KAGPROP_MAXCOLUMNSINORDERBY)|Указывает максимальное число столбцов, которые могут быть перечислены в предложении ORDER BY инструкции SELECT.|
|Максимальное количество столбцов в Select (KAGPROP_MAXCOLUMNSINSELECT)|Указывает максимальное число столбцов, которые могут быть перечислены в части SELECT инструкции SELECT.|
|Максимальное количество столбцов в таблице (KAGPROP_MAXCOLUMNSINTABLE)|Указывает максимальное число столбцов, допустимое в таблице.|
|Числовые функции (KAGPROP_NUMERICFUNCTIONS)|Указывает числовые функции, которые поддерживаются драйвером ODBC. Список имен функций и связанных значений, используемых в этой битовой маске, см. в разделе [приложении E: скалярные функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md), в документации ODBC.|
|Возможности внешнего соединения (KAGPROP_OJCAPABILITY)|Указывает типы ВНЕШНИХ соединений, поддерживаемых поставщиком.|
|Внешние соединения (KAGPROP_OUTERJOINS)|Указывает, поддерживает ли поставщик ВНЕШНИЕ соединения.|
|Специальные символы (KAGPROP_SPECIALCHARACTERS)|Указывает, какие символы имеют особое значение для драйвера ODBC.|
|Хранимые процедуры (KAGPROP_PROCEDURES)|Указывает, доступны ли хранимые процедуры для использования с помощью этого драйвера ODBC.|
|Строковые функции (KAGPROP_STRINGFUNCTIONS)|Указывает, какие строки функции поддерживаются драйвером ODBC. Список имен функций и связанных значений, используемых в этой битовой маске, см. в разделе [приложении E: скалярные функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md), в документации ODBC.|
|Системные функции (KAGPROP_SYSTEMFUNCTIONS)|Указывает, какие системные функции поддерживаются драйвером ODBC. Список имен функций и связанных значений, используемых в этой битовой маске, см. в разделе [приложении E: скалярные функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md), в документации ODBC.|
|Функции даты и времени, (KAGPROP_TIMEDATEFUNCTIONS)|Указывает, какие функции даты и времени поддерживаются драйвером ODBC. Список имен функций и связанных значений, используемых в этой битовой маске, см. в разделе [приложении E: скалярные функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md), в документации ODBC.|
|Поддержка Грамматика SQL (KAGPROP_ODBCSQLCONFORMANCE)|Указывает, драйвер ODBC поддерживает грамматику SQL.|

## <a name="provider-specific-recordset-and-command-properties"></a>Набор записей поставщика и свойства команды
 Поставщик OLE DB для ODBC добавляет несколько свойств, чтобы **свойства** коллекцию **записей** и **команда** объектов. Ниже перечислены эти свойства с именем соответствующего свойства OLE DB в круглые скобки.

|Имя свойства|Описание|
|-------------------|-----------------|
|Запрос на основе обновлений/удалений и вставок (KAGPROP_QUERYBASEDUPDATES)|Указывает, могут быть выполнены обновления, удаления и вставки с помощью SQL-запросов.|
|Тип параллелизма ODBC (KAGPROP_CONCURRENCY)|Указывает метод, используемый для уменьшения потенциальных проблем, из-за двух пользователей, пытается получить доступ к тем же данным из источника данных одновременно.|
|Специальные возможности BLOB-ОБЪЕКТОВ на однопроходный курсор (KAGPROP_BLOBSONFOCURSOR)|Указывает, является ли BLOB-ОБЪЕКТОВ **поля** возможен при использовании однопроходный курсор.|
|Включить SQL_FLOAT SQL_DOUBLE и SQL_REAL в предложений QBU WHERE (KAGPROP_INCLUDENONEXACT)|Указывает, можно ли включать в предложение QBU WHERE SQL_FLOAT SQL_DOUBLE и SQL_REAL значения.|
|Позиция в последней строке после вставки (KAGPROP_POSITIONONNEWROW)|Указывает, что после вставки новой записи в таблице, последней строки в таблице будут поступать текущей строки.|
|IRowsetChangeExtInfo (KAGPROP_IROWSETCHANGEEXTINFO)|Указывает, является ли **IRowsetChange** интерфейс обеспечивает поддержку расширенных сведений.|
|Тип курсора ODBC (KAGPROP_CURSOR)|Указывает тип курсора, используемые **записей**.|
|Создать набор строк, который может маршалироваться (KAGPROP_MARSHALLABLE)|Указывает, что драйвер ODBC создает набор записей, который может маршалироваться|

## <a name="command-text"></a>Текст команды
 Как использовать [команда](../../../ado/reference/ado-api/command-object-ado.md) объект во многом зависит от источника данных, и какой тип оператора запроса или команды, которые он будет принимать.

 ODBC предоставляет особый синтаксис для вызова хранимых процедур. Для [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) свойство **команда** объекта, *CommandText* аргумент **Execute** метод [ Подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта, или *источника* аргумент **откройте** метод [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объект передает в строке со следующим синтаксисом:

```
"{ [ ? = ] call procedure [ ( ? [, ? [ , … ]] ) ] }"
```

 Каждый **?** ссылается на объект в [параметры](../../../ado/reference/ado-api/parameters-collection-ado.md) коллекции. Первый **?** ссылки на **параметры**(0), Далее **?** ссылки на **параметры**(1), и т. д.

 Ссылки на параметры являются необязательными и зависят от структуры хранимой процедуры. Если вы хотите вызвать хранимую процедуру, которая не определяет параметры, строки будет выглядеть следующим образом:

```
"{ call procedure }"
```

 Если у вас есть два параметра запроса, строка будет выглядеть так:

```
"{ call procedure ( ?, ? ) }"
```

 Если хранимая процедура возвращает значение, возвращаемое значение будет считаться еще один параметр. Если у вас есть параметры запроса, но у вас есть возвращаемое значение, строка будет выглядеть следующим образом:

```
"{ ? = call procedure }"
```

 Наконец Если у вас есть возвращаемое значение и параметры два запроса, строка будет выглядеть так:

```
"{ ? = call procedure ( ?, ? ) }"
```

## <a name="recordset-behavior"></a>Поведение набора записей
 В следующих таблицах перечислены стандартные методы ADO и свойства, доступные на **записей** открыть объект с этим поставщиком.

 Более подробные сведения о **записей** поведение поставщика конфигурации, запустите [поддерживает](../../../ado/reference/ado-api/supports-method.md) метод и перечисление **свойства** коллекцию **Записей** чтобы определить, присутствует ли динамические свойства от поставщика.

 Доступность стандартных ADO **записей** свойства:

|Свойство|ForwardOnly|Динамический|Keyset|Статические|
|--------------|-----------------|-------------|------------|------------|
|[Примеры AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|недоступно|недоступно|чтение/запись|чтение/запись|
|[Примеры AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|недоступно|недоступно|чтение/запись|чтение/запись|
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|только для чтения|только для чтения|только для чтения|только для чтения|
|[Закладка](../../../ado/reference/ado-api/bookmark-property-ado.md)|недоступно|недоступно|чтение/запись|чтение/запись|
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[Примеры CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|только для чтения|только для чтения|только для чтения|только для чтения|
|[Фильтр](../../../ado/reference/ado-api/filter-property.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|чтение/запись|недоступно|только для чтения|только для чтения|
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|чтение/запись|недоступно|только для чтения|только для чтения|
|[Source](../../../ado/reference/ado-api/source-property-ado-recordset.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[Состояние](../../../ado/reference/ado-api/state-property-ado.md)|только для чтения|только для чтения|только для чтения|только для чтения|
|[Состояние](../../../ado/reference/ado-api/status-property-ado-recordset.md)|только для чтения|только для чтения|только для чтения|только для чтения|

 [Примеры AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) и [примеры AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) свойства доступны только для записи, при использовании ADO с версии 1.0 поставщика Microsoft OLE DB для ODBC.

 Доступность стандартных ADO **записей** методы:

|Метод|ForwardOnly|Динамический|Keyset|Статические|
|------------|-----------------|-------------|------------|------------|
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|Да|Да|Да|Да|
|[Отмена](../../../ado/reference/ado-api/cancel-method-ado.md)|Да|Да|Да|Да|
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|Да|Да|Да|Да|
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|Да|Да|Да|Да|
|[Клон](../../../ado/reference/ado-api/clone-method-ado.md)|Нет|Нет|Да|Да|
|[Закрыть](../../../ado/reference/ado-api/close-method-ado.md)|Да|Да|Да|Да|
|[Удаление](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|Да|Да|Да|Да|
|[Получение строк](../../../ado/reference/ado-api/getrows-method-ado.md)|Да|Да|Да|Да|
|[Переместить](../../../ado/reference/ado-api/move-method-ado.md)|Да|Да|Да|Да|
|[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|Да|Да|Да|
|[MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Нет|Да|Да|Да|
|[MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|Да|Да|Да|
|[MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Нет|Да|Да|Да|
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)*|Да|Да|Да|Да|
|[Открытие](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Да|Да|Да|Да|
|[Requery](../../../ado/reference/ado-api/requery-method.md)|Да|Да|Да|Да|
|[Повторная синхронизация](../../../ado/reference/ado-api/resync-method.md)|Нет|Нет|Да|Да|
|[Поддерживает](../../../ado/reference/ado-api/supports-method.md)|Да|Да|Да|Да|
|[Update](../../../ado/reference/ado-api/update-method.md)|Да|Да|Да|Да|
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|Да|Да|Да|Да|

 * Не поддерживается для баз данных Microsoft Access.

## <a name="dynamic-properties"></a>Динамические свойства
 Поставщик Microsoft OLE DB для ODBC вставляет несколько динамических свойств в **свойства** коллекцию неоткрытый [подключения](../../../ado/reference/ado-api/connection-object-ado.md), [записей](../../../ado/reference/ado-api/recordset-object-ado.md)и [Команда](../../../ado/reference/ado-api/command-object-ado.md) объектов.

 В следующих таблицах представлены cross-index имен ADO и OLE DB для каждого динамического свойства. Справочник программиста OLE DB по указано имя свойства ADO с термином «Description». Дополнительные сведения об этих свойствах можно найти в справочнике программиста OLE DB. Найдите имя свойства OLE DB в индексе или см. в разделе [приложение C: OLE DB свойства](http://msdn.microsoft.com/deded3ff-f508-4e1b-b2b1-fd9afd3bd292).

## <a name="connection-dynamic-properties"></a>Динамические свойства подключения
 Следующие свойства добавляются к **подключения** объекта **свойства** коллекции.

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
|Службы OLE DB|DBPROP_INIT_OLEDBSERVICES, УСТАНОВИТЬ|
|Версия OLE DB|DBPROP_PROVIDEROLEDBVER|
|Поддержка объектов OLE|DBPROP_OLEOBJECTS|
|Поддержка открытия наборов данных|DBPROP_OPENROWSETSUPPORT|
|Столбцы ORDER BY в списке выбора|DBPROP_ORDERBYCOLUMNSINSELECT|
|Доступность параметра вывода|DBPROP_OUTPUTPARAMETERAVAILABILITY|
|Пароль|DBPROP_AUTH_PASSWORD|
|Передавать по указанные методы|DBPROP_BYREFACCESSORS|
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
 Следующие свойства добавляются к **записей** объекта **свойства** коллекции.

|Имя свойства ADO|Имя свойства OLE DB|
|-----------------------|--------------------------|
|Порядок доступа|DBPROP_ACCESSORDER|
|Блокирование объектов хранилища|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Тип закладки|DBPROP_BOOKMARKTYPE|
|Bookmarkable|DBPROP_IROWSETLOCATE|
|Изменение вставленных строк|DBPROP_CHANGEINSERTEDROWS|
|Права доступа столбца|DBPROP_COLUMNRESTRICT|
|Уведомление о задании столбца|DBPROP_NOTIFYCOLUMNSET|
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
|IRowsetResynch||
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
|Уникальные строки|DBPROP_UNIQUEROWS|
|Возможности обновления|DBPROP_UPDATABILITY|
|Использование закладок|DBPROP_BOOKMARKS|

## <a name="command-dynamic-properties"></a>Динамические свойства команды
 Следующие свойства добавляются к **команда** объекта **свойства** коллекции.

|Имя свойства ADO|Имя свойства OLE DB|
|-----------------------|--------------------------|
|Порядок доступа|DBPROP_ACCESSORDER|
|Блокирование объектов хранилища|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Тип закладки|DBPROP_BOOKMARKTYPE|
|Bookmarkable|DBPROP_IROWSETLOCATE|
|Изменение вставленных строк|DBPROP_CHANGEINSERTEDROWS|
|Права доступа столбца|DBPROP_COLUMNRESTRICT|
|Уведомление о задании столбца|DBPROP_NOTIFYCOLUMNSET|
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
|IRowsetResynch||
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
|Пропуск удаленных закладок|DBPROP_BOOKMARKSKIP|
|Строгая Идентификация строки|DBPROP_STRONGIDENTITY|
|Возможности обновления|DBPROP_UPDATABILITY|
|Использование закладок|DBPROP_BOOKMARKS|

 Сведения о реализации и функционального сведения о поставщике Microsoft OLE DB для ODBC, см. в разделе [Справочник программиста OLE DB по](http://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8) или посетите узел доступа к данным и веб-хранилища в центре разработчиков на сайте MSDN.

## <a name="see-also"></a>См. также
 [Команда объект (ADO)](../../../ado/reference/ado-api/command-object-ado.md) [свойство CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md) [объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) [свойство ConnectionString (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [выполнения Метод (объект Command ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md) [(объект Recordset ADO) метод Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) [коллекция Parameters (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md) [коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) [Свойство provider (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) [объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [поддерживает метод](../../../ado/reference/ado-api/supports-method.md)
