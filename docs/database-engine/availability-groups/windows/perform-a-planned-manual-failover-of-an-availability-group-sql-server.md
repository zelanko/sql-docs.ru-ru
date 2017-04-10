---
title: "Выполнение запланированного перехода на другой ресурс вручную для группы доступности (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.availabilitygroup.manualfailover.f1"
helpviewer_keywords: 
  - "Группы доступности [SQL Server], отработка отказа"
  - "отработка отказа [SQL Server] группы доступности AlwaysOn"
ms.assetid: 419f655d-3f9a-4e7d-90b9-f0bab47b3178
caps.latest.revision: 36
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 36
---
# Выполнение запланированного перехода на другой ресурс вручную для группы доступности (SQL Server)
  В этом разделе описывается выполнение перехода на другой ресурс вручную без потери данных (*запланированный переход на другой ресурс вручную*) в группе доступности AlwaysOn с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] или PowerShell в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Группа доступности выполняет переход на другой ресурс на уровне реплики доступности. Запланированный переход на другой ресурс вручную, как и любая отработка отказа [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], переводит вторичную реплику в роль первичной и одновременно переводит реплику, бывшую первичной, в роль вторичной.  
  
 При запланированном переходе на другой ресурс вручную, который поддерживается, только если первичная и целевая вторичная реплики работают в режиме синхронной фиксации и в данный момент синхронизированы, сохраняются все данные в базах данных-получателях, присоединенных к группе доступности в целевой вторичной реплике. После того как бывшая первичная реплика перейдет в роль вторичной, ее базы данных станут базами данных-получателями и начнут синхронизироваться с новыми базами данных-источниками. После того как они все перейдут в состояние SYNCHRONIZED, новая вторичная реплика может служить целью будущей запланированного перехода на другой ресурс вручную.  
  
> [!NOTE]  
>  Если для первичной и вторичной реплики задан автоматический переход на другой ресурс, то после синхронизации вторичная реплика также может выступать в качестве цели для автоматического перехода на другой ресурс. Дополнительные сведения см. в статье [Режимы доступности (группы доступности AlwaysOn)](../../../database-engine/availability-groups/windows/availability-modes-always-on-availability-groups.md).  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Требования и ограничения](#Prerequisites)  
  
     [Безопасность](#Security)  
  
-   **Для переключения группы доступности на другой ресурс вручную используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   **Дальнейшие действия.** [После ручной отработки отказа группы доступности](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Команда отработки отказа завершает работу сразу после того, как целевая вторичная реплика примет команду. Однако восстановление базы данных происходит асинхронно после того, как группа доступности закончит отработку отказа.  
  
-   Целостность данных баз данных в группе доступности во время отработки отказа может не обеспечиваться.  
  
    > [!NOTE]  
    >  Поддержка транзакций между базами данных и распределенных транзакций зависит от версий операционной системы и SQL Server. Дополнительные сведения см. в статье [Транзакции между базами данных и распределенные транзакции для групп доступности AlwaysOn и зеркального отображения базы данных (SQL Server)](../../../database-engine/availability-groups/windows/transactions - always on availability and database mirroring.md).  
  
###  <a name="Prerequisites"></a> Требования и ограничения  
  
-   Целевая вторичная реплика и первичная реплика должны работать в режиме доступности с синхронной фиксацией.  
  
-   Целевая вторичная реплика должна в данный момент быть синхронизирована с первичной репликой. Для этого необходимо, чтобы все базы данных-получатели в этой вторичной реплике были присоединены к группе доступности и синхронизированы с соответствующими им базами данных-источниками (локальные базы данных-получатели должны находиться в состоянии SYNCHRONIZED).  
  
    > [!TIP]  
    >  Чтобы определить готовность вторичной реплики к переходу на другой ресурс, запросите столбец **is_failover_ready** в динамическом административном представлении [sys.dm_hadr_database_cluster_states](../../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql.md) или проверьте значение столбца **Готовность к отработке отказа** на [панели мониторинга групп AlwaysOn](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md).  
  
-   Эта задача поддерживается только в целевой вторичной реплике. Необходимо подключиться к экземпляру сервера, на котором размещается целевая вторичная реплика.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Переход на другой ресурс группы доступности вручную**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, на котором размещена вторичная реплика группы доступности, на которую нужно выполнить отработку отказа, и разверните дерево сервера.  
  
2.  Разверните узел **Высокий уровень доступности AlwaysOn** и узел **Группы доступности**.  
  
3.  Щелкните правой кнопкой мыши группу доступности для выполнения отработки отказа и выберите команду **Отработка отказа**.  
  
4.  Будет запущен мастер отработки отказа группой доступности. Дополнительные сведения см. в статье [Использование мастера отработки отказа группы доступности (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-fail-over-availability-group-wizard-sql-server-management-studio.md).  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Переход на другой ресурс группы доступности вручную**  
  
1.  Подключитесь к экземпляру сервера, на котором находится целевая вторичная реплика.  
  
2.  Инструкция [ALTER AVAILABILITY GROUP](../../../t-sql/statements/alter-availability-group-transact-sql.md) используется следующим образом:  
  
     ALTER AVAILABILITY GROUP *имя_группы* FAILOVER  
  
     где *имя_группы* — это имя группы доступности.  
  
     В следующем примере выполняется ручная отработка отказа группы доступности *MyAg* на подключенную вторичную реплику.  
  
    ```  
    ALTER AVAILABILITY GROUP MyAg FAILOVER;  
    ```  
  
##  <a name="PowerShellProcedure"></a> Использование PowerShell  
 **Переход на другой ресурс группы доступности вручную**  
  
1.  Перейдите в каталог (**cd**) экземпляра сервера, на котором размещается целевая вторичная реплика.  
  
2.  Используйте командлет **Switch-SqlAvailabilityGroup**.  
  
    > [!NOTE]  
    >  Чтобы просмотреть синтаксис командлета, воспользуйтесь командлетом **Get-Help** в среде [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md).  
  
     В следующем примере группа доступности *MyAg* вручную выполняет отработку отказа на вторичную реплику с указанным путем.  
  
    ```  
    Switch-SqlAvailabilityGroup -Path SQLSERVER:\Sql\SecondaryServer\InstanceName\AvailabilityGroups\MyAg  
    ```  
  
 **Настройка и использование поставщика SQL Server PowerShell**  
  
-   [SQL Server PowerShell, поставщик](../../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
-   [Получение справок по SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md)  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После ручной отработки отказа группы доступности  
 Если переход был выполнен на ресурс, находящийся за пределами группы доступности [!INCLUDE[ssFosAuto](../../../includes/ssfosauto-md.md)], настройте кворум узлов кластера WSFC, чтобы отразить новую конфигурацию группы доступности. Дополнительные сведения см. в статье [Отказоустойчивая кластеризация Windows Server (WSFC) с SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md).  
  
## См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Отработка отказа и режимы отработки отказа (группы доступности AlwaysOn)](../../../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md)   
 [Выполнение принудительного перехода на другой ресурс вручную для группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
  