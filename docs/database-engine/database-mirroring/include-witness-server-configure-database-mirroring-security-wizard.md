---
title: "Включение следящего сервера (мастер настройки безопасности зеркального отображения баз данных) | Документы Майкрософт"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: database-mirroring
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.configdbmsecurwiz.inclwitness.f1
ms.assetid: f04b38a4-f4e2-4d4c-bdac-7cc70e5a5684
caps.latest.revision: "32"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f4cfbef9951a69a5de388257073f91f20d5daf67
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="include-witness-server-configure-database-mirroring-security-wizard"></a>Включить следящий сервер (мастер настройки безопасности зеркального отображения баз данных)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Используйте эту страницу, чтобы указать, включать ли следящий сервер в конфигурацию безопасности для зеркального отображения базы данных.  
  
 **Настройка зеркального отображения базы данных в среде SQL Server Management Studio**  
  
-   [Создание сеанса зеркального отображения базы данных с использованием проверки подлинности Windows (среда SQL Server Management Studio)](../../database-engine/database-mirroring/establish-database-mirroring-session-windows-authentication.md)  
  
-   [Запуск мастера настройки безопасности зеркального отображения баз данных (среда SQL Server Management Studio)](../../database-engine/database-mirroring/start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>Параметры  
 **Да**  
 Нажмите, чтобы включить экземпляр следящего сервера в конфигурацию безопасности. Следящий сервер необходим для режима высокого уровня безопасности с автоматической отработкой отказа, который дает возможность автоматического перехода на экземпляр зеркального сервера при сбое в работе экземпляра основного сервера.  
  
 **Нет**  
 Нажмите, чтобы настроить безопасность без следящего сервера.  
  
## <a name="see-also"></a>См. также:  
 [Свойства базы данных (страница "Зеркальное отображение")](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Зеркальное отображение базы данных (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Следящий сервер зеркального отображения базы данных](../../database-engine/database-mirroring/database-mirroring-witness.md)  
  
  
