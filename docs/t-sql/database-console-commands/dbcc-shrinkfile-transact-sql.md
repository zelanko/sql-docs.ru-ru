---
title: DBCC SHRINKFILE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 11/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: pmasl
ms.author: umajay
manager: craigg
ms.openlocfilehash: eb1f7d9efbbf260395cff607d5f8aa3209c677c4
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58872274"
---
# <a name="dbcc-shrinkfile-transact-sql"></a>DBCC SHRINKFILE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Эта инструкция позволяет сжать указанный файл данных или журнала в текущей базе данных. С помощью инструкции можно переместить данные из одного файла в другие файлы в той же файловой группе, одновременно очищая файл и разрешая его удаление из базы данных. Вы можете сжать файл до меньшего размера, чем при создании, указав новое значение для минимального размера файла.
  
![Значок ссылки на статью](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на статью") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
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
Идентификационный номер (идентификатор) файла, предназначенного для сжатия. Чтобы получить идентификатор файла, используйте системную функцию [FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md) или выполните запрос к представлению каталога [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md) в текущей базе данных.
  
*target_size*  
Целое число, которое обозначает новый размер файла в мегабайтах. Если значение не указано, инструкция DBCC SHRINKFILE уменьшает файл до его размера при создании.
  
> [!NOTE]  
>  Размер пустого файла по умолчанию можно уменьшить с помощью инструкции DBCC SHRINKFILE *target_size*. Например, при создании файла с размером 5 МБ и последующем уменьшении размера до 3 МБ, в то время как файл остается пустым, размер файла по умолчанию задается равным 3 МБ. Это правило применимо только к пустым файлам, в которых никогда не содержались данные.  
  
Контейнеры файловых групп FILESTREAM не поддерживают этот параметр.  
Если он указан, то инструкция DBCC SHRINKFILE пытается сжать файл до размера *target_size*. Используемые страницы в освобождаемой области файла перемещаются в свободное пространство в сохраняемых областях файла. Например, для файла данных размером 10 МБ при операции DBCC SHRINKFILE с *target_size* 8 все используемые страницы будут перемещены из последних 2 МБ файла на произвольные нераспределенные страницы в первых 8 МБ этого же файла. DBCC SHRINKFILE не сжимает файл не более, чем это нужно для хранимых данных. Например, если в файле данных, размер которого составляет 10 МБ, используется 7 МБ, инструкция DBCC SHRINKFILE со значением аргумента *target_size*, равным 6, сжимает файл только до 7 МБ, а не до 6 МБ.
  
EMPTYFILE  
Переносит все данные из указанного файла в другие файлы в **той же файловой группе**. Другими словами, EMPTYFILE переносит данные из указанного файла в другие файлы в той же файловой группе. EMPTYFILE гарантирует, что новые данные не будут добавлены в файл, даже если в него разрешена запись. Для удаления файла можно использовать инструкцию [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md). Если с помощью инструкции [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) изменяется размер файла, флаг "только для чтения" сбрасывается, позволяя добавлять данные.

В контейнерах файловых групп FILESTREAM нельзя удалить файл с помощью ALTER DATABASE до тех пор, пока не будет выполнен сборщик мусора FILESTREAM, который удалит все ненужные файлы в контейнере файловых групп, скопированные в другой контейнер с помощью EMPTYFILE. Дополнительные сведения см. в статье [sp_filestream_force_garbage_collection (Transact-SQL)](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md)
  
> [!NOTE]  
>  Сведения об удалении контейнера FILESTREAM см. в соответствующем разделе в статье [Параметры инструкции ALTER DATABASE для файлов и файловых групп (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md).  
  
NOTRUNCATE  
Позволяет переместить распределенные страницы из конца файла данных на нераспределенные страницы в начале файла с указанием или без указания *target_percent*. Свободное место в конце файла не возвращается операционной системе, а физический размер файла не изменяется. Таким образом, если указан аргумент NOTRUNCATE, сжатие файла незаметно.
Аргумент NOTRUNCATE применим только к файлам данных. На файлы журнала он не влияет.   Контейнеры файловых групп FILESTREAM не поддерживают этот параметр.
  
TRUNCATEONLY  
Возвращает операционной системе все свободное пространство в конце файла, но не перемещает страницы внутри файла. Файл данных сокращается только до последнего выделенного экстента.
Аргумент *target_size* не учитывается, если указан аргумент TRUNCATEONLY.  
Параметр TRUNCATEONLY не переносит сведения в журнале, но удаляет неактивные VLF в конце файла журнала. Контейнеры файловых групп FILESTREAM не поддерживают этот параметр.
  
WITH NO_INFOMSGS  
Подавляет вывод всех информационных сообщений.
  
## <a name="result-sets"></a>Результирующие наборы  
В приведенной ниже таблице описаны столбцы результирующего набора.
  
|Имя столбца|Описание|  
|---|---|
|**DbId**|Идентификатор базы данных, файл которой компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] пытался сжать.|  
|**FileId**|Идентификационный номер файла, сжатие которого было предпринято компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].|  
|**CurrentSize**|Количество 8-килобайтных страниц, занятых файлом в настоящее время.|  
|**MinimumSize**|Минимальное количество 8-килобайтных страниц, которое может занимать файл. Это число соответствует минимальному размеру файла при его создании.|  
|**UsedPages**|Количество 8-килобайтных страниц, используемых файлом в настоящее время.|  
|**EstimatedPages**|Количество 8-килобайтных страниц, до которого можно было бы сжать файл по оценке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].|  
  
## <a name="remarks"></a>Remarks  
Инструкция DBCC SHRINKFILE применяется к файлам в текущей базе данных. Дополнительные сведения об изменении текущей базы данных см. в статье [USE (Transact-SQL)](../../t-sql/language-elements/use-transact-sql.md).
  
Вы можете в любой момент остановить операцию DBCC SHRINKFILE, и вся выполненная работа сохранится. Если вы отмените операцию, для которой указан параметр EMPTYFILE, маркировка файла, предотвращающая добавление новых данных, не устанавливается.
  
В случае сбоя операции DBCC SHRINKFILE возникает ошибка.
  
 Во время сжатия файла в базе данных могут работать другие пользователи, то есть однопользовательский режим для базы данных не требуется. Для сжатия системных баз данных не обязательно запускать экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в однопользовательском режиме.  
  
## <a name="shrinking-a-log-file"></a>Сжатие файла журнала  

Для файлов журнала с помощью [!INCLUDE[ssDE](../../includes/ssde-md.md)] вычисляется целевой размер всего журнала на основе *target_size*. Таким образом, *target_size* указывает размер свободного места в журнале после операции сжатия. Затем по заданному размеру всего журнала рассчитываются заданные размеры каждого файла журнала. Инструкция DBCC SHRINKFILE сразу же пытается сжать каждый физический файл журнала до намеченного размера. Однако если часть логического журнала хранится в виртуальных журналах за пределами заданного размера, то компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] освобождает как можно больше места, а затем формирует информационное сообщение. Сообщение описывает действия, которые необходимо предпринять, чтобы переместить логический журнал из виртуальных журналов в конец файла. После выполнения всех действий инструкция DBCC SHRINKFILE может быть использована для освобождения оставшегося пространства.
  
Так как файл журнала можно сжать только до границы виртуального файла журнала, сжать файл журнала до меньшего размера, чем у виртуального файла журнала, нельзя, даже если он не используется. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] динамически выбирает размер виртуального файла журнала при его создании или расширении.
  
## <a name="best-practices"></a>Рекомендации 
 
Примите во внимание следующие сведения при планировании сжатия файла.
-   Максимальный эффект от сжатия достигается после операции, при которой создается много неиспользуемого пространства, например после усечения или удаления таблицы.  

-   Большинству баз данных для выполнения обычных ежедневных операций требуется некоторый объем свободного места. Если вы регулярно сжимаете базу данных, но ее размер постоянно увеличивается, скорее всего, освобождаемое пространство необходимо для обычной работы базы данных. В таких случаях повторное сжатие базы данных бессмысленно.  

-   Операция сжатия не исключает фрагментацию индексов в базе данных и даже, наоборот, приводит к усилению фрагментации. Фрагментация — это еще одна причина, по которой не стоит регулярно сжимать базу данных.  

-   Сжимайте несколько файлов в одной базе данных последовательно, а не одновременно. Состязание в системных таблицах может привести к задержке из-за блокировки.  
  
## <a name="troubleshooting"></a>Устранение неполадок  
Этот раздел описывает методы диагностики и устранения проблем, которые могут произойти при выполнении команды DBCC SHRINKFILE:
  
### <a name="the-file-doesnt-shrink"></a>Файл не сжимается
  
Если размер файла не изменяется после сжатия, которое было выполнено без ошибок, проверьте, есть свободное место в файле, с помощью следующей команды:

- Выполните следующий запрос.  
  
```sql
SELECT name ,size/128.0 - CAST(FILEPROPERTY(name, 'SpaceUsed') AS int)/128.0 AS AvailableSpaceInMB
FROM sys.database_files;
```

-   Выполните команду [DBCC SQLPERF](../../t-sql/database-console-commands/dbcc-sqlperf-transact-sql.md), чтобы освободить пространство, используемое журналом транзакций.  

Если свободного пространства недостаточно, сжатие не поможет уменьшить размер файла.
  
Чаще всего результаты сжатия незаметны для файлов журнала. Такая несжимаемость характерна для неусеченных файлов журнала. Чтобы усечь файл журнала, установите значение SIMPLE для модели восстановления базы данных или создайте резервную копию журнала и снова выполните операцию DBCC SHRINKFILE.
  
### <a name="the-shrink-operation-is-blocked"></a>Операция сжатия блокируется  

Транзакция, запущенная [под уровнем изоляции с управлением версиями строк](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md), может блокировать операции сжатия. Например, если выполняется масштабная операция удаления под уровнем изоляции с управлением версиями строк, запущенная инструкция DBCC SHRINK DATABASE будет ожидать, пока завершится такая операция удаления, прежде чем приступить к сжатию файлов. При возникновении такой блокировки для операций DBCC SHRINKFILE и DBCC SHRINKDATABASE в журнале ошибок SQL Server выводится информационное сообщение (5202 для SHRINKDATABASE и 5203 для SHRINKFILE). Это сообщение регистрируется каждые 5 минут в течение первого часа, а затем по одному разу каждый час Например, если журнал ошибок содержит следующее сообщение об ошибке, произойдет следующая ошибка.
  
```sql
DBCC SHRINKFILE for file ID 1 is waiting for the snapshot   
transaction with timestamp 15 and other snapshot transactions linked to   
timestamp 15 or with timestamps older than 109 to finish.  
```  
  
Такое сообщение означает, что операция сжатия блокируется транзакциями с моментальным снимком, отметка времени которого старше, чем 109 (это последняя транзакция, завершенная операцией сжатия). Также сообщение информирует, что столбец **transaction_sequence_num** или **first_snapshot_sequence_num** в динамическом административном представлении [sys.dm_tran_active_snapshot_database_transactions](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md) содержит значение 15. Если столбец **transaction_sequence_num** или **first_snapshot_sequence_num** в представлении содержит меньшее число, чем последняя транзакция, выполненная операцией сжатия (109), то операция сжатия будет ждать завершения этих транзакций.
  
Разрешить эту проблему можно одним из следующих способов.
-   Прервите выполнение транзакции, которая блокирует операцию сжатия.
-   Прервите операцию сжатия. При прерывании операции сжатия вся уже выполненная работа сохраняется.  
-   Пока операция сжатия ожидает завершения блокирующей транзакции, ничего делать не нужно.  
  
## <a name="permissions"></a>Разрешения  
Необходимо быть членом предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** .
  
## <a name="examples"></a>Примеры  
  
### <a name="shrinking-a-data-file-to-a-specified-target-size"></a>Сжатие файла данных до указанного целевого размера  
В приведенном ниже примере файл данных с именем `DataFile1` в пользовательской базе данных `UserDB` сжимается до 7 МБ.
  
```sql  
USE UserDB;  
GO  
DBCC SHRINKFILE (DataFile1, 7);  
GO  
```  
  
### <a name="shrinking-a-log-file-to-a-specified-target-size"></a>Сжатие файла журнала до указанного целевого размера  
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
Следующий пример демонстрирует процедуру очистки файла для его удаления из базы данных. Для этого примера сначала создается файл, содержащий данные.
  
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
  
  
