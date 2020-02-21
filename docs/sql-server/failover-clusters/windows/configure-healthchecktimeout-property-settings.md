---
title: Настройка HealthCheckTimeout для группы доступности
description: Настройте параметр HealthCheckTimeout для группы доступности Always On. Он используется для указания времени, которое библиотека DLL ресурсов SQL Server должна подождать, прежде чем сообщать об отсутствии ответа.
ms.custom: seo-lt-2019
ms.date: 03/09/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 3bbeb979-e6fc-4184-ad6e-cca62108de74
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3e03c9f0a62896daa192fa33e7b1e0a549b1b46f
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "74822003"
---
# <a name="configure-healthchecktimeout-property-settings"></a>Настройка параметров свойства HealthCheckTimeout
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Параметр HealthCheckTimeout используется для задания временного интервала (в миллисекундах) ожидания библиотекой ресурсов SQL Server данных, возвращаемых хранимой процедурой [sp_server_diagnostics](../../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md) , до появления сообщения о том, что экземпляр отказоустойчивого кластера AlwaysOn SQL Server (FCI) не отвечает. Изменения, внесенные в параметры времени ожидания, вступают в силу немедленно и не требуют перезапуска ресурса SQL Server.  
  
-   **Перед началом работы**  [Ограничения](#Limits), [Безопасность](#Security)  
  
-   **Настройка параметра HealthCheckTimeout с помощью:**  [PowerShell](#PowerShellProcedure), [диспетчера отказоустойчивости кластеров](#WSFC), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Limits"></a> Ограничения  
 Значение по умолчанию для этого свойства составляет 30 000 миллисекунд (30 секунд). Минимальное значение равно 15 000 миллисекундам (15 секундам).  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требует разрешения ALTER SETTINGS и VIEW SERVER STATE.  
  
##  <a name="PowerShellProcedure"></a> Использование PowerShell  
  
##### <a name="to-configure-healthchecktimeout-settings"></a>Настройка параметров HealthCheckTimeout  
  
1.  Запустите повышенный режим Windows PowerShell с помощью команды **Запуск от имени администратора**.  
  
2.  Импортируйте модуль **FailoverClusters** для включения командлетов кластера.  
  
3.  C помощью командлета **Get-ClusterResource** найдите ресурс [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , а затем используйте командлет **Set-ClusterParameter** , чтобы настроить свойство **HealthCheckTimeout** для экземпляра отказоустойчивого кластера.  
  
> [!TIP]  
>  Каждый раз при открытии нового окна PowerShell потребуется импортировать модуль **FailoverClusters** .  
  
### <a name="example-powershell"></a>Пример (PowerShell)  
 В следующем примере демонстрируется изменение параметра HealthCheckTimeout ресурса [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] «`SQL Server (INST1)`» на 60 000 миллисекунд.  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter HealthCheckTimeout 60000  
  
```  
  
### <a name="related-content-powershell"></a>См. также (PowerShell)  
  
-   [Кластеризация и высокая доступность](https://blogs.msdn.com/b/clustering/archive/2009/05/23/9636665.aspx) (блог группы отказоустойчивой кластеризации и балансировки сетевой нагрузки)  
  
-   [Приступая к работе с Windows PowerShell в отказоустойчивом кластере](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [Команды ресурса кластера и соответствующие командлеты Windows PowerShell](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="WSFC"></a> Использование оснастки «Диспетчер отказоустойчивости кластеров»  
 **Для настройки параметров HealthCheckTimeout**  
  
1.  Откройте оснастку «Диспетчер отказоустойчивости кластеров»  
  
2.  Раскройте узел **Службы и приложения** и выберите требуемый кластер FCI.  
  
3.  Щелкните правой кнопкой мыши **Ресурс SQL Server** в разделе **Другие ресурсы** и выберите из контекстного меню пункт **Свойства** . Откроется диалоговое окно **Свойства** ресурсов SQL Server.  
  
4.  Перейдите на вкладку **Свойства** , введите желаемое значение свойства **HealthCheckTimeout** и нажмите кнопку **ОК** , чтобы применить изменение.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 С помощью инструкции [ALTER SERVER CONFIGURATION](../../../t-sql/statements/alter-server-configuration-transact-sql.md)[!INCLUDE[tsql](../../../includes/tsql-md.md)] вы можете задать значение свойства HealthCheckTimeOut.  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В следующем примере для параметра HealthCheckTimeout устанавливается значение, равное 15 000 миллисекунд (15 секунд).  
  
```  
ALTER SERVER CONFIGURATION   
SET FAILOVER CLUSTER PROPERTY HealthCheckTimeout = 15000;  
```  
  
## <a name="see-also"></a>См. также:  
 [Failover Policy for Failover Cluster Instances](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md)  
  
  
