---
title: Send SQL Server Agent Error Messages
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- messages [SQL Server], SQL Server Agent
- sending messages
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: 2597d0d7-951a-48cf-989f-abb67b9fdb36
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 3aec88f017ffd9b405a68e15494f980322386690
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "75239188"
---
# <a name="send-sql-server-agent-error-messages"></a>Send SQL Server Agent Error Messages
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описано, как настроить отправку сообщений об ошибках агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] командой net send в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="limitations-and-restrictions"></a><a name="Restrictions"></a>Ограничения  
  
-   Узел агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отображается в обозревателе объектов только при наличии у пользователя разрешения на использование узла.  
  
-   Для приема сообщений net send необходимо запустить службу [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows Messenger.  
  
### <a name="security"></a><a name="Security"></a>безопасность  
  
#### <a name="permissions"></a><a name="Permissions"></a>Permissions  
Для выполнения своих функций агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть настроен на использование учетных данных записи, которая является членом предопределенной роли сервера **sysadmin** в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта учетная запись должна иметь следующие разрешения Windows.  
  
-   Вход в систему в качестве службы (SeServiceLogonRight)  
  
-   Замена токена уровня процесса (SeAssignPrimaryTokenPrivilege)  
  
-   Обход проходной проверки (SeChangeNotifyPrivilege)  
  
-   Назначение квот памяти процессам (SeIncreaseQuotaPrivilege)  
  
Дополнительные сведения о разрешениях Windows, необходимых для учетной записи службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , см. в разделах [Выбор учетной записи для службы агента SQL Server](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) и [Настройка учетных записей служб Windows](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-send-sql-server-agent-error-messages"></a>Отправка сообщений об ошибках агента SQL Server  
  
1.  В **обозревателе объектов**щелкните знак «плюс», чтобы развернуть сервер, содержащий журнал ошибок агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , из которого необходимо отправлять сообщения об ошибках командой net send.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server** и выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Свойства агента SQL Server —** _имя\_сервера_ в разделе **Журнал ошибок** на странице **Общие** в поле **Получатель для команды net send** введите имя пользователя или компьютера, которому следует отправлять сообщения об ошибках.  
  
4.  Нажмите кнопку **ОК**.  
  
