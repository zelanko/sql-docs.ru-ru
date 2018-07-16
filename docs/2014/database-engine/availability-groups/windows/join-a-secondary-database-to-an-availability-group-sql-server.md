---
title: Присоединение базы данных-получателя к группе доступности (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.joindbs.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- secondary databases [SQL Server]
- Availability Groups [SQL Server], joining
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: fd7efe79-c1f9-497d-bfe7-b2a2b2321cf5
caps.latest.revision: 37
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 21218bdd04922de0da35511c0d93f4770d5d6b30
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37269500"
---
# <a name="join-a-secondary-database-to-an-availability-group-sql-server"></a>Присоединение базы данных-получателя к группе доступности (SQL Server)
  В этом разделе объясняется, как присоединить базу данных-получатель к группе доступности AlwaysOn с помощью [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], или PowerShell в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. После подготовки базы данных-получателя для вторичной реплики необходимо как можно скорее присоединить базу данных к группе доступности. При этом начнется перемещение данных из соответствующей основной базы данных в базу данных-получатель.  
  
-   **Перед началом работы**  
  
     [Предварительные требования](#Prerequisites)  
  
     [безопасность](#Security)  
  
-   **Подготовка базы данных-получателя с помощью различных средств.**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
> [!NOTE]  
>  Чтобы узнать, что происходит после базу данных-получатель присоединяется к группе, см. в разделе [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Необходимо подключиться к экземпляру сервера, на котором находится дополнительная реплика.  
  
-   Дополнительная реплика уже должна быть присоединена к группе доступности. Дополнительные сведения см. в статье [Присоединение вторичной реплики к группе доступности (SQL Server)](join-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
-   База данных-получатель должна быть подготовлена заранее. Дополнительные сведения см. в статье [Подготовка базы данных-получателя для присоединения к группе доступности вручную (SQL Server)](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Присоединение базы данных-получателя к группе доступности**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, на котором размещена вторичная реплика, и разверните дерево сервера.  
  
2.  Разверните узел **Высокий уровень доступности AlwaysOn** и узел **Группы доступности** .  
  
3.  Разверните группу доступности, которую необходимо изменить, и разверните узел **Базы данных доступности** .  
  
4.  Щелкните правой кнопкой мыши эту базу данных и выберите **Присоединить к группе доступности**.  
  
5.  Откроется диалоговое окно **Присоединение базы данных к группе доступности** . Проверьте имя группы доступности, которое отображается в панели заголовка. При этом имя или имена баз данных должны отображаться в сетке. Нажмите кнопку **ОК**или **Отмена**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Присоединение базы данных-получателя к группе доступности**  
  
1.  Подключитесь к экземпляру сервера, на котором находится дополнительная реплика.  
  
2.  Используйте предложение [SET HADR в инструкции ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) следующим образом:  
  
     ALTER DATABASE *имя_базы_данных* SET HADR AVAILABILITY GROUP = *имя_группы*  
  
     где *имя_базы_данных* — это имя присоединяемой базы данных, а *имя_группы* — это имя группы доступности.  
  
     В следующем примере база данных-получатель `Db1` включается в локальную вторичную реплику группы доступности `MyAG`.  
  
    ```  
    ALTER DATABASE Db1 SET HADR AVAILABILITY GROUP = MyAG;  
    ```  
  
    > [!NOTE]  
    >  Пример использования инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] в контексте см. в статье [Создание группы доступности (Transact-SQL)](create-an-availability-group-transact-sql.md).  
  
##  <a name="PowerShellProcedure"></a> Использование PowerShell  
 **Присоединение базы данных-получателя к группе доступности**  
  
1.  Перейдите в каталог (`cd`) к экземпляру сервера, на котором размещена вторичная реплика.  
  
2.  Используйте `Add-SqlAvailabilityDatabase` командлет, чтобы присоединить один или несколько баз данных-получателей к группе доступности.  
  
     Например, следующая команда присоединяет базу данных-получатель `Db1`к группе доступности `MyAG` в одном из экземпляров сервера, на котором находится вторичная реплика.  
  
    ```  
    Add-SqlAvailabilityDatabase `   
    -Path SQLSERVER:\SQL\SecondaryServer\InstanceName\AvailabilityGroups\MyAG `   
    -Database "Db1"  
    ```  
  
    > [!NOTE]  
    >  Чтобы просмотреть синтаксис командлета, используйте `Get-Help` командлет в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] среде PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Настройка и использование поставщика SQL Server PowerShell**  
  
-   [Поставщик SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Присоединение вторичной реплики к группе доступности (SQL Server)](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Подготовка базы данных-получателя для присоединения к группе доступности вручную (SQL Server)](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a>См. также  
 [ALTER AVAILABILITY GROUP (Transact-SQL)](/sql/t-sql/statements/alter-availability-group-transact-sql)   
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Устранение неполадок с конфигурацией групп доступности AlwaysOn &#40;SQL Server&#41;удален](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
  
