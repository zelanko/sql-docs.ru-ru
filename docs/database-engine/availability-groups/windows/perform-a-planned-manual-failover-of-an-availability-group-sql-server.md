---
title: Запланированный переход на другой ресурс вручную для группы доступности (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 10/25/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: availability-groups
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.swb.availabilitygroup.manualfailover.f1
helpviewer_keywords:
- Availability Groups [SQL Server], failover
- failover [SQL Server], AlwaysOn Availability Groups
ms.assetid: 419f655d-3f9a-4e7d-90b9-f0bab47b3178
caps.latest.revision: 36
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 1871f7a555647b7c52bd3d4750d047e2281c31f6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="perform-a-planned-manual-failover-of-an-availability-group-sql-server"></a>Запланированный переход на другой ресурс вручную для группы доступности (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
В этом разделе описывается выполнение перехода на другой ресурс вручную без потери данных (*запланированный переход на другой ресурс вручную*) в группе доступности AlwaysOn с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] или PowerShell в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Группа доступности выполняет переход на другой ресурс на уровне реплики доступности. Запланированный переход на другой ресурс вручную, как и любая другая отработка отказа для группы доступности AlwaysOn, переводит вторичную реплику на основную роль. При этом бывшая первичная реплика принимает роль вторичной.  
  
Этот переход поддерживается, только если первичная и целевая вторичная реплики работают в режиме синхронной фиксации и в текущий момент синхронизированы. При запланированном переходе на другой ресурс вручную сохраняются все данные в базах данных-получателях, подключенных к группе доступности на целевой вторичной реплике. После перевода бывшей первичной реплики на роль вторичной ее базы данных становятся базами данных — получателями. Затем они начинают синхронизироваться с новыми базами данных — источниками. После того как они все перейдут в состояние SYNCHRONIZED, новая вторичная реплика может служить целью будущей запланированного перехода на другой ресурс вручную.  
  
> [!NOTE]  
>  Если и первичная, и вторичная реплики настроены на автоматический переход на другой ресурс, то вторичная реплика может служить целевой и для этого перехода после синхронизации. Дополнительные сведения см. в разделе [Режимы доступности &#40;Группы доступности AlwaysOn&#41;](../../../database-engine/availability-groups/windows/availability-modes-always-on-availability-groups.md).  
   
##  <a name="BeforeYouBegin"></a> Перед началом 

>[!IMPORTANT]
>Существуют определенные процедуры по отработке отказа группы доступности для чтения и масштабирования без диспетчера кластеров. Если в группе доступности задан параметр CLUSTER_TYPE = NONE (тип кластера — отсутствует), следуйте процедурам, описанным в разделе [Отработка отказа первичной реплики в группе доступности для чтения и масштабирования](#fail-over-the-primary-replica-on-a-read-scale-availability-group).

###  <a name="Restrictions"></a> Ограничения 
  
- Команда отработки отказа завершает работу сразу после того, как целевая вторичная реплика примет команду. Однако восстановление базы данных происходит асинхронно после того, как группа доступности закончит отработку отказа. 
- Целостность данных баз данных в группе доступности во время отработки отказа может не обеспечиваться. 
  
    > [!NOTE] 
    >  Поддержка транзакций между базами данных и распределенных транзакций зависит от версий операционной системы и SQL Server. Дополнительные сведения: [Транзакции между базами данных и распределенные транзакции для групп доступности AlwaysOn и зеркального отображения базы данных &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md). 
  
###  <a name="Prerequisites"></a> Требования и ограничения 
  
-   Первичная и целевая вторичная реплики должны работать в режиме доступности с синхронной фиксацией. 
-   Целевая вторичная реплика сейчас должна быть синхронизирована с первичной репликой. Все базы данных — получатели в этой вторичной реплике должны быть подключены к группе доступности. Они также должны быть синхронизированы с соответствующими базами данных — источниками (то есть локальные базы данных — получатели должны быть в состоянии SYNCHRONIZED). 
  
    > [!TIP] 
    >  Чтобы определить готовность вторичной реплики к отработке отказа, запросите столбец **is_failover_ready** в динамическом административном представлении [sys.dm_hadr_database_cluster_states](../../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql.md). Либо проверьте значение столбца **Готовность к отработке отказа** в [панели мониторинга группы AlwaysOn](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md). 
-   Эта задача поддерживается только в целевой вторичной реплике. Необходимо подключиться к экземпляру сервера, на котором размещается целевая вторичная реплика. 
  
###  <a name="Security"></a> безопасность 
  
####  <a name="Permissions"></a> Permissions 
 Группе доступности необходимо предоставить разрешение ALTER AVAILABILITY GROUP. Также необходимо разрешение CONTROL AVAILABILITY GROUP, ALTER ANY AVAILABILITY GROUP или CONTROL SERVER. 
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio 
 Чтобы выполнить отработку отказа для группы доступности вручную выполните следующее. 
  
1. В обозревателе объектов подключитесь к экземпляру сервера, где размещена вторичная реплика группы доступности, для которой требуется отработка отказа. Разверните дерево сервера. 
  
2. Разверните узел **Высокий уровень доступности AlwaysOn** и узел **Группы доступности** . 
  
3. Щелкните правой кнопкой мыши группу доступности для отработки отказа и выберите **Отработка отказа**. 
  
4. Запустится мастер отработки отказа группы доступности. Дополнительные сведения: [Использование мастера отработки отказа группы доступности &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-fail-over-availability-group-wizard-sql-server-management-studio.md). 
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL 
 Чтобы выполнить отработку отказа для группы доступности вручную выполните следующее. 
  
1. Подключитесь к экземпляру сервера, на котором находится целевая вторичная реплика. 
  
2. Инструкция [ALTER AVAILABILITY GROUP](../../../t-sql/statements/alter-availability-group-transact-sql.md) используется следующим образом: 
  
     ALTER AVAILABILITY GROUP *имя_группы* FAILOVER 
  
     В этой инструкции *имя_группы* — это имя группы доступности. 
  
     В следующем примере выполняется ручная отработка отказа группы доступности *MyAg* на подключенную вторичную реплику. 
  
    ```  
    ALTER AVAILABILITY GROUP MyAg FAILOVER;  
    ```  
  
##  <a name="PowerShellProcedure"></a> Использование PowerShell 
 Чтобы выполнить отработку отказа для группы доступности вручную выполните следующее. 
  
1. Перейдите в каталог (**cd**) экземпляра сервера, на котором размещена целевая вторичная реплика. 
  
2. Используйте командлет **Switch-SqlAvailabilityGroup** . 
  
    > [!NOTE] 
    >  Чтобы просмотреть синтаксис командлета, воспользуйтесь командлетом **Get-Help** в среде PowerShell [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] . Дополнительные сведения: [Получение справки по SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md). 
  
     В следующем примере выполняется ручная отработка отказа группы доступности *MyAg* на вторичную реплику по указанному пути: 
  
    ```  
    Switch-SqlAvailabilityGroup -Path SQLSERVER:\Sql\SecondaryServer\InstanceName\AvailabilityGroups\MyAg  
    ```  
  
    Настройка и использование поставщика SQL Server PowerShell: 
  
    -   [Поставщик SQL Server PowerShell](../../../relational-databases/scripting/sql-server-powershell-provider.md) 
    -   [Получение справки по SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md) 

##  <a name="FollowUp"></a> Дальнейшие действия: после отработки отказа группы доступности вручную 
 Если отработка отказа была выполнена на ресурс, не входящий в [!INCLUDE[ssFosAuto](../../../includes/ssfosauto-md.md)] группы доступности, перенастройте голоса кворума узлов отказоустойчивой кластеризации Windows Server, чтобы отразить новую конфигурацию группы доступности. Дополнительные сведения: [Отказоустойчивая кластеризация Windows Server &#40;WSFC&#41; с SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md). 

<a name = "ReadScaleOutOnly"><a/>

## <a name="fail-over-the-primary-replica-on-a-read-scale-availability-group"></a>Отработка отказа первичной реплики в группе доступности для чтения и масштабирования

[!INCLUDE[Force failover](../../../includes/ss-force-failover-read-scale-out.md)]

## <a name="see-also"></a>См. также раздел 

 * [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) 
 * [Отработка отказа и режимы отработки отказа &#40;группы доступности AlwaysOn&#41;](../../../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md) 
 * [Принудительный переход на другой ресурс вручную для группы доступности &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md) 
  
  
