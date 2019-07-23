---
title: Обзор монитора SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql13.swb.sqlservermonitor.main.f1
helpviewer_keywords:
- SQL Server Monitor [SQL Server]
ms.assetid: 048ae16d-31c3-489a-9f1e-1400a3bacd39
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a6f5e2b2bcd92c0a17ccada2ca755cbc14b9d647
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68032491"
---
# <a name="sql-server-monitor-overview"></a>Обзор монитора SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Монитор SQL Server не выполняет функций наблюдения, но в нем размещены модули, которые выполняют эти функции. К модулям монитора SQL Server относятся монитор репликации и монитор зеркального отображения баз данных.  
  
 Чтобы использовать один из этих модулей, необходимо выбрать его в меню **Перейти** . Выбранный модуль управляет содержимым панелей навигации и подробных сведений, взаимодействием с пользователем на панелях подробных сведений, а также запросами содержимого и состояния.  
  
> [!NOTE]  
>  Дополнительные сведения об этих мониторах см. в разделах [Наблюдение за репликацией](../../relational-databases/replication/monitor/monitoring-replication.md) и [Наблюдение за зеркальным отображением базы данных (SQL Server)](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md).  
  
## <a name="permissions"></a>Разрешения  
  
-   монитор репликации  
  
     Чтобы наблюдать за репликацией, пользователь должен быть членом предопределенной роли сервера **sysadmin** на распространителе или предопределенной роли базы данных **replmonitor** в базе данных распространителя. Системный администратор может добавить любого пользователя в роль **replmonitor** , которая позволяет пользователю наблюдать операции репликации в мониторе репликации. Однако такой пользователь не может управлять репликацией.  
  
-   Монитор зеркального отображения баз данных.  
  
     Чтобы наблюдать за зеркальным отображением базы данных, пользователь должен быть членом предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **dbm_monitor** на экземпляре сервера. Если пользователь является членом **sysadmin** или **dbm_monitor** только на одном экземпляре сервера-участника, то монитор сможет подключиться только к этому участнику; монитор не сможет получить данные от другого участника. Дополнительные сведения см. в статье [Database Mirroring Monitor Overview](../../database-engine/database-mirroring/database-mirroring-monitor-overview.md).  
  
## <a name="menu-options"></a>Параметры меню  
 В меню монитора SQL Server содержатся команды для работы с монитором SQL Server. Это меню также может содержать команды из выбранного модуля.  
  
 К монитору SQL Server имеют отношение следующие параметры меню.  
  
 **Файл**  
 Это меню содержит команду **Выход** .  
  
 **Действие**  
 Содержит контекстное меню узла, выбранного в дереве навигации.  
  
 **Перейти**  
 Содержит перечень компонентов мониторинга:  
  
-   Зеркальное отображение базы данных  
  
-   Репликация  
  
 **Наблюдение за зеркальным отображением базы данных с помощью среды SQL Server Management Studio**  
  
-   [Запуск монитора зеркального отображения баз данных (среда SQL Server Management Studio)](../../database-engine/database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="see-also"></a>См. также:  
 [Мониторинг зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)  
  
  
