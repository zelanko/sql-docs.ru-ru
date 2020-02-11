---
title: Страница "Веб-конфигурация" (диспетчер конфигурации служб Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.webconfigpg.f1
ms.assetid: 7b900778-0169-4e42-9faf-98dc1c01313e
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 12ba4a2d03e98d5f2dac79917e23a93c0a24cdb0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "65481211"
---
# <a name="web-configuration-page-master-data-services-configuration-manager"></a>Страница «Веб-конфигурация» (диспетчер конфигурации Master Data Services)
  Используйте страницу **Веб-конфигурация** для создания нового веб-сайта или для создания нового веб-сайта и веб-приложения. После выбора веб-приложения [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] можно указать базу данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] приложения и активировать службы Data Quality Services.  
  
## <a name="configure-the-web-application"></a>Настройка веб-приложения  
  
|Имя элемента управления|Description|  
|------------------|-----------------|  
|**Веб-сайт**|Создайте новый веб-сайт, выберите веб-сайт по умолчанию или выберите другой доступный сайт (если таковой имеется в списке). В этом списке показаны веб-сайты, которые определены в службах IIS на локальном компьютере. При создании нового веб-сайта автоматически создается новое веб-приложение. При выборе сайта по умолчанию или другого существующего сайта приложение необходимо создавать вручную.|  
|**Веб-приложение**|Выберите веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] для настройки. Это окно отображает только веб-приложения [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] на выбранном веб-сайте.<br /><br /> Если ничего не отображается, щелкните **Создать приложение** для создания веб-сайта.|  
|**Создание приложения**|Открывает диалоговое окно **Создать веб-приложение** , из которого можно создать веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] для выбранного сайта. Эта кнопка доступна, только если у выбранного сайта нет корневого веб-приложения, настроенного как веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .|  
  
## <a name="associate-application-with-database"></a>Связать приложение с базой данных  
  
|Имя элемента управления|Description|  
|------------------|-----------------|  
|**Метьте**|Открывает диалоговое окно **Соединение с сервером** , из которого можно подключиться к экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и выбрать базу данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] для привязки к выбранному веб-приложению [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .|  
|**Экземпляр SQL Server**|Отображает имя выбранного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , где размещается база данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Не содержит значения до подключения к экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и выбора базы данных.|  
|**База данных**|Отображает имя базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , связанной с выбранным веб-приложением [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Не содержит значения до подключения к экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и выбора базы данных.|  
  
## <a name="enable-dqs-integration"></a>Включение интеграции со средой DQS  
  
|Имя элемента управления|Description|  
|------------------|-----------------|  
|**Включение интеграции со службами Data Quality Services**|Выберите этот параметр для включения функциональных возможностей служб Data Quality Services, доступных в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]. Дополнительные сведения см. в разделе [Включение интеграции служб Data Quality Services со службами Master Data Services](install-windows/enable-data-quality-services-integration-with-master-data-services.md).|  
  
## <a name="see-also"></a>См. также:  
 [Настройка базы данных и веб-сайта для Master Data Services](../../2014/master-data-services/set-up-the-database-and-website-for-master-data-services.md)   
 [Требования к веб-приложениям &#40;Master Data Services&#41;](install-windows/web-application-requirements-master-data-services.md)   
 [Создание диспетчер основных данных &#40;веб-приложения Master Data Services&#41;](install-windows/create-a-master-data-manager-web-application-master-data-services.md)   
 [MDS 2014 и ошибка "Служба недоступна"](https://blogs.msdn.com/b/womeninanalytics/archive/2015/08/19/mds-2014-and-service-unavailable-error.aspx)  
  
  
