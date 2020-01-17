---
title: Мастер настройки безопасности. Учетные записи службы
description: Описание страницы "Учетные записи службы" мастера настройки безопасности зеркального отображения баз данных в SQL Server Management Studio.
ms.custom: seo-lt-2019
ms.date: 05/17/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.configdbmsecurwiz.serviceaccounts.f1
ms.assetid: d58d8f93-7888-4d66-af4d-969ef6a2dbee
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8c8a83b68febee5e00a80bd9977713a786b70f9a
ms.sourcegitcommit: f8cf8cc6650a22e0b61779c20ca7428cdb23c850
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2019
ms.locfileid: "74822449"
---
# <a name="configure-database-mirroring-security-wizard-service-accounts"></a>Мастер настройки безопасности зеркального отображения базы данных. Учетные записи службы
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  При использовании проверки подлинности Windows, в случае если экземпляры сервера используют разные учетные записи, задайте учетные записи службы для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эти учетные записи службы должны быть учетными записями домена (одного и того же или доверенных доменов).  
  
 Если все экземпляры сервера используют одну и ту же учетную запись домена или проверку подлинности, основанную на сертификатах, оставьте поля незаполненными. Просто нажмите кнопку **Готово**, и мастер автоматически настроит учетные записи на основе учетной записи текущего мастера.  
  
> [!IMPORTANT]  
>  Если конечные точки зеркального отображения базы данных экземпляров сервера настроены для использования сертификатов, необходимо оставить все поля учетной записи службы пустыми.  
  
 **Настройка зеркального отображения базы данных в среде SQL Server Management Studio**  
  
-   [Создание сеанса зеркального отображения базы данных с использованием проверки подлинности Windows (среда SQL Server Management Studio)](../../database-engine/database-mirroring/establish-database-mirroring-session-windows-authentication.md)  
  
-   [Запуск мастера настройки безопасности зеркального отображения баз данных (среда SQL Server Management Studio)](../../database-engine/database-mirroring/start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>Параметры  
 **Основной**  
 Укажите учетную запись службы экземпляра основного сервера. Введите имя домена прописными буквами:  
  
 *ИМЯ_ДОМЕНА*\\*имя_пользователя*  
  
 **Зеркальное отображение**  
 Укажите учетную запись службы экземпляра зеркального сервера. Введите имя домена прописными буквами:  
  
 *ИМЯ_ДОМЕНА*\\*имя_пользователя*  
  
 **Свидетель**  
 Укажите учетную запись службы экземпляра следящего сервера. Введите имя домена прописными буквами:  
  
 *ИМЯ_ДОМЕНА*\\*имя_пользователя*  
  
## <a name="see-also"></a>См. также:  
 [Свойства базы данных (страница "Зеркальное отображение")](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Запуск монитора зеркального отображения баз данных (среда SQL Server Management Studio)](../../database-engine/database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Зеркальное отображение базы данных (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Настройка учетных записей входа для зеркального отображения баз данных или групп доступности AlwaysOn (SQL Server)](../../database-engine/database-mirroring/set-up-login-accounts-database-mirroring-always-on-availability.md)  
  
  
