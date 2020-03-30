---
title: Защита и обеспечение безопасности служб Reporting Services | Документы Майкрософт
ms.date: 08/26/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- security [Reporting Services]
- Reporting Services, security
ms.assetid: 270075c5-bf12-4467-a775-abbda3d954a5
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 03234369ed7422433b35a5e3d296f6db1d1b2223
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "65570659"
---
# <a name="reporting-services-security-and-protection"></a>Защита и обеспечение безопасности служб Reporting Services
  Этот раздел содержит сведения о средствах безопасности служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. В разделе также объясняются модели авторизации и поставщики проверки подлинности, поддерживаемые в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="extended-protection-for-authentication"></a>Расширенная защита для проверки подлинности  
 Начиная с [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], доступна поддержка расширенной защиты для проверки подлинности. Функция [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует привязку каналов и служб для повышения уровня защиты проверки подлинности. Функции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно использовать в ОС, поддерживающей расширенную защиту. Дополнительные сведения см. в статье [Extended Protection for Authentication with Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md).  
  
## <a name="authentication-and-authorization"></a>Аутентификация и авторизация  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] предусматривают несколько типов проверки подлинности клиентов и клиентских приложений для доступа к серверу отчетов. Использование правильного типа проверки подлинности для сервера отчетов обеспечивает уровень безопасности, необходимый для организации. Дополнительные сведения см. в статье [Authentication with the Report Server](../../reporting-services/security/authentication-with-the-report-server.md).  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] также использует роли и разрешения для контроля доступа пользователей к содержимому каталога сервера отчетов (иными словами, кто к чему имеет доступ и как этот доступ осуществляется). Дополнительные сведения см. в статье [Роли и разрешения (службы Reporting Services)](../../reporting-services/security/roles-and-permissions-reporting-services.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описания задач|Ссылки|  
|-----------------------|-----------|  
|Настройка протокола Socket Layer (SSL) для защиты клиентских подключений к серверу отчетов.|[Настройка подключений SSL для сервера отчетов в собственном режиме](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md)|  
  
  
