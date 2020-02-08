---
title: Мастер настройки безопасности. Выбор серверов
descriptoin: Describes the properties found on the the 'Choose Servers' page of the 'Configure Database Mirroring Security Wizard'.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.configdbmsecurwiz.choosesrvrs.f1
ms.assetid: 59e23ff3-d7ee-4e32-9629-0b54d3a258f7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cfb2396e97c4cceee534472c07c285aa2a8a371e
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "74822311"
---
# <a name="configure-database-mirroring-wizard-choose-servers-to-configure"></a>Мастер настройки зеркального отображения базы данных. Выбор серверов для настройки 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Используйте данную страницу для задания экземпляров сервера, которые нужно настроить в текущий момент. Перед продолжением выполнения мастера необходимо выбрать хотя бы один экземпляр сервера.  
  
 При снятии флажка для экземпляра сервера мастер не внесет в него никаких изменений. Мастер, однако, выдаст приглашение для ввода данных о данном экземпляре и сохранит эти данные в составе конфигурации других экземпляров сервера. Например, если снять этот флажок для экземпляра следящего сервера, мастер выдаст запрос на ввод учетной записи службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] свидетеля, поскольку имя входа для этой учетной записи необходимо создать как часть конфигурации безопасности, сохраненной в экземплярах основного и зеркального сервера.  
  
 **Настройка зеркального отображения базы данных в среде SQL Server Management Studio**  
  
-   [Создание сеанса зеркального отображения базы данных с использованием проверки подлинности Windows (среда SQL Server Management Studio)](../../database-engine/database-mirroring/establish-database-mirroring-session-windows-authentication.md)  
  
-   [Запуск мастера настройки безопасности зеркального отображения баз данных (среда SQL Server Management Studio)](../../database-engine/database-mirroring/start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>Параметры  
 **Экземпляр основного сервера**  
 Выберите этот пункт для настройки безопасности основного сервера.  
  
 **Экземпляр зеркального сервера**  
 Выберите этот пункт для настройки безопасности зеркального сервера.  
  
 **Экземпляр следящего сервера**  
 Выберите этот пункт для настройки безопасности следящего сервера (при его наличии).  
  
## <a name="see-also"></a>См. также:  
 [Свойства базы данных (страница "Зеркальное отображение")](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Зеркальное отображение базы данных (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
