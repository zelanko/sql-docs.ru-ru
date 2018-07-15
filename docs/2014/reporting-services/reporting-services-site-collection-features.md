---
title: Компоненты семейства сайтов служб Reporting Services | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e05ae162-a4b2-489d-9853-d6b09414e632
caps.latest.revision: 5
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: eb321258a8dc87a499479d66ced85b95ce643b6d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37294124"
---
# <a name="reporting-services-site-collection-features"></a>Компоненты семейства веб-сайтов служб Reporting Services
  Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint предоставляют три компонента коллекции сайтов SharePoint. Эти компоненты поддерживают Общие [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] режиме интеграции с SharePoint среду, создания отчетов [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)], в состав [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для [!INCLUDE[SPS2010](../includes/sps2010-md.md)] Enterprise Edition и операции управления для [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в Центр администрирования SharePoint.  
  
## <a name="site-collection-features"></a>Компоненты семейства веб-сайтов  
 В следующей таблице приводится описание компонентов семейства веб-сайтов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
|Компонент|Описание|  
|-------------|-----------------|  
|**Центр администрирования сервера отчетов**|Включает возможности для управления процессом интеграции с сервером отчетов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Этот компонент устанавливается и используется в семействе веб-сайтов центра администрирования SharePoint.<br /><br /> Компонент интеграции сервера отчетов автоматически активируется в семействе сайтов центра администрирования SharePoint после установки [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] надстройки для продуктов SharePoint. В некоторых ситуациях потребуется активировать этот компонент вручную. Чтобы активировать компонент сервера отчетов, используйте страницы служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] на странице параметров сайта в центре администрирования SharePoint.<br /><br /> [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Версии и более поздней версии надстройки для SharePoint продуктов будет активировать функцию интеграции сервера отчетов для всех существующих веб-сайтов при установке надстройки. Кроме того, эта функция будет автоматически активироваться для новых семейств сайтов.|  
|**Компонент интеграции сервера отчетов**|Включает расширенные возможности создания отчетов с помощью [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<br /><br /> Этот компонент активен по умолчанию.|  
|**Компонент интеграции Power View**|Включает интерактивное исследование данных и визуальное представление для книг PowerPivot и табличных баз данных служб Analsysis Services.<br /><br /> Доступ к этому компоненту можно получить через контекстное меню следующих источников данных:<br /><br /> RDLX;<br /><br /> RSDS<br /><br /> файл соединения с BISM.<br /><br /> <br /><br /> Если [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] отсутствует в контекстном меню, убедитесь, что **интеграция Power View** включена.<br /><br /> По умолчанию эта функция отключена.|  
  
## <a name="see-also"></a>См. также  
 [Активация функций интеграции Power View в SharePoint и сервер отчетов](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Параметры сайта служб и веб-узла отчетов&#40;режиме интеграции с SharePoint&#41;](../../2014/reporting-services/reporting-services-site-settings-and-site-features-sharepoint-mode.md)   
 [активировать функции синхронизации файлов сервера отчетов в центре администрирования SharePoint](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)  
  
  
