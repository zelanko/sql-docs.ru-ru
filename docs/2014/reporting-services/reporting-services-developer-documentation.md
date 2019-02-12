---
title: Разработчик&#39;руководство (службы Reporting Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- developer's guide [Reporting Services]
- Reporting Services, programming
- programming [Reporting Services]
ms.assetid: d8afa405-1012-4349-a72d-e10d94f8453d
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 97d59933a1df11123b153e11f7ae75d926829dcb
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56023445"
---
# <a name="developer39s-guide-reporting-services"></a>Разработчик&#39;руководство (службы Reporting Services)
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] предлагают несколько программных интерфейсов, которые могут быть использованы в пользовательских приложениях. Можно использовать существующие функции и возможности служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для построения пользовательских средств создания отчетов и средств управления на сайтах и в приложениях Windows или расширять платформу служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
 Расширение платформы служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] включает создание новых компонентов и ресурсов, которые могут использоваться для доступа к данным, доставки отчетов и других задач. Эти компоненты и ресурсы можно предлагать компаниям, использующим в своей работе службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
## <a name="in-this-section"></a>в этом разделе  
 [Интеграция Reporting Services в приложения](application-integration/integrating-reporting-services-into-applications.md)  
 Приводит общие сведения об использовании служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для интеграции средств работы с отчетами в пользовательские приложения. Описывает, когда для обращения к серверу отчетов применяется прямой доступ по URL-адресу, а когда — веб-служба.  
  
 [Веб-службы сервера отчетов](report-server-web-service/report-server-web-service.md)  
 Веб-служба сервера отчетов предоставляет доступ ко всем функциональным возможностям сервера отчетов. Веб-служба использует протокол SOAP через протокол HTTP и разработана для работы в качестве интерфейса связи между клиентскими программами и сервером отчетов. Веб-служба и ее методы предоставляют доступ к функциям сервера отчетов и позволяют создавать пользовательские средства для любого этапа жизненного цикла отчета, от управления до выполнения.  
  
 [Доступ по URL-адресу (службы SSRS)](url-access-ssrs.md)  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] поддерживают полный набор запросов на основе URL-адреса, которые можно использовать в качестве точки быстрого и простого доступа для перехода по отчетам и их просмотра. Эту технологию можно использовать совместно с веб-службой сервера отчетов, чтобы интегрировать законченное решение по работе с отчетами в пользовательское бизнес-приложение. Доступ по URL-адресу особенно удобен, если отчеты интегрируются в составе веб-портала, а также для просмотра отчета из веб-браузера.  
  
 [Модули Reporting Services](extensions/reporting-services-extensions.md)  
 Модульная архитектура служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] обеспечивает возможность расширения. Доступен API управляемого кода, что позволяет легко разрабатывать, устанавливать модули, используемые многими компонентами служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , а также управлять этими модулями. Можно создавать сборки с помощью платформы [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] и добавлять в службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] новые функции для подготовки отчетов к просмотру, обеспечения безопасности, доставки и обработки данных, чтобы соответствовать растущим требованиям.  
  
 [Пользовательские элементы отчета](custom-report-items/custom-report-items.md)  
 Описывает создание пользовательских элементов отчета, добавляющих новые функции в язык определения отчетов (RDL) или расширяющих функциональные возможности существующих элементов управления.  
  
 [Использование пользовательских сборок с отчетами](custom-assemblies/using-custom-assemblies-with-reports.md)  
 Описывает использование пользовательских сборок с отчетами путем включения ссылок на код в определение отчета.  
  
 [Доступ к поставщику WMI для служб Reporting Services](tools/access-the-reporting-services-wmi-provider.md)  
 Описывает использование поставщика WMI служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для управления развертыванием сервера отчетов.  
  
## <a name="see-also"></a>См. также  
 [Службы Reporting Services (SSRS)](create-deploy-and-manage-mobile-and-paginated-reports.md)   
 [Язык определения отчетов (службы SSRS)](reports/report-definition-language-ssrs.md)   
 [Технический справочник (службы SSRS)](technical-reference-ssrs.md)   
 [Разработка безопасных приложений (службы Reporting Services)](extensions/secure-development/secure-development-reporting-services.md)  
  
  
