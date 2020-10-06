---
title: Запуск SQL Server с минимальной конфигурацией | Документы Майкрософт
description: Ознакомьтесь с параметром запуска SQL Server с минимальной конфигурацией. Узнайте, когда и как его использовать, а также каким образом он ограничивает функциональность.
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1ae9ee2f231367ebf577f0c5c70e5e64ce32d6cc
ms.sourcegitcommit: 2f868a77903c1f1c4cecf4ea1c181deee12d5b15
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2020
ms.locfileid: "91670767"
---
# <a name="start-sql-server-with-minimal-configuration"></a>Запустите SQL Server с минимальной конфигурацией
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  При наличии ошибок в конфигурации, не позволяющих осуществить запуск сервера, можно применить параметр запуска в минимальной конфигурации для запуска экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это параметр запуска **-f**. Запуск экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с минимальной конфигурацией автоматически переводит сервер в однопользовательский режим.  
  
 При запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в режиме минимальной конфигурации обратите внимание на следующее:  
  
-   может подключиться только один пользователь, операция `CHECKPOINT` не выполняется;  
  
-   удаленный доступ и упреждающее чтение отключены;  
  
-   запуск хранимых процедур не осуществляется.  

-   `tempdb` настраивается с возможно наименьшим размером.

-   Аудит будет отключен, однако DDL-журнал аудита по-прежнему может быть выпущен. На практике **-m** должно быть достаточными для большинства случаев, требующих перенастройки аудита SQL. Дополнительные сведения о безопасности в конфигурации аудита см. в разделе [Аудит в SQL Server](/previous-versions/sql/sql-server-2008/dd392015(v=sql.100)#security).
  
 После запуска сервера с минимальной конфигурацией необходимо изменить значение или значения параметра соответствующего сервера, остановить сервер и заново запустить его.  
  
> [!IMPORTANT]  
>  Используйте программу **sqlcmd** и выделенное административное соединение (DAC) для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При использовании обычного соединения, перед тем как соединяться с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в режиме минимальной конфигурации, необходимо остановить службу агента SQL Server. В противном случае служба агента SQL Server использует это соединение, тем самым блокируя его.  
  
## <a name="see-also"></a>См. также:  
 [Запуск, остановка или приостановка службы агента SQL Server](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)   
 [Диагностическое соединение для администраторов баз данных](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)   
 [sqlcmd Utility](../../tools/sqlcmd-utility.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Параметры запуска службы Database Engine](../../database-engine/configure-windows/database-engine-service-startup-options.md)  
  
