---
title: Настройка параметров свойства HealthCheckTimeout | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 3bbeb979-e6fc-4184-ad6e-cca62108de74
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 435aa6a89b1b7aafd243efbc6de86bcb8f731346
ms.sourcegitcommit: 5a9ec5e28543f106bf9e7aa30dd0a726bb750e25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/08/2020
ms.locfileid: "82925028"
---
# <a name="configure-healthchecktimeout-property-settings"></a>Настройка параметров свойства HealthCheckTimeout
  Параметр HealthCheckTimeout используется для задания временного интервала (в миллисекундах) ожидания библиотекой ресурсов SQL Server данных, возвращаемых хранимой процедурой [sp_server_diagnostics](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) , до появления сообщения о том, что экземпляр отказоустойчивого кластера AlwaysOn SQL Server (FCI) не отвечает. Изменения, внесенные в параметры времени ожидания, вступают в силу немедленно и не требуют перезапуска ресурса SQL Server.  
  
-   **Перед началом:**  [Ограничения](#Limits), [Безопасность](#Security)  
  
-   **Настройка параметра HealthCheckTimeout с помощью следующих средств:**  [PowerShell](#PowerShellProcedure), [диспетчер отказоустойчивого кластера](#WSFC), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Limits"></a> Ограничения  
 Значение по умолчанию для этого свойства составляет 60 000 миллисекунд (60 секунд). Минимальное значение равно 15 000 миллисекундам (15 секундам).  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Требует разрешения ALTER SETTINGS и VIEW SERVER STATE.  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Использование PowerShell  
  
### <a name="to-configure-healthchecktimeout-settings"></a>Настройка параметров HealthCheckTimeout  
  
1.  Запустите повышенный режим Windows PowerShell с помощью команды **Запуск от имени администратора**.  
  
2.  Импортируйте модуль `FailoverClusters` для включения командлетов кластера.  
  
3.  Используйте `Get-ClusterResource` командлет, чтобы найти [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ресурс, а затем используйте `Set-ClusterParameter` командлет, чтобы задать свойство **HealthCheckTimeout** для экземпляра отказоустойчивого кластера.  
  
> [!TIP]  
>  Каждый раз при открытии нового окна Powershell нужно импортировать модуль `FailoverClusters`.  

 В следующем примере демонстрируется изменение параметра HealthCheckTimeout ресурса [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] «`SQL Server (INST1)`» на 60 000 миллисекунд.  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter HealthCheckTimeout 60000  
```  
  
### <a name="related-content-powershell"></a>См. также (PowerShell)  
  
-   [Кластеризация и высокая доступность](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering) (блог группы отказоустойчивой кластеризации и балансировки сетевой нагрузки)  
  
-   [Приступая к работе с Windows PowerShell в отказоустойчивом кластере](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [Команды ресурса кластера и соответствующие командлеты Windows PowerShell](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="using-the-failover-cluster-manager-snap-in"></a><a name="WSFC"></a> Использование оснастки «Диспетчер отказоустойчивости кластеров»  
 **Для настройки параметров HealthCheckTimeout**  
  
1.  Откройте оснастку «Диспетчер отказоустойчивости кластеров»  
  
2.  Раскройте узел **Службы и приложения** и выберите требуемый кластер FCI.  
  
3.  Щелкните правой кнопкой мыши **Ресурс SQL Server** в разделе **Другие ресурсы** и выберите из контекстного меню пункт **Свойства** . Откроется диалоговое окно **Свойства** ресурсов SQL Server.  
  
4.  Перейдите на вкладку **Свойства** , введите желаемое значение свойства **HealthCheckTimeout** и нажмите кнопку **ОК** , чтобы применить изменение.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 С помощью инструкции [ALTER Server Configuration](/sql/t-sql/statements/alter-server-configuration-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] можно указать значение свойства HealthCheckTimeOut.  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В следующем примере для параметра HealthCheckTimeout устанавливается значение, равное 15 000 миллисекунд (15 секунд).  
  
```sql
ALTER SERVER CONFIGURATION   
SET FAILOVER CLUSTER PROPERTY HealthCheckTimeout = 15000;  
```  
  
## <a name="see-also"></a>См. также  
 [Политика отработки отказа для экземпляров отказоустойчивого кластера](failover-policy-for-failover-cluster-instances.md)  
