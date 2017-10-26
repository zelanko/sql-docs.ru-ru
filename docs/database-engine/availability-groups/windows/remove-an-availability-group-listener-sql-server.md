---
title: "Удаление прослушивателя группы доступности (SQL Server) | Документы Майкрософт"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.availabilitygroup.removeaglistener.default.f1
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
ms.assetid: fd9bba9a-d29f-4c23-8ecd-aaa049ed5f1b
caps.latest.revision: 14
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 7c1751fec54325b1f882e4a16d17cb1a01c42d42
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="remove-an-availability-group-listener-sql-server"></a>Удаление прослушивателя группы доступности (SQL Server)
  В этом разделе описывается удаление прослушивателя группы доступности из группы доступности AlwaysOn с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]или PowerShell в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Предварительные требования](#Prerequisites)  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Удаление прослушивателя с помощью**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Необходимо подключиться к экземпляру сервера, на котором размещена первичная реплика.  
  
###  <a name="Recommendations"></a> Рекомендации  
 Перед удалением прослушивателя группы доступности рекомендуется убедиться, что он не используется никакими приложениями.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Удаление прослушивателя группы доступности**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, на котором размещена первичная реплика, и щелкните имя сервера, чтобы развернуть его дерево.  
  
2.  Разверните узел **Высокий уровень доступности AlwaysOn** и узел **Группы доступности** .  
  
3.  Разверните узел группы доступности и разверните узел **Прослушиватели группы доступности** .  
  
4.  Правой кнопкой щелкните прослушиватель, который необходимо удалить, и выберите команду **Удалить** .  
  
5.  Откроется диалоговое окно **Удаление прослушивателя из группы доступности** . Дополнительные сведения см. в подразделе [Удаление прослушивателя из группы доступности](#AgListenerPropertiesDialog)далее в этом разделе.  
  
###  <a name="AgListenerPropertiesDialog"></a> Удаление прослушивателя из группы доступности (диалоговое окно)  
 **Название**  
 Имя удаляемого прослушивателя.  
  
 **Результат**  
 Отображает ссылку **Успешно** или **Ошибка**, которую можно щелкнуть для получения дополнительных сведений.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Удаление прослушивателя группы доступности**  
  
1.  Подключитесь к экземпляру сервера, на котором находится первичная реплика.  
  
2.  Инструкция [ALTER AVAILABILITY GROUP](../../../t-sql/statements/alter-availability-group-transact-sql.md) используется следующим образом:  
  
     ALTER AVAILABILITY GROUP *group_name* REMOVE LISTENER **‘***dns_name***’**,  
  
     где *group_name* — имя группы доступности, а *dns_name* — DNS-имя прослушивателя группы доступности.  
  
     В следующем примере выполняется удаление прослушивателя группы доступности `AccountsAG` . Имя DNS — AccountsAG_Listener.  
  
    ```  
    ALTER AVAILABILITY GROUP AccountsAG REMOVE LISTENER ‘AccountsAG_Listener’;  
    ```  
  
##  <a name="PowerShellProcedure"></a> Использование PowerShell  
 **Удаление прослушивателя группы доступности**  
  
1.  Установите значение по умолчанию (**cd**) равным экземпляру сервера, на котором размещена первичная реплика.  
  
2.  Для удаления прослушивателя используйте встроенный командлет **Remove-Item** . Например, следующая команда удаляет прослушиватель с именем `MyListener` из группы доступности с именем `MyAg`.  
  
    ```  
    Remove-Item `   
    SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AGListeners\MyListener  
    ```  
  
    > [!NOTE]  
    >  Чтобы просмотреть синтаксис командлета, воспользуйтесь командлетом **Get-Help** в среде [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md).  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Создание или настройка прослушивателя группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Просмотр свойств прослушивателя группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/view-availability-group-listener-properties-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Прослушиватели групп доступности, возможность подключения клиентов и отработка отказа приложений (SQL Server)](../../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md)  
  
  

