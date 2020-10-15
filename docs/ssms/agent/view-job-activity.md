---
description: Просмотр активности заданий
title: Просмотр активности заданий
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- viewing job activity
- jobs [SQL Server Agent], viewing
- SQL Server Agent jobs, viewing
- displaying job activity
ms.assetid: 5c284e5e-7775-435d-ac49-f3f12a27ddc7
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 04c42de9a98d507367cb2c2256a7c1f241baf1fc
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92030724"
---
# <a name="view-job-activity"></a>Просмотр активности заданий
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описано, как с помощью хранимых процедур просматривать состояние среды выполнения заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
При запуске службы агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создается новый сеанс, а в таблицу **sysjobactivity** базы данных **msdb** заносятся все существующие определенные задания. В таблице регистрируется текущая активность задания и его состояние. Монитор активности заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет просматривать текущее состояние заданий. Если служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] непредвиденно останавливается, в таблице **sysjobactivity** можно будет увидеть, какие задания выполнялись в момент прекращения работы службы.  
  
## <a name="before-you-begin"></a>Перед началом  
  
### <a name="security"></a><a name="Security"></a>безопасность  
Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMS"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-view-job-activity"></a>Просмотр активности заданий  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Разверните узел **Агент SQL Server**.  
  
3.  Щелкните правой кнопкой мыши **Монитор активности заданий** и выберите команду **Просмотреть активность заданий**.  
  
4.  В **мониторе активности заданий**можно просмотреть подробные сведения о каждом из заданий, определенных для данного сервера.  
  
5.  По щелчку правой кнопки мыши можно запустить задание, остановить его, включить или отключить, обновить состояние, отображаемое в «Мониторе активности задания», удалить задание или просмотреть его историю или свойства.  Чтобы запустить, остановить, включить или отключить либо обновить несколько заданий, выберите несколько строк в «Мониторе активности заданий» и щелкните выделенные элементы правой кнопкой мыши.  
  
6.  Для обновления «Монитора активности заданий» выберите пункт **Обновить**. Для уменьшения количества отображаемых строк щелкните **Фильтр** и введите параметры фильтрации.  
  
## <a name="using-transact-sql"></a><a name="TSQL"></a>Использование Transact-SQL  
  
#### <a name="to-view-job-activity"></a>Просмотр активности заданий  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- lists activity for all jobs that the current user has permission to view.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_jobactivity ;  
    GO  
    ```  
  
Дополнительные сведения см. в разделе [sp_help_jobactivity (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-help-jobactivity-transact-sql.md).  
