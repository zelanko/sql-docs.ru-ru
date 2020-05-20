---
title: Поставщик OLE DB Майкрософт для ODBC | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB provider for ODBC [ADO]
- providers [ADO], OLE DB provider for ODBC
ms.assetid: 2dc0372d-e74d-4d0f-9c8c-04e5a168c148
author: rothja
ms.author: jroth
ms.openlocfilehash: 2b84ce6679071cc3ea90ce23b4dcd9f8e1894bb2
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761632"
---
# <a name="microsoft-ole-db-provider-for-odbc-overview"></a>Обзор поставщика OLE DB Майкрософт для ODBC
Для программистов ADO или RDS идеальным миром будет один, в котором каждый источник данных предоставляет интерфейс OLE DB, чтобы ADO мог напрямую обращаться к источнику данных. Хотя все больше поставщиков баз данных реализуют OLE DB интерфейсы, некоторые источники данных пока не предоставляются таким образом. Однако большинство систем СУБД, используемых сегодня, доступны через ODBC.

 Драйверы ODBC доступны для всех основных СУБД, используемых сегодня, включая Microsoft SQL Server, Microsoft Access (ядро СУБД Microsoft Jet) и Microsoft FoxPro, помимо таких продуктов баз данных, как Oracle.

 Однако поставщик Microsoft ODBC позволяет ADO подключаться к любому источнику данных ODBC. Поставщик бесплатен и поддерживает Юникод.

 Поставщик поддерживает транзакции, хотя различные ядра СУБД предлагают различные типы поддержки транзакций. Например, Microsoft Access поддерживает вложенные транзакции размером до пяти уровней.

 Это поставщик по умолчанию для ADO, и поддерживаются все зависящие от поставщика свойства и методы ADO.

## <a name="connection-string-parameters"></a>Параметры строки соединения
 Чтобы подключиться к этому поставщику, задайте для аргумента **provider =** свойства [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) значение:

```
MSDASQL
```

 При чтении свойства [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) также будет возвращена эта строка.

## <a name="typical-connection-string"></a>Типичная строка подключения
 Типичная строка подключения для этого поставщика:

```
"Provider=MSDASQL;DSN=dsnName;UID=MyUserID;PWD=MyPassword;"
```

 Строка состоит из следующих ключевых слов:

|Ключевое слово|Описание|
|-------------|-----------------|
|**Поставщик**|Указывает поставщика OLE DB для ODBC.|
|**DSN**|Указывает имя источника данных.|
|**UID**|Указывает имя пользователя.|
|**PWD**|Указывает пароль пользователя.|
|**URL-адрес**|Указывает URL-адрес файла или каталога, опубликованного в веб-папке.|

 Так как это поставщик по умолчанию для ADO, если опустить параметр **provider =** из строки подключения, ADO попытается установить соединение с этим поставщиком.

> [!NOTE]
>  При подключении к поставщику источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = Yes** или **Integrated Security = SSPI** вместо сведений об идентификаторе пользователя и пароле в строке подключения.

 Поставщик не поддерживает некоторые параметры соединения в дополнение к определенным в ADO. Однако поставщик передаст параметры подключения, отличные от ADO, к диспетчеру драйверов ODBC.

 Так как параметр **provider** можно опустить, можно создать строку подключения ADO, идентичную строке подключения ODBC для того же источника данных. Используйте те же имена параметров (**Driver =**, **Database =**, **DSN =** и т. д.), значения и синтаксис, как при создании строки подключения ODBC. Можно подключиться к предопределенному имени источника данных (DSN) или FileDSN без него.

## <a name="syntax-with-a-dsn-or-filedsn"></a>Синтаксис с DSN или FileDSN:

```
"[Provider=MSDASQL;] { DSN=name | FileDSN=filename } ;
[DATABASE=database;] UID=user; PWD=password"
```

## <a name="syntax-without-a-dsn-dsn-less-connection"></a>Синтаксис без имени DSN (подключение, не имеющее имени DSN):

```
"[Provider=MSDASQL;] DRIVER=driver; SERVER=server;
DATABASE=database; UID=MyUserID; PWD=MyPassword"
```

## <a name="remarks"></a>Remarks
 Если используется **имя DSN** или **FileDSN**, оно должно быть определено с помощью администратора источников данных ODBC на панели управления Windows. В Microsoft Windows 2000 администратор ODBC находится в разделе Администрирование. В более ранних версиях Windows значок администратора ODBC называется **32-bit ODBC** или просто **ODBC**.

 Вместо установки **имени DSN**можно указать драйвер ODBC (**Driver =**), например "SQL Server;" имя сервера (**Server =**); и имя базы данных (**база данных =**).

 Можно также указать имя учетной записи пользователя (**UID =**) и пароль для учетной записи пользователя (**PWD =**) в параметрах, ОТносящихся к ODBC, или в стандартных параметрах *пользователя* и *пароля* , определяемых ADO.

 Хотя определение **DSN** уже указывает *базу данных, можно указать параметр* *базы данных* в дополнение к **имени DSN** для подключения к другой базе данных. Рекомендуется *всегда включать параметр* *базы данных* при использовании **имени DSN**. Это обеспечит подключение к правильной базе данных, если другой пользователь изменил параметр базы данных по умолчанию, так как вы последним проверили определение **DSN** .

## <a name="provider-specific-connection-properties"></a>Свойства соединения, зависящие от поставщика
 Поставщик OLE DB для ODBC добавляет несколько свойств в коллекцию [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) объекта **Connection** . В следующей таблице перечислены эти свойства с соответствующим OLE DB именем свойства в круглых скобках.

|Имя свойства|Описание|
|-------------------|-----------------|
|Доступные процедуры (KAGPROP_ACCESSIBLEPROCEDURES)|Указывает, имеет ли пользователь доступ к хранимым процедурам.|
|Доступные таблицы (KAGPROP_ACCESSIBLETABLES)|Указывает, имеет ли пользователь разрешение на выполнение инструкций SELECT в таблицах базы данных.|
|Активные инструкции (KAGPROP_ACTIVESTATEMENTS)|Указывает число дескрипторов, которые драйвер ODBC может поддерживать для соединения.|
|Имя драйвера (KAGPROP_DRIVERNAME)|Указывает имя файла драйвера ODBC.|
|Версия ODBC драйвера (KAGPROP_DRIVERODBCVER)|Указывает версию ODBC, поддерживаемую этим драйвером.|
|Использование файлов (KAGPROP_FILEUSAGE)|Указывает, как драйвер обрабатывает файл в источнике данных; в виде таблицы или каталога.|
|Предложение escape-выражения LIKE (KAGPROP_LIKEESCAPECLAUSE)|Указывает, поддерживает ли драйвер определение и использование escape-символа в качестве символа процента (%) и подчеркивание символа (_) в предикате LIKE предложения WHERE.|
|Максимальное число столбцов в Group By (KAGPROP_MAXCOLUMNSINGROUPBY)|Указывает максимальное количество столбцов, которые могут быть перечислены в предложении GROUP BY инструкции SELECT.|
|Максимальное число столбцов в индексе (KAGPROP_MAXCOLUMNSININDEX)|Указывает максимальное число столбцов, которые могут быть добавлены в индекс.|
|Максимальное число столбцов в заданном порядке (KAGPROP_MAXCOLUMNSINORDERBY)|Указывает максимальное количество столбцов, которые могут быть перечислены в предложении ORDER BY инструкции SELECT.|
|Максимальное число столбцов в SELECT (KAGPROP_MAXCOLUMNSINSELECT)|Указывает максимальное количество столбцов, которые могут быть перечислены в части SELECT инструкции SELECT.|
|Максимальное число столбцов в таблице (KAGPROP_MAXCOLUMNSINTABLE)|Указывает максимальное число столбцов, допустимое в таблице.|
|Числовые функции (KAGPROP_NUMERICFUNCTIONS)|Указывает, какие числовые функции поддерживаются драйвером ODBC. Список имен функций и связанных значений, используемых в этой битовой маске, см. в [приложении E: скалярные функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)в документации по ODBC.|
|Возможности внешнего объединения (KAGPROP_OJCAPABILITY)|Указывает типы внешних соединений, поддерживаемые поставщиком.|
|Внешние объединения (KAGPROP_OUTERJOINS)|Указывает, поддерживает ли поставщик внешние объединения.|
|Специальные символы (KAGPROP_SPECIALCHARACTERS)|Указывает, какие символы имеют специальное значение для драйвера ODBC.|
|Хранимые процедуры (KAGPROP_PROCEDURES)|Указывает, доступны ли хранимые процедуры для использования с этим драйвером ODBC.|
|Строковые функции (KAGPROP_STRINGFUNCTIONS)|Указывает, какие строковые функции поддерживаются драйвером ODBC. Список имен функций и связанных значений, используемых в этой битовой маске, см. в [приложении E: скалярные функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)в документации по ODBC.|
|Системные функции (KAGPROP_SYSTEMFUNCTIONS)|Указывает, какие системные функции поддерживаются драйвером ODBC. Список имен функций и связанных значений, используемых в этой битовой маске, см. в [приложении E: скалярные функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)в документации по ODBC.|
|Функции времени и даты (KAGPROP_TIMEDATEFUNCTIONS)|Указывает, какие функции времени и даты поддерживаются драйвером ODBC. Список имен функций и связанных значений, используемых в этой битовой маске, см. в [приложении E: скалярные функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)в документации по ODBC.|
|Поддержка грамматики SQL (KAGPROP_ODBCSQLCONFORMANCE)|Указывает грамматику SQL, поддерживаемую драйвером ODBC.|

## <a name="provider-specific-recordset-and-command-properties"></a>Специфические для поставщика набор записей и свойства команды
 Поставщик OLE DB для ODBC добавляет несколько свойств в коллекцию **свойств** **набора записей** и объектов **команд** . В следующей таблице перечислены эти свойства с соответствующим OLE DB именем свойства в круглых скобках.

|Имя свойства|Описание|
|-------------------|-----------------|
|Обновления, операции удаления и вставки на основе запросов (KAGPROP_QUERYBASEDUPDATES)|Указывает, можно ли выполнять операции обновления, удаления и вставки с помощью запросов SQL.|
|Тип параллелизма ODBC (KAGPROP_CONCURRENCY)|Указывает метод, используемый для уменьшения потенциальных проблем, вызванных двумя пользователями, пытающимися получить доступ к одним и тем же данным из источника данных одновременно.|
|Доступность больших двоичных объектов в однонаправленном курсоре (KAGPROP_BLOBSONFOCURSOR)|Указывает, можно ли получить доступ к **полям** BLOB-объектов при использовании однопроходного курсора.|
|Включить SQL_FLOAT, SQL_DOUBLE и SQL_REAL в предложения WHERE КБУ (KAGPROP_INCLUDENONEXACT)|Указывает, можно ли включать значения SQL_FLOAT, SQL_DOUBLE и SQL_REAL в предложение WHERE КБУ.|
|Расположение в последней строке после вставки (KAGPROP_POSITIONONNEWROW)|Указывает, что после вставки новой записи в таблицу последняя строка в таблице станет текущей.|
|Ировсетчанжеекстинфо (KAGPROP_IROWSETCHANGEEXTINFO)|Указывает, предоставляет ли интерфейс **IRowsetChange** расширенную информацию.|
|Тип курсора ODBC (KAGPROP_CURSOR)|Указывает тип курсора, используемого **набором записей**.|
|Создание набора строк, который можно маршалировать (KAGPROP_MARSHALLABLE)|Указывает, что драйвер ODBC создает набор записей, который можно маршалировать|

## <a name="command-text"></a>Текст команды
 Использование объекта [команды](../../../ado/reference/ado-api/command-object-ado.md) во многом зависит от источника данных и типа запроса или оператора команды, который он будет принимать.

 ODBC предоставляет специальный синтаксис для вызова хранимых процедур. Для свойства [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) объекта **Command** аргумент *CommandText* для метода **EXECUTE** объекта [Connection](../../../ado/reference/ado-api/connection-object-ado.md) или *Исходный* аргумент для метода **Open** объекта [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) передается в виде строки с этим синтаксисом:

```
"{ [ ? = ] call procedure [ ( ? [, ? [ , ... ]] ) ] }"
```

 Каждый **?** ссылается на объект в коллекции [Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md) . Первый **?** ссылается на **Параметры**(0), далее **?** ссылается на **Параметры**(1) и т. д.

 Ссылки на параметры являются необязательными и зависят от структуры хранимой процедуры. Если вы хотите вызвать хранимую процедуру, которая не определяет параметры, строка будет выглядеть следующим образом:

```
"{ call procedure }"
```

 Если у вас есть два параметра запроса, строка будет выглядеть следующим образом:

```
"{ call procedure ( ?, ? ) }"
```

 Если хранимая процедура вернет значение, возвращаемое значение рассматривается как другой параметр. Если у вас нет параметров запроса, но у вас есть возвращаемое значение, ваша строка будет выглядеть следующим образом:

```
"{ ? = call procedure }"
```

 Наконец, если у вас есть возвращаемое значение и два параметра запроса, ваша строка будет выглядеть следующим образом:

```
"{ ? = call procedure ( ?, ? ) }"
```

## <a name="recordset-behavior"></a>Поведение набора записей
 В следующих таблицах перечислены стандартные методы и свойства ADO, доступные в объекте **набора записей** , открытом с помощью этого поставщика.

 Чтобы получить более подробные сведения о поведении **набора записей** для конфигурации поставщика, выполните метод [поддерживает](../../../ado/reference/ado-api/supports-method.md) и перечислите коллекцию **свойств** **набора записей** , чтобы определить, имеются ли связанные с поставщиком динамические свойства.

 Доступность стандартных свойств **набора записей** ADO:

|Свойство|форвардонли|Динамический|Keyset|Статические|
|--------------|-----------------|-------------|------------|------------|
|[Примеры absolutepage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|недоступно|недоступно|чтение/запись|чтение/запись|
|[Примеры AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|недоступно|недоступно|чтение/запись|чтение/запись|
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|Только для чтения|Только для чтения|Только для чтения|Только для чтения|
|[Закладка](../../../ado/reference/ado-api/bookmark-property-ado.md)|недоступно|недоступно|чтение/запись|чтение/запись|
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[Примеры CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|Только для чтения|Только для чтения|Только для чтения|Только для чтения|
|[Filter](../../../ado/reference/ado-api/filter-property.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|чтение/запись|недоступно|Только для чтения|Только для чтения|
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|чтение/запись|недоступно|Только для чтения|Только для чтения|
|[Источник](../../../ado/reference/ado-api/source-property-ado-recordset.md)|чтение/запись|чтение/запись|чтение/запись|чтение/запись|
|[Состояние](../../../ado/reference/ado-api/state-property-ado.md)|Только для чтения|Только для чтения|Только для чтения|Только для чтения|
|[Состояние](../../../ado/reference/ado-api/status-property-ado-recordset.md)|Только для чтения|Только для чтения|Только для чтения|Только для чтения|

 Свойства [примеры AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) и [примеры absolutepage](../../../ado/reference/ado-api/absolutepage-property-ado.md) доступны только для записи при использовании ADO с версией 1,0 поставщика Microsoft OLE DB для ODBC.

 Доступность стандартных методов **набора записей** ADO:

|Метод|форвардонли|Динамический|Keyset|Статические|
|------------|-----------------|-------------|------------|------------|
|[Вызов](../../../ado/reference/ado-api/addnew-method-ado.md)|Да|Да|Да|Да|
|[Отмена](../../../ado/reference/ado-api/cancel-method-ado.md)|Да|Да|Да|Да|
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|Да|Да|Да|Да|
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|Да|Да|Да|Да|
|[Clone](../../../ado/reference/ado-api/clone-method-ado.md) (Клонировать)|Нет|Нет|Да|Да|
|[Закрыть](../../../ado/reference/ado-api/close-method-ado.md)|Да|Да|Да|Да|
|[Удалить](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|Да|Да|Да|Да|
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|Да|Да|Да|Да|
|[Перемещение](../../../ado/reference/ado-api/move-method-ado.md)|Да|Да|Да|Да|
|[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|Да|Да|Да|
|[MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Нет|Да|Да|Да|
|[MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|Да|Да|Да|
|[MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Нет|Да|Да|Да|
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)*|Да|Да|Да|Да|
|[Открыть](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Да|Да|Да|Да|
|[Повтор](../../../ado/reference/ado-api/requery-method.md)|Да|Да|Да|Да|
|[Повторная синхронизация](../../../ado/reference/ado-api/resync-method.md)|Нет|Нет|Да|Да|
|[Поддерживает](../../../ado/reference/ado-api/supports-method.md)|Да|Да|Да|Да|
|[Обновление](../../../ado/reference/ado-api/update-method.md)|Да|Да|Да|Да|
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|Да|Да|Да|Да|

 * Не поддерживается для баз данных Microsoft Access.

## <a name="dynamic-properties"></a>Динамические свойства
 Поставщик OLE DB Майкрософт для ODBC вставляет несколько динамических свойств в коллекцию **свойств** неоткрытыго [соединения](../../../ado/reference/ado-api/connection-object-ado.md), [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md)и [командных](../../../ado/reference/ado-api/command-object-ado.md) объектов.

 В следующих таблицах приведены перекрестные индексы имен ADO и OLE DB для каждого динамического свойства. Ссылка на OLE DB программиста ссылается на имя свойства ADO по термину «Description». Дополнительные сведения об этих свойствах можно найти в справочнике по программисту OLE DB. Найдите имя свойства OLE DB в индексе или см. [приложение в: OLE DB свойства](https://msdn.microsoft.com/deded3ff-f508-4e1b-b2b1-fd9afd3bd292).

## <a name="connection-dynamic-properties"></a>Динамические свойства подключения
 В коллекцию **свойств** объекта **Connection** добавляются следующие свойства.

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
|источника данных|DBPROP_INIT_DATASOURCE|
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
|Пароль|DBPROP_AUTH_PASSWORD|
|Методы доступа для передачи по ссылке|DBPROP_BYREFACCESSORS|
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
 В коллекцию **свойств** объекта **набора записей** добавляются следующие свойства.

|Имя свойства ADO|Имя свойства OLE DB|
|-----------------------|--------------------------|
|Порядок доступа|DBPROP_ACCESSORDER|
|Блокировка объектов хранилища|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Тип закладки|DBPROP_BOOKMARKTYPE|
|С закладками|DBPROP_IROWSETLOCATE|
|Изменить вставленные строки|DBPROP_CHANGEINSERTEDROWS|
|Права доступа к столбцу|DBPROP_COLUMNRESTRICT|
|Уведомление о наборе столбцов|DBPROP_NOTIFYCOLUMNSET|
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
|Интерфейс irowsetresynch||
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
|Уникальные строки|DBPROP_UNIQUEROWS|
|Updatability|DBPROP_UPDATABILITY|
|Использование закладок|DBPROP_BOOKMARKS|

## <a name="command-dynamic-properties"></a>Динамические свойства команды
 Следующие свойства добавляются в коллекцию **Properties** объекта **Command** .

|Имя свойства ADO|Имя свойства OLE DB|
|-----------------------|--------------------------|
|Порядок доступа|DBPROP_ACCESSORDER|
|Блокировка объектов хранилища|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Тип закладки|DBPROP_BOOKMARKTYPE|
|С закладками|DBPROP_IROWSETLOCATE|
|Изменить вставленные строки|DBPROP_CHANGEINSERTEDROWS|
|Права доступа к столбцу|DBPROP_COLUMNRESTRICT|
|Уведомление о наборе столбцов|DBPROP_NOTIFYCOLUMNSET|
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
|Интерфейс irowsetresynch||
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
|Пропустить удаленные закладки|DBPROP_BOOKMARKSKIP|
|Строгая идентификация строк|DBPROP_STRONGIDENTITY|
|Updatability|DBPROP_UPDATABILITY|
|Использование закладок|DBPROP_BOOKMARKS|

 Дополнительные сведения о конкретной реализации и функциональных возможностях о поставщике OLE DB Майкрософт для ODBC см. в [справочнике по программированию OLE DB](https://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8) или на веб-сайте центра разработчиков для доступа к данным и хранилища на сайте MSDN.

## <a name="see-also"></a>См. также
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md) [свойство CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) (ADO) свойство [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) (ADO) метод Execute (ADO) [(объект,](../../../ado/reference/ado-api/connection-object-ado.md) [команда ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md) [Open Method (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md) [Коллекция параметров](../../../ado/reference/ado-api/parameters-collection-ado.md) (ADO [)](../../../ado/reference/ado-api/properties-collection-ado.md) [свойство поставщика](../../../ado/reference/ado-api/provider-property-ado.md) (ADO) [объект Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) (ADO) [поддерживает метод](../../../ado/reference/ado-api/supports-method.md)
