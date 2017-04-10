---
title: "Страница &#171;Веб-конфигурация&#187; (диспетчер конфигурации Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.mds.configmanager.webconfigpg.f1"
ms.assetid: 7b900778-0169-4e42-9faf-98dc1c01313e
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# Страница &#171;Веб-конфигурация&#187; (диспетчер конфигурации Master Data Services)
  Используйте страницу **Веб-конфигурация** для настройки веб-сайта и веб-приложения. Можно также включить службы Data Quality Services  
  
## Настройка веб-приложения  
  
|Имя элемента управления|Description|  
|------------------|-----------------|  
|**Веб-сайт**|Создайте новый веб-сайт, выберите веб-сайт по умолчанию или выберите другой доступный сайт (если таковой имеется в списке). В этом списке показаны веб-сайты, которые определены в службах IIS на локальном компьютере. При создании нового веб-сайта автоматически создается новое веб-приложение. При выборе сайта по умолчанию или другого существующего сайта приложение необходимо создавать вручную.|  
|**Веб-приложение**|Выберите веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] для настройки. Это окно отображает только веб-приложения [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] на выбранном веб-сайте.<br /><br /> Если ничего не отображается, щелкните **Создать** для создания веб-сайта.|  
|**Создание**|Открывает диалоговое окно **Создать веб-приложение** , из которого можно создать веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] для выбранного сайта. Эта кнопка доступна, только если у выбранного сайта нет корневого веб-приложения, настроенного как веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .|  
  
## Связать приложение с базой данных  
  
|Имя элемента управления|Description|  
|------------------|-----------------|  
|**Select**|Открывает диалоговое окно **Соединение с сервером** , из которого можно подключиться к экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и выбрать базу данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] для привязки к выбранному веб-приложению [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .|  
|**Экземпляр SQL Server**|Отображает имя выбранного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , где размещается база данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Не содержит значения до подключения к экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и выбора базы данных.|  
|**База данных**|Отображает имя базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , связанной с выбранным веб-приложением [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Не содержит значения до подключения к экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и выбора базы данных.|  
  
## Включение интеграции со средой DQS  
  
|Имя элемента управления|Description|  
|------------------|-----------------|  
|**Включение интеграции со службами Data Quality Services**|Выберите этот параметр для включения функциональных возможностей служб Data Quality Services, доступных в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]. Дополнительные сведения см. в разделе [Enable Data Quality Services Integration with Master Data Services](../master-data-services/install-windows/enable-data-quality-services-integration-with-master-data-services.md).|  
  
## См. также:  
 [Приступая к работе со службами Master Data Services (SQL Server 2016)](../Topic/Get%20Started%20with%20Master%20Data%20Services%20\(SQL%20Server%202016\).md)   
 [Требования веб-приложений (службы Master Data Services)](../master-data-services/install-windows/web-application-requirements-master-data-services.md)   
 [Создание веб-приложения мастера основных данных (службы Master Data Services)](../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)  
  
  