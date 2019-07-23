---
title: Назначение учетной записи для запуска службы агента SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, service accounts
- startup accounts [SQL Server]
- service startup accounts [SQL Server Agent]
ms.assetid: 46ffe818-ebb5-43a0-840b-923f219a2472
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a8464242443b6a7b75dac227eabdbb32c88fa733
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68262941"
---
# <a name="set-the-service-startup-account-for-sql-server-agent-sql-server-configuration-manager"></a>Set the Service Startup Account for SQL Server Agent (SQL Server Configuration Manager)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Стартовая учетная запись службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет учетную запись Windows, которая запускает агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а также его сетевые разрешения. Этот раздел посвящен назначению учетных записей службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [Ограничения](#Restrictions)  
  
    [безопасность](#Security)  
  
-   [Назначение стартовой учетной записи службы для службы агента SQL Server при помощи среды SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Restrictions"></a>Ограничения  
  
-   Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] больше не требует, чтобы стартовая учетная запись была элементом группы администраторов [!INCLUDE[msCoName](../../includes/msconame_md.md)] . Однако стартовая учетная запись службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должна быть членом предопределенной роли сервера sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы использовать обработку заданий в многосерверной среде, учетная запись должна быть членом роли "TargetServersRole" базы данных "msdb" на главном сервере.  
  
-   Узел агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отображается в обозревателе объектов только при наличии у пользователя разрешения на использование узла.  
  
### <a name="Security"></a>безопасность  
  
#### <a name="Permissions"></a>Permissions  
Для выполнения своих функций агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть настроен на использование учетных данных записи, которая является членом предопределенной роли сервера **sysadmin** в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта учетная запись должна иметь следующие разрешения Windows.  
  
-   Вход в систему в качестве службы (SeServiceLogonRight)  
  
-   Замена токена уровня процесса (SeAssignPrimaryTokenPrivilege)  
  
-   Обход проходной проверки (SeChangeNotifyPrivilege)  
  
-   Назначение квот памяти процессам (SeIncreaseQuotaPrivilege)  
  
Дополнительные сведения о разрешениях Windows, необходимых для учетной записи службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , см. в разделах [Выбор учетной записи для службы агента SQL Server](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) и [Настройка учетных записей служб Windows](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-set-the-service-startup-account-for-sql-server-agent"></a>Назначение стартовой учетной записи службы агента SQL Server  
  
1.  В списке **Зарегистрированные серверы**щелкните знак «плюс», чтобы развернуть **Ядро СУБД**.  
  
2.  Чтобы развернуть папку **Группы локальных серверов** , щелкните знак «плюс» (+).  
  
3.  Щелкните правой кнопкой мыши экземпляр сервера, в котором нужно назначить стартовую учетную запись службы, и выберите **Диспетчер конфигурации SQL Server...**  
  
4.  В диалоговом окне **Контроль учетных записей** нажмите кнопку **Да**.  
  
5.  В диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на панели консоли выберите **Службы SQL Server**.  
  
6.  В области сведений щелкните правой кнопкой **Агент SQL Server** _(имя\_сервера)_ , где *имя_сервера* — это имя экземпляра агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], для которого нужно изменить стартовую учетную запись службы, и выберите пункт **Свойства**.  
  
7.  В диалоговом окне **Свойства агента SQL Server** _(имя\_сервера)_ **выберите** на вкладке **Вход в систему** один из следующих параметров в разделе **Использовать для входа**:  
  
    -   **Встроенная учетная запись**. Выберите этот параметр, если заданиям требуются ресурсы только с локального сервера. Дополнительные сведения о выборе типа встроенной учетной записи Windows см. в разделе [Выбор учетной записи для службы агента SQL Server.](https://msdn.microsoft.com/library/ms191543.aspx)  
  
        > [!IMPORTANT]  
        > Служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает учетную запись **Локальная служба** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
    -   **Указанная учетная запись**. Выберите этот параметр, если заданиям требуются сетевые ресурсы (в том числе ресурсы приложений), а также если необходимо передавать события журналам других программ Windows или уведомлять операторов по электронной почте или на пейджер.  
  
        В случае использования этого параметра:  
  
        1.  В поле **Имя учетной записи** введите учетную запись, которая будет использоваться для запуска агента SQL Server. Или нажмите кнопку **Обзор** , чтобы открыть диалоговое окно **Выбор пользователя или группы** , и выберите учетную запись для использования.  
  
        2.  В поле **Пароль** введите пароль, соответствующий учетной записи. Повторно введите пароль в поле **Подтверждение пароля** .  
  
8.  Нажмите кнопку **ОК**.  
  
9. В диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] нажмите кнопку **Закрыть** .  
  
