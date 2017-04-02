---
title: "Настройка параметров свойства FailureConditionLevel | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 513dd179-9a46-46da-9fdd-7632cf6d0816
caps.latest.revision: 29
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 29
---
# Настройка параметров свойства FailureConditionLevel
  Свойство FailureConditionLevel служит для задания для экземпляра отказоустойчивого кластера FCI в группе AlwaysOn условий отработки отказа или перезапуска. Изменения значения этого свойства вступают в силу немедленно, без перезапуска службы отказоустойчивого кластера Windows Server или ресурса отказоустойчивого кластера SQL Server.  
  
-   **Перед началом работы**: [параметры свойства FailureConditionLevel](#Restrictions), [безопасность](#Security)  
  
-   **Настройка параметров свойства FailureConditionLevel с помощью** [PowerShell](#PowerShellProcedure), [диспетчера отказоустойчивости кластеров](#WSFC), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Параметры свойства FailureConditionLevel  
 Условия сбоя устанавливаются по прогрессирующей шкале. Каждый уровень, с 1 по 5, включает все условия предыдущих уровней, а также собственные дополнительные условия. Это означает, что с каждым уровнем вероятность отработки отказа или перезапуска повышается.  Дополнительные сведения см. в подразделе «Определение сбоев» раздела [Failover Policy for Failover Cluster Instances](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md) .  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Требует разрешения ALTER SETTINGS и VIEW SERVER STATE.  
  
##  <a name="PowerShellProcedure"></a> Использование PowerShell  
  
##### Настройка параметров свойства FailureConditionLevel  
  
1.  Запустите повышенный режим Windows PowerShell с помощью команды **Запуск от имени администратора**.  
  
2.  Импортируйте модуль **FailoverClusters** для включения командлетов кластера.  
  
3.  С помощью командлета **Get-ClusterResource** найдите ресурс [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], а затем с помощью командлета **Set-ClusterParameter** задайте свойство **FailureConditionLevel** для экземпляра отказоустойчивого кластера.  
  
> [!TIP]  
>  Каждый раз при открытии нового окна PowerShell потребуется импортировать модуль **FailoverClusters**.  
  
### Пример (PowerShell)  
 В следующем примере параметр FailureConditionLevel экземпляра в ресурсе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] «`SQL Server (INST1)`» изменяется на обработку отказа или перезапуск при критических ошибках сервера.  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter FailureConditionLevel 3  
  
```  
  
### См. также (PowerShell)  
  
-   [Кластеризация и высокая доступность](http://blogs.msdn.com/b/clustering/archive/2009/05/23/9636665.aspx) (блог группы отказоустойчивой кластеризации и балансировки сетевой нагрузки)  
  
-   [Приступая к работе с Windows PowerShell в отказоустойчивом кластере](http://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [Команды ресурса кластера и соответствующие командлеты Windows PowerShell](http://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="WSFC"></a> Использование оснастки «Диспетчер отказоустойчивости кластеров»  
 **Настройка параметров свойств FailureConditionLevel.**  
  
1.  Откройте оснастку «Диспетчер отказоустойчивости кластеров»  
  
2.  Разверните узел **Службы и приложения** и выберите требуемый кластер FCI.  
  
3.  Щелкните правой кнопкой мыши **Ресурс SQL Server** в разделе **Другие ресурсы** и выберите пункт **Свойства**. Откроется диалоговое окно **Свойства** ресурсов SQL Server.  
  
4.  Перейдите на вкладку **Свойства** , введите необходимое значение свойства **FaliureConditionLevel** и нажмите кнопку **ОК** , чтобы применить изменение.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Настройка параметров свойств FailureConditionLevel.**  
  
 С помощью инструкции [ALTER SERVER CONFIGURATION](../../../t-sql/statements/alter-server-configuration-transact-sql.md)[!INCLUDE[tsql](../../../includes/tsql-md.md)] можно задать значение свойства FailureConditionLevel.  
  
###  <a name="TsqlExample"></a> Пример (Transact-SQL)  
 Следующий пример назначает свойству FailureConditionLevel значение 0, которое указывает, что при любых условиях сбоя отработка отказа или перезапуск не будет выполняться автоматически.  
  
```  
ALTER SERVER CONFIGURATION SET FAILOVER CLUSTER PROPERTY FailureConditionLevel = 0;  
```  
  
## См. также:  
 [sp_server_diagnostics (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md)   
 [Политика отработки отказа для экземпляров отказоустойчивого кластера](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md)  
  
  