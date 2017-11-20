---
title: "Зеркальное отображение базы данных и группы доступности AlwaysOn — PowerShell | Документы Майкрософт"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: availability-groups
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], endpoint
ms.assetid: 6197bbe7-67d4-446d-ba5f-cabfa5df77f1
caps.latest.revision: 9
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 24895c94afd7c43be75d2fcf7f914cebc370497c
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="database-mirroring---always-on-availability-groups--powershell"></a>Зеркальное отображение базы данных и группы доступности AlwaysOn — PowerShell
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  В этом разделе описывается создание конечной точки зеркального отображения базы данных для использования [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью PowerShell.  
  
 **В этом разделе**  
  
-   **Перед началом работы:**  [безопасность](#Security)  
  
-   **Создание конечной точки зеркального отображения базы данных с помощью следующих средств:**  [PowerShell](#PowerShellProcedure)  
  
## <a name="before-you-begin"></a>Перед началом  
  
###  <a name="Security"></a> безопасность  
  
> [!IMPORTANT]  
>  Алгоритм RC4 устарел. [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)] Вместо этого рекомендуется использовать алгоритм AES.  
  
####  <a name="Permissions"></a> Разрешения  
 Требуется разрешение CREATE ENDPOINT или членство в предопределенной роли сервера sysadmin. Дополнительные сведения см. в разделе [GRANT, предоставление разрешений на конечные точки (Transact-SQL)](../../../t-sql/statements/grant-endpoint-permissions-transact-sql.md).  
  
##  <a name="PowerShellProcedure"></a> Использование PowerShell  
 **Создание конечной точки зеркального отображения базы данных**  
  
1.  Перейдите в каталог (**cd**) экземпляра сервера, для которого требуется создать конечную точку зеркального отображения.  
  
2.  Создайте конечную точку с помощью командлета **New-SqlHadrEndpoint** , а затем с помощью командлета **Set-SqlHadrEndpoint** запустите ее.  
  
###  <a name="PShellExample"></a> Пример (PowerShell)  
 Следующие команды PowerShell создают конечную точку зеркального отображения базы данных на экземпляре SQL Server (*Machine*\\*Instance*). Эта конечная точка использует порт 5022.  
  
> [!IMPORTANT]  
>  Этот пример работает только на экземпляре сервера, на котором в данный момент отсутствует конечная точка зеркального отображения базы данных.  
  
```  
# Create the endpoint.  
$endpoint = New-SqlHadrEndpoint MyMirroringEndpoint -Port 5022 -Path SQLSERVER:\SQL\Machine\Instance  
  
# Start the endpoint  
Set-SqlHadrEndpoint -InputObject $endpoint -State "Started"  
  
```  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
 **Настройка конечной точки зеркального отображения базы данных**  
  
-   [Создание конечной точки зеркального отображения базы данных с проверкой подлинности Windows (Transact-SQL)](../../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Использование сертификатов для конечной точки зеркального отображения базы данных (Transact-SQL)](../../../database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [Включение использования сертификатов для исходящих соединений в конечной точке зеркального отображения базы данных (Transact-SQL)](../../../database-engine/database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [Включение использования сертификатов для входящих соединений в конечной точке зеркального отображения базы данных (Transact-SQL)](../../../database-engine/database-mirroring/database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [Указание сетевого адреса сервера (зеркальное отображение базы данных)](../../../database-engine/database-mirroring/specify-a-server-network-address-database-mirroring.md)  
  
-   [Указание URL-адреса конечной точки при добавлении или изменении реплики доступности (SQL Server)](../../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 **Просмотр сведений о конечной точке зеркального отображения базы данных**  
  
-   [sys.database_mirroring_endpoints (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
 [Создание группы доступности (Transact-SQL)](../../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md)   
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  

