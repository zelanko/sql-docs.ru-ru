---
title: Управление таблицами Filetable | Документация Майкрософт
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], security
- FileTables [SQL Server], managing access
ms.assetid: 93af982c-b4fe-4be0-8268-11f86dae27e1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ab88dfa27c63607c312b2a3c757b04cd076745a9
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65094156"
---
# <a name="manage-filetables"></a>Управление таблицами FileTable
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Описывает стандартные административные задачи по управлению таблицами FileTables.  
  
##  <a name="HowToEnumerate"></a> Как получить список таблиц FileTable и связанных объектов  
 Чтобы получить список таблиц FileTable, выполните запрос к одному из следующих представлений каталогов:  
  
-   [sys.filetables (Transact-SQL)](../../relational-databases/system-catalog-views/sys-filetables-transact-sql.md)  
  
-   [sys.tables (Transact-SQL)](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md) (Проверьте значение в столбце **is_filetable**.)  
  
```sql  
SELECT * FROM sys.filetables;  
GO  
  
SELECT * FROM sys.tables WHERE is_filetable = 1;  
GO  
```  
  
 Чтобы получить список системных объектов, которые были созданы при создании связанных таблиц FileTable, выполните запрос к представлению каталога [sys.filetable_system_defined_objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql.md).  
  
```sql  
SELECT object_id, OBJECT_NAME(object_id) AS 'Object Name'  
FROM sys.filetable_system_defined_objects;  
GO  
```  
  
##  <a name="BasicsDisabling"></a> Отключить и снова включить нетранзакционный доступ на уровне базы данных  
 Для монопольного доступа, необходимого для выполнения некоторых задач администрирования, может потребоваться временно отключить нетранзакционный доступ.  
  
 **Поведение инструкции ALTER DATABASE при изменении уровня нетранзакционного доступа**  
  
-   В случае задания для нетранзакционного доступа значения READ_ONLY или OFF команда ALTER DATABASE не возвращает управление пользователю, пока имеются открытые дескрипторы файлов, конфликтующие с запрошенной операцией. Дескрипторы файлов, которые конфликтуют с этой операцией:  
  
    -   Если доступ установлен в режим **NONE**, то все открытые дескрипторы файлов.  
  
    -   Если доступ установлен в режим **READ_ONLY**, все дескрипторы файлов открыты для записи.  
  
     Сведения об уничтожении открытых дескрипторов файлов см. в подразделе [Уничтожение открытых дескрипторов файлов, связанных с таблицей FileTable](#BasicsKilling) этого раздела.  
  
     Если команда ALTER DATABASE отменяется или истекает ее время ожидания, уровень транзакционного доступа изменен не будет.  
  
-   При вызове инструкции ALTER DATABASE с предложением WITH \<termination> (ROLLBACK AFTER integer [ SECONDS ] | ROLLBACK IMMEDIATE | NO_WAIT) все открытые нетранзакционные дескрипторы файлов будут уничтожены.  
  
> [!WARNING]  
>  При уничтожении открытых дескрипторов файлов пользователи могут потерять несохраненные данные. Такое поведение согласуется с поведением самой файловой системы.  
  
 **Последствия отключения нетранзакционного доступа**  
  
 Изменение уровня нетранзакционного доступа на уровне базы данных оказывает следующее влияние на каталоги FileTable, вложенные в каталог уровня базы данных.  
  
-   Если доступ установлен в режим **NONE**, все каталоги FileTable и их содержимое становятся недоступными и невидимыми.  
  
-   Если доступ установлен в режим **READ_ONLY**, все каталоги FileTable и их содержимое доступны только для чтения.  
  
 Отключение FILESTREAM на уровне экземпляра оказывает следующее влияние на каталоги уровня базы данных этого экземпляра и вложенные в них каталоги FileTable.  
  
-   Если FILESTREAM отключен на уровне экземпляра, невидимыми будут все каталоги уровня базы данных этого экземпляра.  
  
###  <a name="HowToDisable"></a> Как отключить и снова включить нетранзакционный доступ на уровне базы данных  
 Дополнительные сведения см. в разделе [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
 **Отключение полного нетранзакционного доступа**  
 Вызовите инструкцию **ALTER DATABASE** и задайте параметру **NON_TRANSACTED_ACCESS** значение **READ_ONLY** или **OFF**.  
  
```sql  
-- Disable write access.  
ALTER DATABASE database_name  
SET FILESTREAM ( NON_TRANSACTED_ACCESS = READ_ONLY );  
GO  
  
-- Disable non-transactional access.  
ALTER DATABASE database_name  
SET FILESTREAM ( NON_TRANSACTED_ACCESS = OFF );  
GO  
```  
  
 **Повторное включение полного нетранзакционного доступа**  
 Вызовите инструкцию **ALTER DATABASE** и задайте параметру **NON_TRANSACTED_ACCESS** значение **FULL**.  
  
```sql  
ALTER DATABASE database_name  
SET FILESTREAM ( NON_TRANSACTED_ACCESS = FULL );  
GO  
```  
  
###  <a name="visible"></a> Как обеспечить видимость таблиц FileTables в базе данных  
 Каталог уровня базы данных и находящиеся в нем каталоги FileTable отображаются при соблюдении всех следующих условий.  
  
1.  Функция FILESTREAM включена на уровне экземпляра.  
  
2.  Нетранзакционный доступ включен на уровне базы данных.  
  
3.  На уровне базы данных указан допустимый каталог.  
  
##  <a name="BasicsEnabling"></a> Отключение и повторное включение пространства имен FileTable на уровне таблицы  
 При отключении пространства имен FileTable отключаются все системные ограничения и триггеры, созданные в таблице FileTable. Это полезно в случаях, когда требуется значительная реорганизация таблицы FileTable с помощью операций [!INCLUDE[tsql](../../includes/tsql-md.md)] без дополнительных затрат на применение семантики FileTable. Но это может привести к несогласованному состоянию таблицы FileTable, что может не позволить снова включить пространство имен FileTable.  
  
 Отключение пространства имен FileTable имеет следующие результаты.  
  
-   Столбцы и данные FileTable не будут физически удалены из таблицы.  
  
-   Каталог таблицы FileTable, а также содержащиеся в нем файлы и каталоги удаляются из файловой системы и становятся недоступными для файлового ввода-вывода.  
  
-   Системные столбцы таблицы FileTable нельзя удалить и создать заново, в остальном же они ведут себя так же, как любые другие столбцы в операциях DML.  
  
-   Открытые дескрипторы файлов не позволяют отключить ограничения FileTable, поскольку для выполнения этой операции требуется заблокировать схему в таблице.  
  
-   Действие семантики FileTable, включая системные ограничения и триггеры, прекращается после отключения пространства имен FileTable.  
  
 Повторное включение пространства имен FileTable имеет следующие результаты.  
  
-   Таблица FileTable проверяется на согласованность. При обнаружении несогласованности возникает ошибка, и таблица FileTable остается отключенной. В противном случае, таблица FileTable будет включена.  
  
-   Действие семантики FileTable, включая системные ограничения и триггеры, будет восстановлено.  
  
-   Каталог таблицы FileTable, а также содержащиеся в нем файлы и каталоги появляются в файловой системе и становятся доступными для файлового ввода-вывода.  
  
###  <a name="HowToEnableNS"></a> Как отключить и снова включить пространство имен FileTable на уровне таблицы  
 Вызовите инструкцию ALTER TABLE с параметром **{ ENABLE | DISABLE } FILETABLE_NAMESPACE** .  
  
 **Отключение пространства имен FileTable**  
 ```sql  
ALTER TABLE filetable_name  
DISABLE FILETABLE_NAMESPACE;  
GO  
```  
  
 **Повторное включение пространства имен FileTable**  
 ```sql  
ALTER TABLE filetable_name  
ENABLE FILETABLE_NAMESPACE;  
GO  
```  
  
##  <a name="BasicsKilling"></a> Уничтожение открытых дескрипторов файлов, связанных с таблицей FileTable  
 Открытые дескрипторы файлов, хранящихся в таблице FileTable, могут помешать монопольному доступу, который требуется для выполнения определенных задач по администрированию. Для включения срочных задач может потребоваться уничтожить открытые дескрипторы файлов, связанные с одной или несколькими таблицами FileTable.  
  
> [!WARNING]  
>  При уничтожении открытых дескрипторов файлов пользователи могут потерять несохраненные данные. Такое поведение согласуется с поведением самой файловой системы.  
  
###  <a name="HowToListOpen"></a> Как получить список открытых дескрипторов файлов, связанных с таблицей FileTable  
 Выполните запрос к представлению каталога [sys.dm_filestream_non_transacted_handles (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md).  
  
```sql  
SELECT * FROM sys.dm_filestream_non_transacted_handles;  
GO  
```  
  
###  <a name="HowToKill"></a> Как уничтожить открытые дескрипторы файлов, связанные с таблицей FileTable  
 Чтобы уничтожить все открытые дескрипторы файлов в базе данных или в таблице FileTable либо конкретный дескриптор, вызовите хранимую процедуру [sp_kill_filestream_non_transacted_handles (Transact-SQL)](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-kill-filestream-non-transacted-handles.md).  
  
```sql  
USE database_name;  
  
-- Kill all open handles in all the filetables in the database.  
EXEC sp_kill_filestream_non_transacted_handles;  
GO  
  
-- Kill all open handles in a single filetable.  
EXEC sp_kill_filestream_non_transacted_handles @table_name = 'filetable_name';  
GO  
  
-- Kill a single handle.  
EXEC sp_kill_filestream_non_transacted_handles @handle_id = integer_handle_id;  
GO  
```  
  
###  <a name="HowToIdentifyLocks"></a> Как определить блокировки, имеющиеся в таблицах FileTable  
 Большинство блокировок в таблице FileTable связано с файлами, открытыми приложениями.  
  
 **Определение открытых файлов и связанных с ними блокировок**  
 Объедините поле **request_owner_id** динамического административного представления [sys.dm_tran_locks (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md) с полем **fcb_id** динамического административного представления [sys.dm_filestream_non_transacted_handles (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md). В некоторых случаях блокировка связана с несколькими открытыми файлами.  
  
```sql  
SELECT opened_file_name  
FROM sys.dm_filestream_non_transacted_handles  
WHERE fcb_id IN  
    ( SELECT request_owner_id FROM sys.dm_tran_locks );  
GO  
```  
  
##  <a name="BasicsSecurity"></a> Безопасность таблицы FileTable  
 Файлы и каталоги, хранящиеся в таблицах FileTable, защищаются только средствами безопасности SQL Server. Средства безопасности на уровне таблицы и столбцов применяются для доступа файловой системы, а также для доступа [!INCLUDE[tsql](../../includes/tsql-md.md)] . API-интерфейсы безопасности файловой системы Windows и параметры ACL не поддерживаются.  
  
 Права и разрешения на доступ, применимые к группам файлов и контейнерам FILESTREAM, также применяются и к таблице FileTable, поскольку данные файлов хранятся в столбце FILESTREAM таблицы FileTable.  
  
 **Безопасность FileTable и доступ Transact-SQL**  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] Защита доступа к данным из таблицы FileTable обеспечивается так же, как и защита доступа к любой другой таблице. Соответствующие проверки безопасности на уровне таблицы и столбца выполняются для каждой операции, которая производит доступ или изменение данных.  
  
 **Безопасность таблиц FileTable и доступ файловой системы**  
 Для открытия дескриптора файла или каталога, хранящегося в таблице FileTable, API-интерфейсам файловой системы требуются соответствующие разрешения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на всю строку таблицы FileTable (то есть разрешение на уровне таблицы). Если у пользователя нет соответствующего разрешения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на любой столбец таблицы FileTable, то доступ к файловой системе будет запрещен.  
  
##  <a name="OtherBackup"></a> Резервное копирование и таблицы FileTable  
 Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется для резервного копирования таблицы FileTable, то резервная копия данных FILESTREAM создается со структурированными данными в базе данных. Если резервное копирование данных FILESTREAM при помощи реляционных данных выполнять нежелательно, для исключения файловых групп FILESTREAM можно воспользоваться частичным резервным копированием.  
  
 **Согласованность транзакций резервных копий таблиц FileTable**  
  
 Многие средства и операции администрирования (включая резервное копирование, резервное копирование журналов и репликацию транзакций) осуществляют чтение транзакционно согласованных данных путем чтения журналов транзакций. В это время они считывают все данные FILESTREAM, обновленные в рамках транзакции. Если нетранзакционный доступ не включен на уровне базы данных, эти средства и операции работают в режиме полной транзакционной согласованности.  
  
 Однако, когда включен полный нетранзакционный доступ, таблица FileTable может содержать данные, которые были обновлены (с помощью нетранзакционного обновления) уже после выполнения транзакции, которую средство или процесс считывает из журнала транзакций. Это означает, что операция восстановления на момент времени для определенной транзакции может содержать данные FILESTREAM более свежие, чем транзакция. Это ожидаемое поведение при включенном нетранзакционном обновлении для таблиц FileTables.  
  
##  <a name="Monitor"></a> Приложение SQL Server Profiler и таблицы FileTable  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler может включать в трассировку операции Windows по открытию и закрытию файлов, хранящихся в таблице FileTable.  
  
##  <a name="OtherAuditing"></a> Аудит и таблицы FileTable  
 Аудит таблицы FileTable проводится так же, как и для любых других таблиц. Однако шаблоны доступа Win32 не являются операциями на основе множеств. Одно действие в файловой системе преобразуется в несколько DML-операций Transact-SQL. Например, открытие файла в Microsoft Word преобразуется в несколько операций открытия/закрытия/создания/переименования/удаления и соответствующие DML-операции Transact-SQL. Это приводит к записи подробных сведений аудита, где трудно сопоставить записи, относящиеся к действиям файловой системы, и соответствующие записи аудита DML в Transact-SQL.  
  
##  <a name="OtherDBCC"></a> DBCC и таблицы FileTable  
 С помощью инструкции DBCC CHECKCONSTRAINTS можно проверить ограничения для таблицы FileTable, включая системные ограничения.  
  
## <a name="see-also"></a>См. также:  
 [Совместимость FileTable с другими компонентами SQL Server](../../relational-databases/blob/filetable-compatibility-with-other-sql-server-features.md)   
 [Инструкции FileTable языка DDL, функции, хранимые процедуры и представления](../../relational-databases/blob/filetable-ddl-functions-stored-procedures-and-views.md)  
