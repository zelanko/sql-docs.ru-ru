---
title: "Создание конечной точки зеркального отображения базы данных для групп доступности AlwaysOn (SQL Server PowerShell) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Группы доступности [SQL Server], экземпляр сервера"
  - "группы доступности [SQL Server], развертывание"
  - "Группы доступности [SQL Server], конечная точка"
ms.assetid: 6197bbe7-67d4-446d-ba5f-cabfa5df77f1
caps.latest.revision: 9
ms.author: "mikeray"
manager: "jhubbard"
---
# Создание конечной точки зеркального отображения базы данных для групп доступности AlwaysOn (SQL Server PowerShell)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  В этом разделе описывается создание конечной точки зеркального отображения базы данных для использования [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью PowerShell.  
  
 **В этом разделе**  
  
-   **Перед началом работы:**  [безопасность](#Security)  
  
-   **Создание конечной точки зеркального отображения базы данных с помощью следующих средств:**  [PowerShell](#PowerShellProcedure)  
  
## Перед началом  
  
###  <a name="Security"></a> Безопасность  
  
> [!IMPORTANT]  
>  Алгоритм RC4 устарел. [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)] Вместо этого рекомендуется использовать алгоритм AES.  
  
####  <a name="Permissions"></a> Разрешения  
 Требуется разрешение CREATE ENDPOINT или членство в предопределенной роли сервера sysadmin. Дополнительные сведения см. в разделе [GRANT, предоставление разрешений на конечные точки (Transact-SQL)](../../../t-sql/statements/grant-endpoint-permissions-transact-sql.md).  
  
##  <a name="PowerShellProcedure"></a> Использование PowerShell  
 **Создание конечной точки зеркального отображения базы данных**  
  
1.  Перейдите в каталог (**cd**) экземпляра сервера, для которого требуется создать конечную точку зеркального отображения.  
  
2.  Создайте конечную точку с помощью командлета **New-SqlHadrEndpoint**, а затем с помощью командлета **Set-SqlHadrEndpoint** запустите ее.  
  
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
  
    -   [Включение использования сертификатов для исходящих соединений в конечной точке зеркального отображения базы данных (Transact-SQL)](../../../database-engine/database-mirroring/database mirroring - use certificates for outbound connections.md)  
  
    -   [Включение использования сертификатов для входящих соединений в конечной точке зеркального отображения базы данных (Transact-SQL)](../../../database-engine/database-mirroring/database mirroring - use certificates for inbound connections.md)  
  
-   [Указание сетевого адреса сервера (зеркальное отображение базы данных)](../../../database-engine/database-mirroring/specify-a-server-network-address-database-mirroring.md)  
  
-   [Указание URL-адреса конечной точки при добавлении или изменении реплики доступности (SQL Server)](../../../database-engine/availability-groups/windows/specify endpoint url - adding or modifying availability replica.md)  
  
 **Просмотр сведений о конечной точке зеркального отображения базы данных**  
  
-   [sys.database_mirroring_endpoints (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql.md)  
  
## См. также:  
 [Создание группы доступности (Transact-SQL)](../../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md)   
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  