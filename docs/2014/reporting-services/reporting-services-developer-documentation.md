---
title: Руководством разработчика&#39;s (Reporting Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- developer's guide [Reporting Services]
- Reporting Services, programming
- programming [Reporting Services]
ms.assetid: d8afa405-1012-4349-a72d-e10d94f8453d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e8c555d853fd791bed29a06f561021b138526ea1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63255098"
---
# <a name="developer39s-guide-reporting-services"></a>Руководством для разработчиков&#39;(Reporting Services)
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] предлагает несколько программных интерфейсов, которые можно использовать в собственных приложениях. Можно использовать существующие функции и возможности служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для построения пользовательских средств создания отчетов и средств управления на сайтах и в приложениях Windows или расширять платформу служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
 Расширение платформы служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] включает создание новых компонентов и ресурсов, которые могут использоваться для доступа к данным, доставки отчетов и других задач. Эти компоненты и ресурсы можно предлагать компаниям, использующим в своей работе службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
## <a name="in-this-section"></a>в этом разделе  
 [Интеграция служб Reporting Services в приложения](application-integration/integrating-reporting-services-into-applications.md)  
 Приводит общие сведения об использовании служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для интеграции средств работы с отчетами в пользовательские приложения. Описывает, когда для обращения к серверу отчетов применяется прямой доступ по URL-адресу, а когда — веб-служба.  
  
 [Веб-службы сервера отчетов](report-server-web-service/report-server-web-service.md)  
 Веб-служба сервера отчетов предоставляет доступ ко всем функциональным возможностям сервера отчетов. Веб-служба использует протокол SOAP через протокол HTTP и разработана для работы в качестве интерфейса связи между клиентскими программами и сервером отчетов. Веб-служба и ее методы предоставляют доступ к функциям сервера отчетов и позволяют создавать пользовательские средства для любого этапа жизненного цикла отчета, от управления до выполнения.  
  
 [Доступ по URL-адресу (службы SSRS)](url-access-ssrs.md)  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] поддерживают полный набор запросов на основе URL-адреса, которые можно использовать в качестве точки быстрого и простого доступа для перехода по отчетам и их просмотра. Эту технологию можно использовать совместно с веб-службой сервера отчетов, чтобы интегрировать законченное решение по работе с отчетами в пользовательское бизнес-приложение. Доступ по URL-адресу особенно удобен, если отчеты интегрируются в составе веб-портала, а также для просмотра отчета из веб-браузера.  
  
 [модули служб Reporting Services](extensions/reporting-services-extensions.md)  
 Модульная архитектура служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] обеспечивает возможность расширения. Доступен API управляемого кода, что позволяет легко разрабатывать, устанавливать модули, используемые многими компонентами служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , а также управлять этими модулями. Вы можете создавать сборки с помощью [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] и добавлять новые [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] функции отрисовки, обеспечения безопасности, доставки и обработки данных в соответствии с растущими бизнес-потребностями.  
  
 [Пользовательские элементы отчета](custom-report-items/custom-report-items.md)  
 Описывает создание пользовательских элементов отчета, добавляющих новые функции в язык определения отчетов (RDL) или расширяющих функциональные возможности существующих элементов управления.  
  
 [Использование пользовательских сборок с отчетами](custom-assemblies/using-custom-assemblies-with-reports.md)  
 Описывает использование пользовательских сборок с отчетами путем включения ссылок на код в определение отчета.  
  
 [Доступ к поставщику WMI для служб Reporting Services](tools/access-the-reporting-services-wmi-provider.md)  
 Описывает использование поставщика WMI служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для управления развертыванием сервера отчетов.  
  
## <a name="see-also"></a>См. также:  
 [Службы Reporting Services (SSRS)](create-deploy-and-manage-mobile-and-paginated-reports.md)   
 [Язык определения отчетов &#40;службы SSRS&#41;](reports/report-definition-language-ssrs.md)   
 [Технический справочник (службы SSRS)](technical-reference-ssrs.md)   
 [Безопасная &#40;разработки Reporting Services&#41;](extensions/secure-development/secure-development-reporting-services.md)  
  
  
