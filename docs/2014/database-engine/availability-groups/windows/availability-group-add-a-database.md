---
title: Добавление базы данных в группу доступности (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- primary databases [SQL Server], in availability group
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: 2a54eef8-9e8e-4e04-909c-6970112d55cc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 69d148f9ef780e28300a6d3e233f2b680f0d37d5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62791990"
---
# <a name="add-a-database-to-an-availability-group-sql-server"></a>Добавление базы данных в группу доступности (SQL Server)
  В этом разделе описывается добавление базы данных в группу доступности AlwaysOn с помощью [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]или PowerShell в среде [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
-   **Перед началом:**  
  
     [Требования и ограничения](#Prerequisites)  
  
     [Разрешения](#Permissions)  
  
-   **Добавление базы данных в группу доступности с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Требования и ограничения  
  
-   Необходимо подключиться к экземпляру сервера, на котором размещена первичная реплика.  
  
-   База данных должна находиться на экземпляре сервера, на котором размещена первичная реплика, и должна соответствовать предварительным условиям и требованиям к базам данных доступности. Дополнительные сведения см. в разделе [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn (SQL Server)](prereqs-restrictions-recommendations-always-on-availability.md).  
  
###  <a name="Security"></a> безопасность  
  
###  <a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Добавление базы данных в группу доступности**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, на котором размещена первичная реплика, и разверните дерево сервера.  
  
2.  Разверните узел **Высокий уровень доступности AlwaysOn** и узел **Группы доступности** .  
  
3.  Щелкните правой кнопкой группу доступности и выберите одну из следующих команд.  
  
    -   Для запуска мастера добавления базы данных в группу доступности выберите команду **Добавление базы данных** . Дополнительные сведения см. в разделе [Использование мастера добавления базы данных в группу доступности (среда SQL Server Management Studio)](availability-group-add-database-to-group-wizard.md).  
  
    -   Для добавления одной или нескольких баз данных путем их указания в диалоговом окне **Свойства группы доступности** выберите команду **Свойства** . Шаги для добавления базы данных.  
  
        1.  На панели **Базы данных доступности** нажмите кнопку **Добавить** . Будет создано и выбрано пустое поле базы данных.  
  
        2.  Введите имя базы данных, удовлетворяющее требованиям баз данных доступности.  
  
         Чтобы добавить другую базу данных, повторите предыдущие шаги. После указания баз данных нажмите кнопку **ОК** для завершения операции.  
  
         После добавления базы данных в группу доступности с помощью диалогового окна **Свойства группы доступности** необходимо настроить соответствующую базу данных-получатель на каждом из экземпляров сервера, на которых размещена вторичная реплика. Дополнительные сведения см. в разделе [Запуск перемещения данных в базе данных-получателе AlwaysOn (SQL Server)](start-data-movement-on-an-always-on-secondary-database-sql-server.md).  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Добавление базы данных в группу доступности**  
  
1.  Подключитесь к экземпляру сервера, на котором размещен экземпляр сервера с первичной репликой доступности.  
  
2.  Инструкция [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) используется следующим образом:  
  
     ALTER AVAILABILITY GROUP *group_name* ADD DATABASE *database_name* [,...*n*]  
  
     где *group_name* — это имя группы доступности, а *database_name* — это имя базы данных, добавляемой в группу.  
  
     В следующем примере добавляется база данных *MyDb3* в группу доступности *MyAG* .  
  
    ```  
    -- Connect to the server instance that hosts the primary replica.  
    -- Add an existing database to the availability group.  
    ALTER AVAILABILITY GROUP MyAG ADD DATABASE MyDb3;  
    GO  
    ```  
  
3.  После добавления базы данных в группу доступности необходимо настроить соответствующую базу данных-получатель на каждом из экземпляров сервера, на которых размещена вторичная реплика. Дополнительные сведения см. в разделе [Запуск перемещения данных в базе данных-получателе AlwaysOn (SQL Server)](start-data-movement-on-an-always-on-secondary-database-sql-server.md).  
  
##  <a name="PowerShellProcedure"></a> Использование PowerShell  
 **Добавление базы данных в группу доступности**  
  
1.  Перейдите в каталог (`cd`) экземпляра сервера, на котором находится первичная реплика.  
  
2.  Используйте командлет `Add-SqlAvailabilityDatabase`.  
  
     Например, следующая команда добавляет базу данных-получатель `MyDd` к группе доступности `MyAG` , первичная реплика которой размещена в расположении `PrimaryServer\InstanceName`.  
  
    ```  
  
    Add-SqlAvailabilityDatabase `   
    -Path SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MyAG `   
    -Database "MyDb"  
    ```  
  
    > [!NOTE]  
    >  Чтобы просмотреть синтаксис командлета, воспользуйтесь командлетом `Get-Help` в среде [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
3.  После добавления базы данных в группу доступности необходимо настроить соответствующую базу данных-получатель на каждом из экземпляров сервера, на которых размещена вторичная реплика. Дополнительные сведения см. в разделе [Запуск перемещения данных в базе данных-получателе AlwaysOn (SQL Server)](start-data-movement-on-an-always-on-secondary-database-sql-server.md).  
  
 **Настройка и использование поставщика SQL Server PowerShell**  
  
-   [Поставщик SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
 Полный пример см. в разделе [Пример (PowerShell)](#PSExample)ниже.  
  
###  <a name="PSExample"></a> Пример (PowerShell)  
 В следующем примере показан полный процесс подготовки базы данных-получателя из базы данных на экземпляре сервера, на котором размещается первичная реплика группы доступности, добавления базы данных в группу доступности (в качестве базы данных-источника) и присоединения базы данных-получателя к группе доступности. Во-первых, в примере выполняется резервное копирование базы данных и ее журнала транзакций. Затем выполняется восстановление из резервной копии базы данных и журнала в экземпляры сервера, в которых размещается вторичная реплика.  
  
 В этом примере `Add-SqlAvailabilityDatabase` вызывается дважды: сначала в первичной реплике для добавления базы данных в группу доступности, а затем во вторичной реплике для присоединения базы данных-получателя из этой реплики к группе доступности. При наличии нескольких вторичных реплик нужно выполнить восстановление и присоединение базы данных-получателя в каждой из них.  
  
```  
$DatabaseBackupFile = "\\share\backups\MyDatabase.bak"  
$LogBackupFile = "\\share\backups\MyDatabase.trn"  
$MyAgPrimaryPath = "SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MyAg"  
$MyAgSecondaryPath = "SQLSERVER:\SQL\SecondaryServer\InstanceName\AvailabilityGroups\MyAg"  
  
Backup-SqlDatabase -Database "MyDatabase" -BackupFile $DatabaseBackupFile -ServerInstance "PrimaryServer\InstanceName"  
Backup-SqlDatabase -Database "MyDatabase" -BackupFile $LogBackupFile -ServerInstance "PrimaryServer\InstanceName" -BackupAction 'Log'  
  
Restore-SqlDatabase -Database "MyDatabase" -BackupFile $DatabaseBackupFile -ServerInstance "SecondaryServer\InstanceName" -NoRecovery  
Restore-SqlDatabase -Database "MyDatabase" -BackupFile $LogBackupFile -ServerInstance "SecondaryServer\InstanceName" -RestoreAction 'Log' -NoRecovery  
  
Add-SqlAvailabilityDatabase -Path $MyAgPrimaryPath -Database "MyDatabase"  
Add-SqlAvailabilityDatabase -Path $MyAgSecondaryPath -Database "MyDatabase"  
  
```  
  
## <a name="see-also"></a>См. также  
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Создание и настройка групп доступности (SQL Server)](creation-and-configuration-of-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)   
 [Отслеживание групп доступности (Transact-SQL)](monitor-availability-groups-transact-sql.md)  
  
  
