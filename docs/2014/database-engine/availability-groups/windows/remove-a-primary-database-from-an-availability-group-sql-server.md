---
title: Удаление базы данных-источника из группы доступности (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.removeprimarydb.f1
helpviewer_keywords:
- primary databases [SQL Server], in availability group
- Availability Groups [SQL Server], removing
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: 6d4ca31e-ddf0-44bf-be5e-a5da060bf096
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 06b9dac5f9074b335afff7c6b71980618a3020ce
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "72782873"
---
# <a name="remove-a-primary-database-from-an-availability-group-sql-server"></a>Удаление базы данных-источника из группы доступности (SQL Server)
  В этом разделе описывается удаление базы данных-источника и соответствующих баз данных-получателей из группы доступности AlwaysOn с использованием среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] или PowerShell в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
-   **Перед началом работы**  
  
     [Предварительные условия и ограничения](#Prerequisites)  
  
     [Безопасность](#Security)  
  
-   **Удаление база данных доступности с помощью**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   **Дальнейшие действия**  [После удаления базы данных доступности из группы доступности](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a>Предварительные условия и ограничения  
  
-   Эта задача поддерживается только на первичных репликах. Необходимо подключиться к экземпляру сервера, на котором размещена первичная реплика.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Удаление базы данных доступности**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, размещающего базы данных, которые требуется удалить, и разверните дерево сервера.  
  
2.  Разверните узел **Высокий уровень доступности AlwaysOn** и узел **Группы доступности** .  
  
3.  Выберите группу доступности и разверните узел **Базы данных доступности** .  
  
4.  Этот шаг зависит от того, удаляется несколько баз данных или только одна база данных.  
  
    -   Чтобы удалить несколько баз данных, используйте панель **Подробности обозревателя объектов** , чтобы просмотреть и выбрать базы данных, которые требуется удалить. Дополнительные сведения см. в разделе [Использование раздела "Подробности обозревателя объектов" для мониторинга групп доступности (среда SQL Server Management Studio)](use-object-explorer-details-to-monitor-availability-groups.md).  
  
    -   Чтобы удалить одну базу данных, выберите ее в **обозревателе объектов** или на панели **Подробности обозревателя объектов** .  
  
5.  Щелкните правой кнопкой мыши выбранную базу данных или базы данных и выберите в контекстном меню команду **Удаление базы данных из группы доступности** .  
  
6.  В диалоговом окне **Удаление баз данных из группы доступности** нажмите кнопку **ОК**, чтобы удалить все выбранные базы данных. Если все удалять не нужно, нажмите кнопку **Отмена**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Удаление базы данных доступности**  
  
1.  Подключитесь к экземпляру сервера, на котором находится первичная реплика.  
  
2.  Инструкция [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) используется следующим образом:  
  
     ALTER AVAILABILITY GROUP *имя_группы* REMOVE DATABASE *имя_базы_данных_доступности*  
  
     где *имя_группы* — имя группы доступности, а *имя_базы_данных_доступности* — имя удаляемой базы данных.  
  
     В следующем примере удаляется база данных с именем `Db6` из группы доступности `MyAG` .  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAG REMOVE DATABASE Db6;  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Использование PowerShell  
 **Удаление базы данных доступности**  
  
1.  Перейдите в каталог (`cd`) экземпляра сервера, на котором находится первичная реплика.  
  
2.  Используйте командлет `Remove-SqlAvailabilityDatabase`, указав имя базы данных доступности, которую требуется удалить из группы доступности. Если установлено подключение к экземпляру сервера, на котором размещается первичная реплика, из группы доступности удаляется как база данных-источник, так и все соответствующие базы данных-получатели.  
  
     Например, следующая команда удаляет базу данных доступности `MyDb9` из группы доступности с именем `MyAg`. Поскольку команда выполняется в экземпляре сервера, на котором размещается первичная реплика, из группы доступности удаляется как база данных-источник, так и все соответствующие базы данных-получатели. Синхронизация данных для этой базы данных во всех вторичных репликах больше происходить не будет.  
  
    ```powershell
    Remove-SqlAvailabilityDatabase -Path SQLSERVER:\Sql\PrimaryComputer\InstanceName\AvailabilityGroups\MyAg\Databases\MyDb9  
    ```  
  
    > [!NOTE]  
    >  Чтобы просмотреть синтаксис командлета, воспользуйтесь командлетом `Get-Help` в среде [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Настройка и использование поставщика SQL Server PowerShell**  
  
-   [Поставщик SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-after-removing-an-availability-database-from-an-availability-group"></a><a name="FollowUp"></a> Дальнейшие действия. После удаления базы данных доступности из группы доступности  
 При удалении базы данных доступности из соответствующей группы доступности выполнение синхронизации данных между бывшей базой данных-источником и соответствующими базами данных-получателями прекращается. Бывшая база данных-источник остается в режиме «в сети». Все соответствующие базы данных-получатели переводятся в состояние RESTORING.  
  
 В этот момент поступить с удаленной базой данных-получателем можно следующим образом.  
  
-   Если база данных-получатель больше не нужна, ее можно удалить.  
  
     Дополнительные сведения см. в разделе [Удаление базы данных](../../../relational-databases/databases/delete-a-database.md).  
  
-   Если после удаления базы данных-получателя из группы доступности она еще может понадобиться, ее можно восстановить. Однако при восстановлении удаленной базы данных-получателя в режиме «в сети» окажутся две разные базы данных с одним именем. Нужно обеспечить, чтобы клиент имел доступ только к одной из них — обычно самой последней базе данных-источнику.  
  
     Дополнительные сведения см. в разделе [Восстановление базы данных без восстановления данных (Transact-SQL)](../../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Удаление базы данных-получателя из группы доступности (SQL Server)](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
