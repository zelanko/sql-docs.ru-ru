---
title: Изменение режима отработки отказа для реплики доступности (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover modes [SQL Server]
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], failover modes
- Availability Groups [SQL Server], configuring
ms.assetid: 619a826f-8e65-48eb-8c34-39497d238279
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6750456d708d68e57aadd4b1139f6e108a93b9ba
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "72783019"
---
# <a name="change-the-failover-mode-of-an-availability-replica-sql-server"></a>Изменение режима отработки отказа для реплики доступности (SQL Server)
  В этом разделе описывается изменение режима отработки отказа для реплики доступности в группе доступности AlwaysOn в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]или PowerShell. Режим отработки отказа ― это свойство реплики, которое определяет режим отработки отказа для реплик, работающих в режиме доступности с синхронной фиксацией. Дополнительные сведения см. в разделах [Отработка отказа и режимы отработки отказа (группы доступности AlwaysOn)](failover-and-failover-modes-always-on-availability-groups.md) и [Режимы доступности (группы доступности AlwaysOn)](availability-modes-always-on-availability-groups.md).  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> Требования и ограничения  
  
-   Эта задача поддерживается только на первичных репликах. Необходимо подключиться к экземпляру сервера, на котором размещена первичная реплика.  
  
-   Экземпляры отказоустойчивого кластера SQL Server не поддерживают автоматический переход на другой ресурс с учетом групп доступности, поэтому любая реплика доступности, размещенная в них, должна быть настроена для перехода на другой ресурс вручную.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Изменение режима отработки отказа для реплики доступности**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, на котором размещена первичная реплика, и разверните дерево сервера.  
  
2.  Разверните узел **Высокий уровень доступности AlwaysOn** и узел **Группы доступности** .  
  
3.  Щелкните группу доступности, реплику которой нужно изменить.  
  
4.  Щелкните правой кнопкой мыши реплику и выберите пункт **Свойства**.  
  
5.  В диалоговом окне **Свойства реплики доступности** используйте раскрывающийся список **Режим отработки отказа** , чтобы изменить режим отработки отказа для этой реплики.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Изменение режима отработки отказа для реплики доступности**  
  
1.  Подключитесь к экземпляру сервера, на котором находится первичная реплика.  
  
2.  Инструкция [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) используется следующим образом:  
  
     ALTER AVAILABILITY GROUP *имя_группы* MODIFY REPLICA ON '*имя_сервера*'  
  
     WITH ( {  
  
     AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }  
  
     | FAILOVER_MODE = { AUTOMATIC | MANUAL }  
  
     }  )  
  
     where  
  
    -   *имя_группы* — это имя группы доступности.  
  
    -   {'*system_name*[\\*instance_name*] ' | "*FCI_network_name*[\\*instance_name*]"}  
  
         Задает адрес экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на котором размещена изменяемая реплика доступности. Этот адрес состоит из следующих компонентов:  
  
         *системное_имя*  
         Имя NetBIOS компьютера, на котором расположен изолированный экземпляр сервера.  
  
         *сетевое_имя_FCI*  
         Сетевое имя, используемое для доступа к отказоустойчивому кластеру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , в котором целевой экземпляр сервера является партнером по обеспечению отработки отказа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
         *instance_name*  
         Имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на котором размещается целевая реплика доступности. Для экземпляра сервера по умолчанию указывать параметр *имя_экземпляра* не обязательно.  
  
     Дополнительные сведения об этих параметрах см. в разделе [ALTER AVAILABILITY GROUP (Transact-SQL)](/sql/t-sql/statements/alter-availability-group-transact-sql).  
  
     В следующем примере для первичной реплики группы доступности *MyAG* режим отработки отказа меняется на автоматический переход на другой ресурс для реплики доступности, находящейся на экземпляре сервера по умолчанию на компьютере *COMPUTER01*.  
  
    ```  
    ALTER AVAILABILITY GROUP MyAG MODIFY REPLICA ON 'COMPUTER01' WITH  
       (FAILOVER_MODE = AUTOMATIC);  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Использование PowerShell  

### <a name="to-change-the-failover-mode-of-an-availability-replica"></a>Изменение режима отработки отказа для реплики доступности
  
1.  Перейдите в каталог (`cd`) экземпляра сервера, на котором находится первичная реплика.  
  
2.  Используйте командлет `Set-SqlAvailabilityReplica` с параметром `FailoverMode`. При выборе автоматического перехода на другой ресурс для реплики может потребоваться указать параметр `AvailabilityMode`, чтобы перевести реплику в режим доступности с синхронной фиксацией.  
  
     Например, следующая команда изменяет реплику `MyReplica` в группе доступности `MyAg` , устанавливая использование режима доступности с синхронной фиксацией и поддержку автоматического перехода на другой ресурс.  
  
    ```powershell
    Set-SqlAvailabilityReplica -AvailabilityMode "SynchronousCommit" -FailoverMode "Automatic" `
     -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\Replicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  Чтобы просмотреть синтаксис командлета, воспользуйтесь командлетом `Get-Help` в среде [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
Сведения о настройке и использовании поставщика SQL Server PowerShell см. в разделе [поставщик SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md).
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
 [Режимы доступности &#40;группы доступности AlwaysOn&#41;](availability-modes-always-on-availability-groups.md)   
 [Отказоустойчивость и режимы отработки отказа &#40;группы доступности AlwaysOn&#41;](failover-and-failover-modes-always-on-availability-groups.md) 
