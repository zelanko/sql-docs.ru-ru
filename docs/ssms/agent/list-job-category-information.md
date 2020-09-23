---
description: Просмотр сведений о категории задания
title: Просмотр сведений о категории задания
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 0fc668d4-6244-4fef-b90e-62d2c776cd7c
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 87a72d720e751999e8de2a1f6e76df43c7348462
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88480333"
---
# <a name="list-job-category-information"></a>Просмотр сведений о категории задания
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описано, как просмотреть сведения о категории задания в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] или управляющих объектов SQL Server.  
  
-   **Перед началом работы**  
  
    [Безопасность](#Security)  
  
-   **Для просмотра сведений о категории задания используются:**  
  
    [Transact-SQL](#TSQL)  
  
    [Управляющие объекты SQL Server](#SMO)  
  
## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="security"></a><a name="Security"></a>безопасность  
Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="using-transact-sql"></a><a name="TSQL"></a>Использование Transact-SQL  
  
#### <a name="to-list-job-category-information"></a>Просмотр сведений о категории задания  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- returns information about jobs that are administered locally  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_category  
        @type = N'LOCAL' ;  
    GO  
    ```  
  
Дополнительные сведения см. в разделе [sp_help_category (Transact-SQL)](https://msdn.microsoft.com/8cad1dcc-b43e-43bd-bea0-cb0055c84169).  
  
## <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Использование управляющих объектов SQL Server  
**Просмотр сведений о категории задания**  
  
Воспользуйтесь классом **JobCategory** на любом языке программирования, таком как Visual Basic, Visual C# или PowerShell.  
  
