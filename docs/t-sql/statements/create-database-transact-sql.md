---
title: CREATE DATABASE (Transact-SQL) | Документация Майкрософт
description: Создание синтаксиса базы данных для SQL Server, Базы данных SQL Azure, Хранилища данных SQL Azure и Parallel Data Warehouse
ms.custom: ''
ms.date: 07/03/2018
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DATABASE_TSQL
- DATABASE
- CONTAINMENT_TSQL
- CREATE DATABASE
- CREATE_DATABASE_TSQL
- CONTAINS_FILESTREAM_TSQL
- CONTAINS FILESTREAM
- CONTAINMENT
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots [SQL Server database snapshots], creating
- databases [SQL Server], creating
- model database [SQL Server], database creation
- mounted drives [SQL Server]
- CREATE DATABASE
- CREATE DATABASE statement
- file creation [SQL Server]
- creating databases
- containment
- filegroups [SQL Server], database creation
- database creation [SQL Server], CREATE DATABASE statement
- moving databases
- attaching databases [SQL Server], CREATE DATABASE...FOR ATTACH
ms.assetid: 29ddac46-7a0f-4151-bd94-75c1908c89f8
caps.latest.revision: 212
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-current||=azuresqldb-mi-current||=azure-sqldw-latest||>=aps-pdw-2016||=sqlallproducts-allversions'
ms.openlocfilehash: b8d694b0afadd7504b60bd7bcc06df3151e42735
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2018
ms.locfileid: "40405941"
---
# <a name="create-database"></a>CREATE DATABASE

Создает новую базу данных. 

Щелкните одну из следующих вкладок, чтобы изучить синтаксис, аргументы, примечания, разрешения и примеры для используемой вам версии SQL.

Дополнительные сведения о соглашениях о синтаксисе см. в статье [Соглашения о синтаксисе в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md). 

## <a name="click-a-product"></a>Выберите продукт!

В следующей строке щелкните имя продукта, который вас интересует. На этой веб-странице отобразится другой контент, относящийся к выбранному продукту.

::: moniker range=">=sql-server-2016||>=sql-server-linux-2017||=sqlallproducts-allversions"

> [!div class="mx-tdCol2BreakAll"]
> <table>
> <tr>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
> </tr>
> <tr>
>   <th><strong><em>* SQL Server *<br />&nbsp;</em></strong></th>
>   <th><a href="create-database-transact-sql.md?view=azuresqldb-current">База данных SQL<br />Базы данных SQL</a></th>
>   <th><a href="create-database-transact-sql.md?view=azuresqldb-mi-current">База данных SQL<br />Базы данных SQL</a></th>
>   <th><a href="create-database-transact-sql.md?view=azure-sqldw-latest">Хранилище данных<br />SQL</a></th>
>   <th><a href="create-database-transact-sql.md?view=aps-pdw-2016">SQL Parallel<br />Data Warehouse</a></th>
> </tr>
> </table>

&nbsp;

# <a name="sql-server"></a>SQL Server

## <a name="overview"></a>Обзор

В SQL Server эта инструкция создает базу данных, используемые для нее файлы и их файловые группы. Также она позволяет создать моментальный снимок базы данных или подключить файлы для создания базы данных из отсоединенных файлов другой базы данных. 


## <a name="syntax"></a>Синтаксис  

Создание базы данных.  

```  
CREATE DATABASE database_name   
[ CONTAINMENT = { NONE | PARTIAL } ]  
[ ON   
      [ PRIMARY ] <filespec> [ ,...n ]   
      [ , <filegroup> [ ,...n ] ]   
      [ LOG ON <filespec> [ ,...n ] ]   
]   
[ COLLATE collation_name ]  
[ WITH  <option> [,...n ] ]  
[;]  
  
<option> ::=  
{  
      FILESTREAM ( <filestream_option> [,...n ] )  
    | DEFAULT_FULLTEXT_LANGUAGE = { lcid | language_name | language_alias }  
    | DEFAULT_LANGUAGE = { lcid | language_name | language_alias }  
    | NESTED_TRIGGERS = { OFF | ON }  
    | TRANSFORM_NOISE_WORDS = { OFF | ON}  
    | TWO_DIGIT_YEAR_CUTOFF = <two_digit_year_cutoff>   
    | DB_CHAINING { OFF | ON }  
    | TRUSTWORTHY { OFF | ON }
    | PERSISTENT_LOG_BUFFER=ON ( DIRECTORY_NAME='<Filepath to folder on DAX formatted volume>' )
}  
  
<filestream_option> ::=  
{  
      NON_TRANSACTED_ACCESS = { OFF | READ_ONLY | FULL }  
    | DIRECTORY_NAME = 'directory_name'   
}  
  
<filespec> ::=   
{  
(  
    NAME = logical_file_name ,  
    FILENAME = { 'os_file_name' | 'filestream_path' }   
    [ , SIZE = size [ KB | MB | GB | TB ] ]   
    [ , MAXSIZE = { max_size [ KB | MB | GB | TB ] | UNLIMITED } ]   
    [ , FILEGROWTH = growth_increment [ KB | MB | GB | TB | % ] ]  
)  
}  
  
<filegroup> ::=   
{  
FILEGROUP filegroup name [ [ CONTAINS FILESTREAM ] [ DEFAULT ] | CONTAINS MEMORY_OPTIMIZED_DATA ]  
    <filespec> [ ,...n ]  
}  
  
<service_broker_option> ::=  
{  
    ENABLE_BROKER  
  | NEW_BROKER  
  | ERROR_BROKER_CONVERSATIONS  
}  
  
```  
 
Присоединение базы данных    

```  
CREATE DATABASE database_name   
    ON <filespec> [ ,...n ]   
    FOR { { ATTACH [ WITH <attach_database_option> [ , ...n ] ] }  
        | ATTACH_REBUILD_LOG }  
[;]  
  
<attach_database_option> ::=  
{  
      <service_broker_option>  
    | RESTRICTED_USER  
    | FILESTREAM ( DIRECTORY_NAME = { 'directory_name' | NULL } )  
}   
```  
  
Создание моментального снимка базы данных    

```  
CREATE DATABASE database_snapshot_name   
    ON   
    (  
        NAME = logical_file_name,  
        FILENAME = 'os_file_name'   
    ) [ ,...n ]   
    AS SNAPSHOT OF source_database_name  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Имя новой базы данных. Имена баз данных должны быть уникальны внутри экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и должны соответствовать правилам для [идентификаторов](../../relational-databases/databases/database-identifiers.md).  
  
 Аргумент *database_name* может иметь максимальную длину 128 символов, если для файла журнала не указано логическое имя. Если логическое имя файла не указано, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формирует для журнала имена *logical_file_name* и *os_file_name* путем добавления суффикса к *database_name*. Это ограничивает длину аргумента *database_name* 123 символами, чтобы формируемое логическое имя файла было не длиннее 128 символов.  
  
 Если имя файла данных не указано, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует аргумент *database_name* как *logical_file_name* и *os_file_name*. Путь по умолчанию берется из реестра. Путь по умолчанию можно изменить на вкладке **Свойства сервера (страница "Параметры базы данных")[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] в среде** . Изменение пути по умолчанию требует перезапуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 CONTAINMENT = { NONE | PARTIAL }  

**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Указывает состояние включения базы данных. NONE = неавтономная база данных. PARTIAL = частично автономная база данных.  
  
 ON  
 Указывает, что дисковые файлы, используемые для хранения разделов данных в базе данных, файлов данных, определяются явно. Параметр ON необходимо применять, если за ним следует список элементов \<filespec> с разделителями-запятыми, которые определяют файлы данных первичной файловой группы. За списком файлов в первичной файловой группе может следовать необязательный список элементов \<filegroup> с разделителями-запятыми, которые определяют файловые группы пользователей и принадлежащие им файлы.  
  
 PRIMARY  
 Указывает, что связанный список \<filespec> определяет первичный файл. Первый файл, указанный в элементе \<filespec> в первичной файловой группе, становится первичным файлом. В базе данных может быть только один первичный файл. Дополнительные сведения см. в статье [Файлы и группы файлов базы данных](../../relational-databases/databases/database-files-and-filegroups.md).  
  
 Если параметр PRIMARY не указан, то первый файл списка в инструкции CREATE DATABASE становится первичным файлом.  
  
 LOG ON  
 Указывает, что дисковые файлы, используемые для хранения журнала базы данных, то есть файлы журналов, определяются явно. За параметром LOG ON следует список элементов \<filespec> с разделителями-запятыми, которые определяют файлы журналов. Если параметр LOG ON не указан, автоматически создается один файл журнала, размер которого определяется большей из следующих двух величин: 512 КБ или 25 процентов от суммы размеров всех файлов данных в базе данных. Этот файл помещается в местоположение для журнала по умолчанию. Сведения об этом расположении см. в разделе [Просмотр или изменение расположения по умолчанию для файлов данных и журнала (среда SQL Server Management Studio)](../../database-engine/configure-windows/view-or-change-the-default-locations-for-data-and-log-files.md).  
  
 Параметр LOG ON не может указываться для моментального снимка базы данных.  
  
 COLLATE *collation_name*  
 Задает параметры сортировки по умолчанию для базы данных. Именем параметров сортировки может быть либо имя параметров сортировки Windows, либо имя параметров сортировки SQL. Если параметр не указан, базе данных назначаются параметры сортировки по умолчанию для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Имя параметров сортировки не может указываться для моментального снимка базы данных.  
  
 Имя параметров сортировки не может указываться с предложениями FOR ATTACH и FOR ATTACH_REBUILD_LOG. Дополнительные сведения о способах изменения параметров сортировки подсоединенной базы данных см. на [веб-сайте корпорации Майкрософт](http://go.microsoft.com/fwlink/?linkid=16419&kbid=325335).  
  
 Дополнительные сведения об именах параметров сортировки Windows и SQL см. в разделе [COLLATE (Transact-SQL)](~/t-sql/statements/collations.md).  
  
> [!NOTE]  
>  Сортировка в автономных базах данных отличается от неавтономных баз данных. Дополнительные сведения см. в разделе [Параметры сортировки автономной базы данных](../../relational-databases/databases/contained-database-collations.md).  
  
 WITH \<option>  
 -   **\<filestream_options>** 
  
     NON_TRANSACTED_ACCESS = { **OFF** | READ_ONLY | FULL }  
**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
     Указывает уровень нетранзакционного доступа FILESTREAM к базе данных.  
  
    |Значение|Описание|  
    |-----------|-----------------|  
    |OFF|Нетранзакционный доступ отключен.|  
    |READONLY|Данные FILESTREAM в этой базе данных могут быть считаны нетранзакционными процессами.|  
    |FULL|Полный нетранзакционный доступ к FILESTREAM FileTable включен.|  
  
     DIRECTORY_NAME = \<directory_name> **Применимо к** : с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
     Имя каталога, совместимое с Windows. Это имя должно быть уникально среди всех имен Database_Directory в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Проверка уникальности выполняется с учетом регистра, независимо от параметров сортировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот параметр необходимо назначить до создания FileTable в этой базе данных.  
  
 Следующие параметры разрешаются, только если параметр CONTAINMENT установлен в состояние PARTIAL. Если параметр CONTAINMENT установлен в состояние NONE, возникнут ошибки.  
  
-   **DEFAULT_FULLTEXT_LANGUAGE = \<lcid> | \<language name> | \<language alias>**  
  
**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
     See [Configure the default full-text language Server Configuration Option](../../database-engine/configure-windows/configure-the-default-full-text-language-server-configuration-option.md) for a full description of this option.  
  
-   **DEFAULT_LANGUAGE = \<lcid> | \<language name> | \<language alias>**  
  
**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
     See [Configure the default language Server Configuration Option](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md) for a full description of this option.  
  
-   **NESTED_TRIGGERS = { OFF | ON}**  
  
**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
     See [Configure the nested triggers Server Configuration Option](../../database-engine/configure-windows/configure-the-nested-triggers-server-configuration-option.md) for a full description of this option.  
  
-   **TRANSFORM_NOISE_WORDS = { OFF | ON}**  
  
**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
     See [transform noise words Server Configuration Option](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md)for a full description of this option.  
  
-   **TWO_DIGIT_YEAR_CUTOFF = { 2049 | \<любой год от 1753 до 9999> }**  
  
     Четыре цифры, обозначающие год. Значение по умолчанию — 2049. Полное описание этого параметра см. в статье [Настройка параметра конфигурации сервера two digit year cutoff](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).  
  
-   **DB_CHAINING { OFF | ON }**  
  
     Если указано значение ON, то база данных может быть источником или целевой базой данных в межбазовой цепочке владения.  
  
     Если задано значение OFF, то база данных не может участвовать в межбазовых цепочках владения. Значение по умолчанию — OFF.  
  
    > [!IMPORTANT]  
    >  Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] распознает эту настройку, если параметр сервера cross db ownership chaining имеет значение 0 (OFF). Если параметр cross db ownership chaining имеет значение 1 (ON), то все пользовательские базы данных могут участвовать в межбазовых цепочках владения, вне зависимости от значения этого параметра. Этот параметр задается с помощью процедуры [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
     Для задания этого параметра необходимо членство в предопределенной роли сервера sysadmin. Параметр DB_CHAINING не может быть задан для системных баз данных: master, model, tempdb.  
  
-   **TRUSTWORTHY { OFF | ON }**  
  
     Если задано значение ON, то модули базы данных (например, представления, определяемые пользователем функции и хранимые процедуры), в которых используется контекст олицетворения, могут обращаться к ресурсам, расположенным за пределами базы данных.  
  
     Если задано значение OFF, то модули базы данных в контексте олицетворения не могут обращаться к ресурсам, расположенным за пределами базы данных. Значение по умолчанию — OFF.  
  
     Параметр TRUSTWORTHY устанавливается в значение OFF при каждом присоединении базы данных.  
  
     По умолчанию для всех системных баз данных, кроме msdb, параметр TRUSTWORTHY установлен в значение OFF. Оно не изменяется для баз данных model и tempdb. Рекомендуется никогда не устанавливать параметр TRUSTWORTHY в состояние ON для базы данных master.  
  
-   **PERSISTENT_LOG_BUFFER=ON ( DIRECTORY_NAME='' )**

     Если указан этот параметр, буфер журнала транзакций создается в томе на дисковом устройстве с поддержкой памяти класса хранилища (энергонезависимое хранилище NVDIMM-N), которое также называется постоянным буфером журнала. Дополнительные сведения см. в записи блога о [сокращении задержки фиксации транзакций с помощью памяти класса хранилища](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/12/02/transaction-commit-latency-acceleration-using-storage-class-memory-in-windows-server-2016sql-server-2016-sp1/). **Применимо к:** [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] и более поздним версиям.
  
 FOR ATTACH [ WITH \< attach_database_option > ] указывает, что база данных создана путем [присоединения](../../relational-databases/databases/database-detach-and-attach-sql-server.md) существующего набора файлов операционной системы. Должен существовать элемент \<filespec>, который указывает первичный файл. Кроме этого элемента, необходимы только элементы \<filespec>, предназначенные для файлов, пути которых отличны от путей, существовавших при создании или последнем присоединении базы данных. Для таких файлов должен быть определен элемент \<filespec>.  
  
 Для параметра FOR ATTACH необходимо выполнение следующих условий.  
  
-   Должны быть доступны все файлы данных (MDF и NDF).  
  
-   Если существует несколько файлов журналов, все они должны быть доступны.  
  
 Если база данных, доступная для чтения и записи, располагает единственным файлом журнала, который недоступен в текущий момент, а также если база данных была закрыта в отсутствие пользователей или открытых транзакций перед операцией присоединения, то параметр FOR ATTACH автоматически перестраивает файл журнала и обновляет первичный файл. Однако журнал невозможно перестроить в базе данных, доступной только для чтения, так как нельзя обновить первичный файл. Поэтому, если присоединяется база данных только для чтения, журнал которой недоступен, необходимо указать в предложении FOR ATTACH файлы журнала или файлы.  
  
> [!NOTE]  
>  База данных, созданная в более поздней версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], не может быть присоединена в ранних версиях.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] любые полнотекстовые файлы, являющиеся частью присоединяемой базы данных, будут присоединены вместе с базой данных. Чтобы задать новый путь полнотекстового каталога, следует указать новое местоположение без имени полнотекстового файла операционной системы. Дополнительные сведения см. в разделе "Примеры".  
  
 При присоединении базы данных, содержащей параметр FILESTREAM "Directory name", к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен проверить уникальность имени Database_Directory. Если это не так, операция присоединения завершится неудачей с ошибкой "Имя FILESTREAM Database_Directory \<name> не уникально в этом экземпляре SQL Server". Чтобы избежать этой ошибки, необходимо передать этой операции необязательный параметр *directory_name*.  
  
 Параметр FOR ATTACH не может указываться для моментального снимка базы данных.  
  
 В предложении FOR ATTACH может указываться параметр RESTRICTED_USER. Предложение RESTRICTED_USER позволяет подключаться к базе данных только членам предопределенных ролей базы данных db_owner и dbcreator и предопределенной роли сервера sysadmin, количество соединений при этом не ограничивается. Пользователям, не соответствующим этому условию, подключение не разрешается.  
  
 Если в базе данных используется компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)], в предложении FOR ATTACH следует использовать WITH \<service_broker_option>: 
  
 \<service_broker_option> управляет доставкой сообщений компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] и идентификатором компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] для базы данных. Параметры [!INCLUDE[ssSB](../../includes/sssb-md.md)] могут указываться только при использовании предложения FOR ATTACH.  
  
 ENABLE_BROKER  
 Определяет, что для указанной базы данных включен компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Это означает, что происходит запуск доставки сообщений и параметр is_broker_enabled устанавливается в значение true в представлении каталога sys.databases. В базе данных сохраняется существующий идентификатор компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
 NEW_BROKER  
 Создает новое значение service_broker_guid в представлении каталога sys.databases и восстановленной базе данных, после чего завершает все конечные точки диалога, очищая их. Посредник включен, но сообщения удаленным конечным точкам диалога не отправляются. Все маршруты, ссылающиеся на старый идентификатор компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)], необходимо создать повторно с новым идентификатором.  
  
 ERROR_BROKER_CONVERSATIONS  
 Завершает все диалоги, находящиеся в состоянии ошибки, которые были присоединены к базе данных или восстановлены. Посредник отключается до завершения этой операции, после чего вновь включается. В базе данных сохраняется существующий идентификатор компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
 При подключении реплицируемой базы данных, которая была скопирована, а не отсоединена, необходимо учитывать следующее.  
  
-   При подключении базы данных к тому же экземпляру и версии сервера, к которому была подключена оригинальная база данных, не требуется никаких дополнительных действий.  
  
-   При подключении базы данных к обновленной версии того же экземпляра сервера необходимо запустить процедуру [sp_vupgrade_replication](../../relational-databases/system-stored-procedures/sp-vupgrade-replication-transact-sql.md) для обновления репликации по завершении операции подключения.  
  
-   При подключении базы данных к другому экземпляру сервера, независимо от его версии, необходимо запустить процедуру [sp_removedbreplication](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) для удаления репликации по завершении операции подключения.  
  
> [!NOTE]  
> Присоединение работает с форматом хранения **vardecimal**, но при этом компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] должен быть обновлен по крайней мере до версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] с пакетом обновления 2 (SP2). Присоединение баз данных, использующих формат хранения vardecimal версий ранее [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], невозможно. Дополнительные сведения о формате хранения **vardecimal** см. в разделе [Сжатие данных](../../relational-databases/data-compression/data-compression.md).  
  
 При первом присоединении базы данных к новому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или ее восстановлении копия главного ключа базы данных (зашифрованная главным ключом службы) еще не хранится на сервере. Необходимо расшифровать главный ключ базы данных с помощью инструкции **OPEN MASTER KEY**. Как только главный ключ базы данных будет расшифрован, появится возможность разрешить автоматическую расшифровку в будущем с помощью инструкции **ALTER MASTER KEY REGENERATE**, чтобы оставить на сервере копию главного ключа базы данных, зашифрованного с помощью главного ключа службы. После обновления базы данных с переходом от более ранней версии главный ключ базы данных должен быть создан повторно для использования нового алгоритма шифрования AES. Дополнительные сведения о повторном создании главного ключа базы данных см. в статье [ALTER MASTER KEY (Transact-SQL)](../../t-sql/statements/alter-master-key-transact-sql.md). Время, необходимое для повторного создания главного ключа базы данных с обновлением до алгоритма шифрования AES, зависит от числа объектов, защищаемых главным ключом базы данных. Повторное создание главного ключа базы данных с обновлением до алгоритма шифрования AES необходимо произвести только один раз. Это никак не повлияет на последующие операции повторного создания, выполняемые в соответствии со стратегией смены ключей. Дополнительные сведения об обновлении базы данных с помощью присоединения см. в разделе [Обновление базы данных с помощью отсоединения и присоединения (Transact-SQL)](../../relational-databases/databases/upgrade-a-database-using-detach-and-attach-transact-sql.md).  
  
> [!IMPORTANT]  
> Рекомендуется не присоединять базы данных из неизвестных или сомнительных источников. В этих базах данных может содержаться вредоносный код, вызывающий выполнение непредусмотренных инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] или появление ошибок из-за изменения схемы или физической структуры базы данных. Перед тем как использовать базу данных, полученную из неизвестного или ненадежного источника, выполните на тестовом сервере инструкцию [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) для этой базы данных, а также изучите исходный код в базе данных, например хранимые процедуры и другой пользовательский код.  
  
> [!NOTE]  
> Параметры **TRUSTWORTHY** и **DB_CHAINING** не оказывают влияния при присоединении базы данных.  
  
 FOR ATTACH_REBUILD_LOG  
 Указывает, что база данных создана путем присоединения существующего набора файлов операционной системы. Этот параметр применяется только в базах данных, доступных для чтения и записи. Должна существовать запись *\<filespec>*, указывающая первичный файл. Если один или несколько файлов журналов транзакций отсутствуют, то файл журнала перестраивается. Параметр ATTACH_REBUILD_LOG автоматически создает новый файл журнала с размером 1 МБ. Этот файл помещается в местоположение для журнала по умолчанию. Сведения об этом расположении см. в разделе [Просмотр или изменение расположения по умолчанию для файлов данных и журнала (среда SQL Server Management Studio)](../../database-engine/configure-windows/view-or-change-the-default-locations-for-data-and-log-files.md).  
  
> [!NOTE]  
>  Если файлы журналов доступны, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] использует их, не перестраивая файлы журнала.  
  
 Для параметра FOR ATTACH_REBUILD_LOG необходимо следующее:  
  
-   Чистое завершение работы базы данных.  
  
-   Должны быть доступны все файлы данных (MDF и NDF).  
  
> [!IMPORTANT]  
> Эта операция разрывает цепочку резервных копий журнала. Рекомендуется выполнить полное резервное копирование базы данных после завершения операции. Дополнительные сведения см. в разделе [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md).  
  
 Как правило, параметр FOR ATTACH_REBUILD_LOG используется при копировании базы данных, доступной для чтения и записи и обладающей большим журналом, на другой сервер, где копия будет использоваться преимущественно или исключительно для операций чтения. Поэтому для журнала требуется меньше места, чем в случае исходной базы данных.  
  
 Параметр FOR ATTACH_REBUILD_LOG не может указываться для моментального снимка базы данных.  
  
 Дополнительные сведения о присоединении и отсоединении баз данных см. в разделе [Присоединение и отсоединение базы данных (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md).  
  
 \<filespec>  
 Управляет свойствами файла.  
  
 NAME *logical_file_name*  
 Задает логическое имя файла. Параметр NAME требуется при указании параметра FILENAME во всех случаях, кроме указания одного из предложений FOR ATTACH. Файловая группа FILESTREAM не может иметь имя PRIMARY.  
  
 *logical_file_name*  
 Логическое имя, используемое в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при обращении к файлу. Аргумент *logical_file_name* должен быть уникальным в базе данных и соответствовать правилам для [идентификаторов](../../relational-databases/databases/database-identifiers.md). Имя может быть символом или константой Юникода, а также обычным идентификатором или идентификатором с разделителями.  
  
 FILENAME { **'***os_file_name***'** | **'***filestream_path***'** }  
 Задает имя файла в операционной системе (физическое имя).  
  
 **'** *os_file_name* **'**  
 Путь и имя файла, используемые операционной системой при создании файла. Файл должен находиться на одном из следующих устройств: на локальном сервере, где установлен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в сети хранения данных [SAN] или в сети на основе iSCSI. Указанный путь должен существовать до выполнения инструкции CREATE DATABASE. Дополнительные сведения см. в подразделе "Файлы и файловые группы базы данных" раздела "Примечания".  
  
 Параметры SIZE, MAXSIZE и FILEGROWTH доступны, если путь к файлу указан в формате UNC.  
  
 Если файл находится в необработанной секции, аргумент *os_file_name* должен указывать только букву диска существующей необработанной секции. В каждой необработанной секции может быть создан только один файл данных.  
  
 Файлы данных не следует размещать в файловых системах со сжатием, за исключением случаев, когда файлы являются вторичными и доступны только для чтения или вся база данных доступна только для чтения. Файлы журналов ни в коем случае не должны размещаться в сжатых файловых системах.  
  
 **'** *filestream_path* **'**  
 Для файловой группы FILESTREAM параметр FILENAME указывает путь, где будут храниться данные FILESTREAM. Должен существовать путь вплоть до последнего каталога, но последний каталог существовать не должен. Например, если указать путь "C:\MyFiles\MyFilestreamData", папка "C:\MyFiles" должна существовать до запуска инструкции ALTER DATABASE, а папка "MyFilestreamData" — не должна.  
  
 Файловую группу и файл (`<filespec>`) необходимо создавать в одной инструкции.  
  
 Свойства SIZE и FILEGROWTH к файловой группе FILESTREAM неприменимы.  
  
 SIZE *size*  
 Указывает размер файла.  
  
 Параметр SIZE не может указываться, если аргумент *os_file_name* задан как путь в формате UNC. Свойство SIZE к файловой группе FILESTREAM не применяется.  
  
 *size*  
 Задает начальный размер файла.  
  
 Если для первичного файла не задан размер, компонент *size* использует размер первичного файла, указанный в базе данных [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Размер модели по умолчанию — 8 МБ (начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]) или 1 МБ (для более ранних версий). Когда указан вторичный файл данных или журнала, но для этого файла не указан аргумент *size*, [!INCLUDE[ssDE](../../includes/ssde-md.md)] задает размер файла равным 8 МБ (начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]) или 1 МБ (для более ранних версий). Размер, указанный для первичного файла, не должен быть менее размера первичного файла базы данных model.  
  
 Можно использовать суффиксы килобайт (KB), мегабайт (MB), гигабайт (GB) и терабайт (TB). По умолчанию — MБ. Укажите целое число (без дробной части). *size* — целочисленное значение. Для значений, превышающих 2 147 483 647, используйте более крупные единицы измерения.  
  
 MAXSIZE *max_size*  
 Задает максимальный размер, до которого может расти файл. Параметр MAXSIZE не может указываться, если аргумент *os_file_name* задан как путь в формате UNC.  
  
 *max_size*  
 Максимальный размер файла. Можно использовать суффиксы KB, MB, GB и TB. По умолчанию — MБ. Укажите целое число (без дробной части). Если аргумент *max_size* не указан, файл будет увеличиваться до исчерпания свободного пространства на диске. *max_size* — целочисленное значение. Для значений, превышающих 2 147 483 647, используйте более крупные единицы измерения.  
  
 UNLIMITED  
 Указывает, что файл может расти вплоть до заполнения диска. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файл журнала, для которого задано неограниченное увеличение размера, имеет максимальный размер 2 ТБ, а файл данных — 16 ТБ.  
  
> [!NOTE]  
> Ограничения размера отсутствуют, если этот параметр указан для контейнера FILESTREAM. Размер продолжает увеличиваться до полного заполнения диска.  
  
 FILEGROWTH *growth_increment*  
 Задает автоматический шаг роста файла. Значение параметра FILEGROWTH для файла не может превосходить значение параметра MAXSIZE. Параметр FILEGROWTH не может указываться, если аргумент *os_file_name* задан как путь в формате UNC. Свойство FILEGROWTH к файловой группе FILESTREAM не применяется.  
  
 *growth_increment*  
 Объем пространства, добавляемого к файлу каждый раз, когда требуется увеличение пространства.  
  
 Значение может быть указано в килобайтах, мегабайтах, гигабайтах, терабайтах или процентах (%). Если указано число без суффикса MB, KB или %, то по умолчанию используется MB. Если размер указан в процентах (%), то шаг роста — это заданная часть в процентах от размера файла во время этого файла. Указанный размер округляется до ближайших 64 КБ, минимальное значение — 64 КБ.  
  
 Значение 0 указывает, что автоматическое приращение отключено и добавление пространства запрещено.  
  
 Если параметр FILEGROWTH не задан, доступны следующие значения по умолчанию.  
  
|Версия|Значения по умолчанию|  
|-------------|--------------------|  
|Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|Данные — 64 МБ. Файлы журналов — 64 МБ.|  
|Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Данные — 1 МБ. Файлы журналов — 10 %.|  
|До [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Данные — 10 %. Файлы журналов — 10 %.|  
  
 \<filegroup>  
 Управляет свойствами файловой группы. Файловая группа не может указываться для моментального снимка базы данных.  
  
 FILEGROUP *filegroup_name*  
 Логическое имя файловой группы.  
  
 *filegroup_name*  
 Аргумент *filegroup_name* должен быть уникальным в базе данных и не может быть именем PRIMARY или PRIMARY_LOG, предоставленным системой. Имя может быть символом или константой Юникода, а также обычным идентификатором или идентификатором с разделителями. Имя должно соответствовать правилам для [идентификаторов](../../relational-databases/databases/database-identifiers.md).  
  
 CONTAINS FILESTREAM  
 Указывает, что файловая группа хранит большие двоичные объекты (BLOB) FILESTREAM в файловой системе.  
  
 CONTAINS MEMORY_OPTIMIZED_DATA  

**Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Указывает, что файловая группа хранит данные memory_optimized в файловой системе. Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md). В каждой базе данных может присутствовать только одна файловая группа MEMORY_OPTIMIZED_DATA. Примеры кода по созданию файловых групп для хранения оптимизированных для памяти данных см. в разделе [Создание таблиц, оптимизированных для памяти, и хранимых процедур, скомпилированных в собственном коде](../../relational-databases/in-memory-oltp/creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md).  
  
 DEFAULT  
 Задает именованную файловую группу как файловую группу по умолчанию в базе данных.  
  
 *database_snapshot_name*  
 Имя нового моментального снимка базы данных. Имена моментальных снимков баз данных должны быть уникальны внутри экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и соответствовать правилам для идентификаторов. *database_snapshot_name* не может превышать 128 символов.  
  
 ON **(** NAME **=***logical_file_name***,** FILENAME **='***os_file_name***')** [ **,**... *n* ]  
 При создании моментального снимка базы данных указывает список файлов в базе данных-источнике. Для работы моментального снимка все файлы данных должны задаваться отдельно. Однако не разрешается указывать файлы журналов для моментальных снимков базы данных. В моментальных снимках базы данных не поддерживаются файловые группы FILESTREAM. Если файл данных FILESTREAM задействован в предложении CREATE DATABASE ON, выполнение этой инструкции завершится сбоем и приведет к возникновению ошибки.  
  
 Описания параметров NAME и FILENAME и их значений см. в описаниях соответствующих значений \<filespec>.  
  
> [!NOTE]  
> При создании моментального снимка базы данных не разрешается применять другие параметры \<filespec> и ключевое слово PRIMARY.  
  
 AS SNAPSHOT OF *source_database_name*  
 Обозначает, что создаваемая база данных является моментальным снимком базы данных-источника, указанной аргументом *source_database_name*. Моментальный снимок и база данных-источник должны находиться в одном экземпляре.  
  
 Дополнительные сведения см. в подразделе "Моментальные снимки базы данных" раздела "Примечания".  
  
## <a name="remarks"></a>Примечания  
 Резервную копию базы данных [master](../../relational-databases/databases/master-database.md) необходимо создавать каждый раз при создании, изменении или удалении пользовательской базы данных.  
  
 Инструкция CREATE DATABASE должна выполняться в режиме автоматической фиксации (режим управления транзакциями по умолчанию) и не может применяться в явной или неявной транзакции.  
  
 Для создания базы данных и файлов, в которых будет храниться база данных, можно использовать одну инструкцию CREATE DATABASE. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] инструкция CREATE DATABASE реализуется посредством следующих действий:  
  
1.  Компонент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует копию базы данных [model](../../relational-databases/databases/model-database.md) для инициализации базы данных и ее метаданных.  
  
2.  Базе данных назначается идентификатор GUID компонента Service Broker.  
  
3.  Затем компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] заполняет остальную часть базы данных пустыми страницами, за исключением страниц, содержащих внутренние данные с описанием способа использования пространства в базе данных.  
  
 В экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может быть задано не более 32 767 баз данных.  
  
 У каждой базы данных есть владелец, который может выполнять специальные действия в базе данных. Владельцем является пользователь, создавший базу данных. Владельца базы данных можно изменить с помощью процедуры [sp_changedbowner](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md).  

Для обеспечения полной функциональности базы данных некоторые функции базы данных зависят от возможностей файловой системы. Далее приведено несколько примеров функций, зависящих от набора функций файловой системы.
- DBCC CHECKDB
- FileStream
- Оперативное резервное копирование с помощью VSS и моментальных снимков файлов
- Создание моментального снимка базы данных
- Файловая группа данных, оптимизированных для памяти
   
## <a name="database-files-and-filegroups"></a>Файлы и файловые группы базы данных  
 В каждой базе данных имеется по крайней мере два файла (*первичный файл* и *файл журнала транзакций*) и по крайней мере одна файловая группа. Для каждой базы данных может указываться не более 32 767 файлов и 32 767 файловых групп.  
  
 При создании базы данных файлы данных следует делать как можно большего размера в соответствии с максимальным предполагаемым объемом данных в базе данных.  
  
 Для хранения файлов базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] рекомендуется использовать сеть хранения данных (SAN), сеть на основе iSCSI или локально подключенный диск, так как в этой конфигурации достигаются оптимальные производительность и надежность [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="database-snapshots"></a>Моментальные снимки базы данных  
 С помощью инструкции CREATE DATABASE можно создать статическое представление, доступное только для чтения, *моментальный снимок* *базы данных-источника*. Моментальный снимок базы данных согласован с базой данных-источником на уровне транзакций в том виде, в котором она существовала в момент создания моментального снимка. База данных-источник может иметь несколько моментальных снимков.  
  
> [!NOTE]  
> При создании моментального снимка инструкция CREATE DATABASE не может обращаться к файлам журналов, файлам вне сети, восстанавливаемым файлам и несуществующим файлам.  
  
 Если создание моментального снимка базы данных не удается, моментальный снимок помечается как подозрительный и подлежит удалению. Дополнительные сведения см. в разделе [DROP DATABASE (Transact-SQL)](../../t-sql/statements/drop-database-transact-sql.md).  
  
 Каждый моментальный снимок существует до тех пор, пока не будет удален с помощью инструкции DROP DATABASE.  
  
 Дополнительные сведения см. в разделе [Моментальные снимки базы данных (SQL Server)](../../relational-databases/databases/database-snapshots-sql-server.md).  
  
## <a name="database-options"></a>Параметры базы данных  
 Каждый раз при создании базы данных автоматически устанавливаются несколько параметров базы данных. Список параметров см. в статье [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
## <a name="the-model-database-and-creating-new-databases"></a>База данных model и создание новых баз данных  
 Все определяемые пользователем объекты в [базе данных model](../../relational-databases/databases/model-database.md) копируются во вновь создаваемые базы данных. В базу данных model можно добавлять любые объекты, такие как таблицы, представления, хранимые процедуры, типы данных и т. д., которые войдут в состав всех вновь созданных баз данных.  
  
 Если инструкция CREATE DATABASE *database_name* указана без дополнительных параметров размера, то создается первичный файл данных того же размера, что и первичный файл в базе данных model.  
  
 Если не указан параметр FOR ATTACH, то каждая новая база данных наследует значения параметров из базы данных model. Например, параметру автоматического сжатия базы данных задано значение **true** в базе данных model и во всех вновь создаваемых базах данных. Если изменить параметры в базе данных model, то эти новые параметры будут использоваться во вновь создаваемых базах данных. Операции, вносящие изменения в базу данных model, не влияют на существующие базы данных. Если параметр FOR ATTACH задан в инструкции CREATE DATABASE, то новая база данных наследует значения параметров исходной базы данных.  
  
## <a name="viewing-database-information"></a>Просмотр сведений о базе данных  
 Для возврата сведений о базах данных, файлах и файловых группах можно использовать представления каталогов, системные функции и системные хранимые процедуры. Дополнительные сведения см. в разделе [Системные представления (Transact-SQL)](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CREATE DATABASE, CREATE ANY DATABASE или ALTER ANY DATABASE.  
  
 В целях сохранения управления над использованием диска в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]разрешение на создание баз данных обычно предоставляется небольшому числу учетных записей входа.  
  
 В следующем примере предоставляется разрешение на создание базы данных для пользователя Fay базы данных.  
  
```sql  
USE master;  
GO  
GRANT CREATE DATABASE TO [Fay];  
GO  
```  
  
### <a name="permissions-on-data-and-log-files"></a>Разрешения на файлы данных и журналов  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для файлов данных и журналов каждой базы данных заданы некоторые разрешения. Следующие разрешения задаются при применении следующих операций к базе данных:  
  
|||  
|-|-|  
|Создание|Изменение для добавления нового файла|  
|Присоединение|Создание резервной копии|  
|Отсоединение|Восстановление|  
  
 Эти разрешения предотвращают случайное повреждение файлов, хранящихся в каталоге с открытыми разрешениями.  
  
> [!NOTE]  
> [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] не задает разрешения на файлы данных и файлы журнала.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-database-without-specifying-files"></a>A. Создание базы данных без указания файлов  
 В следующем примере создается база данных `mytest` и соответствующие первичный файл и файл журнала транзакций. Поскольку инструкция не включает элементы \<filespec>, первичный файл базы данных имеет тот же размер, что и первичный файл базы данных model. Размер журнала транзакций устанавливается как наибольшее из следующих значений: 512 КБ или 25 % размера первичного файла данных. Поскольку параметр MAXSIZE не задан, файлы могут увеличиваться до заполнения всего свободного места на диске. Этот пример также демонстрирует, как удалить базу данных `mytest`, если она существует, перед созданием базы данных `mytest`.  
  
```sql  
USE master;  
GO  
IF DB_ID (N'mytest') IS NOT NULL
DROP DATABASE mytest;
GO
CREATE DATABASE mytest;  
GO  
-- Verify the database files and sizes  
SELECT name, size, size*1.0/128 AS [Size in MBs]   
FROM sys.master_files  
WHERE name = N'mytest';  
GO  
```  
  
### <a name="b-creating-a-database-that-specifies-the-data-and-transaction-log-files"></a>Б. Создание базы данных, в которой заданы файлы данных и журнала транзакций  
 В следующем примере создается база данных `Sales`. Ключевое слово PRIMARY не использовано, поэтому первый файл (`Sales_dat`) становится первичным файлом. Поскольку в параметре SIZE для файла `Sales_dat` не заданы суффиксы MB и KB, используется значение MB и пространство выделяется в мегабайтах. Резервная копия базы данных `Sales_log` выделена в мегабайтах, потому что суффикс `MB` явно указан в параметре `SIZE`.  
  
```sql  
USE master;  
GO  
CREATE DATABASE Sales  
ON   
( NAME = Sales_dat,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\saledat.mdf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 )  
LOG ON  
( NAME = Sales_log,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\salelog.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 25MB,  
    FILEGROWTH = 5MB ) ;  
GO  
```  
  
### <a name="c-creating-a-database-by-specifying-multiple-data-and-transaction-log-files"></a>В. Создание базы данных, в которой указаны несколько файлов данных и журналов транзакций  
 Следующий пример создает базу данных `Archive`, имеющую 3 файла данных объемом по `100-MB` каждый и два файла журнала транзакций по `100-MB`. Первичный файл является первым файлом в списке и явно задан ключевым словом `PRIMARY`. Файлы журналов транзакций заданы следующими ключевыми словами `LOG ON`. Обратите внимание на расширения, используемые для файлов в параметре `FILENAME`: `.mdf` для первичных файлов данных, `.ndf` для вторичных файлов данных и `.ldf` для файлов журнала транзакций. В этом примере база данных размещается на диске `D:`, а не вместе с базой данных `master`.  
  
```sql  
USE master;  
GO  
CREATE DATABASE Archive   
ON  
PRIMARY    
    (NAME = Arch1,  
    FILENAME = 'D:\SalesData\archdat1.mdf',  
    SIZE = 100MB,  
    MAXSIZE = 200,  
    FILEGROWTH = 20),  
    ( NAME = Arch2,  
    FILENAME = 'D:\SalesData\archdat2.ndf',  
    SIZE = 100MB,  
    MAXSIZE = 200,  
    FILEGROWTH = 20),  
    ( NAME = Arch3,  
    FILENAME = 'D:\SalesData\archdat3.ndf',  
    SIZE = 100MB,  
    MAXSIZE = 200,  
    FILEGROWTH = 20)  
LOG ON   
   (NAME = Archlog1,  
    FILENAME = 'D:\SalesData\archlog1.ldf',  
    SIZE = 100MB,  
    MAXSIZE = 200,  
    FILEGROWTH = 20),  
   (NAME = Archlog2,  
    FILENAME = 'D:\SalesData\archlog2.ldf',  
    SIZE = 100MB,  
    MAXSIZE = 200,  
    FILEGROWTH = 20) ;  
GO  
```  
  
### <a name="d-creating-a-database-that-has-filegroups"></a>Г. Создание базы данных с файловыми группами  
 В следующем примере создается база данных `Sales`, в которой есть следующие файловые группы:  
  
-   Первичная файловая группа с файлами `Spri1_dat` и `Spri2_dat`. Для этих файлов задана величина приращения FILEGROWTH, равная `15%`.  
  
-   Файловая группа с именем `SalesGroup1` и файлами `SGrp1Fi1` и `SGrp1Fi2`.  
  
-   Файловая группа с именем `SalesGroup2` и файлами `SGrp2Fi1` и `SGrp2Fi2`.  
  
 В этом примере файлы данных и журналов размещаются на различных дисках с целью повышения производительности.  
  
```sql  
USE master;  
GO  
CREATE DATABASE Sales  
ON PRIMARY  
( NAME = SPri1_dat,  
    FILENAME = 'D:\SalesData\SPri1dat.mdf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 15% ),  
( NAME = SPri2_dat,  
    FILENAME = 'D:\SalesData\SPri2dt.ndf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 15% ),  
FILEGROUP SalesGroup1  
( NAME = SGrp1Fi1_dat,  
    FILENAME = 'D:\SalesData\SG1Fi1dt.ndf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 ),  
( NAME = SGrp1Fi2_dat,  
    FILENAME = 'D:\SalesData\SG1Fi2dt.ndf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 ),  
FILEGROUP SalesGroup2  
( NAME = SGrp2Fi1_dat,  
    FILENAME = 'D:\SalesData\SG2Fi1dt.ndf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 ),  
( NAME = SGrp2Fi2_dat,  
    FILENAME = 'D:\SalesData\SG2Fi2dt.ndf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 )  
LOG ON  
( NAME = Sales_log,  
    FILENAME = 'E:\SalesLog\salelog.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 25MB,  
    FILEGROWTH = 5MB ) ;  
GO  
```  
  
### <a name="e-attaching-a-database"></a>Д. Присоединение базы данных  
 В следующем примере база данных `Archive`, созданная в примере Е, отсоединяется, а затем присоединяется с помощью предложения `FOR ATTACH`. База данных `Archive` была определена с несколькими файлами данных и журналов. Однако поскольку местоположение файлов не изменилось со времени их создания, в предложении `FOR ATTACH` должен быть задан только первичный файл. Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] любые полнотекстовые файлы, являющиеся частью присоединяемой базы данных, будут присоединены вместе с базой данных.  
  
```sql  
USE master;  
GO  
sp_detach_db Archive;  
GO  
CREATE DATABASE Archive  
      ON (FILENAME = 'D:\SalesData\archdat1.mdf')   
      FOR ATTACH ;  
GO  
```  
  
### <a name="f-creating-a-database-snapshot"></a>Е. Создание моментального снимка базы данных  
 В следующем примере создается моментальный снимок базы данных `sales_snapshot0600`. Моментальный снимок базы данных предназначен только для чтения, поэтому нельзя задать файл журнала. В соответствии с синтаксисом задается каждый файл базы данных-источника, а файловые группы не указываются.  
  
 База данных-источник для этого примера — `Sales`, созданная в примере Г.  
  
```sql  
USE master;  
GO  
CREATE DATABASE sales_snapshot0600 ON  
    ( NAME = SPri1_dat, FILENAME = 'D:\SalesData\SPri1dat_0600.ss'),  
    ( NAME = SPri2_dat, FILENAME = 'D:\SalesData\SPri2dt_0600.ss'),  
    ( NAME = SGrp1Fi1_dat, FILENAME = 'D:\SalesData\SG1Fi1dt_0600.ss'),  
    ( NAME = SGrp1Fi2_dat, FILENAME = 'D:\SalesData\SG1Fi2dt_0600.ss'),  
    ( NAME = SGrp2Fi1_dat, FILENAME = 'D:\SalesData\SG2Fi1dt_0600.ss'),  
    ( NAME = SGrp2Fi2_dat, FILENAME = 'D:\SalesData\SG2Fi2dt_0600.ss')  
AS SNAPSHOT OF Sales ;  
GO  
```  
  
### <a name="g-creating-a-database-and-specifying-a-collation-name-and-options"></a>Ж. Создание базы данных и назначение имени и параметров сортировки  
 В следующем примере создается база данных `MyOptionsTest`. Указано имя параметров сортировки, а параметрам `TRUSTYWORTHY` и `DB_CHAINING` присвоено значение `ON`.  
  
```sql  
USE master;  
GO  
IF DB_ID (N'MyOptionsTest') IS NOT NULL  
DROP DATABASE MyOptionsTest;  
GO  
CREATE DATABASE MyOptionsTest  
COLLATE French_CI_AI  
WITH TRUSTWORTHY ON, DB_CHAINING ON;  
GO  
--Verifying collation and option settings.  
SELECT name, collation_name, is_trustworthy_on, is_db_chaining_on  
FROM sys.databases  
WHERE name = N'MyOptionsTest';  
GO  
```  
  
### <a name="h-attaching-a-full-text-catalog-that-has-been-moved"></a>З. Присоединение перемещенного полнотекстового каталога  
 В следующем примере показано, как присоединить полнотекстовый каталог `AdvWksFtCat` наряду с файлами данных и журнала `AdventureWorks2012`. В этом примере полнотекстовый каталог перемещается из расположения по умолчанию в новое расположение `c:\myFTCatalogs`. Файлы данных и журналов остаются в расположениях по умолчанию.  
  
```sql  
USE master;  
GO  
--Detach the AdventureWorks2012 database  
sp_detach_db AdventureWorks2012;  
GO  
-- Physically move the full text catalog to the new location.  
--Attach the AdventureWorks2012 database and specify the new location of the full-text catalog.  
CREATE DATABASE AdventureWorks2012 ON   
    (FILENAME = 'c:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\AdventureWorks2012_data.mdf'),   
    (FILENAME = 'c:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\AdventureWorks2012_log.ldf'),  
    (FILENAME = 'c:\myFTCatalogs\AdvWksFtCat')  
FOR ATTACH;  
GO  
```  
  
### <a name="i-creating-a-database-that-specifies-a-row-filegroup-and-two-filestream-filegroups"></a>И. Создание базы данных, имеющей файловую группу строк и две файловые группы FILESTREAM  
 В следующем примере создается база данных `FileStreamDB`. Эта база данных создается с одной файловой группой строк и двумя файловыми группами FILESTREAM. Каждая файловая группа содержит один файл.  
  
-   Группа `FileStreamDB_data` содержит данные строк. В нее входит один файл `FileStreamDB_data.mdf`, расположенный в пути по умолчанию.  
  
-   Группа `FileStreamPhotos` содержит данные FILESTREAM. В нее входит два контейнера данных FILESTREAM, `FSPhotos`, расположенный в папке `C:\MyFSfolder\Photos`, и `FSPhotos2`, расположенный в папке `D:\MyFSfolder\Photos`. Она отмечена как файловая группа FILESTREAM по умолчанию.  
  
-   Группа `FileStreamResumes` содержит данные FILESTREAM. Она содержит один контейнер данных FILESTREAM — `FSResumes`, расположенный в папке `C:\MyFSfolder\Resumes`.  
  
```sql  
USE master;  
GO  
-- Get the SQL Server data path.  
DECLARE @data_path nvarchar(256);  
SET @data_path = (SELECT SUBSTRING(physical_name, 1, CHARINDEX(N'master.mdf', LOWER(physical_name)) - 1)  
                  FROM master.sys.master_files  
                  WHERE database_id = 1 AND file_id = 1);  
  
 -- Execute the CREATE DATABASE statement.   
EXECUTE ('CREATE DATABASE FileStreamDB  
ON PRIMARY   
    (  
    NAME = FileStreamDB_data   
    ,FILENAME = ''' + @data_path + 'FileStreamDB_data.mdf''  
    ,SIZE = 10MB  
    ,MAXSIZE = 50MB  
    ,FILEGROWTH = 15%  
    ),  
FILEGROUP FileStreamPhotos CONTAINS FILESTREAM DEFAULT  
    (  
    NAME = FSPhotos  
    ,FILENAME = ''C:\MyFSfolder\Photos''  
-- SIZE and FILEGROWTH should not be specified here.  
-- If they are specified an error will be raised.  
, MAXSIZE = 5000 MB  
    ),  
    (  
      NAME = FSPhotos2  
      , FILENAME = ''D:\MyFSfolder\Photos''  
      , MAXSIZE = 10000 MB  
     ),  
FILEGROUP FileStreamResumes CONTAINS FILESTREAM  
    (  
    NAME = FileStreamResumes  
    ,FILENAME = ''C:\MyFSfolder\Resumes''  
    )   
LOG ON  
    (  
    NAME = FileStream_log  
    ,FILENAME = ''' + @data_path + 'FileStreamDB_log.ldf''  
    ,SIZE = 5MB  
    ,MAXSIZE = 25MB  
    ,FILEGROWTH = 5MB  
    )'  
);  
GO  
```  
  
### <a name="j-creating-a-database-that-has-a-filestream-filegroup-with-multiple-files"></a>К. Создание базы данных, имеющей файловую группу FILESTREAM с несколькими файлами  
 В следующем примере создается база данных `BlobStore1`. Эта база данных создается с одной файловой группой строк и одной файловой группой FILESTREAM, `FS`. Файловая группа FILESTREAM содержит два файла, `FS1` и `FS2`. Затем выполняется изменение базы данных путем добавления третьего файла, `FS3`, в файловую группу FILESTREAM.  
  
```sql  
USE master;  
GO  
  
CREATE DATABASE [BlobStore1]  
CONTAINMENT = NONE  
ON PRIMARY   
(   
    NAME = N'BlobStore1',   
    FILENAME = N'C:\BlobStore\BlobStore1.mdf',  
    SIZE = 100MB,  
    MAXSIZE = UNLIMITED,  
    FILEGROWTH = 1MB  
),   
FILEGROUP [FS] CONTAINS FILESTREAM DEFAULT   
(  
    NAME = N'FS1',  
    FILENAME = N'C:\BlobStore\FS1',  
    MAXSIZE = UNLIMITED  
),   
(  
    NAME = N'FS2',  
    FILENAME = N'C:\BlobStore\FS2',  
    MAXSIZE = 100MB  
)  
LOG ON   
(  
    NAME = N'BlobStore1_log',  
    FILENAME = N'C:\BlobStore\BlobStore1_log.ldf',  
    SIZE = 100MB,  
    MAXSIZE = 1GB,  
    FILEGROWTH = 1MB  
);  
GO  
  
ALTER DATABASE [BlobStore1]  
ADD FILE  
(  
    NAME = N'FS3',  
    FILENAME = N'C:\BlobStore\FS3',  
    MAXSIZE = 100MB  
)  
TO FILEGROUP [FS];  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [Присоединение и отсоединение базы данных (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [DROP DATABASE (Transact-SQL)](../../t-sql/statements/drop-database-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_changedbowner (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)   
 [sp_detach_db (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)   
 [sp_removedbreplication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md)   
 [Моментальные снимки базы данных (SQL Server)](../../relational-databases/databases/database-snapshots-sql-server.md)   
 [Перемещение файлов базы данных](../../relational-databases/databases/move-database-files.md)   
 [Базы данных](../../relational-databases/databases/databases.md)   
 [Данные большого двоичного объекта (SQL Server)](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)  

::: moniker-end
::: moniker range="=azuresqldb-current||=sqlallproducts-allversions"

> [!div class="mx-tdCol2BreakAll"]
> <table>
> <tr>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
> </tr>
> <tr>
>   <th><a href="create-database-transact-sql.md?view=sql-server-2016">SQL Server</a></th>
>   <th><strong><em>* База данных SQL<br />Базы данных SQL*</em></strong></th>
>   <th><a href="create-database-transact-sql.md?view=azuresqldb-mi-current">База данных SQL<br />Базы данных SQL</a></th>
>   <th><a href="create-database-transact-sql.md?view=azure-sqldw-latest">Хранилище данных<br />SQL</a></th>
>   <th><a href="create-database-transact-sql.md?view=aps-pdw-2016">SQL Parallel<br />Data Warehouse</a></th>
> </tr>
> </table>

&nbsp;

# <a name="azure-sql-database-logical-server"></a>Логический сервер Базы данных SQL Azure

## <a name="overview"></a>Обзор

На логическом сервере базы данных SQL Azure этот оператор можно применить к серверу Azure SQL для создания отдельной базы данных или базы данных в эластичном пуле. При использовании оператора нужно указать имя базы данных, параметры сортировки, максимальный размер, выпуск, цель обслуживания, и, если это применимо, эластичный пул для новой базы данных. Также он позволяет создать базу данных в эластичном пуле. Кроме того, с его помощью можно создать копию базы данных на другом логическом сервере.

## <a name="syntax"></a>Синтаксис 

### <a name="create-a-database"></a>Создание базы данных
```  
CREATE DATABASE database_name [ COLLATE collation_name ]  
{  
   (<edition_options> [, ...n]) 
}  
[ WITH CATALOG_COLLATION = { DATABASE_DEFAULT | SQL_Latin1_General_CP1_CI_AS }  ]
[;] 
  
<edition_options> ::= 
{  

  MAXSIZE = { 100 MB | 250 MB | 500 MB | 1 … 1024 … 4096 GB }  
  | ( EDITION = {  'basic' | 'standard' | 'premium' | 'GeneralPurpose' | 'BusinessCritical' } 
  | SERVICE_OBJECTIVE = 
    {  'basic' | 'S0' | 'S1' | 'S2' | 'S3' | 'S4'| 'S6'| 'S7'| 'S9'| 'S12' | 
      | 'P1' | 'P2' | 'P4'| 'P6' | 'P11'  | 'P15'  
      | 'GP_GEN4_1' | 'GP_GEN4_2' | 'GP_GEN4_4' | 'GP_GEN4_8' | 'GP_GEN4_16' | 'GP_GEN4_24' |
      | 'BC_GEN4_1' | 'BC_GEN4_2' | 'BC_GEN4_4' | 'BC_GEN4_8' | 'BC_GEN4_16' | 'BC_GEN4_24' |
      | 'GP_GEN5_2' | 'GP_GEN5_4' | 'GP_GEN5_8' | 'GP_GEN5_16' | 'GP_GEN5_24' | 'GP_GEN5_32' | 'GP_GEN5_48' | 'GP_GEN5_80' |
      | 'BC_GEN5_2' | 'BC_GEN5_4' | 'BC_GEN5_8' | 'BC_GEN5_16' | 'BC_GEN5_24' | 'BC_GEN5_32' | 'BC_GEN5_48' | 'BC_GEN5_80' |
      | { ELASTIC_POOL(name = <elastic_pool_name>) } }  ) 
}
```  

### <a name="copy-a-database"></a>Копирование базы данных

```
CREATE DATABASE database_name  
    AS COPY OF [source_server_name.] source_database_name  
    [ ( SERVICE_OBJECTIVE = 
      {  'basic' | 'S0' | 'S1' | 'S2' | 'S3' | 'S4'| 'S6'| 'S7'| 'S9'| 'S12' |  
      | 'GP_GEN4_1' | 'GP_GEN4_2' | 'GP_GEN4_4' | 'GP_GEN4_8' | 'GP_GEN4_16' | 'GP_GEN4_24' |
      | 'BC_GEN4_1' | 'BC_GEN4_2' | 'BC_GEN4_4' | 'BC_GEN4_8' | 'BC_GEN4_16' | 'BC_GEN4_24' |
      | 'GP_GEN5_2' | 'GP_GEN5_4' | 'GP_GEN5_8' | 'GP_GEN5_16' | 'GP_GEN5_24' | 'GP_GEN5_32' | 'GP_GEN5_48' | 'GP_GEN5_80' |
      | 'BC_GEN5_2' | 'BC_GEN5_4' | 'BC_GEN5_8' | 'BC_GEN5_16' | 'BC_GEN5_24' | 'BC_GEN5_32' | 'BC_GEN5_48' | 'BC_GEN5_80' |
        | { ELASTIC_POOL(name = <elastic_pool_name>) } } )  
   ]  
[;] 
```  

## <a name="arguments"></a>Аргументы  
  
*database_name* 
 
Имя новой базы данных. Имя должно быть уникальным в пределах SQL Server и соответствовать правилам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для идентификаторов. Дополнительные сведения: [Идентификаторы](http://go.microsoft.com/fwlink/p/?LinkId=180386).  
  
*Collation_name*  

Задает параметры сортировки по умолчанию для базы данных. Именем параметров сортировки может быть либо имя параметров сортировки Windows, либо имя параметров сортировки SQL. Если параметры не указаны, база данных использует параметры сортировки по умолчанию: SQL_Latin1_General_CP1_CI_AS.  
  
Дополнительные сведения об именах параметров сортировки Windows и SQL: [COLLATE (Transact-SQL)](http://msdn.microsoft.com/library/ms184391.aspx).  
  
CATALOG_COLLATION  

Задает параметры сортировки по умолчанию для каталога метаданных. *DATABASE_DEFAULT* указывает, что каталог метаданных, используемый для системных представлений и таблиц, должен быть сопоставлен параметрам сортировки по умолчанию для базы данных.  Так происходит в SQL Server. 

*SQL_Latin1_General_CP1_CI_AS* указывает, что каталог метаданных, используемый для системных представлений и таблиц, должен быть сопоставлен фиксированным параметрам сортировки SQL_Latin1_General_CP1_CI_AS.  Это параметр используется в базе данных SQL Azure по умолчанию, если никакое иное значение не указано.

EDITION
 
Указывает уровень службы базы данных. 

- Отдельная или включенная в пул база данных на логическом сервере. Доступные значения: "basic", "standard", "premium", "GeneralPurpose" и "BusinessCritical". Поддержка "premiumrs" была упразднена. При возникновении вопросов пишите на следующий адрес premium-rs@microsoft.com.
- Базы данных в Управляемом экземпляре: доступное значение — GeneralPurpose.
  
Если параметр EDITION задан, а MAXSIZE нет, то параметру MAXSIZE задается самое ограничивающее значение, поддерживаемое этим выпуском.  
  
MAXSIZE

Указывает максимальный размер базы данных. Значение параметра MAXSIZE должно быть допустимо для указанного значения параметра EDITION (уровень службы). Далее приведены поддерживаемые значения MAXSIZE и значения по умолчанию (D) для уровней службы.

**Модель на основе DTU для отдельных или включенных в пул баз данных на логическом сервере**

|**MAXSIZE**|**Basic**|**S0–S2**|**S3–S12**|**P1–P6**| **P11–P15** | 
|-----------------|---------------|------------------|-----------------|-----------------|-----------------|-----------------| 
|100 МБ|√|√|√|√|√|  
|250 МБ|√|√|√|√|√|
|500 МБ|√|√|√|√|√|
|1 ГБ|√|√|√|√|√|
|2 ГБ|√ (D)|√|√|√|√|
|5 ГБ|Недоступно|√|√|√|√|
|10 ГБ|Недоступно|√|√|√|√|
|20 ГБ|Недоступно|√|√|√|√|
|30 ГБ|Недоступно|√|√|√|√|
|40 ГБ|Недоступно|√|√|√|√|
|50 ГБ|Недоступно|√|√|√|√|
|100 ГБ|Недоступно|√|√|√|√|
|150 ГБ|Недоступно|√|√|√|√|
|200 ГБ|Недоступно|√|√|√|√|
|250 ГБ|Недоступно|√ (D)|√ (D)|√|√|
|300 ГБ|Недоступно|Недоступно|√|√|√|
|400 ГБ|Недоступно|Недоступно|√|√|√|
|500 ГБ|Недоступно|Недоступно|√|√ (D)|√|
|750 ГБ|Недоступно|Недоступно|√|√|√|
|1024 ГБ|Недоступно|Недоступно|√|√|√ (D)|
|От 1024 до 4096 ГБ с шагом приращения 256 ГБ * |Недоступно|Недоступно|Недоступно|Недоступно|√|√|  
  
\* P11 и P15 позволяют задавать параметру MAXSIZE значение до 4 ТБ, при этом размер по умолчанию — 1024 ГБ.  P11 и P15 могут использовать до 4 ТБ включенного объема хранилища без дополнительной платы. На уровне Premium использование MAXSIZE со значением более 1 ТБ сейчас доступно в следующих регионах: восточная часть США 2, западная часть США, Виргиния (для обслуживания государственных организаций США), Западная Европа, Центральная Германия, Юго-Восточная Азия, Восточная Япония, Восточная Австралия, Центральная Канада и Восточная Канада. Дополнительные сведения об ограничениях по ресурсам для модели на основе DTU см. в разделе [Пределы для ресурсов на основе DTU](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits).  

Значение MAXSIZE для модели на основе DTU, если оно задано, должно быть одним из допустимых значений, приведенных в таблице выше для указанного уровня служб.
 
**Модель на основе виртуальных ядер для отдельных или включенных в пул баз данных на логическом сервере**

**Уровень обслуживания общего назначения — вычислительная платформа поколения 4**
|MAXSIZE|GP_Gen4_1|GP_Gen4_2|GP_Gen4_4|GP_Gen4_8|GP_Gen4_16|GP4_24|
|:--- | --: |--: |--: |--: |--: |--:|
|Максимальный размер данных (ГБ)|1024|1024|1536|3072|4096|4096|

**Уровень обслуживания общего назначения — вычислительная платформа поколения 5**
|MAXSIZE|GP_Gen5_2|GP_Gen5_4|GP_Gen5_8|GP_Gen5_16|GP_Gen5_24|GP_Gen5_32|GP_Gen5_48|GP_Gen5_80|
|:----- | ------: |-------: |-------: |--------: |--------: |---------:|--------: |---------: |
|Максимальный размер данных (ГБ)|1024|1024|1536|3072|4096|4096|4096|4096|

**Уровень обслуживания "Критически важный для бизнеса" — вычислительная платформа поколения 4**
|Уровень производительности|BC_Gen4_1|BC_Gen4_2|BC_Gen4_4|BC_Gen4_8|BC_Gen4_16|
|:--- | --: |--: |--: |--: |--: |--: |
|Максимальный размер данных (ГБ)|1024|1024|1024|1024|1024|1024|

**Уровень обслуживания "Критически важный для бизнеса" — вычислительная платформа поколения 5**
|MAXSIZE|BC_Gen5_2|BC_Gen5_4|BC_Gen5_8|BC_Gen5_16|BC_Gen5_24|BC_Gen5_32|BC_Gen5_48|BC_Gen5_80|
|:----- | ------: |-------: |-------: |--------: |--------: |---------:|--------: |---------: |
|Максимальный размер данных (ГБ)|1024|1024|1024|1024|2048|4096|4096|4096|

Если при использовании модели виртуальных ядер значение `MAXSIZE` не задано, используется значение по умолчанию, равное 32 ГБ. Дополнительные сведения об ограничениях по ресурсам для модели на основе виртуальных ядер см. в разделе [Пределы для ресурсов на основе виртуальных ядер](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits).
  
**Модель на основе виртуальных ядер для баз данных в Управляемом экземпляре**

**Уровень обслуживания общего назначения — вычислительная платформа поколения 4**
|MAXSIZE|GP_Gen4_8|GP_Gen4_16|GP4_24|
|:--- | --: |--: |
|Максимальный размер данных (ТБ)|8|8|8|

**Уровень обслуживания общего назначения — вычислительная платформа поколения 5**
|MAXSIZE|GP_Gen5_8|GP_Gen5_16|GP_Gen5_24|GP_Gen5_32|GP_Gen5_40|
|:----- | ------: |-------: |-------: |--------: |--------: |---------:|
|Максимальный размер данных (ТБ)|8|8|8|8|8|

Следующие правила применяются к аргументам MAXSIZE и EDITION:  
- Если параметр EDITION указан, а параметр MAXSIZE — нет, то в качестве выпуска будет использоваться значение по умолчанию. Например, если параметру EDITION задано значение Standard, а параметру MAXSIZE значение не задано, MAXSIZE автоматически получает значение 250 МБ.  
- Если не указаны значения ни для MAXSIZE, ни для EDITION, то параметру EDITION задается значение Standard (S0), а параметру MAXSIZE — 250 ГБ.  

SERVICE_OBJECTIVE

- **Для отдельных или включенных в пул баз данных на логическом сервере**

  Определяет уровень производительности. Доступные значения для целевого уровня обслуживания: `S0`, `S1`, `S2`, `S3`, `S4`, `S6`, `S7`, `S9`, `S12`, `P1`, `P2`, `P4`, `P6`, `P11`, `P15`, `GP_GEN4_1`, `GP_GEN4_2`, `GP_GEN4_4`, `GP_GEN4_8`, `GP_GEN4_16`, `GP_GEN4_24`, `BC_GEN4_1` `BC_GEN4_2` `BC_GEN4_4` `BC_GEN4_8` `BC_GEN4_16`, `BC_GEN4_24`, `GP_Gen5_2`, `GP_Gen5_4`, `GP_Gen5_8`, `GP_Gen5_16`, `GP_Gen5_24`, `GP_Gen5_32`, `GP_Gen5_48`, `GP_Gen5_80`, `BC_Gen5_2`, `BC_Gen5_4`, `BC_Gen5_8`, `BC_Gen5_16`, `BC_Gen5_24`, `BC_Gen5_32`, `BC_Gen5_48` и `BC_Gen5_80`. 

- **Для баз данных в Управляемом экземпляре**

  Определяет уровень производительности. Доступные значения для целевого уровня обслуживания: `GP_GEN4_8`, `GP_GEN4_16`, `GP_Gen5_8`, `GP_Gen5_16`, `GP_Gen5_24`, `GP_Gen5_32` и `GP_Gen5_40`. 

Дополнительные сведения об описании целях служб и о размере, выпусках и комбинациях целей служб см. в разделе [Уровни служб базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-service-tiers). Если указанное значение SERVICE_OBJECTIVE не поддерживается для значения EDITION, вы получите сообщение об ошибке. Чтобы изменить значение SERVICE_OBJECTIVE с одного уровня на другой (например, с S1 на P1), необходимо также изменить значение EDITION. Описания целей служб и дополнительные сведения о сочетаниях размеров, выпусков и целей служб см. в разделах [Уровни служб и уровни производительности баз данных SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/), [Пределы для ресурсов на основе DTU](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits) и [Пределы для ресурсов на основе виртуальных ядер](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits).  Поддержка целей служб PRS была удалена. При возникновении вопросов пишите на следующий адрес premium-rs@microsoft.com. 
  
ELASTIC_POOL (name = \<имя_эластичного_пула>)
 
**Применимо к:** только отдельная или включенная в пул база данных.

Чтобы создать базу данных в эластичном пуле, задайте для параметра SERVICE_OBJECTIVE базы данных значение ELASTIC_POOL и укажите имя пула. Дополнительные сведения: [Управление несколькими базами данных SQL Azure и их масштабирование с помощью эластичных пулов](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/).  
  
AS COPY OF [имя_исходного_сервера.]имя_исходной_базы

**Применимо к:** только отдельная или включенная в пул база данных.

Для копирования базы данных на тот же или другой сервер [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
*<имя_исходного_сервера>*  

Имя сервера [!INCLUDE[ssSDS](../../includes/sssds-md.md)], на котором размещена база данных-источник. Этот параметр не является обязательным, если исходная и конечная базы данных расположены на одном сервере [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
> [!NOTE]
> Аргумент `AS COPY OF` не поддерживает уникальные полные доменные имена. Другими словами, если полное доменное имя сервера —`serverName.database.windows.net`, во время копирования базы данных используйте только `serverName`.  
  
*<имя_исходной_базы>*

Имя копируемой базы данных.  
  
## <a name="remarks"></a>Remarks
 
Базы данных в [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] используют несколько параметров по умолчанию, устанавливаемых при создании базы данных. Дополнительные сведения об этих параметрах по умолчанию см. в списке значений в разделе [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md).  
  
Параметр MAXSIZE позволяет ограничить размер базы данных. Если размер базы данных достигает ее значения MAXSIZE, выдается ошибка с кодом 40544. В этом случае данные нельзя вставить или обновить данные и создать новые объекты (например, таблицы, представления, хранимые процедуры и функции). Однако можно по-прежнему читать и удалять данные, усекать и удалять таблицы и индексы, а также выполнять перестроение индексов. Затем можно изменить значение MAXSIZE на значение, превышающее текущий размер базы данных, или удалить некоторые данные, чтобы освободить место в хранилище. Перед возобновлением возможности вставлять новые данные может пройти до 15 минут.  
  
> [!IMPORTANT]  
>  Инструкция `CREATE DATABASE` должна быть единственной инструкцией в пакете [!INCLUDE[tsql](../../includes/tsql-md.md)]. 
  
Используйте [ALTER DATABASE &#40;База данных SQL Azure&#41;](../../t-sql/statements/alter-database-transact-sql.md?&tabs=sqldbls), чтобы в дальнейшем изменять значения размера, выпуска или целевого уровня службы.  

Аргумент CATALOG_COLLATION доступен только во время создания базы данных. 
  
## <a name="database-copies"></a>Копирование баз данных  

**Применимо к:** только отдельная или включенная в пул база данных.

Копирование базы данных с помощью инструкции `CREATE DATABASE` — это асинхронная операция. Поэтому соединение с сервером [!INCLUDE[ssSDS](../../includes/sssds-md.md)] не требуется в течение всего процесса копирования. Инструкция `CREATE DATABASE` возвращает управление пользователю после создания записи в sys.databases, но до завершения операции копирования базы данных. Другими словами, инструкция `CREATE DATABASE` возвращает контроль, когда база данных все еще копируется.  
  
- Наблюдение за процессом копирования на сервере [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]: запросите столбцы `percentage_complete` или `replication_state_desc` в [dm_database_copies](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md) или столбец `state` в представлении **sys.databases**. Вы также можете использовать представление [sys.dm_operation_status](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md), так как оно возвращает состояние операций с базой данных, включая ее копирование.  
  
После успешного завершения копирования целевая база данных транзакционно согласована с базой данных-источником.  
  
К аргументу `AS COPY OF` применяются следующие синтаксические и семантические правила.  
  
- Имя исходного и целевого сервера для копирования могут совпадать или отличаться. Если они совпадают, этот параметр не является обязательным, а по умолчанию используется контекст сервера текущего сеанса.  
  
- Необходимо указать имена исходной и целевой базы данных. Они должны быть уникальными и соответствовать правилам для идентификаторов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения: [Идентификаторы](http://go.microsoft.com/fwlink/p/?LinkId=180386).  
  
- Инструкция `CREATE DATABASE` должна выполняться в контексте базы данных master на сервере [!INCLUDE[ssSDS](../../includes/sssds-md.md)], на котором будет создана новая база данных. 
- После завершения копирования целевой базой данных необходимо управлять как независимой базой данных. Инструкции `ALTER DATABASE` и `DROP DATABASE` для новой базы данных можно выполнять независимо от базы данных-источника. Новую базу данных также можно скопировать в другую новую базу данных.  
  
- Пока выполняется копирование базы данных, база данных-источник остается доступной.  
  
 Дополнительные сведения: [Копирование базы данных SQL Azure с использованием Transact-SQL](https://azure.microsoft.com/documentation/articles/sql-database-copy-transact-sql/).  
  
## <a name="permissions"></a>Разрешения  
Создавать базу данных могут следующие пользователи: 
  
- Субъект серверного уровня  
  
- Администратор Azure AD для локального сервера SQL Server Azure  
- Участник роли базы данных `dbmanager`    
**Дополнительные требования по использованию синтаксиса `CREATE DATABASE ... AS COPY OF`:** пользователь, запускающий инструкцию на локальном сервере, должен также иметь как минимум роль `db_owner` на исходном сервере. Если вход основан на проверке подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то запускающий инструкцию на локальном сервере пользователь должен также существовать на исходном сервере [!INCLUDE[ssSDS](../../includes/sssds-md.md)] с идентичным именем для входа и паролем.  
  
## <a name="examples"></a>Примеры
  
### <a name="simple-example"></a>Простой пример  
 Простой пример создания базы данных.  
  
```sql  
CREATE DATABASE TestDB1;  
```  
  
### <a name="simple-example-with-edition"></a>Простой пример с указанием выпуска  
 Простой пример создания базы данных Standard.  
  
```sql  
CREATE DATABASE TestDB2  
( EDITION = 'GeneralPurpose' );  
```  
  
### <a name="example-with-additional-options"></a>Пример с дополнительными параметрами  
 Пример, где используются несколько параметров.  
  
```sql  
CREATE DATABASE hito 
COLLATE Japanese_Bushu_Kakusu_100_CS_AS_KS_WS 
( MAXSIZE = 500 MB, EDITION = 'GeneralPurpose', SERVICE_OBJECTIVE = 'GP_GEN4_8' ) ;  
```  
  
### <a name="creating-a-copy"></a>Создание копии  
 Пример создания копии базы данных.  
  
**Применимо к:** только отдельная или включенная в пул база данных.

```sql  
CREATE DATABASE escuela 
AS COPY OF school;  
```  
  
### <a name="creating-a-database-in-an-elastic-pool"></a>Создание базы данных в эластичном пуле  

Создает новую базу данных в пуле с именем S3M100.  

**Применимо к:** только отдельная или включенная в пул база данных.
  
```sql  
CREATE DATABASE db1 ( SERVICE_OBJECTIVE = ELASTIC_POOL ( name = S3M100 ) ) ;  
```  
  
### <a name="creating-a-copy-of-a-database-on-another-server"></a>Создание копии базы данных на другом сервере  
В следующем примере создается копия базы данных db_original с именем db_copy и уровнем производительности P2, заданным для одной базы данных.  Это происходит вне зависимости от того, находится ли db_original в эластичном пуле и имеет ли эта база уровень производительности, заданный для одной базы данных.  
  
**Применимо к:** только отдельная или включенная в пул база данных.

```sql  
CREATE DATABASE db_copy 
  AS COPY OF ozabzw7545.db_original ( SERVICE_OBJECTIVE = 'P2' )  ;  
```  
  
В следующем примере создается копия базы данных db_original с именем db_copy в эластичном пуле с именем ep1.  Это происходит вне зависимости от того, находится ли db_original в эластичном пуле и имеет ли эта база уровень производительности, заданный для одной базы данных. Если db_original находится в эластичном пуле с другим именем, db_copy все равно создается в ep1.  
  
**Применимо к:** только отдельная или включенная в пул база данных.

```sql  
CREATE DATABASE db_copy 
  AS COPY OF ozabzw7545.db_original 
  (SERVICE_OBJECTIVE = ELASTIC_POOL( name = ep1 ) ) ;  
```  

### <a name="create-database-with-specified-catalog-collation-value"></a>Создание базы данных с указанным значением параметров сортировки каталога

В следующем примере во время создания базы данных параметрам сортировки каталога задается значение DATABASE_DEFAULT, за счет чего параметры сортировки каталога совпадают с параметрами сортировки базы данных.

```sql
CREATE DATABASE TestDB3 COLLATE Japanese_XJIS_140  (MAXSIZE = 100 MB, EDITION = ‘basic’)  
  WITH CATALOG_COLLATION = DATABASE_DEFAULT 
```
  
## <a name="see-also"></a>См. также раздел  

-  [sys.dm_database_copies &#40;база данных SQL Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md)

- [ALTER DATABASE (база данных SQL Azure)](alter-database-transact-sql.md?&tabs=sqldbls) 

::: moniker-end
::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"

> [!div class="mx-tdCol2BreakAll"]
> <table>
> <tr>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
> </tr>
> <tr>
>   <th><a href="create-database-transact-sql.md?view=sql-server-2016">SQL Server</a></th>
>   <th><a href="create-database-transact-sql.md?view=azuresqldb-current">База данных SQL<br />Базы данных SQL</a></th>
>   <th><strong><em>* База данных SQL<br />Управляемый экземпляр *</em></strong></th>
>   <th><a href="create-database-transact-sql.md?view=azure-sqldw-latest">Хранилище данных<br />SQL</a></th>
>   <th><a href="create-database-transact-sql.md?view=aps-pdw-2016">SQL Parallel<br />Data Warehouse</a></th>
> </tr>
> </table>

&nbsp;

# <a name="azure-sql-database-managed-instance"></a>Управляемый экземпляр Базы данных SQL Azure

## <a name="overview"></a>Обзор

В Управляемом экземпляре Azure SQL эта инструкция используется для создания базы данных. При создании базы данных в Управляемом экземпляре вы можете указать имя базы данных и параметры сортировки. 

## <a name="syntax"></a>Синтаксис

```  
CREATE DATABASE database_name [ COLLATE collation_name ]  
[;]  
```
> [!IMPORTANT]
> Чтобы добавить файлы или настроить автономность для базы данных в Управляемом экземпляре, используйте инструкцию [ALTER DATABASE](alter-database-transact-sql.md?view=sqlallproducts-allversions&tabs=sqldbmi).
  
## <a name="arguments"></a>Аргументы  
  
*database_name* 
 
Имя новой базы данных. Имя должно быть уникальным в пределах SQL Server и соответствовать правилам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для идентификаторов. Дополнительные сведения: [Идентификаторы](http://go.microsoft.com/fwlink/p/?LinkId=180386).  
  
*Collation_name*  

Задает параметры сортировки по умолчанию для базы данных. Именем параметров сортировки может быть либо имя параметров сортировки Windows, либо имя параметров сортировки SQL. Если параметры не указаны, база данных использует параметры сортировки по умолчанию: SQL_Latin1_General_CP1_CI_AS.  
  
Дополнительные сведения об именах параметров сортировки Windows и SQL: [COLLATE (Transact-SQL)](http://msdn.microsoft.com/library/ms184391.aspx).  
  
## <a name="remarks"></a>Remarks
 
Базы данных в [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] используют несколько параметров по умолчанию, устанавливаемых при создании базы данных. Дополнительные сведения об этих параметрах по умолчанию см. в списке значений в разделе [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md).  
  
> [!IMPORTANT]  
>  Инструкция `CREATE DATABASE` должна быть единственной инструкцией в пакете [!INCLUDE[tsql](../../includes/tsql-md.md)]. 
  
`CREATE DATABASE` имеет следующие ограничения: 
- невозможно определить файлы и файловые группы;  
- параметры `WITH` не поддерживаются.  

   > [!TIP]
   > В качестве решения можно использовать [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md?&tabs=sqldbmi) после `CREATE DATABASE`, чтобы задать параметры базы данных и (или) добавить файлы.  

## <a name="permissions"></a>Разрешения  
Создавать базу данных могут следующие пользователи: 
  
- Субъект серверного уровня  
- Администратор Azure AD для локального сервера SQL Server Azure  
- Участник роли базы данных `dbmanager`    
  
## <a name="examples"></a>Примеры
  
### <a name="simple-example"></a>Простой пример  
 Простой пример создания базы данных.  
  
```sql  
CREATE DATABASE TestDB1;  
```  
  
## <a name="see-also"></a>См. также раздел  

См. описание [ALTER DATABASE](alter-database-transact-sql.md?&tabs=sqldbmi). 

::: moniker-end
::: moniker range="=azure-sqldw-latest||=sqlallproducts-allversions"

> [!div class="mx-tdCol2BreakAll"]
> <table>
> <tr>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
> </tr>
> <tr>
>   <th><a href="create-database-transact-sql.md?view=sql-server-2016">SQL Server</a></th>
>   <th><a href="create-database-transact-sql.md?view=azuresqldb-current">База данных SQL<br />Базы данных SQL</a></th>
>   <th><a href="create-database-transact-sql.md?view=azuresqldb-mi-current">База данных SQL<br />Базы данных SQL</a></th>
>   <th><strong><em>* Хранилище данных<br />SQL*</em></strong></th>
>   <th><a href="create-database-transact-sql.md?view=aps-pdw-2016">SQL Parallel<br />Data Warehouse</a></th>
> </tr>
> </table>

&nbsp;

# <a name="azure-sql-data-warehouse"></a>Хранилище данных SQL Azure

## <a name="overview"></a>Обзор

В хранилище данных SQL Azure этот оператор можно применить к логическому серверу Azure SQL для создания базы данных в хранилище данных SQL. Для этого оператора нужно указать имя базы данных, параметры сортировки, максимальный размер, выпуск и цель обслуживания.

## <a name="syntax"></a>Синтаксис  
  
```  
CREATE DATABASE database_name [ COLLATE collation_name ]  
(  
    [ MAXSIZE = { 
          250 | 500 | 750 | 1024 | 5120 | 10240 | 20480 | 30720 
        | 40960 | 51200 | 61440 | 71680 | 81920 | 92160 | 102400 
        | 153600 | 204800 | 245760 
      } GB ,
    ]  
    EDITION = 'datawarehouse',  
    SERVICE_OBJECTIVE = { 
         'DW100' | 'DW200' | 'DW300' | 'DW400' | 'DW500' | 'DW600' 
        | 'DW1000' | 'DW1200' | 'DW1500' | 'DW2000' | 'DW3000' | 'DW6000' 
        | 'DW1000c' | 'DW1500c' | 'DW2000c' | 'DW2500c' | 'DW3000c' | 'DW5000c' 
        | 'DW6000c' | 'DW7500c' | 'DW10000c' | 'DW15000c' | 'DW30000c'
    }  
)  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
*database_name*  
Имя новой базы данных. Это имя должно быть уникальным на сервере SQL Server, где могут размещаться базы данных [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] и [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Кроме того, оно должно соответствовать правилам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для идентификаторов. Дополнительные сведения: [Идентификаторы](http://go.microsoft.com/fwlink/p/?LinkId=180386).  
  
*collation_name*  
Задает параметры сортировки по умолчанию для базы данных. Именем параметров сортировки может быть либо имя параметров сортировки Windows, либо имя параметров сортировки SQL. Если параметры не указаны, базе данных назначаются параметры сортировки по умолчанию — SQL_Latin1_General_CP1_CI_AS.  
  
Дополнительные сведения об именах параметров сортировки Windows и SQL: [COLLATE (Transact-SQL)](http://msdn.microsoft.com/library/ms184391.aspx).  
  
*EDITION*  
Указывает уровень службы базы данных. Для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] используйте "datawarehouse".  
  
*MAXSIZE*  
Значение по умолчанию — 245 760 ГБ (240 ТБ).  

**Область применения:** уровень производительности "Оптимизация под гибкость"

Максимально допустимый размер базы данных. Размер базы данных не может превышать MAXSIZE. 

**Область применения:** уровень производительности "Оптимизация под вычисление"

Максимально допустимый размер данных rowstore в базе данных. Размер данных, хранящихся в таблицах rowstore, разностном хранилище индекса columnstore или некластеризованном индексе на базе кластеризованного индекса columnstore, не может превышать MAXSIZE.  Данные, сжатые в формат columnstore, не имеют ограничений на размер и не ограничивается значением MAXSIZE.
  
SERVICE_OBJECTIVE  
Определяет уровень производительности. Дополнительные сведения о целевых уровнях служб для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] см. на странице [Уровни производительности](https://azure.microsoft.com/documentation/articles/performance-tiers/).  
  
## <a name="general-remarks"></a>Общие замечания  
Используйте [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md), чтобы просмотреть свойства базы данных.  
  
Используйте [ALTER DATABASE &#40;Хранилище данных SQL Azure&#41;](../../t-sql/statements/alter-database-transact-sql.md?&tabs=sqldw), чтобы в дальнейшем изменять значения максимального размера или целевого уровня службы.   

Для хранилища данных SQL задано значение COMPATIBILITY_LEVEL 130, изменить которое невозможно. Дополнительные сведения: [Улучшение производительности запросов с уровнем совместимости 130 в базе данных SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-compatibility-level-query-performance-130/).
  
## <a name="permissions"></a>Разрешения  
Необходимые разрешения:  
  
-   имя входа субъекта серверного уровня, созданное процессом подготовки или  
  
-   член роли базы данных `dbmanager`.  
  
## <a name="error-handling"></a>Обработка ошибок  
Если размер базы данных достигает значения MAXSIZE, выдается ошибка с кодом 40544. В этом случае вы не сможете вставлять и изменять данные или создавать новые объекты (например, таблицы, хранимые процедуры, представления и функции). Вы по-прежнему можете считывать и удалять данные, усекать и удалять таблицы и индексы, а также выполнять перестроение индексов. Затем можно изменить значение MAXSIZE на значение, превышающее текущий размер базы данных, или удалить некоторые данные, чтобы освободить место в хранилище. Перед возобновлением возможности вставлять новые данные может пройти до 15 минут.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
Для создания новой базы данных необходимо подключение к базе данных master.  
  
Инструкция `CREATE DATABASE` должна быть единственной инструкцией в пакете [!INCLUDE[tsql](../../includes/tsql-md.md)].

После создания базы данных изменить ее параметры сортировки будет невозможно.   
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]  
  
### <a name="a-simple-example"></a>A. Простой пример  
Простой пример создания базы данных хранилища данных. В примере создается база данных с наименьшим максимальным размером, равным 10 240 ГБ, параметром сортировки по умолчанию SQL_Latin1_General_CP1_CI_AS и наименьшей вычислительной мощностью DW100.  
  
```  
CREATE DATABASE TestDW  
(EDITION = 'datawarehouse', SERVICE_OBJECTIVE='DW100');  
```  
  
### <a name="b-create-a-data-warehouse-database-with-all-the-options"></a>Б. Создание базы данных хранилища данных со всеми параметрами  
Пример создания хранилища данных объемом 10 ТБ с использованием всех параметров.  
  
```  
CREATE DATABASE TestDW COLLATE Latin1_General_100_CI_AS_KS_WS  
(MAXSIZE = 10240 GB, EDITION = 'datawarehouse', SERVICE_OBJECTIVE = 'DW1000');  
```  
  
## <a name="see-also"></a>См. также:  
[ALTER DATABASE &#40;хранилище данных SQL Azure&#40;](../../t-sql/statements/alter-database-transact-sql.md?&tabs=sqldw)
[CREATE TABLE &#40;хранилище данных SQL Azure&#41;](../../t-sql/statements/create-table-azure-sql-data-warehouse.md) 
[DROP DATABASE &#40;Transact-SQL&#40;](../../t-sql/statements/drop-database-transact-sql.md) 
  
::: moniker-end
::: moniker range="=aps-pdw-2016||=sqlallproducts-allversions"

> [!div class="mx-tdCol2BreakAll"]
> <table>
> <tr>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
> </tr>
> <tr>
>   <th><a href="create-database-transact-sql.md?view=sql-server-2016">SQL Server</a></th>
>   <th><a href="create-database-transact-sql.md?view=azuresqldb-current">База данных SQL<br />Базы данных SQL</a></th>
>   <th><a href="create-database-transact-sql.md?view=azuresqldb-mi-current">База данных SQL<br />Базы данных SQL</a></th>
>   <th><a href="create-database-transact-sql.md?view=azure-sqldw-latest">Хранилище данных<br />SQL</a></th>
>   <th><strong><em>* SQL Parallel<br />Data Warehouse *</em></strong></th>
> </tr>
> </table>

&nbsp;

# <a name="sql-parallel-data-warehouse"></a>SQL Parallel Data Warehouse

## <a name="overview"></a>Обзор

В параллельном хранилище данных этот оператор используется для создания базы данных на устройстве с Parallel Data Warehouse. Используйте эту инструкцию, чтобы создать все файлы, связанные с базой данных устройства, и задать максимальный размер и параметры автоматического увеличения для таблицы базы данных и журнала транзакций.

## <a name="syntax"></a>Синтаксис  
  
```  
CREATE DATABASE database_name   
WITH (   
    [ AUTOGROW = ON | OFF , ]   
    REPLICATED_SIZE = replicated_size [ GB ] ,  
    DISTRIBUTED_SIZE = distributed_size [ GB ] ,  
    LOG_SIZE = log_size [ GB ] )  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Имя новой базы данных. Дополнительные сведения о допустимых именах баз данных см. в разделе "Правила именования объектов" и "Зарезервированные имена базы данных" в статье [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 AUTOGROW = ON | **OFF**  
 Указывает, будут ли параметры *replicated_size*, *distributed_size* и *log_size* для этой базы данных автоматически увеличиваться по мере необходимости. Значение по умолчанию — **OFF**.  
  
 Если для параметра AUTOGROW установлено значение ON, параметры *replicated_size*, *distributed_size* и *log_size* будут увеличиваться по мере необходимости (не в блоках начального заданного размера) в результате вставки или обновления данных или другого действия, которое требует больше места, чем уже выделено.  
  
 Если для параметра AUTOGROW установлено значение OFF, размеры не будут увеличиваться автоматически. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] вернет ошибку при попытке выполнения действия, которое требует увеличения значений *replicated_size*, *distributed_size* или *log_size*.  
  
 Параметр AUTOGROW принимает значение ON или OFF для всех размеров. Например, невозможно включить AUTOGROW для *log_size* и отключить для *replicated_size*.  
  
 *replicated_size* [ GB ]  
 Положительное число. Задает размер (в виде целого или десятичного числа гигабайт) всего пространства, выделенного для реплицированных таблиц и соответствующих данных *на каждом вычислительном узле*. Требования к минимальному и максимальному значению *replicated_size* см. в разделе "Минимальные и максимальные значения" в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Если для параметра AUTOGROW установлено значение ON, реплицированные таблицы могут увеличиваться.  
  
 Если для параметра AUTOGROW установлено значение OFF, при попытке пользователя создать новую реплицированную таблицу, вставить данные в существующую реплицированную таблицу или обновить существующую реплицированную таблицу с увеличением значения *replicated_size* будет возвращена ошибка.  
  
 *distributed_size* [ GB ]  
 Положительное число. Размер (в виде целого или десятичного числа гигабайт) всего пространства, выделенного для распределенных таблиц и соответствующих данных *на устройстве*. Требования к минимальному и максимальному значению *distributed_size* см. в разделе "Минимальные и максимальные значения" в статье [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Если для параметра AUTOGROW установлено значение ON, распределенные таблицы могут увеличиваться.  
  
 Если для параметра AUTOGROW установлено значение OFF, при попытке пользователя создать новую распределенную таблицу, вставить данные в существующую распределенную таблицу или обновить существующую распределенную таблицу с увеличением значения *distributed_size* будет возвращена ошибка.  
  
 *log_size* [ GB ]  
 Положительное число. Размер (в виде целого или десятичного числа гигабайт) для журнала транзакций *на устройстве*.  
  
 Требования к минимальному и максимальному значению *log_size* см. в разделе "Минимальные и максимальные значения" в статье [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Если для параметра AUTOGROW установлено значение ON, файл журнала может увеличиваться в размерах. Используйте инструкцию [DBCC SHRINKLOG (хранилище данных SQL Azure)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md), чтобы уменьшить размер файлов журнала до исходного значения.  
  
 Если для параметра AUTOGROW установлено значение OFF, в случае любого действия, которое увеличит размер журнала на отдельном вычислительном узле с превышением значения *log_size*, будет возвращена ошибка.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение **CREATE ANY DATABASE** в базе данных master или членство в предопределенной роли сервера **sysadmin**.  
  
 В следующем примере предоставляется разрешение на создание базы данных для пользователя Fay базы данных.  
  
```  
USE master;  
GO  
GRANT CREATE ANY DATABASE TO [Fay];  
GO  
```  
  
## <a name="general-remarks"></a>Общие замечания  
 Базы данных создаются с уровнем совместимости базы данных 120, который является уровнем совместимости для [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]. Это гарантирует, что база данных сможет использовать все функции [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], которые использует PDW.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 Инструкция CREATE DATABASE не разрешена в явных транзакциях. Дополнительные сведения см. в разделе [Инструкции](../../t-sql/statements/statements.md).  
  
 Сведения о минимальных и максимальных ограничениях для базы данных см. в разделе "Минимальные и максимальные значения" в статье [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Во время создания базы данных должно быть достаточно свободного места *на каждом вычислительном узле* для распределения общей суммы следующих размеров:  
  
-   База данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с таблицами со значением размера *replicated_table_size*.  
  
-   База данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с таблицами со значением размера (*distributed_table_size* / количество вычислительных узлов).  
  
-   Журналы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] со значением размера (*log_size* / количество вычислительных узлов).  
  
## <a name="locking"></a>Блокировка  
 Принимает совмещаемую блокировку для объекта DATABASE.  
  
## <a name="metadata"></a>Метаданные  
 После успешного завершения этой операции запись для этой базы данных будет отображаться в представлениях метаданных [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) и [sys.objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-basic-database-creation-examples"></a>A. Примеры создания базовых баз данных  
 В следующем примере создается база данных `mytest` с выделением 100 ГБ на вычислительный узел для реплицированных таблиц, 500 ГБ на устройство для распределенных таблиц и 100 ГБ на устройство для журнала транзакций. В этом примере параметр AUTOGROW отключен по умолчанию.  
  
```  
CREATE DATABASE mytest  
   WITH   
   (REPLICATED_SIZE = 100 GB,  
   DISTRIBUTED_SIZE = 500 GB,  
   LOG_SIZE = 100 GB );  
```  
  
 В следующем примере создается база данных `mytest` с указанными выше параметрами, но AUTOGROW включен. Это позволяет базе данных увеличиваться и превышать указанные значения размера.  
  
```  
CREATE DATABASE mytest  
   WITH   
   (AUTOGROW = ON,  
   REPLICATED_SIZE = 100 GB,  
   DISTRIBUTED_SIZE = 500 GB,  
   LOG_SIZE = 100 GB);  
```  
  
### <a name="b-creating-a-database-with-partial-gigabyte-sizes"></a>Б. Создание базы данных с десятичным числом гигабайт  
 В следующем примере создается база данных `mytest` с отключенным параметром AUTOGROW, с выделением 1,5 ГБ на вычислительный узел для реплицированных таблиц, 5,25 ГБ на устройство для распределенных таблиц и 10 ГБ на устройство для журнала транзакций.  
  
```  
CREATE DATABASE mytest  
   WITH   
   (REPLICATED_SIZE = 1.5 GB,  
   DISTRIBUTED_SIZE = 5.25 GB,  
   LOG_SIZE = 10 GB);  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER DATABASE (Parallel Data Warehouse)](../../t-sql/statements/alter-database-transact-sql.md?&tabs=sqlpdw)   
 [DROP DATABASE (Transact-SQL)](../../t-sql/statements/drop-database-transact-sql.md)  
  
::: moniker-end
