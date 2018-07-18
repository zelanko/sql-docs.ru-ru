---
title: Учетные записи службы (мастер настройки безопасности зеркального отображения баз данных) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.serviceaccounts.f1
ms.assetid: d58d8f93-7888-4d66-af4d-969ef6a2dbee
caps.latest.revision: 32
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d6479097305016d471a2b5434f7cab18a452928d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37182787"
---
# <a name="service-accounts-configure-database-mirroring-security-wizard"></a>Учетные записи службы (мастер настройки безопасности зеркального отображения баз данных)
  При использовании проверки подлинности Windows, в случае если экземпляры сервера используют разные учетные записи, задайте учетные записи службы для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эти учетные записи службы должны быть учетными записями домена (одного и того же или доверенных доменов).  
  
 Если все экземпляры сервера используют одну и ту же учетную запись домена или проверку подлинности, основанную на сертификатах, оставьте поля незаполненными. Просто нажмите кнопку **Готово**, и мастер автоматически настроит учетные записи на основе учетной записи текущего мастера.  
  
> [!IMPORTANT]  
>  Если конечные точки зеркального отображения базы данных экземпляров сервера настроены для использования сертификатов, необходимо оставить все поля учетной записи службы пустыми.  
  
 **Настройка зеркального отображения базы данных в среде SQL Server Management Studio**  
  
-   [Создание сеанса зеркального отображения базы данных с использованием проверки подлинности Windows (среда SQL Server Management Studio)](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Запуск мастера настройки безопасности зеркального отображения баз данных (среда SQL Server Management Studio)](start-the-configuring-database-mirroring-security-wizard.md)  
  
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
  
## <a name="see-also"></a>См. также  
 [Свойства базы данных (страница "Зеркальное отображение")](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Запуск монитора зеркального отображения баз данных (среда SQL Server Management Studio)](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Зеркальное отображение базы данных (SQL Server)](database-mirroring-sql-server.md)   
 [Настройка учетных записей входа для зеркального отображения базы данных или групп доступности AlwaysOn &#40;SQL Server&#41;](set-up-login-accounts-database-mirroring-always-on-availability.md)  
  
  
