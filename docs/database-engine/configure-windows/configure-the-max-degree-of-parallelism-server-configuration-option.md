---
title: Настройка параметра конфигурации сервера max degree of parallelism | Документы Майкрософт
ms.custom: ''
ms.date: 02/12/2020
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- parallel queries [SQL Server]
- processors [SQL Server], parallel queries
- number of processors for parallel queries
- max degree of parallelism option
- MaxDop
ms.assetid: 86b65bf1-a6a1-4670-afc0-cdfad1558032
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 47b9704591acd305a49ff315eb99314f14e87af1
ms.sourcegitcommit: 38c61c7e170b57dddaae5be72239a171afd293b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2020
ms.locfileid: "77259226"
---
# <a name="configure-the-max-degree-of-parallelism-server-configuration-option"></a>Настройка параметра конфигурации сервера max degree of parallelism
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  В этом разделе описывается настройка параметра конфигурации сервера **max degree of parallelism (MAXDOP)** в SQL Server с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает на многопроцессорном компьютере, он определяет степень параллелизма, то есть количество процессоров, задействованных для выполнения одной инструкции, для каждого из планов параллельного выполнения. Для ограничения количества процессоров в плане параллельного выполнения может быть использован параметр **max degree of parallelism** . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учитывает планы параллельного выполнения для запросов, операций с индексами на языке DDL, параллельной вставки, изменения столбца в режиме "в сети", параллельного сбора статистики и заполнения статических курсоров и курсоров, управляемых набором ключей.

> [!NOTE]
> [!INCLUDE [sssqlv15-md](../../includes/sssqlv15-md.md)] содержит автоматические рекомендации по настройке параметра MAXDOP в процессе установки. Пользовательский интерфейс программы установки позволяет либо принять рекомендуемые параметры, либо настроить их. Дополнительные сведения см. в следующих статьях:
>  - [MaxDOP Added to SQL 2019 Setup](https://techcommunity.microsoft.com/t5/premier-field-engineering/maxdop-added-to-sql-2019-ctp3-0-setup/ba-p/780071) (Параметр MaxDOP, добавленный в программу установки SQL Server 2019)
>  - [SQL Server 2019 Installation Enhancements for MAXDOP and Max Memory](https://www.mssqltips.com/sqlservertip/6211/sql-server-2019-installation-enhancements-for-maxdop-and-max-memory/) (Улучшения установки SQL Server 2019 для параметров MAXDOP и Max Memory)
>

##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Если параметр affinity mask имеет значение, отличное от значения по умолчанию, он может ограничивать число процессоров, доступных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в симметричных многопроцессорных системах (SMP).  

-   Ограничение параметра **max degree of parallelism (MAXDOP)** задается для каждой [задачи](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md). Оно не задается для каждого [запроса](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md). Это значит, что во время параллельного выполнения один запрос может порождать несколько задач, назначаемых планировщику. Дополнительные сведения см. в статье [Руководство по архитектуре потоков и задач](../../relational-databases/thread-and-task-architecture-guide.md). 
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Это расширенный параметр, и изменять его следует только опытным администраторам баз данных или сертифицированным по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] специалистам.  
  
-   Чтобы разрешить серверу определять максимальную степень параллелизма, установите 0 в качестве значения данного параметра, то есть значение по умолчанию. Установка значения 0 в качестве максимальной степени параллелизма позволяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использовать все доступные процессоры (до 64 процессоров). Чтобы отключить создание параллельных планов, присвойте параметру **max degree of parallelism** значение 1. Задайте значение для параметра в диапазоне от 1 до 32 767, чтобы указать максимальное количество процессорных ядер, которые могут быть использованы при выполнении одного запроса. Если указано значение, превышающее количество доступных процессоров, используется действительное количество доступных процессоров. Если у компьютера только один процессор, то значение параметра **max degree of parallelism** учитываться не будет.  
  
-   Значение параметра max degree of parallelism можно переопределить, задав в инструкции указание запроса MAXDOP. Дополнительные сведения см. в разделе [Указания запросов (Transact-SQL)](../../t-sql/queries/hints-transact-sql-query.md).  
  
-   Операции по созданию и перестройке индексов, а также по удалению кластеризованного индекса могут оказаться достаточно ресурсоемкими. Значение параметра max degree of parallelism для операций с индексами можно переопределить, указав в инструкции параметр индекса MAXDOP. Значение MAXDOP применяется к инструкции во время выполнения и в метаданных индекса не хранится. Дополнительные сведения см. в статье [Настройка параллельных операций с индексами](../../relational-databases/indexes/configure-parallel-index-operations.md).  
  
-   Помимо запросов и операций с индексами, этот параметр также управляет степенью параллелизма при выполнении инструкций DBCC CHECKTABLE, DBCC CHECKDB и DBCC CHECKFILEGROUP. Планы параллельного выполнения для этих инструкций можно отключить с помощью флага трассировки 2528. Дополнительные сведения см. в разделе [Флаги трассировки (Transact-SQL)](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).

> [!TIP]
> Для выполнения этого на уровне запросов используйте [указание запроса](../../t-sql/queries/hints-transact-sql-query.md) **MAXDOP**.     
> На уровне базы данных используйте [конфигурацию области баз данных ](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)**MAXDOP**.      
> На уровне рабочих нагрузок используйте [параметр конфигурации группы рабочей нагрузки Resource Governor](../../t-sql/statements/create-workload-group-transact-sql.md) **MAX_DOP**.      

###  <a name="Guidelines"></a> Рекомендации  
Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] по умолчанию система [!INCLUDE[ssde_md](../../includes/ssde_md.md)] автоматически создает узлы архитектуры Soft-NUMA, если во время запуска обнаруживает более восьми физических ядер на один сокет или узел NUMA. [!INCLUDE[ssde_md](../../includes/ssde_md.md)] помещает логические процессоры одного и того же физического ядра в разных узлах программной архитектуры NUMA. Рекомендации, приведенные в следующей таблице, нацелены на сохранение рабочих потоков параллельного запроса на одном узле программной архитектуры NUMA. Это улучшит производительность запросов и распределение рабочих потоков между узлами NUMA для рабочей нагрузки. Дополнительные сведения см. в разделе [Программная архитектура NUMA](../../database-engine/configure-windows/soft-numa-sql-server.md).

Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] при настройке значения параметра **max degree of parallelism** в конфигурации сервера следуйте приведенным ниже рекомендациям.

||||
|----------------|-----------------|-----------------|
|Сервер с одним узлом NUMA|Не более 8 логических процессоров|Значение параметра MAXDOP не должно превышать количество логических процессоров|
|Сервер с одним узлом NUMA|Больше 8 логических процессоров|Значение параметра MAXDOP должно быть равно 8|
|Сервер с несколькими узлами NUMA|Не более 16 логических процессоров на узел NUMA|Значение параметра MAXDOP не должно превышать количество логических процессоров на каждый узел NUMA|
|Сервер с несколькими узлами NUMA|Больше 16 логических процессоров на каждый узел NUMA|Значение MAXDOP должно быть равно половине количества логических процессоров на узел NUMA со значением MAX, равным 16|
  
> [!NOTE]
> Узлы NUMA в приведенной выше таблице — это узлы программной архитектуры NUMA, автоматически создаваемые в [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] и более поздних версий, или аппаратной архитектуры NUMA, если узлы программной архитектуры NUMA отключены.   
>  Эти же правила используются в том случае, если значение max degree of parallelism задано для групп рабочей нагрузки регулятора ресурсов. Дополнительные сведения см. в разделе [CREATE WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/create-workload-group-transact-sql.md).
  
В версиях с [!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)] по [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] при настройке значения параметра **max degree of parallelism** в конфигурации сервера следуйте приведенным ниже рекомендациям.

||||
|----------------|-----------------|-----------------|
|Сервер с одним узлом NUMA|Не более 8 логических процессоров|Значение параметра MAXDOP не должно превышать количество логических процессоров|
|Сервер с одним узлом NUMA|Больше 8 логических процессоров|Значение параметра MAXDOP должно быть равно 8|
|Сервер с несколькими узлами NUMA|Не более 8 логических процессоров на узел NUMA|Значение параметра MAXDOP не должно превышать количество логических процессоров на каждый узел NUMA|
|Сервер с несколькими узлами NUMA|Больше 8 логических процессоров на узел NUMA|Значение параметра MAXDOP должно быть равно 8|
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-max-degree-of-parallelism-option"></a>Настройка параметра максимальной степени параллелизма  
  
1.  В **обозревателе объектов**щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Щелкните узел **Дополнительно** .  
  
3.  В поле **Максимальная степень параллелизма** укажите максимальное число процессоров, которое может быть использовано в плане параллельного выполнения.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-max-degree-of-parallelism-option"></a>Настройка параметра максимальной степени параллелизма  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование процедуры [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) для задания значения параметра `max degree of parallelism` равным `8`.  
  
```sql  
USE AdventureWorks2012 ;  
GO   
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
EXEC sp_configure 'max degree of parallelism', 16;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
```  
  
 Дополнительные сведения см. в разделе [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После настройки параметра max degree of parallelism  
 Параметр вступает в силу немедленно, без перезапуска сервера.  
  
## <a name="see-also"></a>См. также:  
 [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)      
 [Рекомендации и инструкции по использованию параметра конфигурации "Максимальная степень параллелизма" в SQL Server](https://support.microsoft.com/help/2806535)     
 [Параметр конфигурации сервера «affinity mask»](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)   
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Руководство по архитектуре обработки запросов](../../relational-databases/query-processing-architecture-guide.md#DOP)       
 [Руководство по архитектуре потоков и задач](../../relational-databases/thread-and-task-architecture-guide.md)    
 [Настройка параллельных операций с индексами](../../relational-databases/indexes/configure-parallel-index-operations.md)    
 [Указания запросов (Transact-SQL)](../../t-sql/queries/hints-transact-sql-query.md)     
 [Установка параметров индекса](../../relational-databases/indexes/set-index-options.md)     
