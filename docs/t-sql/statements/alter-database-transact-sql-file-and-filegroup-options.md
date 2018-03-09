---
title: "Параметры инструкции ALTER файл базы данных и файловых групп (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ADD FILE
- ADD_FILE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting files
- removing files
- deleting filegroups
- file modifications [SQL Server]
- databases [SQL Server], size
- relocating files
- databases [SQL Server], modifying
- file additions [SQL Server], ALTER DATABASE
- file moving [SQL Server]
- default filegroups
- ALTER DATABASE statement, files and filegroups
- initializing files [SQL Server]
- database files [SQL Server]
- moving files
- filegroups [SQL Server], deleting
- adding filegroups
- adding files
- database filegroups [SQL Server]
- adding log files
- modifying files
- filegroups [SQL Server], adding
- file initialization [SQL Server]
- files [SQL Server], deleting
- files [SQL Server], adding
- databases [SQL Server], moving
ms.assetid: 1f635762-f7aa-4241-9b7a-b51b22292b07
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 826b8a5abb14ee677f89f1c77956215ec72f90c6
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="alter-database-transact-sql-file-and-filegroup-options"></a>Параметры инструкции ALTER DATABASE (Transact-SQL) файла и файловой группы 
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет файлы и файловые группы, связанные с базой данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Добавляет или удаляет файлы и файловые группы из базы данных и изменяет атрибуты базы данных или ее файлов и файловых групп. Для других параметров инструкции ALTER DATABASE. в разделе [инструкции ALTER DATABASE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ALTER DATABASE database_name   
{  
    <add_or_modify_files>  
  | <add_or_modify_filegroups>  
}  
[;]  
  
<add_or_modify_files>::=  
{  
    ADD FILE <filespec> [ ,...n ]   
        [ TO FILEGROUP { filegroup_name } ]  
  | ADD LOG FILE <filespec> [ ,...n ]   
  | REMOVE FILE logical_file_name   
  | MODIFY FILE <filespec>  
}  
  
<filespec>::=   
(  
    NAME = logical_file_name    
    [ , NEWNAME = new_logical_name ]   
    [ , FILENAME = {'os_file_name' | 'filestream_path' | 'memory_optimized_data_path' } ]   
    [ , SIZE = size [ KB | MB | GB | TB ] ]   
    [ , MAXSIZE = { max_size [ KB | MB | GB | TB ] | UNLIMITED } ]   
    [ , FILEGROWTH = growth_increment [ KB | MB | GB | TB| % ] ]   
    [ , OFFLINE ]  
)   
  
<add_or_modify_filegroups>::=  
{  
    | ADD FILEGROUP filegroup_name   
        [ CONTAINS FILESTREAM | CONTAINS MEMORY_OPTIMIZED_DATA ]  
    | REMOVE FILEGROUP filegroup_name   
    | MODIFY FILEGROUP filegroup_name  
        { <filegroup_updatability_option>  
        | DEFAULT  
        | NAME = new_filegroup_name   
        | { AUTOGROW_SINGLE_FILE | AUTOGROW_ALL_FILES }  
        }  
}  
<filegroup_updatability_option>::=  
{  
    { READONLY | READWRITE }   
    | { READ_ONLY | READ_WRITE }  
}  
  
```  
  
## <a name="arguments"></a>Аргументы  
**\<add_or_modify_files >:: =**
  
 Указывает файл, который будет добавлен, удален или изменен.  
  
 *database_name*  
 Имя изменяемой базы данных.  
  
 ADD FILE  
 Добавляет файл к базе данных.  
  
 Файловую ГРУППУ { *filegroup_name* }  
 Указывает файловую группу, к которой необходимо добавить указанный файл. Чтобы отобразить текущую файловую и какие файловая группа доступна по умолчанию, используйте [sys.filegroups](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md) представления каталога.  
  
 ADD LOG FILE  
 Добавляет файл журнала в указанную базу данных.  
  
 Удалите ФАЙЛ *логическое_имя_файла*  
 Удаляет логическое описание файла из экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и физический файл. Файл не может быть удален, если он не пуст.  
  
 *логическое_имя_файла*  
 Логическое имя, используемое в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при обращении к файлу.  
  
> [!WARNING]  
> Удаление файла базы данных, имеющий FILE_SNAPSHOT резервные копии, связанные с ним выполняется успешно, однако сделать резервные копии, ссылающийся на файл базы данных не будут удалены все связанные моментальные снимки. Файл будет усечено, но не будут физически удалены для хранения резервных копий FILE_SNAPSHOT без изменений. Дополнительные сведения см. в разделе [Резервное копирование и восстановление SQL Server с помощью службы хранилища BLOB-объектов Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md). **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).  
  
 MODIFY FILE  
 Указывает файл, который должен быть изменен. Только один \<filespec > свойство можно изменить одновременно. ИМЯ всегда должно быть указано в \<filespec > для идентификации файл будет изменен. Если указано предложение SIZE, новый размер файла должен быть больше, чем текущий.  
  
 Чтобы изменить логическое имя файла данных или файла журнала, укажите логическое имя файла, который будет переименован, в предложении `NAME`, а новое логическое имя для файла — в предложении `NEWNAME`. Пример:  
  
```  
MODIFY FILE ( NAME = logical_file_name, NEWNAME = new_logical_name )   
```  
  
 Чтобы переместить файл данных или файл журнала в новое расположение, укажите текущее логическое имя файла в предложении `NAME` и укажите новый путь и имя файла в операционной системе в предложении `FILENAME`. Пример:  
  
```  
MODIFY FILE ( NAME = logical_file_name, FILENAME = ' new_path/os_file_name ' )  
```  
  
 При перемещении полнотекстового каталога укажите только новый путь в предложении FILENAME. Не указывайте имя файла в операционной системе.  
  
 Дополнительные сведения см. в разделе [перемещение файлов базы данных](../../relational-databases/databases/move-database-files.md).  
  
 Для файловой группы FILESTREAM значение NAME можно изменять в режиме в сети. Значение FILENAME можно изменять в режиме в сети, но внесенное изменение вступает в силу лишь после того, как будет выполнено физическое перемещение контейнера, а также остановка и последующий перезапуск сервера.  
  
 Можно задать значение параметра файла FILESTREAM, равное OFFLINE. Если файл FILESTREAM определен как вне сети, его родительская файловая группа отмечается внутри как вне сети, поэтому любая попытка доступа к данным FILESTREAM в пределах этой файловой группы окончится неудачей.  
  
> [!NOTE]  
>  \<add_or_modify_files > параметры недоступны в автономной базе данных.
  
 **\<filespec >:: =**  
  
 Управляет свойствами файла.  
  
 ИМЯ *логическое_имя_файла*  
 Указывает логическое имя файла.  
  
 *логическое_имя_файла*  
 Логическое имя, используемое экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при обращении к файлу.  
  
 Параметр NEWNAME *new_logical_file_name*  
 Указывает новое логическое имя для файла.  
  
 *new_logical_file_name*  
 Имя, которым будет заменено текущее логическое имя файла. Имя должно быть уникальным в пределах базы данных и соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md). Имя может быть символьной константой или константой Юникода, обычным идентификатором или идентификатором с разделителем.  
  
 Имя файла { **"***имя_файла_ос***"** | **"***filestream_path* **"** | **"***memory_optimized_data_path***"**}  
 Задает имя файла в операционной системе (физическое имя).  
  
 " *имя_файла_ос* "  
 Для стандартной файловой группы (ROWS) этот параметр представляет собой путь и имя файла, которые использовались операционной системой при создании файла. Файл должен постоянно храниться на сервере, на котором установлен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Указанный путь должен существовать до выполнения инструкции ALTER DATABASE.  
  
 Параметры SIZE, MAXSIZE и FILEGROWTH недоступны, если путь к файлу указан в формате UNC.  
  
> [!NOTE]  
> Системные базы данных не могут размещаться в общих каталогах UNC.  
  
 Файлы данных не должны располагаться в сжатой файловой системе, кроме случаев, когда файлы являются вторичными файлами только для чтения или база данных находится в режиме только для чтения. Файлы журналов ни в коем случае не должны размещаться в сжатых файловых системах.  
  
 Если файл находится в необработанной секции *имя_файла_ос* необходимо указать только букву диска существующей необработанной секции. В каждый необработанный раздел может быть помещен только один файл.  
  
 **"** *filestream_path* **"**  
 Для файловой группы FILESTREAM параметр FILENAME указывает путь, где будут храниться данные FILESTREAM. Должен существовать путь вплоть до последнего каталога, но последний каталог существовать не должен. Например, если указать путь «C:\MyFiles\MyFilestreamData», папка «C:\MyFiles» должна существовать до запуска инструкции ALTER DATABASE, а папка «MyFilestreamData» — не должна.  
  
 Свойства SIZE и FILEGROWTH к файловой группе FILESTREAM неприменимы.  
  
 **"** *memory_optimized_data_path* **"**  
 Что касается файловой группы с оптимизацией для памяти, то FILENAME указывает путь, по которому будут храниться данные, оптимизированные для памяти. Должен существовать путь вплоть до последнего каталога, но последний каталог существовать не должен. Например, если указан путь C:\MyFiles\MyData, то каталог C:\MyFiles должен существовать до выполнения инструкции ALTER DATABASE, но папка MyData не должна существовать.  
  
 Файловую группу и файл (`<filespec>`) необходимо создавать в одной инструкции.  
  
 Свойства SIZE, MAXSIZE и FILEGROWTH не относятся к файловой группе, оптимизированной для памяти.  
  
 РАЗМЕР *размер*  
 Указывает размер файла. Параметр SIZE не применяется к файловым группам FILESTREAM.  
  
 *size*  
 Размер файла.  
  
 При использовании в инструкции ADD FILE *размер* — это исходный размер файла. При использовании в инструкции MODIFY FILE *размер* является новым размером файла и должен быть больше, чем текущий размер файла.  
  
 Когда *размер* не задан для первичного файла, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует размер первичного файла в **модели** базы данных. Если указан вторичный файл данных или файл журнала, но *размер* не указан для файла, [!INCLUDE[ssDE](../../includes/ssde-md.md)] задает размер файла 1 МБ.  
  
 Суффиксы KB, MB, GB и TB могут использоваться для указания килобайтов, мегабайтов, гигабайтов или терабайтов. По умолчанию — MБ. Укажите целое число без десятичного разделителя. Для указания долей мегабайта преобразуйте значение в килобайты, умножив число на 1024. Например, укажите «1536 KB» вместо «1,5 MB» (1,5 x 1024 = 1536).  
  
 Параметр MAXSIZE { *max_size*| НЕОГРАНИЧЕННОЕ}  
 Указывает максимальный размер, до которого может расти файл.  
  
 *max_size*  
 Максимальный размер файла. Суффиксы KB, MB, GB и TB могут использоваться для указания килобайтов, мегабайтов, гигабайтов или терабайтов. По умолчанию — MБ. Укажите целое число без десятичного разделителя. Если *max_size* не указан, размер файла может увеличиваться до заполнения диска.  
  
 UNLIMITED  
 Указывает, что файл может расти вплоть до заполнения диска. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файл журнала, для которого задано неограниченное увеличение размера, имеет максимальный размер 2 ТБ, а файл данных — 16 ТБ. Ограничения размера отсутствуют, если этот параметр указан для контейнера FILESTREAM. Размер продолжает увеличиваться до полного заполнения диска.  
  
 FILEGROWTH *growth_increment*  
 Задает автоматический шаг роста файла. Значение параметра FILEGROWTH для файла не может превосходить значение параметра MAXSIZE. Параметр FILEGROWTH не применяется к файловым группам FILESTREAM.  
  
 *growth_increment*  
 Объем пространства, добавляемого к файлу каждый раз, когда требуется увеличение пространства.  
  
 Значение может быть указано в килобайтах, мегабайтах, гигабайтах, терабайтах или процентах (%). Если указано число без суффикса MB, KB или %, то по умолчанию используется MB. Если размер указан в процентах (%), то шаг роста это заданная часть в процентах от размера файла во время этого файла. Указанный размер округляется до ближайших 64 КБ.  
  
 Значение 0 указывает, что автоматическое приращение выключено и дополнительное пространство для файла не разрешено.  
  
 Если параметр FILEGROWTH не задан, доступны следующие значения по умолчанию:  
  
|Version|Значения по умолчанию|  
|-------------|--------------------|  
|Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|Данные 64 МБ. Файлы журналов 64 МБ.|  
|Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Данные 1 МБ. Файлы журнала 10%.|  
|До версии[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Данные 10%. Файлы журнала 10%.|  
  
 OFFLINE  
 Переводит файл в режим вне сети и делает все его объекты в файловой группе недоступными.  
  
> [!CAUTION]  
>  Используйте этот параметр только в том случае, когда файл поврежден и может быть восстановлен. Файл, переведенный в режим OFFLINE, может быть заново включен в режиме в сети только при восстановлении из резервной копии. Дополнительные сведения о восстановлении одного файла см. в разделе [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md).  
  
> [!NOTE]  
> \<filespec > параметры недоступны в автономной базе данных.  
  
 **\<add_or_modify_filegroups >:: =**  
  
 Добавить, изменить или удалить файловую группу из базы данных.  
  
 Добавить файловую ГРУППУ *filegroup_name*  
 Добавляет файловую группу в базу данных.  
  
 CONTAINS FILESTREAM  
 Указывает, что файловая группа хранит большие двоичные объекты (BLOB) FILESTREAM в файловой системе.  
  
 CONTAINS MEMORY_OPTIMIZED_DATA  

**Применяется к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])
  
 Указывает, что файловая группа хранит оптимизируемые для памяти данные в файловой системе. Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md). В каждой базе данных может присутствовать только одна файловая группа MEMORY_OPTIMIZED_DATA. Для создания таблицы, оптимизируемой для памяти, файловая группа не может быть пустой. Должно быть не менее одного файла. *filegroup_name* ссылается на путь. Должен существовать путь вплоть до последнего каталога, но последний каталог существовать не должен.  
  
 В следующем примере создается файловая группа, которая добавляется в базу данных с именем xtp_db; кроме того, добавляется файл в файловую группу. В файловой группе хранятся данные memory_optimized.  
  
```sql  
ALTER DATABASE xtp_db ADD FILEGROUP xtp_fg CONTAINS MEMORY_OPTIMIZED_DATA;  
GO  
ALTER DATABASE xtp_db ADD FILE (NAME='xtp_mod', FILENAME='d:\data\xtp_mod') TO FILEGROUP xtp_fg;  
```  
  
 Удалите файловую ГРУППУ *filegroup_name*  
 Удаляет файловую группу из базы данных. Файловая группа не может быть удалена, пока она не пустая. Вначале удалите из файловой группы все файлы. Дополнительные сведения см. в разделе «удалить ФАЙЛ *логическое_имя_файла*,» ранее в этом разделе.  
  
> [!NOTE]  
> Если сборщик мусора FILESTREAM не удалил все файлы из контейнера FILESTREAM, операция ALTER DATABASE REMOVE FILE по удалению контейнера FILESTREAM завершится неудачей и возвратит ошибку. См. подраздел «Удаление контейнера FILESTREAM» в разделе «Примечания» далее в этом разделе.  
  
MODIFY FILEGROUP *имя_файловой_группы* { \<filegroup_updatability_option > | ПО УМОЛЧАНИЮ | ИМЯ  **=**  *new_filegroup_name* } изменяет файловую группу, задав состояние на READ_ONLY или READ_WRITE, делая ее файловой группой по умолчанию для базы данных, или Изменение имени файловой группы.  
  
 \<filegroup_updatability_option >  
 Устанавливает свойство «только для чтения» или «чтение и запись» для файловой группы.  
  
 DEFAULT  
 Изменяет файловую группу базы данных по умолчанию для *filegroup_name*. Только одна файловая группа в базе данных может быть файловой группой по умолчанию. Дополнительные сведения см. в статье [Database Files and Filegroups](../../relational-databases/databases/database-files-and-filegroups.md).  
  
 ИМЯ = *new_filegroup_name*  
 Изменяет имя файловой группы для *new_filegroup_name*.  
  
 AUTOGROW_SINGLE_FILE  
**Применяется к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])
  
 Если файл в файловой группе удовлетворяет требованиям порога автоматического увеличения, увеличивается только этот файл. Это значение по умолчанию.  
  
 AUTOGROW_ALL_FILES  

**Применяется к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])
  
 Если файл в файловой группе удовлетворяет требованиям порога автоматического увеличения, все файлы в файловой группе расти.  
  
 **\<filegroup_updatability_option >:: =**  
  
 Устанавливает свойство «только для чтения» или «чтение и запись» для файловой группы.  
  
 READ_ONLY | READONLY  
 Определяет, что файловая группа находится в состоянии только для чтения. Изменение ее объектов запрещено. Первичную файловую группу перевести в состояние только для чтения нельзя. Чтобы изменить это состояние, необходимо обладать монопольным доступом к базе данных. Дополнительные сведения см. в описании предложения SINGLE_USER.  
  
 Поскольку база данных находится в состоянии только для чтения, невозможно производить изменения данных:  
  
-   при запуске системы будет пропущено автоматическое восстановление;  
-   сжатие базы данных невозможно;  
-   в базах данных, находящихся в состоянии только для чтения, невозможны блокировки. Это может привести к более быстрому выполнению запросов.  
  
> [!NOTE]  
>  Ключевое слово READONLY будет удалено в будущих версиях [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Избегайте использования ключевого слова READONLY в новых разработках и запланируйте изменение приложений, которые сейчас его используют. Вместо него используйте READ_ONLY.  
  
 READ_WRITE | READWRITE  
 Определяет, что файловая группа находится в состоянии READ_WRITE. Разрешено изменять объекты в файловой группе. Чтобы изменить это состояние, необходимо обладать монопольным доступом к базе данных. Дополнительные сведения см. в описании предложения SINGLE_USER.  
  
> [!NOTE]  
>  Ключевое слово `READWRITE` будет удалена в будущей версии [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Избегайте использования `READWRITE` работать в новых разработках и запланируйте изменение приложений, которые сейчас используют `READWRITE` использование `READ_WRITE` вместо него.  
  
 Состояние этих параметров можно определить с помощью проверки **is_read_only** столбца в **sys.databases** представления каталога или **обновляемости** свойство `DATABASEPROPERTYEX` функции.  
  
## <a name="remarks"></a>Remarks  
 Чтобы уменьшить размер базы данных, используйте [DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
Невозможно добавить или удалить файл во время `BACKUP` выполняется инструкция.  
  
Для каждой базы данных может указываться не более 32 767 файлов и 32 767 файловых групп.  
  
Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], состояние файла базы данных (например, сети или вне сети) поддерживается независимо от состояния базы данных. Дополнительные сведения см. в разделе [состояния файла](../../relational-databases/databases/file-states.md). 
-  Состояние файлов в пределах файловой группы определяет доступность файловой группы в целом. Чтобы файловая группа была доступна, необходимо, чтобы все файлы в файловой группе находились в режиме в сети. 
-  Если файловая группа вне сети, то любая попытка обращения к файловой группе с помощью инструкции SQL закончится ошибкой. При построении планов запросов для `SELECT` инструкций, оптимизатор запросов избегает некластеризованных индексов и индексированных представлений, принадлежащих файловым группам вне сети. Это позволяет успешно выполнить эти инструкции. Тем не менее, если эту файловую группу, содержит кучу или кластеризованный индекс целевой таблицы, `SELECT` инструкции завершаются ошибкой. Кроме того, любой `INSERT`, `UPDATE`, или `DELETE` инструкции, изменяющая таблицу с любым индексом в файловой группе вне сети завершится ошибкой.  
  
## <a name="moving-files"></a>Перемещение файлов  
Системные или определенные пользователем данные и файлы журналов можно перемещать, указывая новое местоположение в параметре FILENAME. Это может быть полезным в следующих случаях:  
  
-   Восстановление после сбоя. Например, база данных находится в подозрительном режиме или завершила работу по причине сбоя оборудования;  
-   Плановое перемещение.  
-   Перемещение для запланированного обслуживания дисков.  
  
Дополнительные сведения см. в разделе [перемещение файлов базы данных](../../relational-databases/databases/move-database-files.md).  
  
## <a name="initializing-files"></a>Инициализация файлов  
По умолчанию файлы данных и журналов инициализируются, заполняясь нулями, при выполнении одной из следующих операций:  
  
-   Создание базы данных.   
-   добавление файлов к существующей базе данных;   
-   увеличение размера существующего файла;   
-   Восстановление базы данных или файловой группы.   
  
Файлы данных могут быть инициализированы мгновенно. Это разрешено для быстрого выполнения этих файловых операций. Дополнительные сведения см. в разделе [Инициализация файлов базы данных](../../relational-databases/databases/database-instant-file-initialization.md). 
  
## <a name="removing-a-filestream-container"></a>Удаление контейнера FILESTREAM  
 Даже если контейнер FILESTREAM был очищен с использованием операции «DBCC SHRINKFILE», базе данных по-прежнему необходимы ссылки на удаленные файлы по различным причинам, связанным с обслуживанием системы. [sp_filestream_force_garbage_collection &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md) запустит сборщик мусора FILESTREAM, чтобы удалить эти файлы в том случае, когда это будет безопасно. Если сборщик мусора FILESTREAM не удалил все файлы из контейнера FILESTREAM, операция ALTER DATABASE REMOVE FILE по удалению контейнера FILESTREAM завершится неудачей и возвратит ошибку. Для удаления контейнера FILESTREAM рекомендуется следующий процесс.  
  
1.  Запустите [DBCC SHRINKFILE &#40; Transact-SQL &#41; ](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md) с параметром EMPTYFILE, чтобы переместить активное содержимое этого контейнера в другие контейнеры.  
  
2.  Убедитесь, что в модели восстановления FULL или BULK_LOGGED было выполнено резервное копирование журналов.  
  
3.  Убедитесь, что было запущено задание чтения журнала репликации, если это необходимо.  
  
4.  Запустите [sp_filestream_force_garbage_collection &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md) чтобы сборщик мусора принудительно удалить все файлы, которые больше не нужны в этом контейнере.  
  
5.  Выполните инструкцию ALTER DATABASE с параметром REMOVE FILE, чтобы удалить этот контейнер.  
  
6.  Повторите шаги с 2 по 4, чтобы завершить сборку мусора.  
  
7.  Используйте инструкцию ALTER Database...REMOVE FILE, чтобы удалить этот контейнер.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-adding-a-file-to-a-database"></a>A. Добавление файла к базе данных  
 В следующем примере к базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] добавляется файл данных размером 5 МБ.  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012   
ADD FILE   
(  
    NAME = Test1dat2,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\t1dat2.ndf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
);  
GO  
  
```  
  
### <a name="b-adding-a-filegroup-with-two-files-to-a-database"></a>Б. Добавление файловой группы с двумя файлами к базе данных  
 В следующем примере в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] создается файловая группа `Test1FG1` и добавляется два файла по 5 МБ в эту файловую группу.  
  
```sql  
USE master  
GO  
ALTER DATABASE AdventureWorks2012  
ADD FILEGROUP Test1FG1;  
GO  
ALTER DATABASE AdventureWorks2012   
ADD FILE   
(  
    NAME = test1dat3,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\t1dat3.ndf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
),  
(  
    NAME = test1dat4,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\t1dat4.ndf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
)  
TO FILEGROUP Test1FG1;  
GO  
  
```  
  
### <a name="c-adding-two-log-files-to-a-database"></a>В. Добавление двух файлов журнала к базе данных  
 В следующем примере к базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] добавляется два файла журнала размером 5 МБ каждый.  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012   
ADD LOG FILE   
(  
    NAME = test1log2,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\test2log.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
),  
(  
    NAME = test1log3,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL10_50.MSSQLSERVER\MSSQL\DATA\test3log.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
);  
GO  
  
```  
  
### <a name="d-removing-a-file-from-a-database"></a>Г. Удаление файла из базы данных  
 В следующем примере удаляется один из файлов, добавленных в примере Б.  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
REMOVE FILE test1dat4;  
GO  
```  
  
### <a name="e-modifying-a-file"></a>Д. Изменение файла  
В следующем примере увеличивается размер одного из файлов, добавленных в примере Б.  
 ALTER DATABASE с помощью команды MODIFY FILE можно только увеличить размер файла, поэтому если вам нужно уменьшить размер файла необходимо использовать DBCC SHRINKFILE.  
  
```sql  
USE master;  
GO
  
ALTER DATABASE AdventureWorks2012   
MODIFY FILE  
(NAME = test1dat3,  
SIZE = 200MB);  
GO  
```

В этом примере уменьшается размер файла данных до 100 МБ, а затем определяют размера, в этот период. 

```sql
USE AdventureWorks2012;
GO

DBCC SHRINKFILE (AdventureWorks2012_data, 100);
GO

USE master;  
GO
  
ALTER DATABASE AdventureWorks2012   
MODIFY FILE  
(NAME = test1dat3,  
SIZE = 200MB);  
GO
```
 
  
### <a name="f-moving-a-file-to-a-new-location"></a>Е. Перемещение файла в новое расположение  
 В следующем примере файл `Test1dat2`, созданный в примере A, перемещается в новый каталог.  
  
> [!NOTE]  
> Перед выполнением этого примера необходимо физически переместить файл в новый каталог. После выполнения остановите и запустите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или переведите базу данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] в состояние OFFLINE, а затем назад в ONLINE, чтобы осуществить изменения.  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
MODIFY FILE  
(  
    NAME = Test1dat2,  
    FILENAME = N'c:\t1dat2.ndf'  
);  
GO  
```  
  
### <a name="g-moving-tempdb-to-a-new-location"></a>Ж. Перемещение базы данных tempdb в новое расположение  
 В следующем примере база данных `tempdb` перемещается из ее текущего расположения на диске в другое расположение. Так как база данных `tempdb` повторно создается при каждом запуске службы MSSQLSERVER, нет необходимости физически переносить файлы данных и журнала. Эти файлы создаются при запуске службы на шаге 3. Пока служба не будет запущена повторно, база данных `tempdb` продолжает функционировать на прежнем месте.  
  
1.  Определите логические имена файлов базы данных `tempdb` и их текущее расположение на диске.  
  
    ```sql  
    SELECT name, physical_name  
    FROM sys.master_files  
    WHERE database_id = DB_ID('tempdb');  
    GO  
    ```  
  
2.  Измените местоположение каждого файла с помощью `ALTER DATABASE`.  
  
    ```sql  
    USE master;  
    GO  
    ALTER DATABASE tempdb   
    MODIFY FILE (NAME = tempdev, FILENAME = 'E:\SQLData\tempdb.mdf');  
    GO  
    ALTER DATABASE  tempdb   
    MODIFY FILE (NAME = templog, FILENAME = 'E:\SQLData\templog.ldf');  
    GO  
    ```  
  
3.  Остановите и перезапустите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
4.  Проверьте изменение файла.  
  
    ```sql  
    SELECT name, physical_name  
    FROM sys.master_files  
    WHERE database_id = DB_ID('tempdb');  
    ```  
  
5.  Удалите файлы tempdb.mdf и templog.ldf из их исходного расположения.  
  
### <a name="h-making-a-filegroup-the-default"></a>З. Назначение файловой группы по умолчанию  
 В нижеследующем примере `Test1FG1` файловая группа, созданная в примере Б файловую группу по умолчанию. Затем файловая группа по умолчанию будет переназначена на файловую группу `PRIMARY`. Обратите внимание, что слово `PRIMARY` должно быть заключено в скобки или в кавычки.  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012   
MODIFY FILEGROUP Test1FG1 DEFAULT;  
GO  
ALTER DATABASE AdventureWorks2012   
MODIFY FILEGROUP [PRIMARY] DEFAULT;  
GO  
```  
  
### <a name="i-adding-a-filegroup-using-alter-database"></a>И. Добавление файловой группы с помощью инструкции ALTER DATABASE  
 В следующем примере в базу данных `FILEGROUP` добавляется файловая группа `FILESTREAM`, содержащая предложение `FileStreamPhotoDB`.  
  
```sql  
--Create and add a FILEGROUP that CONTAINS the FILESTREAM clause to  
--the FileStreamPhotoDB database.  
ALTER DATABASE FileStreamPhotoDB  
ADD FILEGROUP TodaysPhotoShoot  
CONTAINS FILESTREAM;  
GO  
  
--Add a file for storing database photos to FILEGROUP   
ALTER DATABASE FileStreamPhotoDB  
ADD FILE  
(  
    NAME= 'PhotoShoot1',  
    FILENAME = 'C:\Users\Administrator\Pictures\TodaysPhotoShoot.ndf'  
)  
TO FILEGROUP TodaysPhotoShoot;  
GO  
```      
        
### <a name="j-change-filegroup-so-that-when-a-file-in-the-filegroup-meets-the-autogrow-threshold-all-files-in-the-filegroup-grow"></a>К. Измените файловую группу, чтобы когда файл в файловой группе соответствует пороговое значение автоувеличения, все файлы в файловой группе расти
 Следующий пример приводит к возникновению ошибки необходимая `ALTER DATABASE` инструкции для изменения для чтения файловые группы с `AUTOGROW_ALL_FILES` параметр.  
  
```sql  
--Generate ALTER DATABASE ... MODIFY FILEGROUP statements  
--so that all read-write filegroups grow at the same time.  
SET NOCOUNT ON;

DROP TABLE IF EXISTS #tmpdbs
CREATE TABLE #tmpdbs (id int IDENTITY(1,1), [dbid] int, [dbname] sysname, isdone bit);

DROP TABLE IF EXISTS #tmpfgs
CREATE TABLE #tmpfgs (id int IDENTITY(1,1), [dbid] int, [dbname] sysname, fgname sysname, isdone bit);

INSERT INTO #tmpdbs ([dbid], [dbname], [isdone])
SELECT database_id, name, 0 FROM master.sys.databases (NOLOCK) WHERE is_read_only = 0 AND state = 0;

DECLARE @dbid int, @query VARCHAR(1000), @dbname sysname, @fgname sysname

WHILE (SELECT COUNT(id) FROM #tmpdbs WHERE isdone = 0) > 0
BEGIN
    SELECT TOP 1 @dbname = [dbname], @dbid = [dbid] FROM #tmpdbs WHERE isdone = 0

    SET @query = 'SELECT ' + CAST(@dbid AS NVARCHAR) + ', ''' + @dbname + ''', [name], 0 FROM [' + @dbname + '].sys.filegroups WHERE [type] = ''FG'' AND is_read_only = 0;'
    INSERT INTO #tmpfgs
    EXEC (@query)

    UPDATE #tmpdbs
    SET isdone = 1
    WHERE [dbid] = @dbid
END;

IF (SELECT COUNT(ID) FROM #tmpfgs) > 0
BEGIN
    WHILE (SELECT COUNT(id) FROM #tmpfgs WHERE isdone = 0) > 0
    BEGIN
        SELECT TOP 1 @dbname = [dbname], @dbid = [dbid], @fgname = fgname FROM #tmpfgs WHERE isdone = 0

        SET @query = 'ALTER DATABASE [' + @dbname + '] MODIFY FILEGROUP [' + @fgname + '] AUTOGROW_ALL_FILES;'

        PRINT @query

        UPDATE #tmpfgs
        SET isdone = 1
        WHERE [dbid] = @dbid AND fgname = @fgname
    END
END; 
GO  
```      
  
## <a name="see-also"></a>См. также:  
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [DATABASEPROPERTYEX (Transact-SQL)](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [DROP DATABASE (Transact-SQL)](../../t-sql/statements/drop-database-transact-sql.md)   
 [sp_spaceused (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.data_spaces &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
 [sys.filegroups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sys.master_files &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [Большой двоичный объект &#40;BLOB-объект&#41;Данные&#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)   
 [DBCC SHRINKFILE (Transact-SQL)](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md)   
 [sp_filestream_force_garbage_collection (Transact-SQL)](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md)  
 [Инициализация файлов базы данных](../../relational-databases/databases/database-instant-file-initialization.md)    
  
  
