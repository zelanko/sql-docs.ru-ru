---
title: Задача "Выполнение задания агента SQL Server" (план обслуживания) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql13.swb.maint.executejob.f1
helpviewer_keywords:
- Execute SQL Server Agent Job Task dialog box
ms.assetid: 4ed75956-ebb8-4d8c-9c16-fc0eb00bd3a0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0cf96745f6b2b2c904262a4952f63b6ec37f263e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85667364"
---
# <a name="execute-sql-server-agent-job-task-maintenance-plan"></a>Задача «Выполнение задания агента SQL Server» (план обслуживания)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Используйте диалоговое окно **Задача «Выполнение задания агента SQL Server»** для выполнения заданий агента Microsoft SQL Server в соответствии с планом обслуживания. Данный параметр недоступен, если для выбранного соединения нет заданий агента SQL Server.  
  
 Эта задача использует инструкцию **.sp_start_job** .  
  
## <a name="ui-element-list"></a>Список элементов пользовательского интерфейса  
 **Соединение**  
 Выберите соединение с сервером, которое будет использоваться для выполнения этой задачи.  
  
 **Создать**  
 Создать новое соединение с сервером для его использования при выполнении этой задачи. Диалоговое окно **Создание соединения** описано ниже.  
  
 **Доступные задания агента SQL Server**  
 Выберите задание для выполнения. Для идентификации заданий в сетке используются столбцы **Имя задания** и **Описание** .  
  
 **Просмотр T-SQL**  
 Просмотрите инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] , выполняемые для данной задачи по отношению к серверу, на основе выбранных параметров.  
  
> [!NOTE]  
>  Если количество затронутых объектов велико, построение этого отображения может занять значительное время.  
  
## <a name="new-connection-dialog-box"></a>Диалоговое окно «Создание соединения»  
 **Имя соединения**  
 Введите имя нового соединения.  
  
 **Выберите или введите имя сервера**  
 Выберите сервер для подключения при выполнении этой задачи.  
  
 **Обновить**  
 Обновите список доступных серверов.  
  
 **Введите данные для входа на сервер**  
 Укажите способ проверки подлинности на сервере.  
  
 **Использовать встроенную безопасность Windows**  
 Подключение к экземпляру компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] с использованием проверки подлинности Windows.  
  
 **Использовать указанные имя пользователя и пароль**  
 Подключиться к экземпляру компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] с использованием проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот параметр недоступен.  
  
 **User name**  
 Укажите имя входа, используемое при проверке подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Этот параметр недоступен.  
  
 **Пароль**  
 Укажите используемый при проверке подлинности пароль. Этот параметр недоступен.  
  
## <a name="see-also"></a>См. также:  
 [sp_add_job (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [Создание задания](../../ssms/agent/create-a-job.md)   
 [sp_start_job (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md)  
  
  
