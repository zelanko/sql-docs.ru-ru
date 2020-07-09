---
title: Включить следящий сервер (мастер настройки безопасности зеркального отображения баз данных)
description: Описание страницы "Включить следящий сервер" мастера настройки безопасности зеркального отображения баз данных в графическом интерфейсе SQL Server Management Studio (SSMS).
ms.custom: seo-lt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.configdbmsecurwiz.inclwitness.f1
ms.assetid: f04b38a4-f4e2-4d4c-bdac-7cc70e5a5684
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a8b787f59da14c1414e66f158f8001e05cca6006
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85754648"
---
# <a name="include-witness-server-configure-database-mirroring-security-wizard"></a>Включить следящий сервер (мастер настройки безопасности зеркального отображения баз данных)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Используйте эту страницу, чтобы указать, включать ли следящий сервер в конфигурацию безопасности для зеркального отображения базы данных.  
  
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
  
  
