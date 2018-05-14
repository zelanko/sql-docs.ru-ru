---
title: DBCC SHRINKFILE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 11/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SHRINKFILE
- DBCC_SHRINKFILE_TSQL
- DBCC SHRINKFILE
- SHRINKFILE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- data shrinking [SQL Server]
- TRUNCATEONLY option
- shrinking files
- NOTRUNCATE option
- shrinking databases
- decreasing database size
- file shrinking [SQL Server]
- database shrinking [SQL Server]
- logs [SQL Server], shrinking
- reducing database size
- DBCC SHRINKFILE statement
ms.assetid: e02b2318-bee9-4d84-a61f-2fddcf268c9f
caps.latest.revision: 87
author: uc-msft
ms.author: umajay
manager: craigg
ms.openlocfilehash: 70ac1b9a973aff7f15309d29a85e3fddd6f2954f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="dbcc-shrinkfile-transact-sql"></a>DBCC SHRINKFILE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Сокращает размер указанного файла данных или журнала для текущей базы данных или освобождает файл, перемещая данные из указанного файла в другие файлы из той же файловой группы, разрешая удаление файла из базы данных. Можно сжать файл до размера, который будет меньше, чем размер, указанный во время его создания. В результате будет установлено новое значение минимального размера файла.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
  
DBCC SHRINKFILE   
(  
    { file_name | file_id }   
    { [ , EMPTYFILE ]   
    | [ [ , target_size ] [ , { NOTRUNCATE | TRUNCATEONLY } ] ]  
    }  
)  
[ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Аргументы  
*file_name*  
Логическое имя файла, предназначенного для сжатия.
  
*file_id*  
Идентификационный номер (идентификатор) файла, предназначенного для сжатия. Для получения идентификатора файла используйте функцию [FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md) или выполните запрос к представлению каталога [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md) текущей базы данных.
  
*target_size*  
Размер файла (в мегабайтах), выражаемый целым числом. Если он не указан, то инструкция DBCC SHRINKFILE уменьшает файл до размера файла по умолчанию. Размер по умолчанию представляет собой размер, указанный в момент создания файла.
  
> [!NOTE]  
>  Размер пустого файла, заданный по умолчанию, можно уменьшить с помощью инструкции DBCC SHRINKFILE *target_size*. Например, при создании файла с размером 5 МБ и последующем уменьшении размера до 3 МБ, в то время как файл остается пустым, размер файла по умолчанию задается равным 3 МБ. Это правило применимо только к пустым файлам, в которых никогда не содержались данные.  
  
Этот параметр не поддерживается для контейнеров файловых групп FILESTREAM.  
Если аргумент *target_size* указан, то инструкция DBCC SHRINKFILE пытается сжать файл до заданного размера. Используемые страницы в освобождаемой части файла перемещаются в свободное место сохраняемой части файла. Например, если размер файла данных составляет 10 МБ, инструкция DBCC SHRINKFILE со значением аргумента *target_size*, равным 8, перемещает все страницы, используемые в последних 2 МБ файла, на место любых нераспределенных страниц в первых 8 МБ файла. Инструкция DBCC SHRINKFILE не сжимает файл до меньшего размера, чем требуется для хранения данных в файле. Например, если в файле данных, размер которого составляет 10 МБ, используется 7 МБ, инструкция DBCC SHRINKFILE со значением аргумента *target_size*, равным 6, сжимает файл только до 7 МБ, а не до 6 МБ.
  
EMPTYFILE  
Переносит все данные из указанного файла в другие файлы в **той же файловой группе**. Другими словами, EmptyFile переносит данные из указанного файла в другие файлы в той же файловой группе. Emptyfile гарантирует, что новые данные не будут добавляться в файл. Файл можно удалить с помощью инструкции [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md).
Для контейнеров файловых групп FILESTREAM файл нельзя удалить с помощью ALTER DATABASE до тех пор, пока сборщик мусора FILESTREAM не выполнит и не удалит все ненужные файлы контейнеров файловых групп, которые были скопированы в другой контейнер с помощью EMPTYFILE. Дополнительные сведения см. в статье [sp_filestream_force_garbage_collection (Transact-SQL)](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md)
  
> [!NOTE]  
>  Сведения об удалении контейнера FILESTREAM см. в соответствующем разделе в статье [Параметры инструкции ALTER DATABASE для файлов и файловых групп (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md).  
  
NOTRUNCATE  
Перемещает распределенные страницы из конца файла данных на место нераспределенных страниц в начале файла с параметром *target_percent* или без него. Свободное место в конце файла операционной системе не возвращается, и физический размер файла не изменяется. Следовательно, если указан аргумент NOTRUNCATE, файл сжимается незначительно.
Аргумент NOTRUNCATE применим только к файлам данных. На файлы журнала он не влияет.   Этот параметр не поддерживается для контейнеров файловых групп FILESTREAM.
  
TRUNCATEONLY  
Освобождает все свободное пространство в конце файла операционной системе, но не перемещает страницы внутри файла. Файл данных сокращается только до последнего выделенного экстента.
Аргумент *target_size* не учитывается, если указан аргумент TRUNCATEONLY.  
Параметр TRUNCATEONLY не переносит сведения в журнале, но удаляет неактивные VLF в конце файла журнала. Этот параметр не поддерживается для контейнеров файловых групп FILESTREAM.
  
WITH NO_INFOMSGS  
Подавляет вывод всех информационных сообщений.
  
## <a name="result-sets"></a>Результирующие наборы  
В следующей таблице отображены столбцы результирующего набора.
  
|Имя столбца|Description|  
|---|---|
|**DbId**|Идентификатор базы данных, файл которой компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] пытался сжать.|  
|**FileId**|Идентификационный номер файла, сжатие которого было предпринято компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].|  
|**CurrentSize**|Количество 8-килобайтных страниц, занятых файлом в настоящее время.|  
|**MinimumSize**|Минимальное количество 8-килобайтных страниц, которое может занимать файл. Оно соответствует минимальному размеру или размеру файла, указанному при создании.|  
|**UsedPages**|Количество 8-килобайтных страниц, используемых файлом в настоящее время.|  
|**EstimatedPages**|Количество 8-килобайтных страниц, до которого можно было бы сжать файл по оценке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].|  
  
## <a name="remarks"></a>Remarks  
Инструкция DBCC SHRINKFILE применяется к файлам в текущей базе данных. Дополнительные сведения об изменении текущей базы данных см. в статье [USE (Transact-SQL)](../../t-sql/language-elements/use-transact-sql.md).
  
Операции DBCC SHRINKFILE могут быть остановлены на любом этапе процесса, при этом вся выполненная работа сохраняется. Если в файле используется параметр EMPTYFILE, в случае отмены операции файл не будет помечен, чтобы предотвратить добавление дополнительных данных.
  
В случае сбоя операции DBCC SHRINKFILE возникает ошибка.
  
 Сжимаемая база данных необязательно должна находиться в однопользовательском режиме; при выполнении сжатия файла в базе данных могут работать другие пользователи. Для сжатия системных баз данных также не обязательно запускать экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в однопользовательском режиме.  
  
## <a name="shrinking-a-log-file"></a>Сжатие файла журнала  
Для файлов журнала [!INCLUDE[ssDE](../../includes/ssde-md.md)] использует аргумент *target_size* для вычисления целевого размера всего журнала. Поэтому аргумент *target_size* является объемом свободного пространства в журнале после операции сжатия. Затем по заданному размеру всего журнала рассчитываются заданные размеры каждого файла журнала. Инструкция DBCC SHRINKFILE сразу же пытается сжать каждый физический файл журнала до намеченного размера. Однако если часть логического журнала хранится в виртуальных журналах за пределами заданного размера, то компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] освобождает как можно больше места, а затем формирует информационное сообщение. Сообщение описывает действия, которые необходимо предпринять, чтобы переместить логический журнал из виртуальных журналов в конец файла. После выполнения всех действий инструкция DBCC SHRINKFILE может быть использована для освобождения оставшегося пространства.
  
Так как файл журнала может быть сжат только до границы виртуального файла журнала, сжатие файла журнала к размеру, меньшему, чем размер виртуального файла журнала, невозможно, даже если он не используется. Размер виртуального файла журнала динамически выбирается компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)] при создании или расширении файлов журнала.
  
## <a name="best-practices"></a>Рекомендации  
Примите во внимание следующие сведения при планировании сжатия файла.
-   Наибольший эффект от операции сжатия достигается при ее применении после операции, создающей много неиспользуемого пространства, например после усечения таблицы или удаления таблицы.  
-   Большинству баз данных требуется некоторое свободное пространство для выполнения обычных ежедневных операций. Если сжатие базы данных производится регулярно, но она снова увеличивается в размерах, это означает, что место, освобожденное при сжатии, необходимо для нормальной работы. В таких случаях повторное сжатие базы данных бессмысленно.  
-   Операция сжатия не избавляет от фрагментации индексов в базе данных и обычно приводит к еще более сильной фрагментации. Это еще одна причина, по которой не стоит выполнять регулярное сжатие базы данных.  
-   Сжимайте несколько файлов в одной базе данных последовательно, а не одновременно. Состязание в системных таблицах может привести к задержке из-за блокировки.  
  
## <a name="troubleshooting"></a>Устранение неполадок  
Этот раздел описывает методы диагностики и устранения проблем, которые могут произойти при выполнении команды DBCC SHRINKFILE:
  
### <a name="the-file-does-not-shrink"></a>Файл не удалось сжать  
Если операция сжатия выполняется без ошибки, но файл не изменяется в размере, убедитесь, что он имеет свободное пространство для удаления, выполнив одну из следующих операций.
- Выполните следующий запрос.  
  
```sql
SELECT name ,size/128.0 - CAST(FILEPROPERTY(name, 'SpaceUsed') AS int)/128.0 AS AvailableSpaceInMB
FROM sys.database_files;
```

-   Выполните команду [DBCC SQLPERF](../../t-sql/database-console-commands/dbcc-sqlperf-transact-sql.md), чтобы освободить пространство, используемое журналом транзакций.  
Если свободного пространства недостаточно, операция сжатия не сможет уменьшить размер файла в дальнейшем.
  
Обычно это файл журнала, который сжимается незначительно. Это характерно для файла журнала, который не был усечен. Можно усечь файл журнала, установив значение SIMPLE для модели восстановления базы данных или создав резервную копию журнала, а затем выполнив операцию DBCC SHRINKFILE снова.
  
### <a name="the-shrink-operation-is-blocked"></a>Операция сжатия заблокирована  
Операции сжатия могут быть блокированы транзакцией, запущенной с [уровнем изоляции, основанным на управлении версиями строк](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md). Например, если при выполнении масштабной операции удаления с уровнем изоляции, основанном на управлении версиями строк, выполнить инструкцию DBCC SHRINK DATABASE, то, прежде чем приступить к сжатию файлов, она будет ожидать завершения операции удаления. В этом случае операции DBCC SHRINKFILE и DBCC SHRINKDATABASE выводят информационное сообщение (5202 для SHRINKDATABASE и 5203 для SHRINKFILE) в журнал ошибок SQL Server каждые 5 минут в течение первого часа, а затем по одному сообщению каждый час. Например, если журнал ошибок содержит следующее сообщение об ошибке, произойдет следующая ошибка.
  
```sql
DBCC SHRINKFILE for file ID 1 is waiting for the snapshot   
transaction with timestamp 15 and other snapshot transactions linked to   
timestamp 15 or with timestamps older than 109 to finish.  
```  
  
Это означает, что операция сжатия блокируется транзакциями моментального снимка, которые имеют отметки времени старше, чем метка 109, представляющая последнюю транзакцию, завершающую операцию сжатия. Это также показывает, что столбец **transaction_sequence_num** или **first_snapshot_sequence_num** в динамическом административном представлении [sys.dm_tran_active_snapshot_database_transactions](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md) содержит значение 15. Если столбцы **transaction_sequence_num** или **first_snapshot_sequence_num** в представлении содержат меньшее число, чем последняя транзакция, выполненная операцией сжатия (109), то операция сжатия будет ждать завершения этих транзакций.
  
Разрешить эту проблему можно одним из следующих способов.
-   Прервите выполнение транзакции, блокирующей операцию сжатия.
-   Прервите операцию сжатия. Если операция сжатия прервана, любая завершенная работа сохранена.  
-   Пока операция сжатия ожидает завершения блокирующей транзакции, ничего делать не нужно.  
  
## <a name="permissions"></a>Разрешения  
Необходимо быть членом предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** .
  
## <a name="examples"></a>Примеры  
  
### <a name="a-shrinking-a-data-file-to-a-specified-target-size"></a>A. Сжатие файла данных до указанного целевого размера  
В приведенном ниже примере файл данных с именем `DataFile1` в пользовательской базе данных `UserDB` сжимается до 7 МБ.
  
```sql  
USE UserDB;  
GO  
DBCC SHRINKFILE (DataFile1, 7);  
GO  
```  
  
### <a name="b-shrinking-a-log-file-to-a-specified-target-size"></a>Б. Сжатие файла журнала до указанного целевого размера  
В следующем примере файл журнала в базе данных `AdventureWorks` сжимается до 1 МБ. Чтобы разрешить команде DBCC SHRINKFILE сжать файл, сначала необходимо усечь его, установив значение SIMPLE в модели восстановления базы данных.
  
```sql  
USE AdventureWorks2012;  
GO  
-- Truncate the log by changing the database recovery model to SIMPLE.  
ALTER DATABASE AdventureWorks2012  
SET RECOVERY SIMPLE;  
GO  
-- Shrink the truncated log file to 1 MB.  
DBCC SHRINKFILE (AdventureWorks2012_Log, 1);  
GO  
-- Reset the database recovery model.  
ALTER DATABASE AdventureWorks2012  
SET RECOVERY FULL;  
GO  
```  
  
### <a name="c-truncating-a-data-file"></a>В. Усечение файла данных  
В следующем примере усекается первичный файл данных в базе данных `AdventureWorks`. Выполняется запрос к представлению каталога `sys.database_files` для получения идентификатора файла данных `file_id`.
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT file_id, name  
FROM sys.database_files;  
GO  
DBCC SHRINKFILE (1, TRUNCATEONLY);  
```  
  
### <a name="d-emptying-a-file"></a>Г. Очистка файла  
Следующий пример демонстрирует процедуру освобождения файла для его удаления из базы данных. Для этого примера создан файл данных, содержащий данные.
  
```sql  
USE AdventureWorks2012;  
GO  
-- Create a data file and assume it contains data.  
ALTER DATABASE AdventureWorks2012   
ADD FILE (  
    NAME = Test1data,  
    FILENAME = 'C:\t1data.ndf',  
    SIZE = 5MB  
    );  
GO  
-- Empty the data file.  
DBCC SHRINKFILE (Test1data, EMPTYFILE);  
GO  
-- Remove the data file from the database.  
ALTER DATABASE AdventureWorks2012  
REMOVE FILE Test1data;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
[ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[DBCC SHRINKDATABASE (Transact-SQL)](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md)  
[FILE_ID (Transact-SQL)](../../t-sql/functions/file-id-transact-sql.md)  
[sys.database_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)  
[Сжатие файла](../../relational-databases/databases/shrink-a-file.md)
  
  
