---
title: Компоненты семейства веб-сайтов Reporting Services | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e05ae162-a4b2-489d-9853-d6b09414e632
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9475ee323222b800a9c4b9a86e737fdd161e7a60
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66102760"
---
# <a name="reporting-services-site-collection-features"></a>Компоненты семейства веб-сайтов служб Reporting Services
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint предоставляют три компонента коллекции сайтов SharePoint. Эти компоненты поддерживают среду создания отчетов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint — [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)], компонент надстройки служб [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для [!INCLUDE[SPS2010](../includes/sps2010-md.md)] Enterprise Edition и операции управления для служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в центре администрирования SharePoint.  
  
## <a name="site-collection-features"></a>Компоненты семейства веб-сайтов  
 В следующей таблице приводится описание компонентов семейства веб-сайтов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
|Компонент|Описание|  
|-------------|-----------------|  
|**Центр администрирования сервера отчетов**|Включает возможности для управления процессом интеграции с сервером отчетов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Этот компонент устанавливается и используется в семействе веб-сайтов центра администрирования SharePoint.<br /><br /> Функция интеграции сервера отчетов автоматически активируется в семействе веб-сайтов центра администрирования SharePoint после установки [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] надстройки для продуктов SharePoint. В некоторых ситуациях потребуется активировать этот компонент вручную. Чтобы активировать компонент сервера отчетов, используйте страницы служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] на странице параметров сайта в центре администрирования SharePoint.<br /><br /> Версия служб [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] и более поздние версии надстройки для продуктов SharePoint активируют функцию интеграции сервера отчетов для всех существующих на момент установки надстройки семейств веб-сайтов. Кроме того, эта функция будет автоматически активироваться для новых семейств сайтов.|  
|**Компонент интеграции сервера отчетов**|Включает широкие возможности создания [!INCLUDE[msCoName](../includes/msconame-md.md)] отчетов с помощью[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<br /><br /> Этот компонент активен по умолчанию.|  
|**Компонент интеграции Power View**|Включает интерактивное исследование данных и визуальное представление для книг PowerPivot и табличных баз данных служб Analsysis Services.<br /><br /> Доступ к этому компоненту можно получить через контекстное меню следующих источников данных:<br /><br /> RDLX;<br /><br /> RSDS<br /><br /> файл соединения с BISM.<br /><br /> <br /><br /> Если [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] отсутствует в контекстном меню, убедитесь, что **интеграция Power View** включена.<br /><br /> По умолчанию эта функция отключена.|  
  
## <a name="see-also"></a>См. также  
 [Активация функций интеграции сервера отчетов и Power View в SharePoint](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Reporting Services параметры сайта и компоненты сайта&#40;режиме интеграции с SharePoint&#41;](../../2014/reporting-services/reporting-services-site-settings-and-site-features-sharepoint-mode.md)   
 [активировать функции синхронизации файлов сервера отчетов в центре администрирования SharePoint](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)  
  
  
