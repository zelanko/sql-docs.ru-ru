---
title: Настройка базы данных и веб-сайта для Master Data Services | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.general.f1
ms.assetid: d50863e7-50d9-4ab8-aabb-fd68e2d132a1
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 478dea9095fe22a437aecf138c22374b5a70885b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66054094"
---
# <a name="set-up-the-database-and-website-for-master-data-services"></a>Настройка базы данных и веб-сайта для служб Master Data Services
  Использование [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] для настройки базы данных и веб-сайта для [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS)  
  
 Чтобы настроить базу данных и веб-сайт, выполните следующие задачи.  
  
1.  Создайте базу данных с помощью страницы **Конфигурация базы данных** в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]среде.  
  
     Дополнительные сведения см. в разделе [&#40;страницы конфигурации базы данных диспетчер конфигурации Master Data Services&#41;](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md) и [Мастер создания базы данных &#40;Диспетчер конфигурации Master Data Services&#41;](../../2014/master-data-services/create-database-wizard-master-data-services-configuration-manager.md).  
  
2.  Создайте новый веб-сайт, выберите веб-сайт по умолчанию или выберите другой существующий веб-сайт с помощью [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]страницы **веб-конфигурация** в. Затем свяжите базу данных MDS с создаваемым или выбранным веб-приложением.  
  
     Дополнительные сведения см. в разделе [веб-страница конфигурации &#40;диспетчер конфигурации Master Data Services&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) и [Создание веб-сайта &#40;Диспетчер конфигурации Master Data Services&#41;](../../2014/master-data-services/create-website-dialog-box-master-data-services-configuration-manager.md).  
  
3.  Используемых Включите интеграцию со службами Data Quality Services с помощью страницы **веб-конфигурация** в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].  
  
     Дополнительные сведения см. в разделе [Web Configuration Page &#40;диспетчер конфигурации Master Data Services&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) и [Включение интеграции служб Data Quality Services с Master Data Services](install-windows/enable-data-quality-services-integration-with-master-data-services.md).  
  
 Также можно использовать [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] для указания параметров веб-приложений и служб, связанных с базой данных MDS. К примеру, можно указать, как часто загружаются данные или как часто отправляются сообщения проверки. Дополнительные сведения см. в разделе [Системные параметры (службы Master Data Services)](../../2014/master-data-services/system-settings-master-data-services.md).  
  
## <a name="see-also"></a>См. также  
 [База данных Master Data Services](../../2014/master-data-services/master-data-services-database.md)   
 [Веб-приложение диспетчера основных данных](../../2014/master-data-services/master-data-manager-web-application.md)  
  
  
