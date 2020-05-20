---
title: Использование политик AlwaysOn для просмотра работоспособности группы доступности (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 6f1bcbc3-1220-4071-8e53-4b957f5d3089
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 090c6fb7e19099ed5ad2650a99aa12f9ae3d5033
ms.sourcegitcommit: 37a3e2c022c578fc3a54ebee66d9957ff7476922
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2020
ms.locfileid: "82921975"
---
# <a name="use-alwayson-policies-to-view-the-health-of-an-availability-group-sql-server"></a>Использование политик AlwaysOn для определения работоспособности группы доступности (SQL Server)
  В этом разделе описано, как определить состояние работоспособности группы доступности AlwaysOn с помощью политики AlwaysOn в среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или с помощью Powershell в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Дополнительные сведения об управлении на основе политик AlwaysOn см. [в разделе политики AlwaysOn для проблем в работе с группы доступности AlwaysOn (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).  
  
> [!IMPORTANT]  
>  При работе с политиками AlwaysOn имена категорий используются в качестве идентификаторов. При изменении имени категории AlwaysOn ее функция оценки работоспособности будет нарушена. Поэтому имена категорий AlwaysOn изменять не следует никогда.  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Требуются разрешения CONNECT, VIEW SERVER STATE и VIEW ANY DEFINITION.  
  
##  <a name="using-the-alwayson-dashboard"></a><a name="SSMSProcedure"></a>Использование панели мониторинга AlwaysOn  
 **Открытие панели мониторинга AlwaysOn**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, на котором размещена одна из реплик доступности. Чтобы просмотреть сведения обо всех репликах доступности в группе доступности, используйте экземпляр сервера, на котором размещена первичная реплика.  
  
2.  Щелкните имя сервера, чтобы развернуть дерево сервера.  
  
3.  Разверните узел **Высокий уровень доступности AlwaysOn** .  
  
     Щелкните правой кнопкой мыши узел **Группы доступности** или разверните этот узел и щелкните правой кнопкой мыши определенную группу доступности.  
  
4.  Выберите команду **Показать панель мониторинга** .  
  
 Дополнительные сведения об использовании панели мониторинга AlwaysOn см. в разделе [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](use-the-always-on-dashboard-sql-server-management-studio.md).  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Использование PowerShell  
 **Использование политик AlwaysOn для просмотра работоспособности группы доступности**  
  
1.  Перейдите в каталог (`cd`) экземпляра сервера, на котором размещена одна из реплик доступности. Чтобы просмотреть сведения обо всех репликах доступности в группе доступности, используйте экземпляр сервера, на котором размещена первичная реплика.  
  
2.  Используйте следующие командлеты.  
  
     `Test-SqlAvailabilityGroup`  
     Оценивает работоспособность группы доступности при помощи оценки состояния политик управления SQL Server. Для выполнения этого командлета необходимо иметь разрешения CONNECT, VIEW SERVER STATE и VIEW ANY DEFINITION.  
  
     Например, следующая команда показывает все группы доступности с состоянием работоспособности «Ошибка» в экземпляре сервера `Computer\Instance`.  
  
    ```powershell
    Get-ChildItem SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups |
        Test-SqlAvailabilityGroup |
        Where-Object { $_.HealthState -eq "Error" }  
    ```  
  
     `Test-SqlAvailabilityReplica`  
     Оценивает работоспособность реплик доступности при помощи оценки состояния политик управления SQL Server. Для выполнения этого командлета необходимо иметь разрешения CONNECT, VIEW SERVER STATE и VIEW ANY DEFINITION.  
  
     Например, следующая команда оценивает работоспособность реплики доступности с именем `MyReplica` в группе доступности `MyAg` и выводит краткую сводку.  
  
    ```powershell
    Test-SqlAvailabilityReplica -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
     `Test-SqlDatabaseReplicaState`  
     Оценивает работоспособность базы данных доступности на всех присоединенных репликах доступности при помощи оценки состояния политик управления SQL Server.  
  
     Например, следующая команда оценивает работоспособность всех баз данных доступности в группе доступности `MyAg` и выводит краткую сводку по каждой базе данных.  
  
    ```powershell
    Get-ChildItem SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\DatabaseReplicaStates |
        Test-SqlDatabaseReplicaState  
    ```  
  
     Эти командлеты принимают следующие параметры.  
  
    |Параметр|Описание|  
    |------------|-----------------|  
    |`AllowUserPolicies`|Выполняет пользовательские политики из категорий политик AlwaysOn.|  
    |`InputObject`|Коллекция объектов, представляющих состояния групп доступности, реплик доступности или базы данных доступности (в зависимости от того, какой используется командлет). Этот командлет вычисляет исправность указанных объектов.|  
    |`NoRefresh`|Если задан этот параметр, командлет не обновляет вручную объекты, указанные в параметре `-Path` или `-InputObject`.|  
    |`Path`|Путь к группе доступности, одной или нескольким репликам доступности или состоянию кластера реплики базы данных доступности (в зависимости от того, какой используется командлет). Этот параметр является необязательным. Если этот параметр не указан, его значение по умолчанию соответствует текущему рабочему расположению.|  
    |`ShowPolicyDetails`|Показывает результат оценки каждой политики, выполненной этим командлетом. В результате работы командлета формируется по одному объекту для оценки каждой политики. Каждый такой объект имеет поле с описанием результатов оценки (было установлено соответствие политике или нет, имя и категория политики и так далее).|  
  
     Например, следующая команда `Test-SqlAvailabilityGroup` указывает параметр `-ShowPolicyDetails`, чтобы показать результат вычисления, выполненного этим командлетом для управления на основе политик PBM в группе доступности с именем `MyAg`.  
  
    ```powershell
    Test-SqlAvailabilityGroup -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\AgName -ShowPolicyDetails  
    ```  
  
    > [!NOTE]  
    >  Чтобы просмотреть синтаксис командлета, воспользуйтесь командлетом `Get-Help` в среде [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Настройка и использование поставщика SQL Server PowerShell**  
  
-   [Поставщик SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
-   [Получение справок по SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> См. также  
 **Блоги группы SQL Server AlwaysOn. Мониторинг работоспособности AlwaysOn с помощью PowerShell:**  
  
-   [Часть 1. Общие сведения о командлете](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-1-basic-cmdlet-overview)  
  
-   [Часть 2. Расширенное использование командлета](https://docs.microsoft.com/archive/blogs/sqlalwayson/the-alwayson-health-model-part-2-extending-the-health-model)  
  
-   [Часть 3. Простое приложение для мониторинга](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-3-a-simple-monitoring-application)  
  
-   [Часть 4. Интеграция с агентом SQL Server](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-4-integration-with-sql-server-agent)  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Администрирование &#40;SQL Server группы доступности&#41;](administration-of-an-availability-group-sql-server.md)   
 [Отслеживание групп доступности (SQL Server)](monitoring-of-availability-groups-sql-server.md)   
 [Политики AlwaysOn на случай проблем в работе с группами доступности AlwaysOn (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md) 
