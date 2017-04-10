---
title: "Присоединение базы данных-получателя к группе доступности (SQL Server) | Microsoft Docs"
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
  - "sql13.swb.availabilitygroup.joindbs.f1"
helpviewer_keywords: 
  - "базы данных-получатели [SQL Server], в группе доступности"
  - "базы данных-получатели [SQL Server]"
  - "группы доступности [SQL Server], присоединение"
  - "группы доступности [SQL Server], настройка"
  - "Группы доступности [SQL Server], базы данных"
ms.assetid: fd7efe79-c1f9-497d-bfe7-b2a2b2321cf5
caps.latest.revision: 39
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 39
---
# Присоединение базы данных-получателя к группе доступности (SQL Server)
  В этом разделе описывается присоединение базы данных-получателя к группе доступности AlwaysOn с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] или PowerShell в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. После подготовки базы данных-получателя для вторичной реплики необходимо как можно скорее присоединить базу данных к группе доступности. При этом начнется перемещение данных из соответствующей основной базы данных в базу данных-получатель.  
  
-   **Перед началом работы**  
  
     [Предварительные требования](#Prerequisites)  
  
     [Безопасность](#Security)  
  
-   **Подготовка базы данных-получателя с помощью различных средств.**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
> [!NOTE]  
>  Сведения о том, что происходит после присоединения базы данных-получателя к группе, см. в статье [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Необходимо подключиться к экземпляру сервера, на котором находится дополнительная реплика.  
  
-   Дополнительная реплика уже должна быть присоединена к группе доступности. Дополнительные сведения см. в статье [Присоединение вторичной реплики к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/join-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
-   База данных-получатель должна быть подготовлена заранее. Дополнительные сведения см. в статье [Ручная подготовка базы данных-получателя для присоединения к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Присоединение базы данных-получателя к группе доступности**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, на котором размещена вторичная реплика, и разверните дерево сервера.  
  
2.  Разверните узел **Высокий уровень доступности AlwaysOn** и узел **Группы доступности**.  
  
3.  Разверните группу доступности, которую необходимо изменить, и разверните узел **Базы данных доступности** .  
  
4.  Щелкните правой кнопкой мыши эту базу данных и выберите **Присоединить к группе доступности**.  
  
5.  Откроется диалоговое окно **Присоединение базы данных к группе доступности** . Проверьте имя группы доступности, которое отображается в панели заголовка. При этом имя или имена баз данных должны отображаться в сетке. Нажмите кнопку **ОК**или **Отмена**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Присоединение базы данных-получателя к группе доступности**  
  
1.  Подключитесь к экземпляру сервера, на котором находится дополнительная реплика.  
  
2.  Используйте предложение [SET HADR в инструкции ALTER DATABASE](../Topic/ALTER%20DATABASE%20SET%20HADR%20\(Transact-SQL\).md) следующим образом:  
  
     ALTER DATABASE *имя_базы_данных* SET HADR AVAILABILITY GROUP = *имя_группы*  
  
     где *имя_базы_данных* — это имя присоединяемой базы данных, а *имя_группы* — это имя группы доступности.  
  
     В следующем примере база данных-получатель `Db1` включается в локальную вторичную реплику группы доступности `MyAG`.  
  
    ```  
    ALTER DATABASE Db1 SET HADR AVAILABILITY GROUP = MyAG;  
    ```  
  
    > [!NOTE]  
    >  Пример использования инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] в контексте см. в статье [Создание группы доступности (Transact-SQL)](../../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md).  
  
##  <a name="PowerShellProcedure"></a> Использование PowerShell  
 **Присоединение базы данных-получателя к группе доступности**  
  
1.  Перейдите в каталог (**cd**) экземпляра сервера, на котором размещается вторичная реплика.  
  
2.  С помощью командлета **Add-SqlAvailabilityDatabase** присоедините одну или несколько баз данных-получателей к группе доступности.  
  
     Например, следующая команда присоединяет базу данных-получатель `Db1` к группе доступности `MyAG` в одном из экземпляров сервера, на котором находится вторичная реплика.  
  
    ```  
    Add-SqlAvailabilityDatabase `   
    -Path SQLSERVER:\SQL\SecondaryServer\InstanceName\AvailabilityGroups\MyAG `   
    -Database "Db1"  
    ```  
  
    > [!NOTE]  
    >  Чтобы просмотреть синтаксис командлета, воспользуйтесь командлетом **Get-Help** в среде [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md).  
  
 **Настройка и использование поставщика SQL Server PowerShell**  
  
-   [SQL Server PowerShell, поставщик](../../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Присоединение вторичной реплики к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Подготовка базы данных-получателя для присоединения к группе доступности вручную (SQL Server)](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
## См. также:  
 [ALTER AVAILABILITY GROUP (Transact-SQL)](../../../t-sql/statements/alter-availability-group-transact-sql.md)   
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Поиск и устранение неисправностей конфигурации групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
  