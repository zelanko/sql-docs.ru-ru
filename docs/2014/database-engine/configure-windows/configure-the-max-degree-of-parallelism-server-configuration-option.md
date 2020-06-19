---
title: Настройка параметра конфигурации сервера max degree of parallelism | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- parallel queries [SQL Server]
- processors [SQL Server], parallel queries
- number of processors for parallel queries
- max degree of parallelism option
ms.assetid: 86b65bf1-a6a1-4670-afc0-cdfad1558032
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 824dc837142acc4a0898cb04b4a8687bc5be4043
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935675"
---
# <a name="configure-the-max-degree-of-parallelism-server-configuration-option"></a>Настройка параметра конфигурации сервера max degree of parallelism
  В этом разделе описывается настройка `max degree of parallelism` параметра конфигурации сервера в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)] . Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает на многопроцессорном компьютере, он определяет оптимальную степень параллелизма, то есть количество процессоров, задействованных для выполнения одной инструкции, для каждого из планов параллельного выполнения. Можно использовать параметр `max degree of parallelism` для ограничения числа процессоров, применяемых в планах параллельного выполнения. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учитывает планы параллельного выполнения для запросов, операций DDL с индексами, а также заполнения статических курсоров и курсоров, управляемых набором ключей.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Настройка максимальной степени параллелизма с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Продолжение**  [после настройки параметра max degree of parallelism](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Если параметр affinity mask имеет значение, отличное от значения по умолчанию, он может ограничивать число процессоров, доступных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в симметричных многопроцессорных системах (SMP).  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Рекомендации  
  
-   Этот параметр является дополнительным и его следует изменять только опытным администраторам баз данных или сертифицированным техническим специалистам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Чтобы разрешить серверу определять максимальную степень параллелизма, установите 0 в качестве значения данного параметра, то есть значение по умолчанию. Установка значения 0 в качестве максимальной степени параллелизма позволяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использовать все доступные процессоры (до 64 процессоров). Чтобы отключить создание параллельных планов, присвойте параметру `max degree of parallelism` значение 1. Задайте значение для параметра в диапазоне от 1 до 32 767, чтобы указать максимальное количество процессорных ядер, которые могут быть использованы при выполнении одного запроса. Если указано значение, превышающее количество доступных процессоров, используется действительное количество доступных процессоров. Если у компьютера только один процессор, то значение параметра `max degree of parallelism` учитываться не будет.  
  
-   Значение параметра max degree of parallelism можно переопределить, задав в инструкции указание запроса MAXDOP. Дополнительные сведения см. в разделе [Указания запросов (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query).  
  
-   Операции по созданию и перестройке индексов, а также по удалению кластеризованного индекса могут оказаться достаточно ресурсоемкими. Значение параметра max degree of parallelism для операций с индексами можно переопределить, указав в инструкции параметр индекса MAXDOP. Значение MAXDOP применяется к инструкции во время выполнения и в метаданных индекса не хранится. Дополнительные сведения см. в статье [Настройка параллельных операций с индексами](../../relational-databases/indexes/configure-parallel-index-operations.md).  
  
-   Помимо запросов и операций с индексами, этот параметр также управляет степенью параллелизма при выполнении инструкций DBCC CHECKTABLE, DBCC CHECKDB и DBCC CHECKFILEGROUP. Планы параллельного выполнения для этих инструкций можно отключить с помощью флага трассировки 2528. Дополнительные сведения см. в разделе [Флаги трассировки (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-max-degree-of-parallelism-option"></a>Настройка параметра максимальной степени параллелизма  
  
1.  В **обозревателе объектов**щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Щелкните узел **Дополнительно** .  
  
3.  В поле **Максимальная степень параллелизма** укажите максимальное число процессоров, которое может быть использовано в плане параллельного выполнения.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-max-degree-of-parallelism-option"></a>Настройка параметра максимальной степени параллелизма  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование процедуры [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) для задания значения параметра `max degree of parallelism` равным `8`.  
  
```sql  
USE AdventureWorks2012 ;  
GO   
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
EXEC sp_configure 'max degree of parallelism', 8;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
```  
  
 Дополнительные сведения см. в разделе [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md).  
  
##  <a name="follow-up-after-you-configure-the-max-degree-of-parallelism-option"></a><a name="FollowUp"></a> Дальнейшие действия. После настройки параметра max degree of parallelism  
 Параметр вступает в силу немедленно, без перезапуска сервера.  
  
## <a name="see-also"></a>См. также:  
 [Параметр конфигурации сервера «affinity mask»](affinity-mask-server-configuration-option.md)   
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql)   
 [ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql)   
 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)   
 [DBCC CHECKTABLE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql)   
 [DBCC CHECKDB &#40;&#41;Transact-SQL](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)   
 [DBCC CHECKFILEGROUP &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkfilegroup-transact-sql)   
 [Настройка параллельных операций с индексами](../../relational-databases/indexes/configure-parallel-index-operations.md)   
 [Указания запросов (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query)   
 [Установка параметров индекса](../../relational-databases/indexes/set-index-options.md)  
  
  
