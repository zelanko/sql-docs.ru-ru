---
title: Обновлено — документы по реляционным базам данных | Документация Майкрософт
description: Отображение фрагментов обновленного содержимого для последних изменений в документации по реляционным базам данных.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: relational-databases
ms.date: 02/03/2018
ms.openlocfilehash: f30e38adef7faedb273dbd1b22c4ac9d3e8223b4
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2018
---
# <a name="new-and-recently-updated-relational-databases-docs"></a>Новые и недавно обновленные статьи — документы по реляционным базам данных



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Диапазон дат обновлений:* &nbsp; **03.12.2017**&nbsp;–&nbsp;**03.02.2018**
- *Предметная область:* &nbsp; **Реляционные базы данных**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


1. [Хранение документов JSON в SQL Server или базе данных SQL](json/store-json-documents-in-sql-tables.md)
2. [Оценка уязвимостей SQL](security/sql-vulnerability-assessment.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [Инициализация файлов базы данных](#TitleNum_1)
2. [База данных tempdb](#TitleNum_2)
3. [Данные JSON в SQL Server](#TitleNum_3)
4. [Занятие 1. Подключение к ядру СУБД](#TitleNum_4)
5. [Управление размером файла журнала транзакций](#TitleNum_5)
6. [bcp_bind](#TitleNum_6)
7. [Руководство по проектированию индексов SQL Server](#TitleNum_7)
8. [sp_execute_external_script (Transact-SQL)](#TitleNum_8)
9. [Создание первичных ключей](#TitleNum_9)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-database-file-initializationdatabasesdatabase-instant-file-initializationmd"></a>1. &nbsp; [Инициализация файлов базы данных](databases/database-instant-file-initialization.md)

*Обновление: 23.01.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Далее](#TitleNum_2))

<!-- Source markdown line 81.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c5f2aa53a8b43d4c43e0602cf945cb7c7028a27d 04c261c6588af1f53cda2fce3e9a86167c50b686  (PR=4702  ,  Filename=database-instant-file-initialization.md  ,  Dirpath=docs\relational-databases\databases\  ,  MergeCommitSha40=3206a31870f8febab7d1718fa59fe0590d4d45db) -->



```
Database Instant File Initialization: disabled. For security and performance considerations see the topic 'Database Instant File Initialization' in SQL Server Books Online. This is an informational message only. No user action is required.
```

**Применимо к:** SQL Server (начиная с SQL Server 2012 с пакетом обновления 4 (SP4), SQL Server 2014 с пакетом обновления 2 (SP2) и с SQL Server 2016 по SQL Server 2017)

**Вопросы безопасности**

При использовании мгновенной инициализации файлов (IFI), так как удаленное содержимое диска перезаписывается только по мере записи в файлы новых данных, пока в помеченную удаленной область файла данных не будут записаны другие данные, неавторизованный субъект может получить доступ к удаленному содержимому. Когда файл базы данных подключен к экземпляру SQL Server, риск раскрытия информации уменьшается благодаря списку управления доступом на уровне пользователей (DACL) в файле. DACL разрешает доступ к файлу только учетной записи службы SQL Server и локальному администратору. Однако при отключении файла доступ к нему может получить пользователь или служба, которым не предоставлено разрешение SE\_MANAGE\_VOLUME_NAME. Аналогичная проблема существует при резервном копировании базы данных. Если файл резервной копии не защищен с помощью соответствующего DACL, удаленное содержимое может стать доступным неавторизованному пользователю или службе.

Следует учитывать и то, что при увеличении файла с помощью IFI администратор SQL Server потенциально может получить доступ к содержимому необработанных страниц и просматривать ранее удаленное содержимое.

Если файлы базы данных размещаются в сети хранения данных, она может всегда представлять новые страницы в виде предварительно инициализированных, что может создавать излишнюю нагрузку, так как операционной системе требуется инициализировать эти страницы повторно.



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-tempdb-databasedatabasestempdb-databasemd"></a>2. &nbsp; [База данных tempdb](databases/tempdb-database.md)

*Обновлено: 17.01.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_1) | [Далее](#TitleNum_3))

<!-- Source markdown line 100.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 337555ea28f4c3fdd6b78f1bfb4d62607a6bf92d 3257c92d6e2a88968fc44e5f6262c02cd0624635  (PR=0  ,  Filename=tempdb-database.md  ,  Dirpath=docs\relational-databases\databases\  ,  MergeCommitSha40=45e6082acc29ba306525e7c08d2c22cc2b86eec3) -->



 Описание этих баз данных см. в статье [Параметры ALTER DATABASE SET (Transact-SQL)](databases/../../t-sql/statements/alter-database-transact-sql-set-options.md).

**База данных tempdb в базе данных SQL**


|SLO|Максимальный размер файла данных Tempdb (МБ)|Число файлов данных tempdb|Максимальный размер данных tempdb (МБ)|
|---|---:|---:|---:|
|Basic|14,225|1|14,225|
|S0|14,225|1|14,225|
|S1|14,225|1|14,225|
|S2|14,225| 1|14,225|
|S3|32,768|1|32,768|
|S4|32,768|2|65 536|
|S6|32,768|3|98,304|
|S7|32,768|6|196,608|
|S9|32,768|12|393,216|
|S12|32,768|12|393,216|
|P1|32,768|12|393,216|
|P2|32,768|12|393,216|
|P4|32,768|12|393,216|
|P6|32,768|12|393,216|
|P11|32,768|12|393,216|
|P15|32,768|12|393,216|
|Эластичные пулы уровня "Премиум" (все конфигурации DTU)|14,225|12|170,700|
|Эластичные пулы уровня "Стандартный" (все конфигурации DTU)|14,225|12|170,700|
|Эластичные пулы уровня "Базовый" (все конфигурации DTU)|14,225|12|170,700|
||||




&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-json-data-in-sql-serverjsonjson-data-sql-servermd"></a>3. &nbsp; [Данные JSON в SQL Server](json/json-data-sql-server.md)

*Обновлено: 01.02.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_2) | [Далее](#TitleNum_4))

<!-- Source markdown line 233.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 62dd9c68d8cb72d6bf51b941a0731224514f0a7f 19e276637a463b412f2c29a84f9fb7d0b0f5fcc5  (PR=4783  ,  Filename=json-data-sql-server.md  ,  Dirpath=docs\relational-databases\json\  ,  MergeCommitSha40=73f18ae24a9a48234bf997ee9a2ef441bc4918b9) -->



-   [Загрузка данных GeoJSON в SQL Server 2016](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/01/05/loading-geojson-data-into-sql-server/)

**Анализ данных JSON с помощью запросов SQL**

Если вам нужно отфильтровать или вычислить данные JSON для целей отчетности, JSON можно преобразовать в реляционный формат с помощью **OPENJSON**. После этого подготовьте отчеты, используя стандартный язык Transact-SQL и встроенные функции.

```
SELECT Tab.Id, SalesOrderJsonData.Customer, SalesOrderJsonData.Date
FROM   SalesOrderRecord AS Tab
          CROSS APPLY
     OPENJSON (Tab.json, N'$.Orders.OrdersArray')
           WITH (
              Number   varchar(200) N'$.Order.Number',
              Date     datetime     N'$.Order.Date',
              Customer varchar(200) N'$.AccountNumber',
              Quantity int          N'$.Item.Quantity'
           )
  AS SalesOrderJsonData
WHERE JSON_VALUE(Tab.json, '$.Status') = N'Closed'
ORDER BY JSON_VALUE(Tab.json, '$.Group'), Tab.DateModified
```



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-lesson-1-connecting-to-the-database-enginelesson-1-connecting-to-the-database-enginemd"></a>4. &nbsp; [Урок 1. Соединение с ядром СУБД](lesson-1-connecting-to-the-database-engine.md)

*Обновлено: 13.12.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_3) | [Далее](#TitleNum_5))

<!-- Source markdown line 79.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 3c070935895450fd2ea054e2be9e1c48f7dc2b6c 0c386e3d47fb7f8f1e63b9301f0cafec2bc88ab0  (PR=4282  ,  Filename=lesson-1-connecting-to-the-database-engine.md  ,  Dirpath=docs\relational-databases\  ,  MergeCommitSha40=6e016a4ffd28b09456008f40ff88aef3d911c7ba) -->



2.  Выберите **Компонент Database Engine**.

    ![object-explorer](../relational-databases/media/object-explorer.png)

3.  В поле **Имя сервера** введите имя экземпляра ядра СУБД. В экземпляре SQL Server по умолчанию имя сервера совпадает с именем компьютера. Для именованного экземпляра SQL Server имя сервера имеет вид *<имя_компьютера>***\\***<имя_экземпляра>*, например **ACCTG_SRVR\SQLEXPRESS**. На снимке экрана ниже показано подключение к экземпляру SQL Server по умолчанию (неименованному) на компьютере с именем PracticeComputer. В Windows вошел пользователь Mary из домена Contoso. При использовании проверки подлинности Windows нельзя изменить имя пользователя.

    ![connect-to-server](../relational-databases/media/connect-to-server.png)

4.  Нажмите кнопку **Соединить**.

> [!NOTE]
> В этом учебнике предполагается, что вы не знакомы с SQL Server и у вас нет проблем с подключением. Этого достаточно в большинстве случаев, и это позволяет упростить учебник. Подробные инструкции по устранению неполадок см. в разделе [Устранение неполадок при соединении с компонентом SQL Server Database Engine](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md).

**<a name="additional"></a>Разрешение дополнительных подключений**

Теперь, после подключения к SQL Server в качестве администратора, одной из первых задач будет обеспечить возможность подключения других пользователей. Это делается посредством создания имени входа и предоставления ему разрешения на доступ к базе данных в качестве пользователя. Имена входа могут быть или именами входа для проверки подлинности Windows, использующей учетные данные Windows, или именами входа для проверки подлинности SQL Server, при которой учетные данные хранятся в SQL Server и не зависят от учетных данных Windows. По возможности используйте проверку подлинности Windows.



&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-manage-the-size-of-the-transaction-log-filelogsmanage-the-size-of-the-transaction-log-filemd"></a>5. &nbsp; [Управление размером файла журнала транзакций](logs/manage-the-size-of-the-transaction-log-file.md)

*Обновлено: 17.01.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_4) | [Далее](#TitleNum_6))

<!-- Source markdown line 105.  ms.author= "jhubbard".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5847b31cf8f6003a380f0c8aaa289efdc55be678 84e45320d81db218cde17fbf8b9668a9ac3805a7  (PR=0  ,  Filename=manage-the-size-of-the-transaction-log-file.md  ,  Dirpath=docs\relational-databases\logs\  ,  MergeCommitSha40=45e6082acc29ba306525e7c08d2c22cc2b86eec3) -->



-   При небольшом шаге приращения может формироваться слишком много [виртуальных файлов журнала](logs/../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) малого размера и снижаться производительность. Чтобы определить оптимальное распределение виртуальных файлов журнала для текущего размера журнала транзакций всех баз данных в определенном экземпляре, а также требуемые приращения для достижения нужного размера, см. следующий [скрипт](http://github.com/Microsoft/tigertoolbox/tree/master/Fixing-VLFs).

-   При большом шаге приращения может формироваться слишком мало крупных [виртуальных файлов журнала](logs/../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch), что также повлияет на производительность. Чтобы определить оптимальное распределение виртуальных файлов журнала для текущего размера журнала транзакций всех баз данных в определенном экземпляре, а также требуемые приращения для достижения нужного размера, см. следующий [скрипт](http://github.com/Microsoft/tigertoolbox/tree/master/Fixing-VLFs).

-   Даже если включено автоматическое увеличение, вы можете получить сообщение, что журнал транзакций заполнен, если его размер не может достаточно быстро увеличиваться под нужды вашего запроса. Дополнительные сведения об изменении шага приращения см. в разделе [Параметры инструкции ALTER DATABASE (Transact-SQL) для файлов и файловых групп](logs/../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md)

-   Наличие множества файлов журнала в базе данных не способствует повышению производительности, так как файлы журнала транзакций не используют [пропорциональное заполнение](logs/../../relational-databases/pages-and-extents-architecture-guide.md#ProportionalFill), как файлы данных в одной файловой группе.

-   Вы можете настроить автоматическое сжатие файлов журналов. Но делать это **не рекомендуется**, и параметру базы данных **auto_shrink** по умолчанию задано значение FALSE. Если параметру **auto_shrink** задано значение TRUE, автоматическое сжатие уменьшает размер файла, только если в нем не использовано более 25 % объема.



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-bcpbindnative-client-odbc-extensions-bulk-copy-functionsbcp-bindmd"></a>6. &nbsp; [bcp_bind](native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)

*Обновлено: 30.01.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_5) | [Далее](#TitleNum_7))

<!-- Source markdown line 127.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 d50791cef948ce8b3066438e317ab4d34d535258 e6f70559e7237cfc86dfc5746d218c08bec52af6  (PR=4762  ,  Filename=bcp-bind.md  ,  Dirpath=docs\relational-databases\native-client-odbc-extensions-bulk-copy-functions\  ,  MergeCommitSha40=60006e90d03fdb75b282bbc0dad3d40571bacacc) -->



 В приведенной ниже таблице перечислены допустимые перечисляемые типы данных и соответствующие типы данных C в ODBC.

|eDataType|Тип C|
|-----------------------|------------|
|SQLTEXT|char *|
|SQLNTEXT|wchar_t *|
|SQLCHARACTER|char *|
|SQLBIGCHAR|char *|
|SQLVARCHAR|char *|
|SQLBIGVARCHAR|char *|
|SQLNCHAR|wchar_t *|
|SQLNVARCHAR|wchar_t *|
|SQLBINARY|unsigned char *|
|SQLBIGBINARY|unsigned char *|
|SQLVARBINARY|unsigned char *|
|SQLBIGVARBINARY|unsigned char *|
|SQLBIT|char;|
|SQLBITN|char;|
|SQLINT1|char;|
|SQLINT2|short int|
|SQLINT4|ssNoversion|
|SQLINT8|_int64|
|SQLINTN|*cbIndicator*<br /> 1: SQLINT1<br /> 2: SQLINT2<br /> 4: SQLINT4<br /> 8: SQLINT8|
|SQLFLT4|FLOAT|
|SQLFLT8|FLOAT|
|SQLFLTN|*cbIndicator*<br /> 4: SQLFLT4<br /> 8: SQLFLT8|
|SQLDECIMALN|SQL_NUMERIC_STRUCT|
|SQLNUMERICN|SQL_NUMERIC_STRUCT|
|SQLMONEY|DBMONEY|
|SQLMONEY4|DBMONEY4|
|SQLMONEYN|*cbIndicator*<br /> 4: SQLMONEY4<br /> 8: SQLMONEY|
|SQLTIMEN|SQL_SS_TIME2_STRUCT|
|SQLDATEN|SQL_DATE_STRUCT|
|SQLDATETIM4|DBDATETIM4|
|SQLDATETIME|DBDATETIME|
|SQLDATETIMN|*cbIndicator*<br /> 4: SQLDATETIM4<br /> 8: SQLDATETIME|
|SQLDATETIME2N|SQL_TIMESTAMP_STRUCT|
|SQLDATETIMEOFFSETN|SQL_SS_TIMESTAMPOFFSET_STRUCT|
|SQLIMAGE|unsigned char *|
|SQLUDT|unsigned char *|
|SQLUNIQUEID|SQLGUID|
|SQLVARIANT|*Любой тип данных, кроме следующих:*<br />— text<br />— ntext<br />— image<br />— varchar(max)<br />— varbinary(max)<br />— nvarchar(max)<br />— xml<br />— timestamp|
|SQLXML|*Поддерживаемые типы данных C:*<br />— char *<br />— wchar_t *<br />— unsigned char *|



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-sql-server-index-design-guidesql-server-index-design-guidemd"></a>7. &nbsp; [Руководство по проектированию индексов SQL Server](sql-server-index-design-guide.md)

*Обновлено: 02.01.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_6) | [Далее](#TitleNum_8))

<!-- Source markdown line 700.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 bd09c9e66cd3cf5f3ebebe7ffa6e937978353169 8e5cbbf0063971676a8bafefba75aa5c7c28be61  (PR=0  ,  Filename=sql-server-index-design-guide.md  ,  Dirpath=docs\relational-databases\  ,  MergeCommitSha40=74daee358fef75a25d75c69d971d08536c5bd2be) -->



Начиная с версии SQL Server 2016 можно создавать обновляемый **некластеризованный индекс columnstore в таблице rowstore**. Индекс columnstore сохраняет копию данных, так что вам обязательно потребуется дополнительное хранилище. Тем не менее данные в индексе columnstore будут сжаты до меньшего размера, чем это требуется для таблицы rowstore.  Таким образом, вы сможете выполнять аналитику на основе индекса columnstore и транзакции на основе индекса rowstore одновременно. Хранилище столбцов обновляется при каждом изменении данных в таблице rowstore, поэтому оба индекса работают с одними и теми же данными.

Начиная с версии SQL Server 2016 **индекс columnstore может включать один или несколько некластеризованных индексов rowstore**. Это обеспечивает эффективность поиска по таблицам на основе базового индекса columnstore. Кроме того, появляется доступ к другим возможностям. Например, можно принудительно задать ограничение PRIMARY KEY, применив к таблице rowstore ограничение UNIQUE. Поскольку неуникальное значение в таблицу rowstore не вставляется, SQL Server не может вставить значение в columnstore.

**Вопросы производительности**


-   Определение некластеризованного индекса columnstore поддерживает использование отфильтрованных условий. Чтобы свести к минимуму негативное влияние на производительность, вызванное добавлением некластеризованного индекса columnstore для таблицы OLTP, можно использовать отфильтрованное условие для создания некластеризованного индекса columnstore только для холодных данных операционной рабочей нагрузки.

-   Таблица в памяти может включать один индекс columnstore. Его можно создать при создании таблицы или добавить позже с помощью процедуры [ALTER TABLE (Transact-SQL)](../t-sql/statements/alter-table-transact-sql.md). До версии SQL Server 2016 создание индекса columnstore допускалось только в таблицах на дисках.

Дополнительные сведения см. в статье [Производительность запросов по индексам columnstore](../relational-databases/indexes/columnstore-indexes-query-performance.md).

**Руководство по проектированию**


-   Таблица rowstore может включать один обновляемый некластеризованный индекс columnstore. До версии SQL Server 2014 некластеризованный индекс columnstore был доступен только для чтения.



&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-spexecuteexternalscript-transact-sqlsystem-stored-proceduressp-execute-external-script-transact-sqlmd"></a>8. &nbsp; [sp_execute_external_script (Transact-SQL)](system-stored-procedures/sp-execute-external-script-transact-sql.md)

*Обновлено: 23.01.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_7) | [Далее](#TitleNum_9))

<!-- Source markdown line 207.  ms.author= "edmaca".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0ee4d591ae9d9a5c015eec98aad9ccbb86268761 ac9b439c23ffae5fcc77639de6ff955763cf5844  (PR=4696  ,  Filename=sp-execute-external-script-transact-sql.md  ,  Dirpath=docs\relational-databases\system-stored-procedures\  ,  MergeCommitSha40=d7dcbcebbf416298f838a39dd5de6a46ca9f77aa) -->



Чтобы создать аналогичную модель с помощью Python, необходимо изменить идентификатор языка с `@language=N'R'` на `@language = N'Python'` и внести необходимые изменения в аргумент `@script`. В противном случае все параметры будут работать так же, как в R.

**В. Создание модели Python и формирование оценок на ее основе**


В этом примере показано, как использовать процедуру sp\_execute\_external\_script для создания оценок на основе простой модели Python.

```
CREATE PROCEDURE [dbo].[py_generate_customer_scores]
AS
BEGIN

**Input query to generate the customer data**

DECLARE @input_query NVARCHAR(MAX) = N'SELECT customer, orders, items, cost FROM dbo.Sales.Orders`

EXEC sp_execute_external_script @language = N'Python', @script = N'
import pandas as pd
from sklearn.cluster import KMeans

**Get data from input query**

customer_data = my_input_data

**Define the model**

n_clusters = 4
est = KMeans(n_clusters=n_clusters, random_state=111).fit(customer_data[["orders","items","cost"]])
clusters = est.labels_
customer_data["cluster"] = clusters

OutputDataSet = customer_data
'
, @input_data_1 = @input_query
, @input_data_1_name = N'my_input_data'
WITH RESULT SETS (("CustomerID" int, "Orders" float,"Items" float,"Cost" float,"ClusterResult" float));
END;
GO
```

Заголовки столбцов, используемые в коде Python, не выводятся в SQL Server, поэтому используйте инструкцию WITH RESULTS, чтобы указать имена столбцов и типы данных для SQL.

Для оценки можно также применять собственную функцию [PREDICT](system-stored-procedures/../../t-sql/queries/predict-transact-sql.md), которая обычно выполняется быстрее, так как не вызывает среду выполнения Python или R.




&nbsp;

&nbsp;

---

<a name="TitleNum_9"/>

### <a name="9-nbsp-create-primary-keystablescreate-primary-keysmd"></a>9. &nbsp; [Создание первичных ключей](tables/create-primary-keys.md)

*Обновлено: 18.01.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_8))

<!-- Source markdown line 102.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 d18b485f314cc005d624cab8a51650d3b8f55f89 9bd2e9453206e8940d30b0a01c43f9d8e1aed606  (PR=4652  ,  Filename=create-primary-keys.md  ,  Dirpath=docs\relational-databases\tables\  ,  MergeCommitSha40=6b4aae3706247ce9b311682774b13ac067f60a79) -->



**Создание первичного ключа с некластеризованным индексом в новой таблице**


1.  В **обозревателе объектов** подключитесь к экземпляру ядра СУБД.

2.  На стандартной панели выберите пункт **Создать запрос**.

3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере создается таблица и определяется первичный ключ для столбца `CustomerID` и кластеризованный индекс для `TransactionID`.

```
    USE AdventureWorks2012;
    GO
    CREATE TABLE Production.TransactionHistoryArchive1
    (
       CustomerID uniqueidentifier DEFAULT NEWSEQUENTIALID(),
       TransactionID int IDENTITY (1,1) NOT NULL,
       CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY NONCLUSTERED (uniqueidentifier)
    );
    GO

    -- Now add the clustered index
    CREATE CLUSTERED INDEX CIX_TransactionID ON Production.TransactionHistoryArchive1 (TransactionID);
    GO
```







## <a name="similar-articles-about-new-or-updated-articles"></a>Статьи, близкие к новым или измененным статьям

Этот раздел содержит статьи, очень близкие к недавно измененным статьям из других предметных областей в общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Предметные области, *содержащие* новые или недавно обновленные статьи


- [Новые + обновленные (1+3):&nbsp; **Углубленная аналитика для SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новые + обновленные (0+1):&nbsp; **Analytics Platform System для SQL**](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Новые + обновленные (0+1):&nbsp; **Подключение к SQL**](../connect/new-updated-connect.md)
- [Новые + обновленные (0+1):&nbsp; **Ядро СУБД для SQL**](../database-engine/new-updated-database-engine.md)
- [Новые + обновленные (12+1): **Integration Services для SQL**](../integration-services/new-updated-integration-services.md)
- [Новые + обновленные (6+2):&nbsp; **Linux для SQL**](../linux/new-updated-linux.md)
- [Новые + обновленные (15+0): **PowerShell для SQL**](../powershell/new-updated-powershell.md)
- [Новые + обновленные (2+9):&nbsp; **Реляционные базы данных для SQL**](../relational-databases/new-updated-relational-databases.md)
- [Новые + обновленные (1+0):&nbsp; **Reporting Services для SQL**](../reporting-services/new-updated-reporting-services.md)
- [Новые + обновленные (1+1):&nbsp; **SQL Operations Studio**](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Новые + обновленные(1+1):&nbsp; **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Новые + обновленные (0+1):&nbsp; **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Новые + обновленные (1+2):&nbsp; **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Новые + обновленные (0+2):&nbsp; **Transact-SQL**](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Предметные области, *не* содержащие новые или недавно обновленные статьи


- [Новые + обновленные (0+0): **Data Migration Assistant (DMA) для SQL**](../dma/new-updated-dma.md)
- [Новые + обновленные (0+0): **объекты данных ActiveX (ADO) для SQL**](../ado/new-updated-ado.md)
- [Новые + обновленные (0+0): документация **Analysis Services для SQL**](../analysis-services/new-updated-analysis-services.md)
- [Новые + обновленные (0+0): **Data Quality Services для SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Новые + обновленные (0+0): **расширения интеллектуального анализа данных (DMX) для SQL**](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новые + обновленные (0+0): **многомерные выражения (MDX) для SQL**](../mdx/new-updated-mdx.md)
- [Новые + обновленные (0+0): **ODBC (Open Database Connectivity) для SQL**](../odbc/new-updated-odbc.md)
- [Новые + обновленные (0+0): **примеры для SQL**](../samples/new-updated-samples.md)
- [Новые + обновленные (0+0): **помощник по миграции SQL Server (SSMA)**](../ssma/new-updated-ssma.md)
- [Новые + обновленные (0+0): **Инструменты для SQL**](../tools/new-updated-tools.md)
- [Новые + обновленные (0+0): **XQuery для SQL**](../xquery/new-updated-xquery.md)


