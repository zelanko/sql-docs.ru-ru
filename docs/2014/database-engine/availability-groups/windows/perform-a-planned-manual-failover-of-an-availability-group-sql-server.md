---
title: Выполнение запланированного перехода на другой ресурс вручную для группы доступности (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.manualfailover.f1
helpviewer_keywords:
- Availability Groups [SQL Server], failover
- failover [SQL Server], AlwaysOn Availability Groups
ms.assetid: 419f655d-3f9a-4e7d-90b9-f0bab47b3178
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c62942eaa8f4ab4472bca5c7123e5999eb069216
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936675"
---
# <a name="perform-a-planned-manual-failover-of-an-availability-group-sql-server"></a>Выполнение запланированного перехода на другой ресурс вручную для группы доступности (SQL Server)
   Этот раздел описывает, как выполнить переход на другой ресурс вручную без потери данных (*запланированный переход на другой ресурс вручную*) в группе доступности AlwaysOn с помощью [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] или PowerShell в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Группа доступности выполняет переход на другой ресурс на уровне реплики доступности. Запланированный переход на другой ресурс вручную, как и любая отработка отказа [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] , переводит вторичную реплику в роль первичной и одновременно переводит реплику, бывшую первичной, в роль вторичной.  
  
 При запланированном переходе на другой ресурс вручную, который поддерживается, только если первичная и целевая вторичная реплики работают в режиме синхронной фиксации и в данный момент синхронизированы, сохраняются все данные в базах данных-получателях, присоединенных к группе доступности в целевой вторичной реплике. После того как бывшая первичная реплика перейдет в роль вторичной, ее базы данных станут базами данных-получателями и начнут синхронизироваться с новыми базами данных-источниками. После того как они все перейдут в состояние SYNCHRONIZED, новая вторичная реплика может служить целью будущей запланированного перехода на другой ресурс вручную.  
  
> [!NOTE]  
>  Если для первичной и вторичной реплики задан автоматический переход на другой ресурс, то после синхронизации вторичная реплика также может выступать в качестве цели для автоматического перехода на другой ресурс. Дополнительные сведения см. в разделе [Режимы доступности (группы доступности AlwaysOn)](availability-modes-always-on-availability-groups.md).  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Команда отработки отказа завершает работу сразу после того, как целевая вторичная реплика примет команду. Однако восстановление базы данных происходит асинхронно после того, как группа доступности закончит отработку отказа.  
  
-   Целостность данных между базами данных в рамках группы доступности во время отработки отказа не поддерживается.  
  
    > [!NOTE]  
    >  Транзакции между базами данных и распределенные транзакции не поддерживаются в [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Дополнительные сведения см. в разделе [Транзакции между базами данных не поддерживаются при зеркальном отображении баз данных или в группах доступности AlwaysOn (SQL Server)](transactions-always-on-availability-and-database-mirroring.md).  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a>Предварительные условия и ограничения  
  
-   Целевая вторичная реплика и первичная реплика должны работать в режиме доступности с синхронной фиксацией.  
  
-   Целевая вторичная реплика должна в данный момент быть синхронизирована с первичной репликой. Для этого необходимо, чтобы все базы данных-получатели в этой вторичной реплике были присоединены к группе доступности и синхронизированы с соответствующими им базами данных-источниками (локальные базы данных-получатели должны находиться в состоянии SYNCHRONIZED).  
  
    > [!TIP]  
    >  Чтобы определить готовность вторичной реплики к переходу на другой ресурс, запросите столбец **is_failover_ready** в динамическом административном представлении [sys.dm_hadr_database_cluster_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql) или проверьте значение столбца **Готовность к отработке отказа** на [панели мониторинга групп AlwaysOn](use-the-always-on-dashboard-sql-server-management-studio.md).  
  
-   Эта задача поддерживается только в целевой вторичной реплике. Необходимо подключиться к экземпляру сервера, на котором размещается целевая вторичная реплика.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Переход на другой ресурс группы доступности вручную**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, на котором размещена вторичная реплика группы доступности, на которую нужно выполнить отработку отказа, и разверните дерево сервера.  
  
2.  Разверните узел **Высокий уровень доступности AlwaysOn** и узел **Группы доступности** .  
  
3.  Щелкните правой кнопкой мыши группу доступности для выполнения отработки отказа и выберите команду **Отработка отказа** .  
  
4.  Будет запущен мастер отработки отказа группой доступности. Дополнительные сведения см. в подразделе [Использование мастера отработки отказа группы доступности (среда SQL Server Management Studio)](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md).  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Переход на другой ресурс группы доступности вручную**  
  
1.  Подключитесь к экземпляру сервера, на котором находится целевая вторичная реплика.  
  
2.  Инструкция [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) используется следующим образом:  
  
     ALTER AVAILABILITY GROUP *имя_группы* FAILOVER  
  
     где *имя_группы* — это имя группы доступности.  
  
     В следующем примере вручную выполняется отработка отказа группы доступности *MyAg»* на подключенную вторичную реплику.  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAg FAILOVER;  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Использование PowerShell  
 **Переход на другой ресурс группы доступности вручную**  
  
1.  Перейдите в каталог (`cd`) экземпляра сервера, на котором размещается целевая вторичная реплика.  
  
2.  Используйте командлет `Switch-SqlAvailabilityGroup`.  
  
    > [!NOTE]  
    >  Чтобы просмотреть синтаксис командлета, воспользуйтесь командлетом `Get-Help` в среде [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
     В следующем примере вручную выполняется отработка отказа группы доступности *MyAg»* на вторичную реплику с указанным путем.  
  
    ```powershell
    Switch-SqlAvailabilityGroup -Path SQLSERVER:\Sql\SecondaryServer\InstanceName\AvailabilityGroups\MyAg  
    ```  
  
 **Настройка и использование поставщика SQL Server PowerShell**  
  
-   [Поставщик SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
-   [Получение справок по SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
##  <a name="follow-up-after-manually-failing-over-an-availability-group"></a><a name="FollowUp"></a> Дальнейшие действия. После ручной отработки отказа группы доступности  
 Если переход был выполнен на ресурс, находящийся за пределами группы доступности [!INCLUDE[ssFosAuto](../../../includes/ssfosauto-md.md)] , настройте кворум узлов кластера WSFC, чтобы отразить новую конфигурацию группы доступности. Дополнительные сведения см. в разделе [отказоустойчивая кластеризация Windows Server &#40;WSFC&#41; с SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md).  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Отказоустойчивость и режимы отработки отказа &#40;группы доступности AlwaysOn&#41;](failover-and-failover-modes-always-on-availability-groups.md)   
 [Выполнение принудительного перехода на другой ресурс вручную для группы доступности &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
