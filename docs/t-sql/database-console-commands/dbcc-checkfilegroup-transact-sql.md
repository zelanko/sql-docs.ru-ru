---
title: "Инструкция DBCC CHECKFILEGROUP (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 11/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CHECKFILEGROUP_TSQL
- DBCC_CHECKFILEGROUP_TSQL
- DBCC CHECKFILEGROUP
- CHECKFILEGROUP
dev_langs:
- TSQL
helpviewer_keywords:
- DBCC CHECKFILEGROUP statement
- database objects [SQL Server], checking
- allocation checks
- integrity [SQL Server], database objects
- filegroups [SQL Server], consistency checks
- table integrity checks [SQL Server]
- checking database objects
ms.assetid: 8c70bf34-7570-4eb6-877a-e35064a1380a
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fc36aa0cfddcceefda1aefc6f4e7dc040f9a4b5f
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-checkfilegroup-transact-sql"></a>DBCC CHECKFILEGROUP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]В проверке распределения и структурной целостности всех таблиц и индексированных представлений в указанной файловой группе текущей базы данных.
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
  
DBCC CHECKFILEGROUP   
[  
    [ ( { filegroup_name | filegroup_id | 0 }   
        [ , NOINDEX ]   
  ) ]  
    [ WITH   
        {   
            [ ALL_ERRORMSGS | NO_INFOMSGS ]   
            [ , TABLOCK ]   
            [ , ESTIMATEONLY ]  
            [ , PHYSICAL_ONLY ]    
            [ , MAXDOP  = number_of_processors ]  
        }   
    ]  
]  
```  
  
## <a name="arguments"></a>Аргументы  
 *filegroup_name*  
 Имя файловой группы текущей базы данных, для которой производится проверка распределения и структурной целостности таблиц. Если не указано или равно 0, по умолчанию используется первичная файловая группа. Файловая группа имена должны соответствовать требованиям, предъявляемым к [идентификаторы](../../relational-databases/databases/database-identifiers.md).  
 *filegroup_name* не может быть файловая группа FILESTREAM.  
  
 *filegroup_id*  
 Идентификатор файловой группы текущей базы данных, для которой производится проверка распределения и структурной целостности.  
  
 NOINDEX  
 Указывает, что тщательную проверку некластеризованных индексов для пользовательских таблиц выполнять не следует. Это уменьшает общее время выполнения. Аргумент NOINDEX не оказывает влияния на системные таблицы, так как инструкция DBCC CHECKFILEGROUP всегда проверяет все индексы системных таблиц.  
  
 ALL_ERRORMSGS  
 Отображает неограниченное число ошибок на каждый объект. Все сообщения об ошибках выводятся по умолчанию. Указание или пропуск этого параметра не приводит к изменениям.  
  
 NO_INFOMSGS  
 Подавляет вывод всех информационных сообщений.  
  
 TABLOCK  
 Заставляет инструкцию DBCC CHECKFILEGROUP устанавливать блокировку вместо использования внутреннего моментального снимка базы данных.  
  
 ESTIMATE ONLY  
 Отображает оценочный объем места в базе данных tempdb, необходимый для запуска инструкции DBCC CHECKFILEGROUP со всеми остальными заданными параметрами.  
  
 PHYSICAL_ONLY  
 Ограничивает область проверки целостностью физической структуры страниц, заголовков записей и физической структуры сбалансированных деревьев. Параметр предназначен для выполнения облегченной проверки физической согласованности файловой группы, а также может выявлять поврежденные страницы и общие сбои оборудования, которые могут нарушить целостность данных. Полное выполнение инструкции DBCC CHECKFILEGROUP может занять значительно больше времени, чем в предыдущих версиях. Это вызвано следующими причинами.  
 -   Логические проверки стали более сложными.  
 -   Усложнился ряд базовых структур, нуждающихся в проверке.  
 -   Добавлено много новых проверок для поддержки новых функций.  
 Таким образом, применение параметра PHYSICAL_ONLY может значительно сократить время выполнения инструкции DBCC CHECKFILEGROUP для больших файловых групп, поэтому рекомендуется использовать его для частых проверок в рабочих системах. Также рекомендуется периодически производить полный запуск инструкции DBCC CHECKFILEGROUP. Периодичность запуска зависит от факторов, индивидуальных для каждого предприятия и каждой производственной среды. Аргумент PHYSICAL_ONLY всегда неявно включает аргумент NO_INFOMSGS и не должен указываться вместе с параметрами исправления ошибок.  
  
> [!NOTE]  
>  Указание аргумента PHYSICAL_ONLY приводит к пропуску инструкцией DBCC CHECKFILEGROUP всех проверок данных FILESTREAM.  
  
 MAXDOP  
 **Применяется к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 SP2 через [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658).  
  
 Переопределяет **максимальная степень параллелизма** параметр конфигурации **sp_configure** для инструкции. MAXDOP может превысить значение, настроенное с помощью хранимой процедуры sp_configure. Если MAXDOP превышает значение, настроенное с помощью регулятора ресурсов, компонент Database Engine использует значение MAXDOP регулятора ресурсов, описанное в инструкцию ALTER WORKLOAD GROUP (Transact-SQL). Все семантические правила, используемые параметром конфигурации max degree of parallelism, применимы при использовании указания запроса MAXDOP. Дополнительные сведения см. в разделе [Настройка параметра конфигурации сервера max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md).  
  
> [!CAUTION]  
>  Если значение MAXDOP равно нулю, то сервер выбирает максимальную степень параллелизма.  
  
## <a name="remarks"></a>Remarks  
Команды DBCC CHECKFILEGROUP и DBCC CHECKDB похожи. Основное отличие состоит в том, что инструкция DBCC CHECKFILEGROUP ограничена отдельной конкретной файловой группой и обязательными таблицами.
Инструкция DBCC CHECKFILEGROUP выполняет следующие команды.
-   [Инструкция DBCC CHECKALLOC](../../t-sql/database-console-commands/dbcc-checkalloc-transact-sql.md) файловой группы.  
-   [Инструкция DBCC CHECKTABLE](../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md) из каждой таблицы и индексированные представления в файловой группе.  
  
Запуск инструкций DBCC CHECKALLOC или DBCC CHECKTABLE отдельно от DBCC CHECKFILEGROUP не требуется.
  
## <a name="internal-database-snapshot"></a>Моментальный снимок внутренней базы данных  
В инструкции DBCC CHECKFILEGROUP используется внутренний моментальный снимок базы данных для обеспечения согласованности транзакций, необходимой для выполнения таких проверок. Дополнительные сведения см. в разделе [Просмотр размера разреженного файла моментального снимка базы данных &#40; Transact-SQL &#41; ](../../relational-databases/databases/view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md) и в разделе «DBCC внутренней базы данных моментальных снимков использование» [DBCC &#40; Transact-SQL &#41; ](../../t-sql/database-console-commands/dbcc-transact-sql.md).
Если моментальный снимок создать невозможно или указан параметр TABLOCK, инструкция DBCC CHECKFILEGROUP устанавливает блокировки для получения необходимой согласованности. В таком случае для проверки выделенных ресурсов необходима монопольная блокировка базы данных, а для проверки таблиц — разделяемая блокировка таблицы. Аргумент TABLOCK позволяет быстрее выполнять инструкцию DBCC CHECKFILEGROUP в базе данных с большой загрузкой, но уменьшает уровень доступного параллелизма для базы данных во время запуска инструкции DBCC CHECKFILEGROUP.
  
> [!NOTE]  
>  При выполнении инструкции DBCC CHECKFILEGROUP в базе данных tempdb не выполняется никакой проверки выделенных ресурсов, а для выполнения проверки таблиц необходимо получить совмещаемую блокировку таблицы. Это обусловлено тем, что по соображениям, связанным с производительностью, моментальные снимки базы данных недоступны для базы данных tempdb. Это означает, что нельзя достичь требуемой согласованности транзакций.  
  
## <a name="checking-objects-in-parallel"></a>Проверка объектов в параллельном режиме  
По умолчанию инструкция DBCC CHECKFILEGROUP выполняет параллельную проверку объектов. Степень параллелизма определяется автоматически обработчиком запросов. Максимальная степень параллелизма настраивается так же, как и в параллельных запросах. Чтобы ограничить максимальное количество процессоров, доступных для проверки DBCC, используется [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md). Дополнительные сведения см. в разделе [Настройка параметра конфигурации сервера max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md).
Параллельную проверку можно отключить с помощью флага трассировки 2528. Дополнительные сведения см. в разделе [Флаги трассировки (Transact-SQL)](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).
  
## <a name="nonclustered-indexes-on-separate-filegroups"></a>Некластеризованные индексы для отдельных файловых групп  
Если некластеризованный индекс в указанной файловой группе связан с таблицей в другой файловой группе, индекс не проверяется, так как базовая таблица недоступна для проверки.
Если для таблицы из проверяемой файловой группы имеется некластеризованный индекс в другой файловой группе, этот индекс не проверяется по следующим причинам.
-   Структура базовой таблицы не зависит от структуры некластеризованного индекса. Для проверки базовой таблицы просмотр некластеризованных индексов не требуется.  
-   Команда DBCC CHECKFILEGROUP проверяет объекты только в указанной файловой группе.  
Кластеризованный индекс и таблица не могут принадлежать к различным файловым группам, поэтому предыдущие соображения применяются только к некластеризованным индексам.
  
## <a name="partitioned-tables-on-separate-filegroups"></a>Секционированные таблицы в отдельных файловых группах  
Если секционированная таблица расположена в нескольких файловых группах, то команда DBCC CHECKFILEGROUP проверяет наборы строк секции, существующие в указанной файловой группе, и не обрабатывает наборы строк в других файловых группах. Информационное сообщение 2594 указывает непроверенные секции. Некластеризованные индексы, не расположенные в указанной файловой группе, не проверяются.
  
## <a name="understanding-dbcc-error-messages"></a>Основные сведения о сообщениях об ошибках DBCC  
После завершения выполнения команды DBCC CHECKFILEGROUP в журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] записывается сообщение. При успешном выполнении команды DBCC сообщается об успешном завершении и количестве времени, затраченном на выполнение команды. Если выполнение команды DBCC прерывается до завершения проверки по причине ошибки, сообщение указывает на прерывание команды и приводит значение состояния и количество времени, затраченного на выполнение команды. В следующей таблице перечислены и описаны значения состояний, которые могут быть включены в сообщение.
  
|Состояние|Описание|  
|-----------|-----------------|  
|0|Возникла ошибка с номером 8930. Это указывает на повреждение метаданных, вызвавшее прекращение выполнения команды DBCC.|  
|1|Возникла ошибка с номером 8967. Внутренняя ошибка DBCC.|  
|2|При аварийном восстановлении базы данных произошла ошибка.|  
|3|Это указывает на повреждение метаданных, вызвавшее прекращение выполнения команды DBCC.|  
|4|Обнаружено нарушение доступа или утверждения.|  
|5|Возникла неизвестная ошибка, которая привела к прекращению выполнения команды DBCC.|  
  
## <a name="error-reporting"></a>Отчет об ошибках  
Файл мини-дампа (SQLDUMP*nnnn*.txt) создается в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] каталог ЖУРНАЛА всякий раз, когда инструкция DBCC CHECKFILEGROUP обнаруживает ошибку повреждения. При включении сбора данных об использовании компонентов и отчета об ошибках для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], файл автоматически отправляется корпорации Майкрософт [!INCLUDE[msCoName](../../includes/msconame-md.md)]. Собранные данные используются для улучшения функциональности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
Файл дампа содержит результаты выполнения команды DBCC CHECKFILEGROUP и дополнительные диагностические сведения. Доступ к этому файлу ограничен списками управления доступом на уровне пользователей. Доступ ограничен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетная запись службы и члены **sysadmin** роли. По умолчанию **sysadmin** роль содержит всех членов группы Windows BUILTIN\Administrators и группы локальных администраторов. В случае ошибки процесса сбора данных команда DBCC не завершается ошибкой.
  
## <a name="resolving-errors"></a>Разрешение ошибок  
Если инструкцией DBCC CHECKFILEGROUP выдаются какие-либо ошибки, рекомендуется восстановить базу данных из резервной копии. Обратите внимание, что для инструкции DBCC CHECKFILEGROUP параметры восстановления указать нельзя.
В случае отсутствия резервных копий запуск инструкции DBCC CHECKDB с заданным параметром восстановления позволяет исправить выдаваемые ошибки. Если выдаются ошибки, используемый параметр восстановления указывается в конце списка. При исправлении ошибок с помощью аргумента REPAIR_ALLOW_DATA_LOSS может потребоваться удаление некоторых страниц и, следовательно, данных.
  
## <a name="result-sets"></a>Результирующие наборы  
Инструкция DBCC CHECKFILEGROUP возвращает следующий результирующий набор (значения могут различаться):
-   кроме случаев, когда заданы параметры ESTIMATEONLY или NO_INFOMSGS;  
-   для текущей базы данных, если база данных не указана, независимо от того, заданы ли какие-либо аргументы (кроме NOINDEX).  
  
```sql
DBCC results for 'master'.  
DBCC results for 'sys.sysrowsetcolumns'.  
There are 630 rows in 7 pages for object 'sys.sysrowsetcolumns'.  
DBCC results for 'sys.sysrowsets'.  
There are 97 rows in 1 pages for object 'sys.sysrowsets'.  
DBCC results for 'sysallocunits'.  
There are 195 rows in 3 pages for object 'sysallocunits'.  
  
There are 2340 rows in 16 pages for object 'spt_values'.  
DBCC results for 'MSreplication_options'.  
There are 2 rows in 1 pages for object 'MSreplication_options'.  
CHECKFILEGROUP found 0 allocation errors and 0 consistency errors in database 'master'.  
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
Если задан аргумент NO_INFOMSGS, инструкция DBCC CHECKFILEGROUP возвращает:
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
 Если задан аргумент ESTIMATEONLY, инструкция DBCC CHECKFILEGROUP возвращает следующее (значения могут различаться):  

```sql
Estimated TEMPDB space needed for CHECKALLOC (KB)
-------------------------------------------------   
15  
  
(1 row(s) affected)  
  
Estimated TEMPDB space needed for CHECKTABLES (KB)   
--------------------------------------------------   
207  
  
(1 row(s) affected)  
  
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Разрешения  
Необходимо быть членом предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** .
  
## <a name="examples"></a>Примеры  
### <a name="a-checking-the-primary-filegroup-in-the-a-database"></a>A. Проверка файловой группы PRIMARY в базе данных  
В следующем примере выполняется проверка первичной файловой группы текущей базы данных.
  
```sql  
  
DBCC CHECKFILEGROUP;  
GO  
```  
  
### <a name="b-checking-the-adventureworks-primary-filegroup-without-nonclustered-indexes"></a>Б. Проверка первичной файловой группы (PRIMARY) базы данных AdventureWorks без некластеризованных индексов  
В следующем примере проверяется `AdventureWorks2012` первичной файловой группы базы данных (за исключением некластеризованных индексов) путем указания идентификационного номера первичной файловой группы и указав `NOINDEX`.
  
```sql  
USE AdventureWorks2012;  
GO  
DBCC CHECKFILEGROUP (1, NOINDEX);  
GO  
```  
  
### <a name="c-checking-the-primary-filegroup-with-options"></a>В. Проверка первичной файловой группы с параметрами  
В следующем примере выполняется проверка первичной файловой группы базы данных `master` с указанием параметра `ESTIMATEONLY`.
  
```sql  
USE master;  
GO  
DBCC CHECKFILEGROUP (1)  
WITH ESTIMATEONLY;  
```  
  
## <a name="see-also"></a>См. также  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[FILEGROUP_ID &#40; Transact-SQL &#41;](../../t-sql/functions/filegroup-id-transact-sql.md)  
[sp_helpfile &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)  
[sp_helpfilegroup &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpfilegroup-transact-sql.md)  
[sys.sysfilegroups &#40; Transact-SQL &#41;](../../relational-databases/system-compatibility-views/sys-sysfilegroups-transact-sql.md)  
[DBCC CHECKDB (Transact-SQL)](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
[DBCC CHECKALLOC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-checkalloc-transact-sql.md)  
[DBCC CHECKTABLE (Transact-SQL)](../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md)
  
  
