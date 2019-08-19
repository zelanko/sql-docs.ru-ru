---
title: Настройка агента SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, configuring
- accounts [SQL Server], SQL Server Agent
- SQL Server Agent, permissions
- security [SQL Server], SQL Server Agent
ms.assetid: 2e361a62-9e92-4fcd-80d7-d6960f127900
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 7b5f766351e9551143fdbd66571224e11845d659
ms.sourcegitcommit: 57e20b7d02853ec9af46b648106578aed133fb45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69553150"
---
# <a name="configure-sql-server-agent"></a>Configure SQL Server Agent
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Включение и отключение агента SQL Server в настоящее время не поддерживается для управляемого экземпляра базы данных SQL. Агент SQL работает всегда. Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описывается задание некоторых параметров конфигурации для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] во время установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Доступ к полному набору параметров конфигурации агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно получить с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], управляющих объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SMO) или хранимых процедур агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Restrictions"></a>Ограничения  
  
-   Щелкните элемент **Агент SQL Server** в обозревателе объектов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для администрирования заданий, операторов, оповещений и службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Однако с узлом агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в обозревателе объектов можно работать только при наличии соответствующего разрешения.  
  
-   В экземплярах отказоустойчивых кластеров не должен быть включен автоматический перезапуск службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="Security"></a>Безопасность  
  
#### <a name="Permissions"></a>Permissions  
Для выполнения своих функций агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть настроен на использование учетных данных записи, которая является членом предопределенной роли сервера **sysadmin** в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта учетная запись должна иметь следующие разрешения Windows.  
  
-   Вход в систему в качестве службы (SeServiceLogonRight)  
  
-   Замена токена уровня процесса (SeAssignPrimaryTokenPrivilege)  
  
-   Обход проходной проверки (SeChangeNotifyPrivilege)  
  
-   Назначение квот памяти процессам (SeIncreaseQuotaPrivilege)  
  
Дополнительные сведения о разрешениях Windows, необходимых для учетной записи службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , см. в разделах [Выбор учетной записи для службы агента SQL Server](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) и [Настройка учетных записей служб Windows](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-sql-server-agent"></a>Настройка агента SQL Server  
  
1.  Нажмите кнопку **Пуск** и щелкните в меню **Пуск**  элемент **Панель управления**.  
  
2.  На панели управления выберите категорию **Система и безопасность**, щелкните элемент **Администрирование**, а затем выберите пункт **Локальная политика безопасности**.  
  
3.  В окне «Локальная политика безопасности» щелкните треугольник, чтобы развернуть папку **Локальные политики** , а затем щелкните папку **Назначение прав пользователя** .  
  
4.  Щелкните правой кнопкой мыши разрешение, которое нужно настроить для использования с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , и выберите пункт **Свойства**.  
  
5.  В диалоговом окне свойств разрешения убедитесь, что указана учетная запись, с которой работает агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если это не так, нажмите кнопку **Добавить пользователя или группу**, введите учетную запись, с которой работает агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в диалоговом окне **Выбор пользователей, компьютеров, учетных записей служб или групп** , а затем нажмите кнопку **ОК**.  
  
6.  Повторите эту процедуру для каждого разрешения, которое нужно добавить для работы с агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . После завершения нажмите кнопку **ОК**.  
  
