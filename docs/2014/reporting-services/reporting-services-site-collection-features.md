---
title: Компоненты семейства сайтов служб Reporting Services | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e05ae162-a4b2-489d-9853-d6b09414e632
caps.latest.revision: 5
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 88dd168355249d5b1f2dfd645ad7f42505597cde
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098814"
---
# <a name="reporting-services-site-collection-features"></a>Компоненты семейства веб-сайтов служб Reporting Services
  Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint предоставляют три компонента коллекции сайтов SharePoint. Компоненты поддерживают [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] режиме интеграции с SharePoint reporting среде [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)], функция [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] надстройки для [!INCLUDE[SPS2010](../includes/sps2010-md.md)] Enterprise Edition и операции управления для [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в Центр администрирования SharePoint.  
  
## <a name="site-collection-features"></a>Компоненты семейства веб-сайтов  
 В следующей таблице приводится описание компонентов семейства веб-сайтов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
|Компонент|Описание|  
|-------------|-----------------|  
|**Центр администрирования сервера отчетов**|Включает возможности для управления процессом интеграции с сервером отчетов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Этот компонент устанавливается и используется в семействе веб-сайтов центра администрирования SharePoint.<br /><br /> Компонент интеграции сервера отчетов автоматически активируется в коллекции сайта центра администрирования SharePoint после установки [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] надстройки для продуктов SharePoint. В некоторых ситуациях потребуется активировать этот компонент вручную. Чтобы активировать компонент сервера отчетов, используйте страницы служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] на странице параметров сайта в центре администрирования SharePoint.<br /><br /> [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Версии и более поздней версии надстройки для SharePoint продуктов будет активировать функции интеграции сервера отчетов для всех существующих коллекциях сайтов при установке надстройки. Кроме того, эта функция будет автоматически активироваться для новых семейств сайтов.|  
|**Компонент интеграции сервера отчетов**|Позволяет использовать широкие возможности создания отчетов [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<br /><br /> Этот компонент активен по умолчанию.|  
|**Компонент интеграции Power View**|Включает интерактивное исследование данных и визуальное представление для книг PowerPivot и табличных баз данных служб Analsysis Services.<br /><br /> Доступ к этому компоненту можно получить через контекстное меню следующих источников данных:<br /><br /> RDLX;<br /><br /> RSDS<br /><br /> файл соединения с BISM.<br /><br /> <br /><br /> Если [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] отсутствует в контекстном меню, убедитесь, что **интеграция Power View** включена.<br /><br /> По умолчанию эта функция отключена.|  
  
## <a name="see-also"></a>См. также  
 [Активируйте сервер отчетов и Power View Integration Features in SharePoint](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Параметры узла службы и компоненты сайта отчетов&#40;режиме интеграции с SharePoint&#41;](../../2014/reporting-services/reporting-services-site-settings-and-site-features-sharepoint-mode.md)   
 [активировать функции синхронизации файлов сервера отчетов в центре администрирования SharePoint](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)  
  
  