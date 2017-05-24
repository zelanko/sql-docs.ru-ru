---
title: "Автоматизированное администрирование в организации | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 618e199812a39ec29e032f8371419ec6184c713f
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="automated-administration-across-an-enterprise"></a>Автоматизация администрирования в масштабах предприятия
Автоматическое администрирование нескольких экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] называется *администрированием нескольких серверов*. Оно предназначено для выполнения следующих задач.  
  
-   Управления двумя или несколькими серверами.  
  
-   Планирования потоков данных между серверами предприятия для организации хранилищ данных.  
  
Чтобы воспользоваться преимуществами администрирования нескольких серверов, необходимо иметь, по меньшей мере, один главный сервер и один целевой. Главный сервер распределяет задания целевым серверам и получает от них события. На главном сервере также хранится центральная копия определений заданий, выполняющихся на целевых серверах. Целевые серверы периодически подключаются к главному серверу для обновления расписаний своих заданий. Если на главном сервере имеется новое задание, то целевой сервер получает его. После завершения задания целевой сервер подключается к главному серверу и сообщает о состоянии его завершения. Обратите внимание, что определение задания должно быть одинаковым при выполнении любых действий, связанных с базой данных.  
  
На следующем рисунке показана связь между главным и целевыми серверами.  
  
![Конфигурация многосерверного администрирования](../../ssms/agent/media/multisvr.gif "Конфигурация многосерверного администрирования")  
  
При администрировании серверов подразделений крупного предприятия можно определить:  
  
-   единое задание резервного копирования, разбитое на шаги;  
  
-   операторов, которые будут уведомлены в случае сбоя при резервном копировании;  
  
-   расписание выполнения для этого задания.  
  
Один раз сохраните это задание резервного копирования на сервере, а затем прикрепите серверы подразделений как целевые. С этого момента все серверы подразделений выполняют одно и то же задание, хотя оно было определено всего один раз.  
  
> [!NOTE]  
> Функции администрирования нескольких серверов предназначены для членов роли sysadmin. Тем не менее член роли sysadmin на целевом сервере не может изменить операции, которые главный сервер выполняет на целевом сервере. Такая мера предосторожности предохраняет шаги задания от случайного удаления, а операции на целевом сервере — от постороннего вмешательства.  
  
## <a name="in-this-section"></a>В этом разделе  
[Создание многосерверной среды](../../ssms/agent/create-a-multiserver-environment.md)  
Содержит сведения о создании главного и целевых серверов и управлении ими.  
  
[Выбор правильной учетной записи службы агента SQL Server для многосерверной среды](../../ssms/agent/choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)  
Содержит сведения о влиянии использования неадминистративных учетных записей Windows или учетной записи Local System службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] на многосерверное окружение.  
  
[Установка параметров шифрования на целевых серверах](../../ssms/agent/set-encryption-options-on-target-servers.md)  
Содержит сведения о настройке подраздела реестра MsxEncryptChannelOptions агента[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] на целевых серверах.  
  
[Управление заданиями в масштабе предприятия](../../ssms/agent/manage-jobs-across-an-enterprise.md)  
Содержит сведения о проверке состояния задания, изменения для него целевых серверов, синхронизации времени на целевых серверах и опросе главных серверов о состоянии текущих заданий.  
  
[Устранение неполадок, связанных с многосерверными заданиями, использующими учетные записи-посредники](../../ssms/agent/troubleshoot-multiserver-jobs-that-use-proxies.md)  
Содержит сведения об устранении неполадок многосерверных заданий, которые используют неверные учетные записи-посредники.  
  
[Опрос серверов](../../ssms/agent/poll-servers.md)  
Содержит сведения о том, как явно или неявно заставить целевые серверы синхронизировать сведения о заданиях с главным сервером.  
  
[Управление событиями](../../ssms/agent/manage-events.md)  
Содержит сведения о пересылке событий от целевых серверов к главному.  
  
[Настройка автоматизированного администрирования в организации](../../ssms/agent/tune-automated-administration-across-an-enterprise.md)  
Содержит сведения о том, как автоматизированное администрирование в многосерверном окружении использует функции самонастройки [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
## <a name="see-also"></a>См. также:  
[Разделы, посвященные обратной совместимости при установке ядра СУБД SQL Server](http://msdn.microsoft.com/en-us/10de5ec6-d3cf-42ef-aa62-1bdf3fbde841)  
[Регистрация серверов](http://msdn.microsoft.com/en-us/c2a2513e-fa09-419c-99e7-a12d57c5a0db)  
[sp_add_targetservergroup](http://msdn.microsoft.com/en-us/acb69343-d766-46ff-b771-0c7655c5231a)  
[sp_delete_targetserver, хранимая процедура, хранимая процедура](http://msdn.microsoft.com/en-us/cc438701-ad91-419d-9f23-ebc4c548c700)  
[sp_delete_targetservergroup](http://msdn.microsoft.com/en-us/d8dd838e-64aa-419f-9ccb-ff04908cf3e4)  
[sp_help_downloadlist](http://msdn.microsoft.com/en-us/745b265b-86e8-4399-b928-c6969ca1a2c8)  
[sp_help_jobserver](http://msdn.microsoft.com/en-us/57971787-f9f5-4199-9f64-c2b61a308906)  
[sp_help_targetservergroup](http://msdn.microsoft.com/en-us/ec3a4a68-b591-431c-9518-053ede522d0c)  
[sp_resync_targetserver](http://msdn.microsoft.com/en-us/40e44df7-d3e3-44ee-b149-08aba629a21f)  
[sp_update_targetservergroup](http://msdn.microsoft.com/en-us/4ac65ed6-e07e-40e4-a282-13bfd92dfa41)  
[sysjobservers](http://msdn.microsoft.com/en-us/9abcc20f-a421-4591-affb-62674d04575e)  
[syslogins](http://msdn.microsoft.com/en-us/4cb34f17-a4bb-469f-a218-71f074e6308f)  
[systargetservers](http://msdn.microsoft.com/en-us/479d1314-be37-4d19-ac9c-419fc9110e53)  
  

