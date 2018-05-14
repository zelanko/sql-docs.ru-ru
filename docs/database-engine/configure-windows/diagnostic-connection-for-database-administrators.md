---
title: Диагностическое соединение для администраторов баз данных | Документы Майкрософт
ms.custom: ''
ms.date: 10/16/2015
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- server management [SQL Server], connections
- administrator connections [SQL Server]
- ports [SQL Server], DAC
- DAC
- network connections [SQL Server], dedicated administrator
- diagnostic connections [SQL Server]
- connections [SQL Server], dedicated administrator
- ports [SQL Server]
- dedicated administrator connections [SQL Server]
ms.assetid: 993e0820-17f2-4c43-880c-d38290bf7abc
caps.latest.revision: 65
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a26a318a0675c0c0fe54e31ac8ea33376c1b2e6a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="diagnostic-connection-for-database-administrators"></a>Диагностическое соединение для администраторов баз данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет специальное диагностическое соединение для администраторов, когда стандартное соединение с сервером невозможно. Это диагностическое соединение позволяет администратору получить доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения диагностических запросов и устранения проблем, даже когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не отвечает на стандартные запросы на соединение.  
  
 Такое выделенное административное соединение (DAC) поддерживает шифрование и другие средства безопасности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Выделенное административное соединение позволяет только изменять контекст пользователя на другого пользователя с правами администратора.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] делает все возможное для успешного установления выделенного административного соединения, но в чрезвычайных ситуациях это может не дать результата.  
  
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
## <a name="connecting-with-dac"></a>Соединение с помощью выделенного административного соединения  
 По умолчанию, соединение разрешено только из клиента, запущенного на сервере. Сетевые подключения не разрешаются, пока они не настроены с помощью хранимой процедуры sp_configure с параметром [remote admin connections](../../database-engine/configure-windows/remote-admin-connections-server-configuration-option.md).  
  
 Только члены роли [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sysadmin могут подключаться с использованием выделенного административного соединения.  
  
 Выделенное административное соединение доступно и поддерживается через программу командной строки **sqlcmd** со специальным административным параметром (**-A**). Дополнительные сведения об использовании **sqlcmd** см. в разделе [Использование программы sqlcmd с переменными скрипта](../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md). Можно также подключиться, добавив префикс **admin:** к имени экземпляра следующим образом: **sqlcmd -S admin:<*имя_экземпляра*>**. Соединение DAC можно также инициировать через редактор запросов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], подключившись к **admin:\<*имя_экземпляра*>**.  
  
## <a name="restrictions"></a>Ограничения  
 Так как выделенное административное соединение существует только для диагностики проблем на сервере в редких обстоятельствах, у подключения есть некоторые ограничения.  
  
-   Чтобы гарантировать, что для подключения есть доступные ресурсы, на один экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]разрешено только одно выделенное административное соединение. Если выделенное административное соединение уже активно, любой новый запрос на соединение через DAC отклоняется с ошибкой 17810.  
  
-   Для экономии ресурсов [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] прослушивает порт выделенного административного соединения только при запуске с флагом трассировки 7806.  
  
-   Сначала выделенное административное соединение подключается к базе данных по умолчанию, связанной с именем входа. После успешного соединения можно подключиться к базе данных master. Если база данных по умолчанию находится в режиме вне сети или недоступна по другой причине, соединение вернет ошибку 4060. При этом соединение будет успешным, если вместо базы данных по умолчанию подключиться к базе данных master с помощью следующей команды:  
  
     **sqlcmd –A –d master**  
  
     Рекомендуется подключаться через выделенное административное соединение к базе данных master, так как база данных master будет в любом случае доступна, если запущен экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запрещает выполнение параллельных запросов или команд через выделенное административное соединение. Например, ошибка 3637 возникает при выполнении через выделенное административное соединение любой из следующих инструкций:  
  
    -   RESTORE  
  
    -   BACKUP  
  
-   Через выделенное административное соединение гарантированно доступны только ограниченные ресурсы. Не используйте выделенное административное соединение для запуска ресурсоемких запросов (например, сложного соединения для большой таблицы) или запросов, которые могут блокироваться. Это позволяет обезопасить выделенное административное соединение от осложнения любыми существующими проблемами на сервере. Чтобы избежать сценариев, которые могут приводить к блокировке, следует при возможности запускать запросы, которые могут вызвать блокировку, на уровне изоляции моментального снимка. В противном случае следует установить уровень изоляции транзакций READ UNCOMMITTED и малое значение LOCK_TIMEOUT, например 2000 миллисекунд. Можно также использовать оба способа одновременно. Это позволит предотвратить блокировку сеанса выделенного административного соединения. Но в зависимости от состояния [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сеанс выделенного административного соединения может быть заблокирован с помощью кратковременной блокировки. Возможно, удастся завершить сеанс DAC с помощью клавиш CTRL+C, но это не гарантируется. В таком случае единственным вариантом остается перезапуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Чтобы гарантировать соединение и устранение неполадок через выделенное административное соединение, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] резервирует ограниченные ресурсы для обработки команд, запущенных через него. Этих ресурсов обычно хватает только для простых диагностических функций и устранения неполадок, которые приведены ниже.  
  
 Теоретически можно запустить любую инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] , которая не должна исполняться параллельно через выделенное административное соединение, но корпорация Майкрософт настоятельно рекомендует ограничиться применением следующих команд диагностики и устранения неполадок.  
  
-   Запрос таких динамических административных представлений (DMV) для базовой диагностики, как [sys.dm_tran_locks](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md) для состояния блокировки, [sys.dm_os_memory_cache_counters](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-counters-transact-sql.md) для проверки работоспособности кэша, а [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md) и [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md) для активных сеансов и запросов. Старайтесь не использовать DMV, потребляющие много ресурсов (например, представление [sys.dm_tran_version_store](../../relational-databases/system-dynamic-management-views/sys-dm-tran-version-store-transact-sql.md) полностью проверяет хранилище версий, что может привести к резкому увеличению объема операций ввода-вывода) или использующие сложные соединения. Сведения о влиянии на производительность см. в документации к конкретному [динамическому административному представлению](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).  
  
-   Запрос представлений каталога.  
  
-   Основные команды DBCC, например [DBCC FREEPROCCACHE](../..//t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md), [DBCC FREESYSTEMCACHE](../../t-sql/database-console-commands/dbcc-freesystemcache-transact-sql.md), [DBCC DROPCLEANBUFFERS](../../t-sql/database-console-commands/dbcc-dropcleanbuffers-transact-sql.md), а также [DBCC SQLPERF](../../t-sql/database-console-commands/dbcc-sqlperf-transact-sql.md). Не выполняйте такие ресурсоемкие команды, как [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md), [DBCC DBREINDEX](../../t-sql/database-console-commands/dbcc-dbreindex-transact-sql.md) или [DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] Команда KILL*\<spid>*. В зависимости от состояния [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]команда KILL не всегда выполняется успешно. В этом случае единственным выходом остается перезапуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Рассмотрим несколько общих правил.  
  
    -   С помощью запроса `SELECT * FROM sys.dm_exec_sessions WHERE session_id = <spid>`убедитесь, что SPID был действительно отключен. Если строки не возвращаются, значит, сеанс был остановлен.  
  
    -   Если сеанс продолжается, проверьте с помощью запроса `SELECT * FROM sys.dm_os_tasks WHERE session_id = <spid>`наличие задач, назначенных для этого сеанса. Если задача присутствует, то, скорее всего, сеанс закрывается в настоящий момент. Заметьте, что это может занять немало времени и завершиться неуспешно.  
  
    -   Если в sys.dm_os_tasks нет задач, связанных с данным сеансом, но сеанс остается в sys.dm_exec_sessions после выполнения команды KILL, это означает, что отсутствует доступный рабочий процессор. Чтобы освободить рабочий поток, выберите одну из текущих задач (задача в представлении sys.dm_os_tasks со значением `sessions_id <> NULL`) и остановите связанный с ней сеанс. Заметьте, что остановка одного сеанса может оказаться недостаточной: может потребоваться остановить несколько сеансов.  
  
## <a name="dac-port"></a>Порт выделенного административного соединения  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выделенных административных соединений прослушивает TCP-порт 1434, если он доступен, или TCP-порт, динамически назначаемый при запуске компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Журнал ошибок содержит номер порта, на котором ожидается выделенное административное соединение. По умолчанию, выделенное административное соединение ожидается только на местном порте. Образец кода, активирующего удаленные административные соединения, см. в разделе [Параметр конфигурации сервера "remote admin connections"](../../database-engine/configure-windows/remote-admin-connections-server-configuration-option.md).  
  
 После настройки административного соединения средство прослушивания выделенных административных соединений включается без необходимости перезапуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , и клиент может удаленно подключиться к DAC. Средству прослушивания соединений DAC можно разрешить прием удаленных соединений, даже если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не отвечает. Для этого можно сначала подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] локально посредством выделенного административного соединения, а затем выполнить хранимую процедуру sp_configure для приема удаленных соединений.  
  
 В кластерных конфигурациях выделенное административное соединение по умолчанию выключено. Обеспечить доступ к удаленным соединениям средству прослушивания DAC пользователи могут с помощью хранимой процедуры sp_configure с параметром remote admin connection. Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не отвечает, а средство прослушивания выделенных административных соединений отключено, то для подключения к DAC, возможно, потребуется перезапустить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Поэтому корпорация Майкрософт рекомендует включать вариант конфигурации remote admin connections в кластеризованных системах.  
  
 Порт выделенных административных соединений присваивается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] динамически во время запуска. При соединении с экземпляром по умолчанию DAC стремится не использовать запрос протокола разрешения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SSRP) к службе обозревателя SQL Server. Сначала выполняется попытка подключиться через TCP-порт 1434. В случае ошибки следует вызов SSRP на получение порта. Если браузер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не ожидает запросов SSRP, запрос на подключение возвращает ошибку. Обратитесь к журналу ошибок, чтобы найти номер порта, на котором ожидается выделенное административное соединение. Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен для приема удаленных административных подключений, выделенное административное соединение должно быть инициировано с явно указанным номером порта:  
  
 **sqlcmd –S tcp:***\<сервер>,\<порт>*  
  
 Журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] приводит номер порта для выделенного административного соединения; по умолчанию он равен 1434. Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен для приема только локальных выделенных административных соединений, подключайтесь через адаптер замыкания на себя с использованием следующей команды:  
  
 **sqlcmd –S 127.0.0.1,1434**  
  
> [!TIP]  
>  При подключении к [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] с помощью DAC необходимо указать в строке подключения имя базы данных, используя параметр -d.  
  
## <a name="example"></a>Пример  
 В этом примере администратор видит, что сервер `URAN123` не отвечает, и пытается определить неполадку. Для этого пользователь активирует программу командной строки `sqlcmd` и подключается к серверу `URAN123` с помощью ключа `-A` , чтобы обозначить выделенное административное соединение.  
  
 `sqlcmd -S URAN123 -U sa -P <xxx> –A`  
  
 Теперь администратор может запускать запросы для определения проблемы и, возможно, прекращения не отвечающих сеансов.  
  
 Аналогичный пример для подключения к [!INCLUDE[ssSDS](../../includes/sssds-md.md)] : здесь используется команда с параметром -d для указания базы данных.  
  
 `sqlcmd -S serverName.database.windows.net,1434 -U sa -P <xxx> -d AdventureWorks`  
  
## <a name="related-content"></a>См. также  
 [Использование программы sqlcmd с переменными скрипта](../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md)  
 [Программа sqlcmd](../../tools/sqlcmd-utility.md)  
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)  
 [sp_who (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)  
 [sp_lock (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-lock-transact-sql.md)  
 [KILL (Transact-SQL)](../../t-sql/language-elements/kill-transact-sql.md)  
 [DBCC CHECKALLOC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-checkalloc-transact-sql.md)  
 [DBCC CHECKDB (Transact-SQL)](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
 [DBCC OPENTRAN (Transact-SQL)](../../t-sql/database-console-commands/dbcc-opentran-transact-sql.md)  
 [DBCC INPUTBUFFER (Transact-SQL)](../../t-sql/database-console-commands/dbcc-inputbuffer-transact-sql.md)  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
 [Динамические административные представления и функции, связанные с транзакциями (Transact-SQL)](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
 [Флаги трассировки (Transact-SQL)](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
  
  

