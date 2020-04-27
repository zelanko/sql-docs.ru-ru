---
title: Просмотр активности заданий | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- viewing job activity
- jobs [SQL Server Agent], viewing
- SQL Server Agent jobs, viewing
- displaying job activity
ms.assetid: 5c284e5e-7775-435d-ac49-f3f12a27ddc7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3fc6099fa9f523b351489ce4301596aeb90c1509
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "68211308"
---
# <a name="view-job-activity"></a>Просмотр активности заданий
  В этом разделе описано, как с помощью хранимых процедур просматривать состояние среды выполнения заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 При запуске службы агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создается новый сеанс, а в таблицу **sysjobactivity** базы данных **msdb** заносятся все существующие определенные задания. В таблице регистрируется текущая активность задания и его состояние. Монитор активности заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет просматривать текущее состояние заданий. Если служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] непредвиденно останавливается, в таблице **sysjobactivity** можно будет увидеть, какие задания выполнялись в момент прекращения работы службы.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Для просмотра активности заданий используется:**  
  
     [Среда SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
## <a name="before-you-begin"></a>Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
 Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-job-activity"></a>Просмотр активности заданий  
  
1.  В **обозревателе объектов**подключитесь к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], а затем разверните этот экземпляр.  
  
2.  Разверните узел **Агент SQL Server**.  
  
3.  Щелкните правой кнопкой мыши **Монитор активности заданий** и выберите команду **Просмотреть активность заданий**.  
  
4.  В **мониторе активности заданий**можно просмотреть подробные сведения о каждом из заданий, определенных для данного сервера.  
  
5.  По щелчку правой кнопки мыши можно запустить задание, остановить его, включить или отключить, обновить состояние, отображаемое в «Мониторе активности задания», удалить задание или просмотреть его историю или свойства.  Чтобы запустить, остановить, включить или отключить либо обновить несколько заданий, выберите несколько строк в «Мониторе активности заданий» и щелкните выделенные элементы правой кнопкой мыши.  
  
6.  Для обновления «Монитора активности заданий» выберите пункт **Обновить**. Для уменьшения количества отображаемых строк щелкните **Фильтр** и введите параметры фильтрации.  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Использование Transact-SQL  
  
#### <a name="to-view-job-activity"></a>Просмотр активности заданий  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- lists activity for all jobs that the current user has permission to view.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_jobactivity ;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_help_jobactivity &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobactivity-transact-sql).  
  
  
