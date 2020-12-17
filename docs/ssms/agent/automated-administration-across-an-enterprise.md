---
description: Автоматизация администрирования в масштабах предприятия
title: Автоматизация администрирования в масштабах предприятия
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- enterprise automatic administration [SQL Server]
- multiserver administration [SQL Server]
- SQL Server Agent jobs, multiserver administration
- jobs [SQL Server Agent], multiserver administration
- master servers [SQL Server], about master servers
- target servers [SQL Server], about target servers
- master servers [SQL Server]
- multiple instances of SQL Server
- target servers [SQL Server]
ms.assetid: 44d8365b-42bd-4955-b5b2-74a8a9f4a75f
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016
ms.openlocfilehash: fbd8507befa387e64a85153a9ccc08311f3577f1
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97424706"
---
# <a name="automated-administration-across-an-enterprise"></a>Автоматизация администрирования в масштабах предприятия
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

 Автоматическое администрирование нескольких экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] называется *администрированием нескольких серверов*. Оно предназначено для выполнения следующих задач.  
  
-   Управления двумя или несколькими серверами.  
  
-   Планирования потоков данных между серверами предприятия для организации хранилищ данных.  
  
Чтобы воспользоваться преимуществами администрирования нескольких серверов, необходимо иметь, по меньшей мере, один главный сервер и один целевой. Главный сервер распределяет задания целевым серверам и получает от них события. На главном сервере также хранится центральная копия определений заданий, выполняющихся на целевых серверах. Целевые серверы периодически подключаются к главному серверу для обновления расписаний своих заданий. Если на главном сервере имеется новое задание, то целевой сервер получает его. После завершения задания целевой сервер подключается к главному серверу и сообщает о состоянии его завершения. Обратите внимание, что определение задания должно быть одинаковым при выполнении любых действий, связанных с базой данных.  
  
На следующем рисунке показана связь между главным и целевыми серверами.  
  
![Настройка администрирования нескольких серверов](../../ssms/agent/media/multisvr.gif "Настройка администрирования нескольких серверов")  
  
При администрировании серверов подразделений крупного предприятия можно определить:  
  
-   единое задание резервного копирования, разбитое на шаги;  
  
-   операторов, которые будут уведомлены в случае сбоя при резервном копировании;  
  
-   расписание выполнения для этого задания.  
  
Один раз сохраните это задание резервного копирования на сервере, а затем прикрепите серверы подразделений как целевые. С этого момента все серверы подразделений выполняют одно и то же задание, хотя оно было определено всего один раз.  
  
> [!NOTE]  
> Функции администрирования нескольких серверов предназначены для членов роли sysadmin. Тем не менее член роли sysadmin на целевом сервере не может изменить операции, которые главный сервер выполняет на целевом сервере. Такая мера предосторожности предохраняет шаги задания от случайного удаления, а операции на целевом сервере — от постороннего вмешательства.  
  
## <a name="in-this-section"></a>в этом разделе  
[Создание многосерверной среды](../../ssms/agent/create-a-multiserver-environment.md)  
Содержит сведения о создании главного и целевых серверов и управлении ими.  
  
[Выбор правильной учетной записи службы агента SQL Server для многосерверной среды](../../ssms/agent/choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)  
Содержит сведения о влиянии использования неадминистративных учетных записей Windows или учетной записи Local System службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на многосерверное окружение.  
  
[Установка параметров шифрования на целевых серверах](../../ssms/agent/set-encryption-options-on-target-servers.md)  
Содержит сведения о настройке подраздела реестра MsxEncryptChannelOptions агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на целевых серверах.  
  
[Управление заданиями в масштабе предприятия](../../ssms/agent/manage-jobs-across-an-enterprise.md)  
Содержит сведения о проверке состояния задания, изменения для него целевых серверов, синхронизации времени на целевых серверах и опросе главных серверов о состоянии текущих заданий.  
  
[Устранение неполадок, связанных с многосерверными заданиями, использующими учетные записи-посредники](../../ssms/agent/troubleshoot-multiserver-jobs-that-use-proxies.md)  
Содержит сведения об устранении неполадок многосерверных заданий, которые используют неверные учетные записи-посредники.  
  
[Опрос серверов](../../ssms/agent/poll-servers.md)  
Содержит сведения о том, как явно или неявно заставить целевые серверы синхронизировать сведения о заданиях с главным сервером.  
  
[Управление событиями](../../ssms/agent/manage-events.md)  
Содержит сведения о пересылке событий от целевых серверов к главному.  
  
[Настройка автоматизированного администрирования в организации](../../ssms/agent/tune-automated-administration-across-an-enterprise.md)  
Содержит сведения о том, как автоматизированное администрирование в многосерверном окружении использует функции самонастройки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
[Разделы, посвященные обратной совместимости при установке ядра СУБД SQL Server](../../database-engine/discontinued-database-engine-functionality-in-sql-server.md)  
[Регистрация серверов](../register-servers/register-servers.md)  
[sp_add_targetservergroup](../../relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql.md)  
[sp_delete_targetserver, хранимая процедура](../../relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql.md)  
[sp_delete_targetservergroup](../../relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql.md)  
[sp_help_downloadlist](../../relational-databases/system-stored-procedures/sp-help-downloadlist-transact-sql.md)  
[sp_help_jobserver](../../relational-databases/system-stored-procedures/sp-help-jobserver-transact-sql.md)  
[sp_help_targetservergroup](../../relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql.md)  
[sp_resync_targetserver](../../relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql.md)  
[sp_update_targetservergroup](../../relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql.md)  
[sysjobservers](../../relational-databases/system-tables/dbo-sysjobservers-transact-sql.md)  
[syslogins](../../relational-databases/system-compatibility-views/sys-syslogins-transact-sql.md)  
[systargetservers](../../relational-databases/system-tables/dbo-systargetservers-transact-sql.md)  
