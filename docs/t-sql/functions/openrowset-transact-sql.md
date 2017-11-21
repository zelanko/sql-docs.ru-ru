---
title: "OPENROWSET (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPENROWSET_TSQL
- OPENROWSET
dev_langs:
- TSQL
helpviewer_keywords:
- data sources [SQL Server]
- OPENROWSET function
- remote data access [SQL Server], OPENROWSET
- ad hoc distributed queries
- OPENROWSET function, Transact-SQL
- OPENROWSET statement
- OLE DB data sources [SQL Server]
- ad hoc connection information
ms.assetid: f47eda43-33aa-454d-840a-bb15a031ca17
caps.latest.revision: 130
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3c23ec85299af595305a5f6d5141dbbf3ffab96d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="openrowset-transact-sql"></a>OPENROWSET (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит все необходимые сведения о соединении, которые требуются для доступа к удаленным данным источника данных OLE DB. Это альтернативный метод для доступа к таблицам на связанном сервере и является однократным нерегламентированным методом соединения и удаленного доступа к данным с помощью OLE DB. Вместо этого для более частых ссылок на источники данных OLE DB используйте связанные серверы. Дополнительные сведения см. в разделе [Связанные серверы (компонент Database Engine)](../../relational-databases/linked-servers/linked-servers-database-engine.md). `OPENROWSET` Функцию можно ссылаться в предложении FROM запроса, как будто имя таблицы. `OPENROWSET` Функция также может быть использована как целевая таблица `INSERT`, `UPDATE`, или `DELETE` инструкции, зависит от возможностей поставщика OLE DB. Несмотря на то, что запрос может возвратить несколько результирующих наборов, `OPENROWSET` возвращает только первый из них.  
  
 `OPENROWSET`также поддерживает массовые операции с помощью встроенного поставщика BULK, обеспечивающий данных из файла для чтения и возвращаются в виде набора строк.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
OPENROWSET   
( { 'provider_name' , { 'datasource' ; 'user_id' ; 'password'   
   | 'provider_string' }   
   , {   [ catalog. ] [ schema. ] object   
       | 'query'   
     }   
   | BULK 'data_file' ,   
       { FORMATFILE = 'format_file_path' [ <bulk_options> ]  
       | SINGLE_BLOB | SINGLE_CLOB | SINGLE_NCLOB }  
} )   
  
<bulk_options> ::=  
   [ , CODEPAGE = { 'ACP' | 'OEM' | 'RAW' | 'code_page' } ]   
   [ , DATASOURCE = 'data_source_name' ]
   [ , ERRORFILE = 'file_name' ]  
   [ , ERRORFILE_DATASOURCE = 'data_source_name' ]   
   [ , FIRSTROW = first_row ]   
   [ , LASTROW = last_row ]   
   [ , MAXERRORS = maximum_errors ]   
   [ , ROWS_PER_BATCH = rows_per_batch ]  
   [ , ORDER ( { column [ ASC | DESC ] } [ ,...n ] ) [ UNIQUE ] ]
  
   -- bulk_options related to input file format
   [ , FORMAT = 'CSV' ]
   [ , FIELDQUOTE = 'quote_characters']
   [ , FORMATFILE = 'format_file_path' ]   
```

  
## <a name="arguments"></a>Аргументы  
 "*provider_name*"  
 Символьная строка, которая представляет понятное имя (или PROGID) поставщика OLE DB, указанное в реестре. *provider_name* нет значения по умолчанию.  
  
 "*источник данных*"  
 Строковая константа, соответствующая конкретному источнику данных OLE DB. *источник данных* — это свойство DBPROP_INIT_DATASOURCE, должны быть переданы интерфейс IDBProperties поставщика для инициализации поставщика. Обычно эта строка содержит имя файла базы данных, имя сервера баз данных или имя, с помощью которого поставщик находит базу или базы данных.  
  
 "*user_id*"  
 Строковая константа, представляющая имя пользователя, передаваемое указанному поставщику OLE DB. *функция USER_ID* определяет контекст безопасности для соединения и передается как свойство DBPROP_AUTH_USERID для инициализации поставщика. *функция USER_ID* не может быть именем входа Microsoft Windows.  
  
 "*пароль*"  
 Строковая константа, представляющая пароль пользователя, передаваемый поставщику OLE DB. *пароль* передается как свойство DBPROP_AUTH_PASSWORD при инициализации поставщика. *пароль* не может быть паролем Microsoft Windows.  
  
 "*provider_string*"  
 Строковая константа для конкретного поставщика, которая передается как свойство DBPROP_INIT_PROVIDERSTRING для инициализации поставщика OLE DB. *provider_string* обычно включает в себя все сведения о соединении, необходимые для инициализации поставщика. Список ключевых слов, которые распознаются [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента в разделе [свойства инициализации и авторизации](../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
 *каталог*  
 Имя каталога или базы данных, в котором хранится указанный объект.  
  
 *схемы*  
 Имя схемы или владелец указанного объекта.  
  
 *объект*  
 Имя объекта, уникальным образом идентифицирующее объект, с которым производится взаимодействие.  
  
 "*запроса*"  
 Строковая константа, посылаемая поставщику и исполняемая им. Локальный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не обрабатывает этот запрос, но обрабатывает результаты запроса, возвращаемые поставщиком, это так называемый транзитный запрос. Передаваемые запросы полезны при использовании поставщиков, которые не предоставляют свои табличные данные через таблицы имен, а только через командный язык. Передаваемые запросы поддерживаются на удаленном сервере, при условии, что поставщик запросов поддерживает объект OLE DB Command и его обязательные интерфейсы. Дополнительные сведения см. в разделе [собственный клиент SQL Server &#40; OLE DB &#41; Справочник по](../../relational-databases/native-client-ole-db-interfaces/sql-server-native-client-ole-db-interfaces.md).  
  
 BULK  
 Использует поставщик больших наборов строк для функции OPENROWSET, чтобы читать данные из файла. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] функция OPENROWSET может считывать данные из файла без их загрузки в целевую таблицу. Это позволяет использовать функцию OPENROWSET совместно с обычной инструкцией SELECT.  
  
 Аргументы параметра BULK позволяют полностью управлять началом и концом считывания данных, отладку ошибок и способ обработки полученных данных. Например, можно указать, что считать файл данных в виде набора строк с одной строкой и одним столбцом типа **varbinary**, **varchar**, или **nvarchar**. Поведение по умолчанию описано в следующем далее описании аргументов.  
  
 Дополнительные сведения об использовании параметра BULK см. в подразделе «Примечания» далее в этом разделе. Дополнительные сведения о разрешениях, необходимых параметру BULK, см. в подразделе «Разрешения» далее в этом разделе.  
  
> [!NOTE]  
>  Функция OPENROWSET (BULK ...) не оптимизирует ведение журнала при использовании ее для импорта данных с моделью полного восстановления.  
  
 Сведения о подготовке данных к массовому импорту см. в разделе [Подготовка данных для массового экспорта или импорта &#40; SQL Server &#41; ](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md).  
  
 "*data_file*"  
 Полный путь к файлу данных, данные из которого копируются в целевую таблицу.   
 **Область применения:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
Начиная с версии [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP-версии 1.1, может быть data_file в хранилище Azure блога. Примеры см. в разделе [примеры массового доступ к данным в хранилище больших двоичных объектов Azure](../../relational-databases/import-export/examples-of-bulk-access-to-data-in-azure-blob-storage.md).
  
 \<bulk_options >  
 Указывает один или более аргументов для параметра BULK.  
  
 КОДОВАЯ СТРАНИЦА = {'ACP» | «OEM» | «ПЕРВИЧНАЯ» | "*code_page*"}  
 Указывает кодовую страницу данных в файле данных. Кодовая страница является применимо только в том случае, если данные содержат **char**, **varchar**, или **текст** столбцов с символьными значениями более 127 или меньше 32.  
  
> [!NOTE]  
>  Рекомендуется указывать имя параметров сортировки для каждого столбца в файле форматирования, за исключением того, при необходимости параметр 65001 должен иметь приоритет над спецификацией параметров сортировки или кодовой страницы.  
  
|Значение аргумента CODEPAGE|Description|  
|--------------------|-----------------|  
|ACP|Преобразует столбцы **char**, **varchar**, или **текст** тип данных из кодировки ANSI /[!INCLUDE[msCoName](../../includes/msconame-md.md)] кодовую страницу Windows (ISO 1252) для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] кодовую страницу.|  
|OEM (по умолчанию)|Преобразует столбцы **char**, **varchar**, или **текст** тип данных из кодовой страницы OEM системы для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] кодовую страницу.|  
|RAW|Преобразование из одной кодовой страницы в другую не выполняется. Это наиболее быстрый параметр.|  
|*code_page*|Показывает исходную кодовую страницу, в которой представлены символы в файле данных, например 850.<br /><br /> **\*\*Важные \* \***  версии, предшествующие [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] не поддерживают кодовую страницу 65001 (кодировка UTF-8).|  
  
 ERRORFILE = "*имя_файла*"  
 Указывает файл, используемый для сбора строк, которые имеют ошибки форматирования и не могут быть преобразованы в набор строк OLE DB. Эти строки без изменений копируются из файла данных в файл ошибок.  
  
 Файл ошибок создается в начале выполнения команды. Если он уже существует, возникнет ошибка. Дополнительно создается управляющий файл с расширением ERROR.txt. Этот файл ссылается на каждую строку в файле ошибок и позволяет провести их диагностику. После исправления ошибок данные могут быть загружены.  
**Область применения:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.
Начиная с версии [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)], `error_file_path` может находиться в хранилище Azure блога. 

«errorfile_data_source_name»   
**Область применения:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.
Именованный внешний источник данных, указывающий на место хранения больших двоичных объектов Azure файла ошибок, который будет содержать ошибки, обнаруженные во время импорта. Внешний источник данных должен быть создан с помощью `TYPE = BLOB_STORAGE` , который доступен в [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP-версии 1.1. Дополнительные сведения см. в разделе [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).
  
 FIRSTROW =*first_row*  
 Указывает номер первой строки для загрузки. Значение по умолчанию равно 1. Значение по умолчанию — первая строка указанного файла данных. Номера строк определяются с помощью подсчета признаков конца строки. Значения аргумента FIRSTROW начинаются с 1.  
  
 LASTROW =*last_row*  
 Указывает номер последней строки для загрузки. Значение по умолчанию равно 0. Оно указывает на последнюю строку в используемом файле данных.  
  
 MAXERRORS =*maximum_errors*  
 Указывает максимальное количество синтаксических ошибок или ошибок форматирования строк, указанное в файле форматирования, которое может произойти до того, как функция OPENROWSET сформирует исключение. Пока значение MAXERRORS не достигнуто, функция OPENROWSET не учитывает все ошибочные строки, не загружая их, и считает каждую ошибочную строку за одну ошибку.  
  
 Значение по умолчанию для *maximum_errors* — 10.  
  
> [!NOTE]  
>  Max_errors не применяется к ПРОВЕРОЧНЫМ ограничениям или преобразование **money** и **bigint** типов данных.  
  
 ROWS_PER_BATCH =*rows_per_batch*  
 Указывает примерное количество строк данных в файле данных. Значение должно быть того же порядка, что и реальное количество строк.  
  
 Функция OPENROWSET всегда импортирует файл данных в одном пакете. Тем не менее при указании *rows_per_batch* со значением > 0, обработчик запросов использует значение *rows_per_batch* как подсказку для выделения ресурсов в плане запроса.  
  
 По умолчанию значение аргумента ROWS_PER_BATCH неизвестно. Указание аргумента ROWS_PER_BATCH = 0 равносильно опусканию аргумента ROWS_PER_BATCH.  
  
 ПОРЯДОК ({ *столбца* [ASC | DESC]} [,... *n*  ] [UNIQUE])  
 Необязательное указание; задает, каким образом отсортированы данные в файле. По умолчанию массовая операция считает, что файл данных не упорядочен. Производительность можно повысить, если оптимизатор запросов сможет использовать заданный порядок для создания более эффективного плана запроса. Ниже приведены примеры, в которых указано, когда полезно назначить сортировку.  
  
-   Вставка строк в таблицу с кластеризованным индексом, в которой данные набора строк сортируются по ключу кластеризованного индекса.  
  
-   Соединение набора строк с другой таблицей с совпадающими столбцами сортировки и соединения.  
  
-   Статистическая обработка данных набора строк по столбцам сортировки.  
  
-   Использование набора строк как исходной таблицы в предложении FROM запроса с совпадающими столбцами сортировки и соединения.  
  
 Подсказка UNIQUE указывает, что в файле данных нет повторяющихся записей.  
  
 Если собственные строки файла данных не отсортированы в соответствии с заданным порядком или если задано указание UNIQUE и присутствуют повторяющиеся ключи, то будет возвращена ошибка.  
  
 При использовании ORDER обязательны псевдонимы столбцов. Список псевдонимов столбцов должен ссылаться на производную таблицу, к которой обращается предложение BULK. Имена столбцов, указанных в предложении ORDER, ссылаются на список псевдонимов столбцов. Типы больших значений (**varchar(max)**, **nvarchar(max)**, **varbinary(max)**, и **xml**) и типов больших объектов (LOB) (**текст**, **ntext**, и **изображения**) нельзя указывать столбцы.  
  
 SINGLE_BLOB  
 Возвращает содержимое *data_file* в виде набора строк с одной строкой и одним столбцом типа **varbinary(max)**.  
  
> [!IMPORTANT]  
>  XML-данные рекомендуется импортировать с помощью параметра SINGLE_BLOB, а не SINGLE_CLOB или SINGLE_NCLOB, потому что только параметр SINGLE_BLOB поддерживает все возможные преобразования кодировок в Windows.  
  
 SINGLE_CLOB  
 Прочитав *data_file* в формате ASCII, возвращает содержимое в виде набора строк с одной строкой и одним столбцом типа **varchar(max)**, используя параметры сортировки текущей базы данных.  
  
 SINGLE_NCLOB  
 Прочитав *data_file* кодировке Юникод и возвращает содержимое в виде набора строк с одной строкой и одним столбцом типа **nvarchar(max)**, используя параметры сортировки текущей базы данных.  

### <a name="input-file-format-options"></a>Параметры формата входных файлов
  
ФОРМАТ  **=**  «CSV»   
**Область применения:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
Указывает файл разделенный запятыми соответствует условиям [RFC 4180](https://tools.ietf.org/html/rfc4180) standard.

 FORMATFILE ='*путь_к_файлу_форматирования*"  
 Указывает полный путь к файлу форматирования. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]поддерживает два типа файлов форматирования: XML и отличный от XML.  
  
 Файл форматирования необходим для определения типов столбцов в результирующем наборе. Единственное исключение — случай, когда указаны аргументы SINGLE_CLOB, SINGLE_BLOB или SINGLE_NCLOB, при которых файл форматирования не обязателен.  
  
 Сведения о файлах форматирования см. в разделе [использование файла форматирования для массового импорта данных &#40; SQL Server &#41; ](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md).  

**Область применения:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
Начиная с версии [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP-версии 1.1, может быть путь_к_файлу_форматирования в хранилище Azure блога. Примеры см. в разделе [примеры массового доступ к данным в хранилище больших двоичных объектов Azure](../../relational-databases/import-export/examples-of-bulk-access-to-data-in-azure-blob-storage.md).

FIELDQUOTE  **=**  «field_quote»   
**Область применения:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
Определяет символ, который будет использоваться в качестве символа кавычки в CSV-файле. Если не указан символ кавычки ("") будет использоваться как символ кавычки, определенный в [RFC 4180](https://tools.ietf.org/html/rfc4180) standard.

  
## <a name="remarks"></a>Замечания  
 `OPENROWSET`может использоваться для доступа к удаленным данным из источников OLE DB данных только тогда, когда **DisallowAdhocAccess** параметр реестра явно установлен в 0 для указанного поставщика, и является Ad Hoc Distributed Queries дополнительный параметр конфигурации включена. Если эти параметры не установлены, поведение по умолчанию запрещает нерегламентированный доступ.  
  
 При удаленном доступе к источнику данных OLE DB автоматическое делегирование идентификатора имени входа доверительных соединений с сервера, к которому подключен клиент, на запрашиваемый сервер не выполняется. Делегирование проверки подлинности должно быть настроено.  
  
 Имена каталога или схемы необходимы, если поставщик OLE DB поддерживает несколько каталогов и схем для указанного источника данных. Значения для *каталога* и *схемы* можно опустить, если поставщик OLE DB не поддерживает их. Если поставщик поддерживает только имена схем, но двухкомпонентное имя в формате *схемы***.** *объект* должен быть указан. Если поставщик поддерживает только имена каталогов, но трехчастное имя формы *каталога***.** *схемы***.** *объект* должен быть указан. Трехсоставное должен быть указан для передаваемых запросов, используйте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента. Дополнительные сведения см. в разделе [синтаксические обозначения Transact-SQL &#40; Transact-SQL &#41; ](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
 `OPENROWSET`не принимает переменные в качестве аргументов.  
  
 Каждый вызов `OPENDATASOURCE`, `OPENQUERY`, или `OPENROWSET` в `FROM` предложение вычисляется отдельно и независимо от любого вызова этих функций, используется в качестве цели обновления, даже если одинаковые аргументы предоставляются для двух вызовов. В частности, условия фильтра или соединения, применяемые к результатам одного из таких вызовов, никак не влияют на результаты другого.  
  
## <a name="using-openrowset-with-the-bulk-option"></a>Применение инструкции OPENROWSET с параметром BULK  
 Следующие усовершенствования [!INCLUDE[tsql](../../includes/tsql-md.md)] поддерживают функцию OPENROWSET(BULK…).  
  
-   Предложение FROM, используемое с `SELECT` можно вызвать `OPENROWSET(BULK...)` вместо имени таблицы с полной `SELECT` функциональные возможности.  
  
     `OPENROWSET`с `BULK` параметра требуется корреляционное имя, также известные как переменная диапазона или псевдоним в `FROM` предложения. Могут быть указаны псевдонимы столбцов. Если список псевдонимов столбцов не указан, файл форматирования должен содержать имена столбцов. Указание псевдонимов столбцов переопределяет имена столбцов в файле форматирования, такие как:  
  
     `FROM OPENROWSET(BULK...) AS table_alias`  
  
     `FROM OPENROWSET(BULK...) AS table_alias(column_alias,...n)`  
>    [!IMPORTANT]  
>    Сбой при добавлении `AS <table_alias>` приведет к ошибке:    
>    Сообщение 491, уровень 16, состояние 1, строка 20    
>    Корреляционное имя должно быть указано для группового набора строк в предложении FROM.    
  
-   Объект `SELECT...FROM OPENROWSET(BULK...)` запрос данных в файл напрямую без импортирования данных в таблицу. `SELECT…FROM OPENROWSET(BULK...)`инструкции можно также список псевдонимы массовых столбцов с помощью файла форматирования для указания имен столбцов и типов данных.  
  
-   С помощью `OPENROWSET(BULK...)` как исходной таблицы в `INSERT` или `MERGE` инструкции массовый импорт данных из файла данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицу. Дополнительные сведения см. в разделе [массовый импорт данных с помощью инструкции BULK INSERT или OPENROWSET &#40; BULK... &#41; &#40; SQL Server &#41; ](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md) .  
  
-   Когда `OPENROWSET BULK` используется с `INSERT` инструкции, предложение BULK поддерживает табличные указания. Помимо обычного табличные указания, такие как `TABLOCK`, `BULK` предложение может принимать следующие специальные табличные указания: `IGNORE_CONSTRAINTS` (игнорирует только `CHECK` и `FOREIGN KEY` ограничения), `IGNORE_TRIGGERS`, `KEEPDEFAULTS`, и `KEEPIDENTITY`. Дополнительные сведения см. в разделе [Табличные указания (Transact-SQL)](../../t-sql/queries/hints-transact-sql-table.md).  
  
 Дополнительные сведения об использовании `INSERT...SELECT * FROM OPENROWSET(BULK...)` см. инструкции, [массовый импорт и экспорт данных &#40; SQL Server &#41; ](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md). Сведения о том, когда в журнале транзакций регистрируются операции вставки строк, выполняемые при массовом импорте, см. в разделе [Предварительные условия для минимального протоколирования массового импорта данных](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md).  
  
> [!NOTE]  
>  При использовании `OPENROWSET`, важно понимать, каким образом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обрабатывает олицетворение. Сведения о вопросах безопасности см. в разделе [массовый импорт данных с помощью инструкции BULK INSERT или OPENROWSET &#40; BULK... &#41; &#40; SQL Server &#41; ](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).  
  
### <a name="bulk-importing-sqlchar-sqlnchar-or-sqlbinary-data"></a>Массовый импорт данных SQLCHAR, SQLNCHAR или SQLBINARY  
 Функция OPENROWSET(BULK...) предполагает, что максимальная длина данных SQLCHAR, SQLNCHAR или SQLBINARY не превышает 8 000 байт (если не указано иное). Если в поле данных LOB, содержащий все импортируемые данные **varchar(max)**, **nvarchar(max)**, или **varbinary(max)** объектов, превышает 8 000 байт, необходимо использовать XML-файл форматирования, который определяет максимальную длину для поля данных. Чтобы указать максимальную длину, измените файл форматирования и объявите атрибут MAX_LENGTH.  
  
> [!NOTE]  
>  Автоматически сформированный файл форматирования не задает длину или максимальную длину для поля LOB. Однако можно изменить файл форматирования и указать длину или максимальную длину вручную.  
  
### <a name="bulk-exporting-or-importing-sqlxml-documents"></a>Массовый экспорт или импорт документов SQLXML  
 Чтобы выполнить массовый экспорт или импорт SQLXML-данных используйте один из следующих типов данных в файле форматирования:  
  
|Тип данных|Действие|  
|---------------|------------|  
|SQLCHAR или SQLVARYCHAR|Данные отправляются в кодовой странице клиента или кодовой странице, определенной параметрами сортировки.|  
|SQLNCHAR или SQLNVARCHAR|Данные отправляются в Юникоде.|  
|SQLBINARY или SQLVARYBIN|Данные отправляются без преобразования.|  
  
## <a name="permissions"></a>Permissions  
 `OPENROWSET`разрешения определяются разрешениями имени пользователя, которое передается поставщику OLE DB. Для использования `BULK` параметра требуется `ADMINISTER BULK OPERATIONS` разрешение.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-openrowset-with-select-and-the-sql-server-native-client-ole-db-provider"></a>A. Использование функции OPENROWSET с инструкцией SELECT и поставщиком OLE DB для собственного клиента SQL Server  
 В следующем примере используется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента для доступа к `HumanResources.Department` в таблицу [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] базы данных на удаленном сервере `Seattle1`. (При использовании SQLNCLI [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет использовать последнюю версию поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].) Инструкция `SELECT` используется для определения возвращаемого набора строк. Строка поставщика содержит ключевые слова `Server` и `Trusted_Connection`. Эти ключевые слова распознаются [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента.  
  
```tsql  
SELECT a.*  
FROM OPENROWSET('SQLNCLI', 'Server=Seattle1;Trusted_Connection=yes;',  
     'SELECT GroupName, Name, DepartmentID  
      FROM AdventureWorks2012.HumanResources.Department  
      ORDER BY GroupName, Name') AS a;  
```  
  
### <a name="b-using-the-microsoft-ole-db-provider-for-jet"></a>Б. Использование поставщика Microsoft OLE DB для Jet  
 Следующий пример обращается к `Customers` в таблицу [!INCLUDE[msCoName](../../includes/msconame-md.md)] доступа `Northwind` базы данных через [!INCLUDE[msCoName](../../includes/msconame-md.md)] поставщик OLE DB для Jet.  
  
> [!NOTE]  
>  В этом примере предполагается, что Access установлен. Для запуска данного примера необходимо установить базу данных Northwind.  
  
```tsql  
SELECT CustomerID, CompanyName  
   FROM OPENROWSET('Microsoft.Jet.OLEDB.4.0',  
      'C:\Program Files\Microsoft Office\OFFICE11\SAMPLES\Northwind.mdb';  
      'admin';'',Customers);  
GO  
```  
  
### <a name="c-using-openrowset-and-another-table-in-an-inner-join"></a>В. Использование функции OPENROWSET и другой таблицы в предложении INNER JOIN  
 В следующем примере выбираются все данные из `Customers` таблицу из локального экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `Northwind` базы данных и из `Orders` таблицы из Access `Northwind` базу данных, расположенную на том же компьютере.  
  
> [!NOTE]  
>  В этом примере предполагается, что Access установлен. Для запуска данного примера необходимо установить базу данных Northwind.  
  
```tsql  
USE Northwind  ;  
GO  
SELECT c.*, o.*  
FROM Northwind.dbo.Customers AS c   
   INNER JOIN OPENROWSET('Microsoft.Jet.OLEDB.4.0',   
   'C:\Program Files\Microsoft Office\OFFICE11\SAMPLES\Northwind.mdb';'admin';'', Orders)      
   AS o   
   ON c.CustomerID = o.CustomerID ;  
GO  
```  
  
### <a name="d-using-openrowset-to-bulk-insert-file-data-into-a-varbinarymax-column"></a>Г. Использование функции OPENROWSET для массовой вставки данных из файла в столбец типа varbinary(max)  
 В следующем примере создается небольшая таблица для демонстрационных целей и вставляются данные из файла с именем `Text1.txt`, расположенного в корневом каталоге диска `C:`, в столбец `varbinary(max)`.  
  
```tsql  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTable(FileName nvarchar(60),   
  FileType nvarchar(60), Document varbinary(max));  
GO  
  
INSERT INTO myTable(FileName, FileType, Document)   
   SELECT 'Text1.txt' AS FileName,   
      '.txt' AS FileType,   
      * FROM OPENROWSET(BULK N'C:\Text1.txt', SINGLE_BLOB) AS Document;  
GO  
```  
  
### <a name="e-using-the-openrowset-bulk-provider-with-a-format-file-to-retrieve-rows-from-a-text-file"></a>Д. Использование поставщика OPENROWSET BULK с файлом форматирования для получения строк из текстового файла  
 В следующем примере используется файл форматирования для получения строк, разделенных символами табуляции, из файла `values.txt`, который содержит следующие данные:  
  
```tsql  
1     Data Item 1  
2     Data Item 2  
3     Data Item 3  
```  
  
 Файл форматирования `values.fmt` описывает столбцы в файле `values.txt`:  
  
```tsql  
9.0  
2  
1  SQLCHAR  0  10 "\t"        1  ID                SQL_Latin1_General_Cp437_BIN  
2  SQLCHAR  0  40 "\r\n"      2  Description        SQL_Latin1_General_Cp437_BIN  
```  
  
 Это запрос, который возвращает данные:  
  
```tsql  
SELECT a.* FROM OPENROWSET( BULK 'c:\test\values.txt',   
   FORMATFILE = 'c:\test\values.fmt') AS a;  
```  
  
### <a name="f-specifying-a-format-file-and-code-page"></a>Е. Указание формата файла и код страницы  
 В следующем примере показано, как использовать оба формата файла кода страницы параметров и в то же время.  
  
```tsql  
INSERT INTO MyTable SELECT a.* FROM  
OPENROWSET (BULK N'D:\data.csv', FORMATFILE =   
    'D:\format_no_collation.txt', CODEPAGE = '65001') AS a;  
```  
### <a name="g-accessing-data-from-a-csv-file-with-a-format-file"></a>Ж. Доступ к данным из CSV-файла с файлом форматирования  
**Область применения:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
```tsql
SELECT *
FROM OPENROWSET(BULK N'D:\XChange\test-csv.csv',
    FORMATFILE = N'D:\XChange\test-csv.fmt', 
    FIRSTROW=2, 
    FORMAT='CSV') AS cars;  
```

### <a name="h-accessing-data-from-a-csv-file-without-a-format-file"></a>З. Доступ к данным из CSV-файла без файла форматирования

```tsql
SELECT * FROM OPENROWSET(
   BULK 'C:\Program Files\Microsoft SQL Server\MSSQL14.CTP1_1\MSSQL\DATA\inv-2017-01-19.csv',
   SINGLE_CLOB) AS DATA;
```

### <a name="i-accessing-data-from-a-file-stored-on-azure-blob-storage"></a>И. Доступ к данным из файла, который хранится в хранилище больших двоичных объектов Azure   
**Область применения:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
В следующем примере внешнего источника данных, указывающий на контейнер в учетной записи хранилища Azure и учетные данные уровня базы данных, созданных для подписанного URL-адреса.     

```tsql
SELECT * FROM OPENROWSET(
   BULK  'inv-2017-01-19.csv',
   DATA_SOURCE = 'MyAzureInvoices',
   SINGLE_CLOB) AS DataFile;
```   
Для завершения `OPENROWSET` примеры, включая настройку учетных данных и внешнего источника данных, см. в [примеры массового доступ к данным в хранилище больших двоичных объектов Azure](../../relational-databases/import-export/examples-of-bulk-access-to-data-in-azure-blob-storage.md).
 
### <a name="additional-examples"></a>Дополнительные примеры  
 Дополнительные примеры, показывающие использование `INSERT...SELECT * FROM OPENROWSET(BULK...)`, см. в следующих разделах:  
  
-   [Примеры массового импорта и экспорта XML-документов (SQL Server)](../../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [Сохранение значений идентификаторов при массовом импорте данных (SQL Server)](../../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Сохранение значений NULL или использование значений по умолчанию при массовом импорте данных (SQL Server)](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [Использование файла форматирования для массового импорта данных (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Использование символьного формата для импорта и экспорта данных (SQL Server)](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Пропуск столбца таблицы с помощью файла форматирования (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [Использование файла форматирования для пропуска поля данных (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [Использование файла форматирования для сопоставления столбцов таблицы с полями файла данных (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [DELETE (Transact-SQL)](../../t-sql/statements/delete-transact-sql.md)   
 [FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md)   
 [Массовый импорт и экспорт данных (SQL Server)](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)   
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [OPENDATASOURCE (Transact-SQL)](../../t-sql/functions/opendatasource-transact-sql.md)   
 [OPENQUERY &#40; Transact-SQL &#41;](../../t-sql/functions/openquery-transact-sql.md)   
 [Функции наборов строк &#40; Transact-SQL &#41;](../../t-sql/functions/rowset-functions-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [sp_addlinkedserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_serveroption &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md)   
 [UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md)   
 [ГДЕ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
  
  

