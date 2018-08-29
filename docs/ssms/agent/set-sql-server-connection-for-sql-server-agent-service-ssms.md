---
title: Настройка подключения SQL Server с агентом SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, connections
- connections [SQL Server], SQL Server Agent service
ms.assetid: 28b6178b-0a9e-4f2c-8562-7a62d2d2a285
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e09cd006762aae5ad9e0bb3b39742339f650bce6
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "42775091"
---
# <a name="set-the-sql-server-connection-for-the-sql-server-agent-service-sql-server-management-studio"></a>Настройка соединения SQL Server для агента SQL Server (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описывается настройка соединения между агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и компонентом [!INCLUDE[ssDE](../../includes/ssde_md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может подключаться к локальному экземпляру SQL Server с использованием проверки подлинности Windows.  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [Ограничения](#Restrictions)  
  
    [безопасность](#Security)  
  
-   **Для настройки соединения SQL Server с агентом SQL Server используется:**  
  
    [Среда SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Restrictions"></a>Ограничения  
  
-   Узел агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отображается в обозревателе объектов только при наличии у пользователя разрешения на использование узла.  
  
-   Начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Данная возможность доступна только в случае администрирования более ранней версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="Security"></a>безопасность  
  
#### <a name="Permissions"></a>Permissions  
Для выполнения своих функций агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть настроен на использование учетных данных записи, которая является членом предопределенной роли сервера **sysadmin** в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта учетная запись должна иметь следующие разрешения Windows.  
  
-   Вход в систему в качестве службы (SeServiceLogonRight)  
  
-   Замена токена уровня процесса (SeAssignPrimaryTokenPrivilege)  
  
-   Обход проходной проверки (SeChangeNotifyPrivilege)  
  
-   Назначение квот памяти процессам (SeIncreaseQuotaPrivilege)  
  
Дополнительные сведения о разрешениях Windows, необходимых для учетной записи службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , см. в разделах [Выбор учетной записи для службы агента SQL Server](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) и [Настройка учетных записей служб Windows](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-set-the-sql-server-connection"></a>Настройка соединения с сервером SQL Server  
  
1.  В **обозревателе объектов**щелкните знак «плюс», чтобы развернуть сервер, который нужно настроить для соединения со службой агента SQL Server.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server** и выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Свойства агента SQL Server***имя_сервера* в разделе **Выберите страницу** щелкните элемент **Соединение**.  
  
4.  В разделе **Соединение SQL Server**установите флажок **Использовать проверку подлинности Windows** , чтобы позволить агенту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подключаться к экземпляру компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde_md.md)] с использованием проверки подлинности [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows. Проверка подлинности Windows необходима для соединений с базами данных [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версий.  
  
