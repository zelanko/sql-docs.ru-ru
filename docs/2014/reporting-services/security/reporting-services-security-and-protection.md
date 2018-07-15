---
title: Защита и обеспечение безопасности служб Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- security [Reporting Services]
- Reporting Services, security
ms.assetid: 270075c5-bf12-4467-a775-abbda3d954a5
caps.latest.revision: 20
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 3be671426856e57e62ea7de3733f6109bbcd0a31
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37232454"
---
# <a name="reporting-services-security-and-protection"></a>Защита и обеспечение безопасности служб Reporting Services
  Этот раздел содержит сведения о средствах безопасности служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. В разделе также объясняются модели авторизации и поставщики проверки подлинности, поддерживаемые в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="extended-protection-for-authentication"></a>Расширенная защита для проверки подлинности  
 Начиная с [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], доступна поддержка расширенной защиты для проверки подлинности. Функция [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует привязку каналов и служб для повышения уровня защиты проверки подлинности. Функции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно использовать в ОС, поддерживающей расширенную защиту. Дополнительные сведения см. в разделе [расширенная защита для проверки подлинности со службами Reporting Services](extended-protection-for-authentication-with-reporting-services.md).  
  
## <a name="authentication-and-authorization"></a>Проверка подлинности и авторизация  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] предусматривают несколько типов проверки подлинности клиентов и клиентских приложений для доступа к серверу отчетов. Использование правильного типа проверки подлинности для сервера отчетов обеспечивает уровень безопасности, необходимый для организации. Дополнительные сведения см. в статье [Authentication with the Report Server](authentication-with-the-report-server.md).  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] также использует роли и разрешения для контроля доступа пользователей к содержимому каталога сервера отчетов (иными словами, кто к чему имеет доступ и как этот доступ осуществляется). Дополнительные сведения см. в статье [Роли и разрешения (службы Reporting Services)](roles-and-permissions-reporting-services.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Описания задач|Ссылки|  
|-----------------------|-----------|  
|Настройка протокола Socket Layer (SSL) для защиты клиентских подключений к серверу отчетов.|[Настройка подключений SSL для сервера отчетов в собственном режиме](configure-ssl-connections-on-a-native-mode-report-server.md)|  
  
  
