---
title: Учетные записи службы (мастер настройки безопасности зеркального отображения баз данных) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.serviceaccounts.f1
ms.assetid: d58d8f93-7888-4d66-af4d-969ef6a2dbee
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 69877c6a20e37e012925185d0b807e9579066e35
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62754389"
---
# <a name="service-accounts-configure-database-mirroring-security-wizard"></a>Учетные записи службы (мастер настройки безопасности зеркального отображения баз данных)
  При использовании проверки подлинности Windows, в случае если экземпляры сервера используют разные учетные записи, задайте учетные записи службы для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эти учетные записи службы должны быть учетными записями домена (одного и того же или доверенных доменов).  
  
 Если все экземпляры сервера используют одну и ту же учетную запись домена или проверку подлинности, основанную на сертификатах, оставьте поля незаполненными. Просто нажмите кнопку **Готово**, и мастер автоматически настроит учетные записи на основе учетной записи текущего мастера.  
  
> [!IMPORTANT]  
>  Если конечные точки зеркального отображения базы данных экземпляров сервера настроены для использования сертификатов, необходимо оставить все поля учетной записи службы пустыми.  
  
 **Настройка зеркального отображения базы данных в среде SQL Server Management Studio**  
  
-   [Создание сеанса зеркального отображения базы данных с использованием проверки подлинности Windows &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Запустите мастер настройки безопасности зеркального отображения баз данных &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>Параметры  
 **Основного**  
 Укажите учетную запись службы экземпляра основного сервера. Введите имя домена прописными буквами:  
  
 *Имя_домена*\\*имя пользователя*  
  
 **Зеркальное отображение**  
 Укажите учетную запись службы экземпляра зеркального сервера. Введите имя домена прописными буквами:  
  
 *Имя_домена*\\*имя пользователя*  
  
 **Свидетель**  
 Укажите учетную запись службы экземпляра следящего сервера. Введите имя домена прописными буквами:  
  
 *Имя_домена*\\*имя пользователя*  
  
## <a name="see-also"></a>См. также:  
 [Свойства базы данных &#40;страница зеркального отображения&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Запуск монитора зеркального отображения баз данных &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [SQL Server &#40;зеркального отображения базы данных&#41;](database-mirroring-sql-server.md)   
 [Настройка учетных записей входа для зеркального отображения базы данных или группы доступности AlwaysOn &#40;SQL Server&#41;](set-up-login-accounts-database-mirroring-always-on-availability.md)  
  
  
