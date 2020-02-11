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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "72782992"
---
# <a name="create-a-database-mirroring-endpoint-for-alwayson-availability-groups-sql-server-powershell"></a>Create a Database Mirroring Endpoint for AlwaysOn Availability Groups (SQL Server PowerShell)
  В этом разделе описывается создание конечной точки зеркального отображения базы данных для использования [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью PowerShell.  
  
 **В этом разделе**  
  
-   **Перед началом:**  [Безопасность](#Security)  
  
-   **Создание конечной точки зеркального отображения базы данных с помощью:**  [PowerShell](#PowerShellProcedure)  
  
## <a name="before-you-begin"></a>Перед началом  
  
###  <a name="Security"></a> безопасность  
  
> [!IMPORTANT]  
>  Алгоритм RC4 устарел. [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)]Рекомендуется использовать алгоритм AES.  
  
####  <a name="Permissions"></a> Permissions  
 Требуется разрешение CREATE ENDPOINT или членство в предопределенной роли сервера sysadmin. Дополнительные сведения см. в разделе [GRANT, предоставление разрешений на конечную точку (Transact-SQL)](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql).  
  
##  <a name="PowerShellProcedure"></a>Использование PowerShell  
 **Создание конечной точки зеркального отображения базы данных**  
  
1.  Перейдите в каталог (`cd`) экземпляра сервера, для которого хотите создать конечную точку зеркального отображения.  
  
2.  Создайте конечную точку с помощью командлета `New-SqlHadrEndpoint`, а затем с помощью командлета `Set-SqlHadrEndpoint` запустите эту конечную точку.  
  
###  <a name="PShellExample"></a>Пример (PowerShell)  
 Следующие команды PowerShell создают конечную точку зеркального отображения базы данных на экземпляре SQL Server (*экземпляре**компьютера*\\). Эта конечная точка использует порт 5022.  
  
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
  
-   [Создание конечной точки зеркального отображения базы данных для проверки подлинности Windows &#40;Transact-SQL&#41;](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Использование сертификатов для конечной точки зеркального отображения базы данных &#40;Transact-SQL&#41;](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [Разрешить использование сертификатов для исходящих соединений в конечной точке зеркального отображения базы данных &#40;Transact-SQL&#41;](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [Разрешить использование сертификатов для входящих соединений в конечной точке зеркального отображения базы данных &#40;Transact-SQL&#41;](../../database-mirroring/database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [Укажите сетевой адрес сервера &#40;зеркальное отображение базы данных&#41;](../../database-mirroring/specify-a-server-network-address-database-mirroring.md)  
  
-   [Укажите URL-адрес конечной точки при добавлении или изменении &#40;реплики доступности SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 **Просмотр сведений о конечной точке зеркального отображения базы данных**  
  
-   [sys. database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
## <a name="see-also"></a>См. также:  
 [Создание группы доступности &#40;&#41;Transact-SQL](create-an-availability-group-transact-sql.md)   
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
