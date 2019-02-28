---
title: Настройка параметра конфигурации сервера max worker threads | Документы Майкрософт
ms.custom: ''
ms.date: 11/23/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- worker threads [SQL Server]
- max worker threads option
ms.assetid: abeadfa4-a14d-469a-bacf-75812e48fac1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c35aab2ebd2b31fbbe7067bc8049930f791543c3
ms.sourcegitcommit: 009bee6f66142c48477849ee03d5177bcc3b6380
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2019
ms.locfileid: "56230981"
---
# <a name="configure-the-max-worker-threads-server-configuration-option"></a>Настройка параметра конфигурации сервера max worker threads
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  В этом разделе описываются способы настройки параметра конфигурации сервера **max worker threads** в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр **max worker threads** используется для установки количества рабочих потоков, доступных процессам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используются собственные службы для потоков операционных систем, поэтому один или несколько потоков одновременно поддерживают все сети, которые поддерживает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , еще один поток обрабатывает контрольные точки базы данных, а пул потоков обрабатывает запросы от всех пользователей. Значение по умолчанию для параметра **max worker threads** — 0. Это позволяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически настраивать количество рабочих потоков при запуске. Настройка по умолчанию является оптимальной для большинства систем. Но иногда, в зависимости от конфигурации системы, установка параметра **max worker threads** в другое определенное значение может улучшить производительность.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
     [безопасность](#Security)  
  
-   **Настройка параметра max worker threads с помощью различных средств.**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После настройки параметра max worker threads](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Если реальное количество запросов меньше значения, заданного параметром **max worker threads**, каждый запрос обрабатывается одним потоком. Однако если реальное количество потоков превышает число, заданное параметром **max worker threads**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует пул рабочих потоков, так что следующий доступный рабочий поток сможет обработать запрос.  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Это расширенный параметр, и изменять его следует только опытным администраторам баз данных или сертифицированным по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] специалистам. Если вы считаете, что есть проблема с производительностью, вероятно, причина не в доступности рабочих потоков. Скорее всего, их ожидание вызвано чем-то наподобие операций ввода-вывода. Рекомендуется найти причину проблемы производительности, прежде чем изменять параметр max worker threads.  
  
-   Пул потоков помогает оптимизировать производительность при подключении к серверу большого числа пользователей. Обычно для каждого запроса в операционной системе создается отдельный поток. Однако в случае сотен соединений с сервером, использование одного потока на каждый запрос приводит к потреблению большого числа системных ресурсов. Параметр **max worker threads** позволяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создавать пул рабочих потоков, чтобы обслужить большое число запросов, что улучшает производительность.  
  
-   В следующей таблице показано автоматически настраиваемое максимальное число рабочих потоков для различных сочетаний процессоров и версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    |Число процессоров|32-разрядный компьютер|64-разрядный компьютер|  
    |------------|------------|------------|  
    |\< — 4 процессора|256|512|  
    |8 процессоров|288|576|  
    |16 процессоров|352|704|  
    |32 процессора|480|960|  
    |64 процессора|736|1472|  
    |128 процессоров|4224|4480|  
    |256 процессоров|8320|8576| 
    
    Используется следующая формула.
    
    |Число процессоров|32-разрядный компьютер|64-разрядный компьютер|  
    |------------|------------|------------| 
    |\< — 4 процессора|256|512|
    |\> — 4 процессора и \< — 64 процессора|256 + ((число логических ЦП – 4) * 8)|512 + ((число логических ЦП – 4) * 16)|
    |\> — 64 процессора|256 + ((число логических ЦП – 4) * 32)|512 + ((число логических ЦП – 4) * 32)|
  
    > [!NOTE]  
    > [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] больше нельзя устанавливать в 32-разрядной операционной системе. Значения для 32-разрядного компьютера приведены, чтобы помочь клиентам, работающим с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] и более ранних версий.   Для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , работающего в 32-разрядном компьютере, рекомендуется ограничить число рабочих потоков до 1024.  
  
    > [!NOTE]  
    >  Рекомендации по использованию процессоров в количестве, превышающем 64, см. в разделе [Рекомендации по использованию SQL Server на компьютерах, которые имеют более 64 процессоров](../../relational-databases/thread-and-task-architecture-guide.md#best-practices-for-running-sql-server-on-computers-that-have-more-than-64-cpus).  
  
-   Если все рабочие потоки заняты выполнением длительных запросов, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может не отвечать на другие запросы, пока один из потоков не завершит работу и не станет доступным. Хотя это и не ошибка, такое поведение иногда нежелательно. Если процесс не отвечает и новые запросы не могут быть обработаны, подключитесь к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] через выделенное административное соединение (DAC) и уничтожьте процесс. Во избежание этого увеличьте максимальное число потоков управления.  
  
 Параметр конфигурации сервера **max worker threads** не учитывает потоки, которые необходимы для всех системных задач, таких как группы доступности, компонент Service Broker, диспетчер блокировок и другие. Если число настроенных потоков превышается, то следующий запрос будет содержать сведения о системных задачах, породивших дополнительные потоки.  
  
 ```sql  
 SELECT  s.session_id, r.command, r.status,  
    r.wait_type, r.scheduler_id, w.worker_address,  
    w.is_preemptive, w.state, t.task_state,  
    t.session_id, t.exec_context_id, t.request_id  
 FROM sys.dm_exec_sessions AS s  
 INNER JOIN sys.dm_exec_requests AS r  
    ON s.session_id = r.session_id  
 INNER JOIN sys.dm_os_tasks AS t  
    ON r.task_address = t.task_address  
 INNER JOIN sys.dm_os_workers AS w  
    ON t.worker_address = w.worker_address  
 WHERE s.is_user_process = 0;  
 ```  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Использование [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
#### <a name="to-configure-the-max-worker-threads-option"></a>Настройка параметра max worker threads  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Щелкните узел **Процессоры** .  
  
3.  В поле **Максимальное число рабочих потоков** введите или выберите значение от 128 до 32 767.  
  
> [!TIP]
> Используйте параметр **max worker threads** для установки количества рабочих потоков, доступных процессам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Значение по умолчанию параметра **max worker threads** является оптимальным для большинства систем. Но в зависимости от конфигурации системы установка параметра **max worker threads** в меньшее значение может улучшить производительность.
> Дополнительные сведения см. в разделе [Рекомендации](#Recommendations) на этой странице.
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-max-worker-threads-option"></a>Настройка параметра max worker threads  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование процедуры [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) для задания значения параметра `max worker threads` равным `900`.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'max worker threads', 900 ;  
GO  
RECONFIGURE;  
GO  
```  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После настройки параметра max worker threads  
 Изменения вступят в силу сразу после выполнения [RECONFIGURE](../../t-sql/language-elements/reconfigure-transact-sql.md) без необходимости перезапуска [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Диагностическое соединение для администраторов баз данных](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)  
  
  
