---
title: Защита и обеспечение безопасности служб Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- security [Reporting Services]
- Reporting Services, security
ms.assetid: 270075c5-bf12-4467-a775-abbda3d954a5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ca88c252e37362f2a5b64bb8d41ebac27f0e24dd
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "59943140"
---
# <a name="reporting-services-security-and-protection"></a>Защита и обеспечение безопасности служб Reporting Services
  Этот раздел содержит сведения о средствах безопасности служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. В разделе также объясняются модели авторизации и поставщики проверки подлинности, поддерживаемые в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="extended-protection-for-authentication"></a>Расширенная защита для проверки подлинности  
 Начиная с [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], доступна поддержка расширенной защиты для проверки подлинности. Функция [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует привязку каналов и служб для повышения уровня защиты проверки подлинности. Функции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно использовать в ОС, поддерживающей расширенную защиту. Дополнительные сведения см. в статье [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md).  
  
## <a name="authentication-and-authorization"></a>Проверка подлинности и авторизация  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] предусматривают несколько типов проверки подлинности клиентов и клиентских приложений для доступа к серверу отчетов. Использование правильного типа проверки подлинности для сервера отчетов обеспечивает уровень безопасности, необходимый для организации. Дополнительные сведения см. в статье [Authentication with the Report Server](authentication-with-the-report-server.md).  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] также использует роли и разрешения для контроля доступа пользователей к содержимому каталога сервера отчетов (иными словами, кто к чему имеет доступ и как этот доступ осуществляется). Дополнительные сведения см. в статье [Роли и разрешения (службы Reporting Services)](roles-and-permissions-reporting-services.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описания задач|Ссылки|  
|-----------------------|-----------|  
|Настройка протокола Socket Layer (SSL) для защиты клиентских подключений к серверу отчетов.|[Настройка соединений SSL для сервера отчетов, работающего в собственном режиме](configure-ssl-connections-on-a-native-mode-report-server.md)|  
  
  
