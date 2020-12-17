---
description: Просмотр сведений об операторе
title: Просмотр сведений об операторе
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- viewing operators
- operators (users) [Database Engine], viewing with Management Studio
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
- displaying operators
ms.assetid: 92c82cdf-f704-444e-9539-82aea7fe6fb7
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016
ms.openlocfilehash: a9fb20b3a5d161c4d69d15740defc3dd10ebe7a4
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97480715"
---
# <a name="view-information-about-an-operator"></a>Просмотр сведений об операторе
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этой статье описывается просмотр сведений об операторе агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="security"></a><a name="Security"></a>безопасность  
  
#### <a name="permissions"></a><a name="Permissions"></a>Permissions  
По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-view-information-about-an-operator"></a>Просмотр сведений об операторе  
  
1.  В **обозревателе объектов** щелкните знак «плюс», чтобы развернуть сервер, содержащий оператора, которого нужно проверить.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните значок «плюс», чтобы развернуть папку **Операторы** .  
  
4.  Щелкните правой кнопкой оператор, который нужно просмотреть, и выберите пункт **Свойства**.  
  
    Дополнительные сведения о доступных параметрах, содержащихся в диалоговом окне _Свойства_**имя_оператора** , см. в разделе:  
  
    -   [Свойства оператора — создание оператора (страница "Общие")](../../ssms/agent/operator-properties-new-operator-general-page.md)  
  
    -   [Свойства оператора — создание оператора (страница "Уведомления")](../../ssms/agent/operator-properties-new-operator-notifications-page.md)  
  
    -   [Свойства оператора (страница "Журнал")](../../ssms/agent/operator-properties-history-page.md)  
  
5.  После завершения нажмите кнопку **ОК**.  
  
## <a name="using-transact-sql"></a><a name="TsqlProcedure"></a>Использование Transact-SQL  
  
#### <a name="to-view-information-about-an-operator"></a>Просмотр сведений об операторе  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- reports information about operator François Ajenstat   
    -- This example assumes that the operator exists.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_operator  
        @operator_name = N'François Ajenstat' ;  
    GO  
    ```  
  
Дополнительные сведения см. в разделе [sp_help_operator (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md).  
