---
title: "Удаление вторичной реплики из группы доступности (SQL Server) | Документы Майкрософт"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.availabilitygroup.removesecondaryar.f1
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], configuring
ms.assetid: 35ddc8b6-3e7c-4417-9a0a-d4987a09ddf7
caps.latest.revision: "38"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 50c8a91c4a5838b479ca9a09dedd2daa772825cb
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="remove-a-secondary-replica-from-an-availability-group-sql-server"></a>Удаление вторичной реплики из группы доступности (SQL Server)
  В этом разделе описывается удаление вторичной реплики из группы доступности AlwaysOn с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]или PowerShell в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Предварительные требования](#Prerequisites)  
  
     [Безопасность](#Security)  
  
-   **Удаление вторичной реплики с помощью**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   **Дальнейшие действия.**  [После удаления вторичной реплики](#PostBestPractices)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Эта задача поддерживается только в первичной реплике.  
  
-   Из группы доступности может быть удалена только вторичная реплика.  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Необходимо иметь подключение к экземпляру сервера, на котором размещена первичная реплика группы доступности.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Удаление вторичной реплики**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, на котором размещена первичная реплика, и разверните дерево сервера.  
  
2.  Разверните узел **Высокий уровень доступности AlwaysOn** и узел **Группы доступности** .  
  
3.  Выберите группу доступности и разверните узел **Реплики доступности** .  
  
4.  Этот шаг имеет следующие различия в зависимости от того, удаляется одна или несколько реплик.  
  
    -   Чтобы удалить несколько реплик, используйте область **Подробности** обозревателя объектов, чтобы просмотреть и выбрать реплики для удаления. Дополнительные сведения см. в статье [Использование раздела "Подробности обозревателя объектов" для мониторинга групп доступности (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-object-explorer-details-to-monitor-availability-groups.md).  
  
    -   Чтобы удалить одну реплику, выберите ее на панели **Обозреватель объектов** или на панели **Подробности обозревателя объектов** .  
  
5.  Щелкните правой кнопкой мыши выбранную вторичную реплику или реплики и выберите в контекстном меню команду **Удалить из группы доступности** .  
  
6.  Чтобы удалить все перечисленные вторичные реплики, в диалоговом окне **Удаление вторичных реплик из группы доступности** нажмите кнопку **ОК**. Если все перечисленные группы доступности удалять не нужно, нажмите кнопку **Отмена**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Удаление вторичной реплики**  
  
1.  Подключитесь к экземпляру сервера, на котором находится первичная реплика.  
  
2.  Инструкция [ALTER AVAILABILITY GROUP](../../../t-sql/statements/alter-availability-group-transact-sql.md) используется следующим образом:  
  
     ALTER AVAILABILITY GROUP *имя_группы* REMOVE REPLICA ON "*имя_экземпляра*" [,...*n*],  
  
     где *имя_группы* — имя группы доступности, а *имя_экземпляра* — экземпляр сервера, на котором размещена вторичная реплика.  
  
     В следующем примере удаляется вторичная реплика из группы доступности *MyAG* . Целевая вторичная реплика расположена на экземпляре сервера с именем *HADR_INSTANCE* на компьютере *COMPUTER02*.  
  
    ```  
    ALTER AVAILABILITY GROUP MyAG REMOVE REPLICA ON 'COMPUTER02\HADR_INSTANCE';  
    ```  
  
##  <a name="PowerShellProcedure"></a> Использование PowerShell  
 **Удаление вторичной реплики**  
  
1.  Перейдите в каталог (**cd**) экземпляра сервера, в котором находится первичная реплика.  
  
2.  Используйте командлет **Remove-SqlAvailabilityReplica** .  
  
     Например, следующая команда удаляет реплику доступности на сервере `MyReplica` из группы доступности с именем `MyAg`.  Эта команда должна выполняться на экземпляре сервера, на котором размещена первичная реплика группы доступности.  
  
    ```  
    Remove-SqlAvailabilityReplica `   
    -Path SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  Чтобы просмотреть синтаксис командлета, воспользуйтесь командлетом **Get-Help** в среде [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md).  
  
 **Настройка и использование поставщика SQL Server PowerShell**  
  
-   [SQL Server PowerShell, поставщик](../../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
##  <a name="PostBestPractices"></a> Дальнейшие действия. После удаления вторичной реплики  
 Если была выбрана реплика, которая в данный момент недоступна, ее удаление произойдет в момент перехода в режим «в сети».  
  
 Удаление реплики прекращает поступление в нее данных. После того, как вторичная реплика подтверждает, что она была удалена из глобального хранилища, реплика удаляет параметры группы доступности из своих баз данных, которые остаются на экземпляре локального сервера в состоянии RECOVERING.  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Добавление вторичной реплики к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/add-a-secondary-replica-to-an-availability-group-sql-server.md)   
 [Удаление группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/remove-an-availability-group-sql-server.md)  
  
  
