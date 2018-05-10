---
title: Триггеры входа | Документация Майкрософт
ms.custom: ''
ms.date: 03/19/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: triggers
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- logon triggers
- login triggers
helpviewer_keywords:
- triggers [SQL Server], logon
ms.assetid: 2f0ebb2f-de10-482d-9806-1a5de5b312b8
caps.latest.revision: 13
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b3043b79f55b7968104f87e590dc10023f87ac6b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="logon-triggers"></a>Триггеры входа
[!INCLUDE[tsql-appliesto-ss2008-xxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Триггеры входа вызывают срабатывание хранимых процедур в ответ на событие LOGON. Это событие вызывается при установке пользовательского сеанса с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Триггеры входа срабатывают после завершения этапа проверки подлинности при входе, но перед тем, как пользовательский сеанс реально устанавливается. Следовательно, все сообщения, которые возникают внутри триггера и обычно достигают пользователя, такие как сообщения об ошибках и сообщения от инструкции PRINT, перенаправляются в журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если проверка подлинности завершается сбоем, триггеры входа не срабатывают.  
  
 Можно использовать триггеры входа для проверки и управления сеансами сервера, например для отслеживания входов в систему, ограничения входов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]или ограничения числа сеансов для конкретного имени входа. Например, в следующем коде триггер входа запрещает попытки входа на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , инициированные под именем входа *login_test* , если уже созданы три пользовательских сеанса под этим именем входа.  
  
```  
USE master;  
GO  
CREATE LOGIN login_test WITH PASSWORD = '3KHJ6dhx(0xVYsdf' MUST_CHANGE,  
    CHECK_EXPIRATION = ON;  
GO  
GRANT VIEW SERVER STATE TO login_test;  
GO  
CREATE TRIGGER connection_limit_trigger  
ON ALL SERVER WITH EXECUTE AS 'login_test'  
FOR LOGON  
AS  
BEGIN  
IF ORIGINAL_LOGIN()= 'login_test' AND  
    (SELECT COUNT(*) FROM sys.dm_exec_sessions  
            WHERE is_user_process = 1 AND  
                original_login_name = 'login_test') > 3  
    ROLLBACK;  
END;  
```  
  
 Обратите внимание, что событие LOGON соответствует событию AUDIT_LOGIN трассировки SQL, которое можно использовать в [уведомлениях о событии](../../relational-databases/service-broker/event-notifications.md). Основное отличие между триггерами и уведомлениями о событиях состоит в том, что триггеры вызываются синхронно с событиями, тогда как уведомления о событиях асинхронны. Это означает, например, что если необходимо остановить установление сеанса, необходимо использовать триггер входа. Для этой цели нельзя использовать уведомление о событии AUDIT_LOGIN.  
  
## <a name="specifying-first-and-last-trigger"></a>Указание первого и последнего триггера  
 В событии LOGON может быть определено несколько триггеров. Любой из этих триггеров может быть назначен как первый или последний триггер, активируемый при возникновении некоторого события с использованием системной хранимой процедуры [sp_settriggerorder](../../relational-databases/system-stored-procedures/sp-settriggerorder-transact-sql.md) . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не гарантирует порядок выполнения остальных триггеров.  
  
## <a name="managing-transactions"></a>Управление транзакциями  
 Перед тем как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] активирует триггер входа, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает неявную транзакцию, которая не зависит ни от какой пользовательской транзакции. Таким образом, при срабатывании первого триггера входа счетчик транзакций имеет значение 1. После завершения выполнения всех триггеров входа происходит фиксация транзакции. Как и для триггеров других типов, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает ошибку, если триггер входа завершает выполнение со значением счетчика транзакций, равным 0. Инструкция ROLLBACK TRANSACTION сбрасывает счетчик транзакций в 0, даже если инструкция выдана внутри вложенной транзакции. Инструкция COMMIT TRANSACTION может уменьшить значение счетчика транзакций до 0. В связи с этим не рекомендуется использовать инструкции COMMIT TRANSACTION внутри триггеров входа.  
  
 Учитывайте следующее при использовании инструкции ROLLBACK TRANSACTION в триггерах входа.  
  
-   Происходит откат любых изменений данных, сделанных до точки отката ROLLBACK TRANSACTION. В эти изменения входят как изменения, сделанные текущим триггером, так и те изменения, которые были сделаны предыдущими триггерами, выполнявшимися в том же событии. Оставшиеся триггеры указанного события выполняться не будут.  
  
-   Текущий триггер продолжает выполнять все оставшиеся инструкции после инструкции ROLLBACK. Если какая-нибудь из инструкций изменит данные, откат этих изменений выполнен не будет.  
  
 Сеанс пользователя не будет установлен, если произойдет одно из следующих событий при выполнении триггера на событии LOGON.  
  
-   Произойдет либо откат, либо сбой исходной неявной транзакции.  
  
-   В тексте триггера появится ошибка с уровнем серьезности свыше 20.  
  
## <a name="disabling-a-logon-trigger"></a>Отключение триггера входа  
 Триггер входа может эффективно запрещать подключения к службам [!INCLUDE[ssDE](../../includes/ssde-md.md)] для всех пользователей, в том числе членов предопределенной роли сервера **sysadmin** . Если триггер входа запрещает соединения, члены предопределенной роли сервера **sysadmin** могут подключаться с помощью выделенного административного соединения или путем вызова [!INCLUDE[ssDE](../../includes/ssde-md.md)] в режиме минимальной конфигурации (-f). Дополнительные сведения см. в разделе [Параметры запуска службы Database Engine](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Задача|Раздел|  
|----------|-----------|  
|Описывает, как создать триггеры входа. Триггеры входа могут создаваться из любой базы данных, но регистрируются на уровне сервера и принадлежат базе данных **master** .|[CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)|  
|Описывает, как изменить триггеры входа.|[ALTER TRIGGER (Transact-SQL)](../../t-sql/statements/alter-trigger-transact-sql.md)|  
|Описывает, как удалить триггеры входа.|[DROP TRIGGER (Transact-SQL)](../../t-sql/statements/drop-trigger-transact-sql.md)|  
|Описывает, как возвратить сведения о триггерах входа.|[sys.server_triggers (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md)<br /><br /> [sys.server_trigger_events (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql.md)|  
|Описывает, как перехватить данные события триггером входа.||  
  
## <a name="see-also"></a>См. также:  
 [Триггеры DDL](../../relational-databases/triggers/ddl-triggers.md)  
  
  
