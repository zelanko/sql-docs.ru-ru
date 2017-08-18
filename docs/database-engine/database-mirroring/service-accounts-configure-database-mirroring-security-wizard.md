---
title: "Учетные записи службы (мастер настройки безопасности зеркального отображения баз данных) | Документы Майкрософт"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.configdbmsecurwiz.serviceaccounts.f1
ms.assetid: d58d8f93-7888-4d66-af4d-969ef6a2dbee
caps.latest.revision: 34
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b1dcb128eb2269265d9439825e163421fa1b3ede
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="service-accounts-configure-database-mirroring-security-wizard"></a>Учетные записи службы (мастер настройки безопасности зеркального отображения баз данных)
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
  
  

