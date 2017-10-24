---
title: "DBCC (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC
- DBCC_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- transactional consistency
- Database Console Command statements
- status information [SQL Server], DBCC statements
- snapshots [SQL Server database snapshots], DBCC statements
- emergency database state [SQL Server]
- TABLOCK
- internal database snapshots [SQL Server]
- reporting DBCC statement progress
- logical consistency of data [SQL Server]
- DBCC statements
- validation statements [SQL Server]
- miscellaneous statements [SQL Server]
- statements [SQL Server], DBCC statements
- DBCC commands [SQL Server]
- result sets [SQL Server], DBCC statements
- maintenance statements [SQL Server]
- physical consistency of data [SQL Server]
- current DBCC statement status
- progress reporting [DBCC statements]
- informational statements [SQL Server]
ms.assetid: c6da8c04-5b6b-459a-9f76-110c92ca8b29
caps.latest.revision: 50
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8e8750f4b44ec206bb5a26586acd6b567f7dac37
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-transact-sql"></a>DBCC (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Язык [!INCLUDE[tsql](../../includes/tsql-md.md)] предоставляет инструкции DBCC, которые выступают в качестве консольных команд базы данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
Инструкции консольных команд базы данных группируются по следующим категориям.
  
|Категория команды|Выполнение|  
|---|---|
|Обслуживание|Обслуживание задач в базе данных, индексе или в файловой группе.|  
|Разное|Вспомогательные задачи, например установка флага трассировки или удаление из памяти библиотеки DLL.|  
|Информационные|Задачи, собирающие и отображающие разные типы сведений.|  
|Проверка|Проверочные операции в базе данных, таблице, индексе, каталоге, в файловой группе или распределение страниц базы данных.|  
  
Команды DBCC принимают входные параметры и возвращают значения. Все команды DBCC могут принимать в качестве параметров как литералы в Юникоде, так и литералы в двухбайтовой кодировке.
  
## <a name="dbcc-internal-database-snapshot-usage"></a>Использование внутреннего моментального снимка базы данных в командах DBCC  
Следующие команды DBCC выполняют операции с внутренним моментальным снимком базы данных, предназначенным только для чтения, который создает компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Тем самым предотвращаются проблемы блокировки и параллелизма при выполнении этих команд. Дополнительные сведения см. в разделе [Моментальные снимки базы данных (SQL Server)](../../relational-databases/databases/database-snapshots-sql-server.md).
- DBCC CHECKALLOC
- DBCC CHECKCATALOG
- DBCC CHECKDB
- DBCC CHECKFILEGROUP
- DBCC CHECKTABLE

При выполнении одной из этих команд DBCC компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] создает моментальный снимок базы данных и приводит ее в согласованное состояние на уровне транзакций. Затем команда DBCC выполняет проверку этого моментального снимка. После завершения команды DBCC этот моментальный снимок удаляется.
  
Иногда внутренний моментальный снимок базы данных не требуется или его невозможно создать. В этом случае команда DBCC выполняется в отношении реальной базы данных. Если база данных находится в режиме в сети, команда DBCC использует блокировку таблиц для обеспечения согласованности проверяемых объектов. Это поведение то же самое, как если бы был указан параметр WITH TABLOCK.
  
Внутренний моментальный снимок базы данных не создается, если команда DBCC выполняется:
-   К **master**и экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает в однопользовательском режиме.  
-   В базе данных, отличных от **master**, но база данных была переведена в однопользовательский режим, с помощью инструкции ALTER DATABASE.  
-   в базе данных, предназначенной только для чтения;  
-   в базе данных, которая была переведена в аварийный режим инструкцией ALTER DATABASE;  
-   К **tempdb**. В этом случае моментальный снимок базы данных невозможно создать из-за внутренних ограничений;  
-   с использованием параметра WITH TABLOCK. В этом случае команда DBCC соблюдает ограничение запроса и не создает моментальный снимок.  
  
Команды DBCC используют блокировки таблиц, а не внутренние моментальные снимки базы данных, если выполняются:
-   в файловой группе, предназначенной только для чтения;  
-   в файловой системе FAT;  
-   в томе, который не поддерживает «именованные потоки»;  
-   в томе, который не поддерживает «альтернативные потоки».  
  
> [!NOTE]  
>  Для запуска команды DBCC CHECKALLOC или эквивалентной части DBCC CHECKDB с параметром WITH TABLOCK требуется X-блокировка базы данных. Эта блокировка базы данных не может быть задано **tempdb** или **master** и может привести к ошибкам во всех остальных базах данных.  
  
> [!NOTE]  
>  Инструкция DBCC CHECKDB завершается со сбоем при запуске для **master** Если не удается создать моментальный снимок внутренней базы данных.  
  
## <a name="progress-reporting-for-dbcc-commands"></a>Формирование отчета о состоянии команд DBCC  
**Sys.dm_exec_requests** представление каталога содержит сведения о ходе выполнения и текущем этапе выполнения команд DBCC CHECKDB, CHECKFILEGROUP и CHECKTABLE. **Percent_complete** столбца указывается процент выполнения команды и **команда** столбца сообщает о текущем этапе выполнения команды.
  
Определение единицы хода выполнения зависит от текущего этапа выполнения команды DBCC. Иногда отчет о состоянии формируется на уровне гранулярности страницы базы данных, на других этапах — на уровне гранулярности одной базы данных или исправления распределения пространства. В следующей таблице представлены все этапы выполнения и уровень гранулярности, на котором команда формирует отчет о состоянии.
  
|Этап выполнения|Description|Уровень гранулярности отчетов о состоянии|  
|---------------------|-----------------|------------------------------------|  
|DBCC TABLE CHECK|Во время этого этапа проверяется логическая и физическая согласованность объектов в базе данных.|Отчет о состоянии сформирован на уровне страниц базы данных.<br /><br /> Значение отчета о состоянии обновляется через каждые 1000 проверенных страниц базы данных.|  
|DBCC TABLE REPAIR|Во время этого этапа выполняются исправления базы данных, если указывается параметр REPAIR_FAST, REPAIR_REBUILD или REPAIR_ALLOW_DATA_LOSS и имеются ошибки на уровне объектов.|Отчет о состоянии сформирован на уровне отдельных исправлений.<br /><br /> Счетчик обновляется для каждой завершенной операции исправления.|  
|DBCC ALLOC CHECK|Во время этого этапа проверяются структуры распределения.<br /><br /> Примечание: Инструкция DBCC CHECKALLOC выполняет те же проверки.|О состоянии не сообщается|  
|DBCC ALLOC REPAIR|Во время этого этапа выполняются исправления базы данных, если указывается параметр REPAIR_FAST, REPAIR_REBUILD или REPAIR_ALLOW_DATA_LOSS и имеются ошибки на уровне распределения пространства.|О состоянии не сообщается.|  
|DBCC SYS CHECK|Во время этого этапа проверяются системные таблицы базы данных.|Отчет о состоянии сформирован на уровне страниц базы данных.<br /><br /> Значение отчета о состоянии обновляется через каждую 1 000 проверенных страниц базы данных.|  
|DBCC SYS REPAIR|Во время этого этапа выполняются исправления базы данных, если указывается параметр REPAIR_FAST, REPAIR_REBUILD или REPAIR_ALLOW_DATA_LOSS и имеются ошибки на уровне системных таблиц.|Отчет о состоянии сформирован на уровне отдельных исправлений.<br /><br /> Счетчик обновляется для каждой завершенной операции исправления.|  
|DBCC SSB CHECK|Во время этого этапа проверяются объекты компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Broker.<br /><br /> Примечание: На этом этапе не выполняется при выполнении инструкции DBCC CHECKTABLE.|О состоянии не сообщается.|  
|DBCC CHECKCATALOG|Во время этого этапа проверяется согласованность каталогов базы данных.<br /><br /> Примечание: На этом этапе не выполняется при выполнении инструкции DBCC CHECKTABLE.|О состоянии не сообщается.|  
|DBCC IVIEW CHECK|Во время этого этапа проверяется логическая согласованность всех индексированных представлений базы данных.|Отчет о состоянии сформирован на уровне отдельных представлений баз данных.|  
  
## <a name="informational-statements"></a>Информационные инструкции  
  
|||  
|-|-|  
|[ИНСТРУКЦИЯ DBCC INPUTBUFFER](../../t-sql/database-console-commands/dbcc-inputbuffer-transact-sql.md)|[ИНСТРУКЦИЯ DBCC SHOWCONTIG](../../t-sql/database-console-commands/dbcc-showcontig-transact-sql.md)|  
|[ИНСТРУКЦИЯ DBCC OPENTRAN](../../t-sql/database-console-commands/dbcc-opentran-transact-sql.md)|[DBCC SQLPERF.](../../t-sql/database-console-commands/dbcc-sqlperf-transact-sql.md)|  
|[DBCC OUTPUTBUFFER](../../t-sql/database-console-commands/dbcc-outputbuffer-transact-sql.md)|[ИНСТРУКЦИЯ DBCC TRACESTATUS](../../t-sql/database-console-commands/dbcc-tracestatus-transact-sql.md)|  
|[DBCC PROCCACHE](../../t-sql/database-console-commands/dbcc-proccache-transact-sql.md)|[ИНСТРУКЦИЯ DBCC USEROPTIONS](../../t-sql/database-console-commands/dbcc-useroptions-transact-sql.md)|  
|[ИНСТРУКЦИЯ DBCC SHOW_STATISTICS](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)||  
  
## <a name="validation-statements"></a>Инструкции проверки  
  
|||  
|-|-|  
|[ИНСТРУКЦИЯ DBCC CHECKALLOC](../../t-sql/database-console-commands/dbcc-checkalloc-transact-sql.md)|[ИНСТРУКЦИЯ DBCC CHECKFILEGROUP](../../t-sql/database-console-commands/dbcc-checkfilegroup-transact-sql.md)|  
|[DBCC CHECKCATALOG](../../t-sql/database-console-commands/dbcc-checkcatalog-transact-sql.md)|[ИНСТРУКЦИЯ DBCC CHECKIDENT](../../t-sql/database-console-commands/dbcc-checkident-transact-sql.md)|  
|[DBCC CHECKCONSTRAINTS](../../t-sql/database-console-commands/dbcc-checkconstraints-transact-sql.md)|[ИНСТРУКЦИЯ DBCC CHECKTABLE](../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md)|  
|[ИНСТРУКЦИЯ DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)||  
  
## <a name="maintenance-statements"></a>Инструкции обслуживания  
  
|||  
|-|-|  
|[ИНСТРУКЦИЯ DBCC CLEANTABLE](../../t-sql/database-console-commands/dbcc-cleantable-transact-sql.md)|[ИНСТРУКЦИЯ DBCC INDEXDEFRAG](../../t-sql/database-console-commands/dbcc-indexdefrag-transact-sql.md)|  
|[ИНСТРУКЦИЯ DBCC DBREINDEX](../../t-sql/database-console-commands/dbcc-dbreindex-transact-sql.md)|[ИНСТРУКЦИЯ DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md)|  
|[DBCC DROPCLEANBUFFERS](../../t-sql/database-console-commands/dbcc-dropcleanbuffers-transact-sql.md)|[ИНСТРУКЦИЯ DBCC SHRINKFILE](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md)|  
|[ИНСТРУКЦИЯ DBCC FREEPROCCACHE](../../t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md)|[DBCC UPDATEUSAGE](../../t-sql/database-console-commands/dbcc-updateusage-transact-sql.md)|  
  
## <a name="miscellaneous-statements"></a>Вспомогательные инструкции  
  
|||  
|-|-|  
|[Имя DLL-библиотеки DBCC (FREE)](../../t-sql/database-console-commands/dbcc-dllname-free-transact-sql.md)|[DBCC HELP](../../t-sql/database-console-commands/dbcc-help-transact-sql.md)|  
|[DBCC FLUSHAUTHCACHE](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md)|[DBCC TRACEOFF](../../t-sql/database-console-commands/dbcc-traceoff-transact-sql.md)|  
|[DBCC FREESESSIONCACHE](../../t-sql/database-console-commands/dbcc-freesessioncache-transact-sql.md)|[DBCC TRACEON](../../t-sql/database-console-commands/dbcc-traceon-transact-sql.md)|  
|[DBCC FREESYSTEMCACHE](../../t-sql/database-console-commands/dbcc-freesystemcache-transact-sql.md)|[DBCC CLONEDATABASE](https://support.microsoft.com/en-us/kb/3177838) <br /><br /> **Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] пакетом обновления 2.|  
  
  

