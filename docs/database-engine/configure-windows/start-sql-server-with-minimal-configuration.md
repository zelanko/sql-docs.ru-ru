---
title: Запуск SQL Server с минимальной конфигурацией | Документы Майкрософт
ms.custom: ''
ms.date: 01/20/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- minimal configuration [SQL Server]
- starting SQL Server, minimal configuration
ms.assetid: 4d733c99-28b3-42d8-b7f6-7b943b548173
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 71fd26df641c1ac551dcc430c0fef555fc3c5df8
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68037153"
---
# <a name="start-sql-server-with-minimal-configuration"></a>Запустите SQL Server с минимальной конфигурацией
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  При наличии ошибок в конфигурации, не позволяющих осуществить запуск сервера, можно применить параметр запуска в минимальной конфигурации для запуска экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это параметр запуска **-f**. Запуск экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с минимальной конфигурацией автоматически переводит сервер в однопользовательский режим.  
  
 При запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в режиме минимальной конфигурации обратите внимание на следующее:  
  
-   может подключиться только один пользователь, операция `CHECKPOINT` не выполняется;  
  
-   удаленный доступ и упреждающее чтение отключены;  
  
-   запуск хранимых процедур не осуществляется.  

-   `tempdb` настраивается с возможно наименьшим размером.
  
 После запуска сервера с минимальной конфигурацией необходимо изменить значение или значения параметра соответствующего сервера, остановить сервер и заново запустить его.  
  
> [!IMPORTANT]  
>  Используйте программу **sqlcmd** и выделенное административное соединение (DAC) для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При использовании обычного соединения, перед тем как соединяться с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в режиме минимальной конфигурации, необходимо остановить службу агента SQL Server. В противном случае служба агента SQL Server использует это соединение, тем самым блокируя его.  
  
## <a name="see-also"></a>См. также:  
 [Запуск, остановка или приостановка службы агента SQL Server](https://msdn.microsoft.com/library/c95a9759-dd30-4ab6-9ab0-087bb3bfb97c)   
 [Диагностическое соединение для администраторов баз данных](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)   
 [sqlcmd Utility](../../tools/sqlcmd-utility.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Параметры запуска службы Database Engine](../../database-engine/configure-windows/database-engine-service-startup-options.md)  
  
  
