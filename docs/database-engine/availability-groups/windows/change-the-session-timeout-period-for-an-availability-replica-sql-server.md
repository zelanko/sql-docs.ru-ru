---
title: "Изменение периода ожидания сеанса для реплики доступности (SQL Server) | Документы Майкрософт"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: availability-groups
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], session timeout
- session timeout [SQL Server]
ms.assetid: e23c6e06-1cd1-4d4a-9bc2-e3e06ab2933d
caps.latest.revision: "26"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: db9dcb48c165f6e18f26384d478ef16a21e5e273
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="change-the-session-timeout-period-for-an-availability-replica-sql-server"></a>Изменение периода ожидания сеанса для реплики доступности (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В этом разделе описывается настройка времени ожидания сеанса реплики доступности AlwaysOn с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] или PowerShell в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Время ожидания сеанса — это свойство реплики, которое определяет, сколько секунд будет эта реплика доступности ждать отклика на команду ping, отправленную с подключенной реплики перед тем, как признать попытку подключения неудачной. По умолчанию реплика ожидает ответа на команду ping 10 секунд. Это свойство реплики применимо только к подключению данной вторичной реплики к первичной реплике группы доступности. Дополнительные сведения о периоде времени ожидания сеанса см. в разделе [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Предварительные требования](#Prerequisites)  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Изменение времени ожидания с помощью**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Необходимо подключиться к экземпляру сервера, на котором размещена первичная реплика.  
  
###  <a name="Recommendations"></a> Рекомендации  
 Рекомендуется установить интервал времени ожидания в 10 секунд или более. При установке значения меньше 10 секунд возникает вероятность пропуска команды PING в сильно загруженной системе и вероятность ошибочного сообщения об ошибке.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Изменение значения времени ожидания сеанса для реплики доступности**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, на котором размещена первичная реплика, и разверните дерево сервера.  
  
2.  Разверните узел **Высокий уровень доступности AlwaysOn** и узел **Группы доступности** .  
  
3.  Щелкните группу доступности, реплику которой нужно настроить.  
  
4.  Щелкните правой кнопкой мыши реплику доступности, которую нужно настроить, и выберите пункт **Свойства**.  
  
5.  В диалоговом окне **Свойства реплики доступности** используйте поле **Время ожидания сеанса (в секундах)** , чтобы изменить число секунд, заданное в качестве времени ожидания для этой реплики.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Изменение значения времени ожидания сеанса для реплики доступности**  
  
1.  Подключитесь к экземпляру сервера, на котором находится первичная реплика.  
  
2.  Инструкция [ALTER AVAILABILITY GROUP](../../../t-sql/statements/alter-availability-group-transact-sql.md) используется следующим образом:  
  
     ALTER AVAILABILITY GROUP *имя_группы*  
  
     MODIFY REPLICA ON '*имя_экземпляра*' WITH ( SESSION_TIMEOUT =*число_секунд* )  
  
     где *имя_группы* ― это имя группы доступности, *имя_экземпляра* ― это имя экземпляра сервера, где расположена реплика доступности, свойство которой необходимо изменить, а параметр *число_секунд* указывает количество секунд, которое реплика, будучи вторичной, будет ожидать до момента применения журнала к базам данных. Значение по умолчанию равно 0 секунд. Это означает, что время задержки равно 0.  
  
     В следующем примере, введенном на первичной реплике группы доступности `AccountsAG` , выполняется изменение значения времени ожидания сеанса на значение `15` секунд для реплики, размещенной на экземпляре сервера `INSTANCE09` .  
  
    ```  
    ALTER AVAILABILITY GROUP AccountsAG   
       MODIFY REPLICA ON 'INSTANCE09' WITH (SESSION_TIMEOUT = 15);  
    ```  
  
##  <a name="PowerShellProcedure"></a> Использование PowerShell  
 **Изменение значения времени ожидания сеанса для реплики доступности**  
  
1.  Перейдите в каталог (**cd**) экземпляра сервера, в котором находится первичная реплика.  
  
2.  Используйте командлет **Set-SqlAvailabilityReplica** с параметром **SessionTimeout** , чтобы изменить число секунд времени ожидания сеанса для указанной реплики доступности.  
  
     Например, следующая команда задает период времени ожидания сеанса 15 секунд.  
  
    ```  
    Set-SqlAvailabilityReplica –SessionTimeout 15 `   
    -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  Чтобы просмотреть синтаксис командлета, воспользуйтесь командлетом **Get-Help** в среде [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md).  
  
 **Настройка и использование поставщика SQL Server PowerShell**  
  
-   [SQL Server PowerShell, поставщик](../../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
