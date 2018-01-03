---
title: "Просмотр активности заданий | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- viewing job activity
- jobs [SQL Server Agent], viewing
- SQL Server Agent jobs, viewing
- displaying job activity
ms.assetid: 5c284e5e-7775-435d-ac49-f3f12a27ddc7
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: db455e9d96d1d63b44dc4a462576c1a605d16dab
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="view-job-activity"></a>Просмотр активности заданий
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В этом разделе описано, как с помощью хранимых процедур просматривать состояние среды выполнения заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] или [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
При запуске службы агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] создается новый сеанс, а в таблицу **sysjobactivity** базы данных **msdb** заносятся все определенные задания. В таблице регистрируется текущая активность задания и его состояние. Монитор активности заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] позволяет просматривать текущее состояние заданий. Если служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] непредвиденно останавливается, в таблице **sysjobactivity** можно будет увидеть, какие задания выполнялись в момент прекращения работы службы.  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [безопасность](#Security)  
  
-   **Для просмотра активности заданий используется:**  
  
    [Среда SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
## <a name="before-you-begin"></a>Перед началом  
  
### <a name="Security"></a>безопасность  
Дополнительные сведения см. в разделе [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-view-job-activity"></a>Просмотр активности заданий  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Разверните узел **Агент SQL Server**.  
  
3.  Щелкните правой кнопкой мыши **Монитор активности заданий** и выберите команду **Просмотреть активность заданий**.  
  
4.  В **мониторе активности заданий**можно просмотреть подробные сведения о каждом из заданий, определенных для данного сервера.  
  
5.  По щелчку правой кнопки мыши можно запустить задание, остановить его, включить или отключить, обновить состояние, отображаемое в «Мониторе активности задания», удалить задание или просмотреть его историю или свойства.  Чтобы запустить, остановить, включить или отключить либо обновить несколько заданий, выберите несколько строк в «Мониторе активности заданий» и щелкните выделенные элементы правой кнопкой мыши.  
  
6.  Для обновления «Монитора активности заданий» выберите пункт **Обновить**. Для уменьшения количества отображаемых строк щелкните **Фильтр** и введите параметры фильтрации.  
  
## <a name="TSQL"></a>Использование Transact-SQL  
  
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
  
Дополнительные сведения см. в разделе [sp_help_jobactivity (Transact-SQL)](http://msdn.microsoft.com/en-us/d344864f-b4d3-46b1-8933-b81dec71f511).  
  
