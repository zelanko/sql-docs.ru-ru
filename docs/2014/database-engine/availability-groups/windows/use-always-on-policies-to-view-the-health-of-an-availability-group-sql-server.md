---
title: Использование политик AlwaysOn для определения работоспособности группы доступности (SQL Server) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 6f1bcbc3-1220-4071-8e53-4b957f5d3089
caps.latest.revision: 16
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.openlocfilehash: ba1f977cf2846438494bedc7b084ade659fca753
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192517"
---
# <a name="use-alwayson-policies-to-view-the-health-of-an-availability-group-sql-server"></a>Использование политик AlwaysOn для определения работоспособности группы доступности (SQL Server)
  В этом разделе описано, как определить состояние работоспособности группы доступности AlwaysOn с помощью политики AlwaysOn в среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или с помощью Powershell в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Сведения об управлении на основе политики AlwaysOn см. в разделе [политики AlwaysOn на случай проблем в работе с группами доступности AlwaysOn (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).  
  
> [!IMPORTANT]  
>  При работе с политиками AlwaysOn имена категорий используются в качестве идентификаторов. При изменении имени категории AlwaysOn ее функция оценки работоспособности будет нарушена. Поэтому имена категорий AlwaysOn изменять не следует никогда.  
  

  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуются разрешения CONNECT, VIEW SERVER STATE и VIEW ANY DEFINITION.  
  
##  <a name="SSMSProcedure"></a> Использование панели мониторинга AlwaysOn  
 **Чтобы открыть панель мониторинга AlwaysOn**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, на котором размещена одна из реплик доступности. Чтобы просмотреть сведения обо всех репликах доступности в группе доступности, используйте экземпляр сервера, на котором размещена первичная реплика.  
  
2.  Щелкните имя сервера, чтобы развернуть дерево сервера.  
  
3.  Разверните узел **Высокий уровень доступности AlwaysOn** .  
  
     Щелкните правой кнопкой мыши узел **Группы доступности** или разверните этот узел и щелкните правой кнопкой мыши определенную группу доступности.  
  
4.  Выберите команду **Показать панель мониторинга** .  
  
 Дополнительные сведения об использовании панели мониторинга AlwaysOn см. в разделе [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](use-the-always-on-dashboard-sql-server-management-studio.md).  
  
##  <a name="PowerShellProcedure"></a> Использование PowerShell  
 **Использование политик AlwaysOn для определения работоспособности группы доступности**  
  
1.  Значение по умолчанию (`cd`) к экземпляру сервера, на котором размещена одна из реплик доступности. Чтобы просмотреть сведения обо всех репликах доступности в группе доступности, используйте экземпляр сервера, на котором размещена первичная реплика.  
  
2.  Используйте следующие командлеты.  
  
     `Test-SqlAvailabilityGroup`  
     Оценивает работоспособность группы доступности при помощи оценки состояния политик управления SQL Server. Для выполнения этого командлета необходимо иметь разрешения CONNECT, VIEW SERVER STATE и VIEW ANY DEFINITION.  
  
     Например, следующая команда показывает все группы доступности с состоянием работоспособности «Ошибка» в экземпляре сервера `Computer\Instance`.  
  
    ```  
    Get-ChildItem SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups `   
    | Test-SqlAvailabilityGroup | Where-Object { $_.HealthState -eq "Error" }  
    ```  
  
     `Test-SqlAvailabilityReplica`  
     Оценивает работоспособность реплик доступности при помощи оценки состояния политик управления SQL Server. Для выполнения этого командлета необходимо иметь разрешения CONNECT, VIEW SERVER STATE и VIEW ANY DEFINITION.  
  
     Например, следующая команда оценивает работоспособность реплики доступности с именем `MyReplica` в группе доступности `MyAg` и выводит краткую сводку.  
  
    ```  
    Test-SqlAvailabilityReplica `   
    -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
     `Test-SqlDatabaseReplicaState`  
     Оценивает работоспособность базы данных доступности на всех присоединенных репликах доступности при помощи оценки состояния политик управления SQL Server.  
  
     Например, следующая команда оценивает работоспособность всех баз данных доступности в группе доступности `MyAg` и выводит краткую сводку по каждой базе данных.  
  
    ```  
    Get-ChildItem SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\DatabaseReplicaStates `   
     | Test-SqlDatabaseReplicaState  
    ```  
  
     Эти командлеты принимают следующие параметры.  
  
    |Параметр|Описание|  
    |------------|-----------------|  
    |`AllowUserPolicies`|Выполняет пользовательские политики из категорий политик AlwaysOn.|  
    |`InputObject`|Коллекция объектов, представляющих состояния групп доступности, реплик доступности или базы данных доступности (в зависимости от того, какой используется командлет). Этот командлет вычисляет исправность указанных объектов.|  
    |`NoRefresh`|Если задан этот параметр, командлет не обновляет вручную объекты, указанные в `-Path` или `-InputObject` параметра.|  
    |`Path`|Путь к группе доступности, одной или нескольким репликам доступности или состоянию кластера реплики базы данных доступности (в зависимости от того, какой используется командлет). Этот параметр является необязательным. Если этот параметр не указан, его значение по умолчанию соответствует текущему рабочему расположению.|  
    |`ShowPolicyDetails`|Показывает результат оценки каждой политики, выполненной этим командлетом. В результате работы командлета формируется по одному объекту для оценки каждой политики. Каждый такой объект имеет поле с описанием результатов оценки (было установлено соответствие политике или нет, имя и категория политики и так далее).|  
  
     Например, следующая команда `Test-SqlAvailabilityGroup` указывает параметр `-ShowPolicyDetails`, чтобы показать результат вычисления, выполненного этим командлетом для управления на основе политик PBM в группе доступности с именем `MyAg`.  
  
    ```  
    Test-SqlAvailabilityGroup `   
    -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\AgName `  
    -ShowPolicyDetails  
  
    ```  
  
    > [!NOTE]  
    >  Чтобы просмотреть синтаксис командлета, воспользуйтесь `Get-Help` командлета в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] среде PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Настройка и использование поставщика SQL Server PowerShell**  
  
-   [Поставщик SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
-   [Получение справок по SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
##  <a name="RelatedContent"></a> См. также  
 **Блоги SQL Server AlwaysOn Team — наблюдение за исправностью AlwaysOn с помощью PowerShell:**  
  
-   [Часть 1. Общие сведения о командлете](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/monitoring-alwayson-health-with-powershell-part-1.aspx)  
  
-   [Часть 2. Расширенное использование командлета](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/monitoring-alwayson-health-with-powershell-part-2.aspx)  
  
-   [Часть 3. Простое приложение для мониторинга](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/15/monitoring-alwayson-health-with-powershell-part-3.aspx)  
  
-   [Часть 4. Интеграция с агентом SQL Server](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/15/the-always-on-health-model-part-4.aspx)  
  
## <a name="see-also"></a>См. также  
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Администрирование группы доступности (SQL Server)](administration-of-an-availability-group-sql-server.md)   
 [Отслеживание групп доступности (SQL Server)](monitoring-of-availability-groups-sql-server.md)   
 [Политики AlwaysOn на случай проблем в работе с группами доступности AlwaysOn (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md) 
  
  