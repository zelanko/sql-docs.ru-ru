---
title: Создание конечной точки зеркального отображения базы данных для группы доступности AlwaysOn (SQL Server PowerShell) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], endpoint
ms.assetid: 6197bbe7-67d4-446d-ba5f-cabfa5df77f1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5fb67c488da5f01ac572ec78a369790fc9014513
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72782992"
---
# <a name="create-a-database-mirroring-endpoint-for-alwayson-availability-groups-sql-server-powershell"></a>Создайте конечную точку зеркального отображения базы данных для групп доступности AlwaysOn (SQL Server PowerShell)
  В этом разделе описывается создание конечной точки зеркального отображения базы данных для использования [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью PowerShell.  
  
 **В этом разделе**  
  
-   **Перед началом работы:**  [безопасность](#Security)  
  
-   **Создание конечной точки зеркального отображения базы данных с помощью следующих средств:**  [PowerShell](#PowerShellProcedure)  
  
## <a name="before-you-begin"></a>Перед началом  
  
###  <a name="Security"></a> Безопасность  
  
> [!IMPORTANT]  
>  Алгоритм RC4 устарел. [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)] Вместо этого рекомендуется использовать алгоритм AES.  
  
####  <a name="Permissions"></a> Разрешения  
 Требуется разрешение CREATE ENDPOINT или членство в предопределенной роли сервера sysadmin. Дополнительные сведения см. в разделе [GRANT, предоставление разрешений конечной точке (Transact-SQL)](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql).  
  
##  <a name="PowerShellProcedure"></a> Использование PowerShell  
 **Создание конечной точки зеркального отображения базы данных**  
  
1.  Перейдите в каталог (`cd`) экземпляра сервера, для которого хотите создать конечную точку зеркального отображения.  
  
2.  Создайте конечную точку с помощью командлета `New-SqlHadrEndpoint`, а затем с помощью командлета `Set-SqlHadrEndpoint` запустите эту конечную точку.  
  
###  <a name="PShellExample"></a> Пример (PowerShell)  
 Следующие команды PowerShell создают конечную точку зеркального отображения базы данных на экземпляре SQL Server (*Machine*\\*Instance*). Эта конечная точка использует порт 5022.  
  
> [!IMPORTANT]  
>  Этот пример работает только на экземпляре сервера, на котором в данный момент отсутствует конечная точка зеркального отображения базы данных.  
  
```powershell
# Create the endpoint.  
$endpoint = New-SqlHadrEndpoint MyMirroringEndpoint -Port 5022 -Path SQLSERVER:\SQL\Machine\Instance  
  
# Start the endpoint  
Set-SqlHadrEndpoint -InputObject $endpoint -State "Started"
```  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
 **Настройка конечной точки зеркального отображения базы данных**  
  
-   [Создание конечной точки зеркального отображения базы данных с проверкой подлинности Windows (Transact-SQL)](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Использование сертификатов для конечной точки зеркального отображения базы данных (Transact-SQL)](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [Включение использования сертификатов для исходящих соединений в конечной точке зеркального отображения базы данных (Transact-SQL)](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [Включение использования сертификатов для входящих соединений в конечной точке зеркального отображения базы данных (Transact-SQL)](../../database-mirroring/database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [Указание сетевого адреса сервера (зеркальное отображение базы данных)](../../database-mirroring/specify-a-server-network-address-database-mirroring.md)  
  
-   [Указание URL-адреса конечной точки при добавлении или изменении реплики доступности (SQL Server)](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 **Просмотр сведений о конечной точке зеркального отображения базы данных**  
  
-   [sys.database_mirroring_endpoints (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
## <a name="see-also"></a>См. также статью  
 [Создание группы доступности (Transact-SQL)](create-an-availability-group-transact-sql.md)   
 [Общие сведения о &#40;группы доступности AlwaysOn SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
