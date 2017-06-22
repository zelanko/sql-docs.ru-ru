---
title: "Документация для разработчиков служб Reporting Services | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- developer's guide [Reporting Services]
- Reporting Services, programming
- programming [Reporting Services]
ms.assetid: d8afa405-1012-4349-a72d-e10d94f8453d
caps.latest.revision: 21
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 3704373a08b29a8f36ce843db5f67a860a04a47b
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="reporting-services-developer-documentation"></a>Документация для разработчиков служб отчетов
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] предлагают несколько программных интерфейсов, которые могут быть использованы в пользовательских приложениях. Можно использовать существующие функции и возможности служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для построения пользовательских средств создания отчетов и средств управления на сайтах и в приложениях Windows или расширять платформу служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
 Расширение платформы служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] включает создание новых компонентов и ресурсов, которые могут использоваться для доступа к данным, доставки отчетов и других задач. Эти компоненты и ресурсы можно предлагать компаниям, использующим в своей работе службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
> В службы  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] включены образцы программирования и учебники, помогающие приступить к работе. Дополнительные сведения см. в разделе [образцы служб Reporting Services](https://msdn.microsoft.com/library/ms160954\(v=sql.110\).aspx) и [руководство разработчика: учебники (службы Reporting Services)](https://msdn.microsoft.com/library/aa337423\(v=sql.110\).aspx).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Интеграция служб Reporting Services в приложения](../reporting-services/application-integration/integrating-reporting-services-into-applications.md)  
 Приводит общие сведения об использовании служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для интеграции средств работы с отчетами в пользовательские приложения. Описывает, когда для обращения к серверу отчетов применяется прямой доступ по URL-адресу, а когда — веб-служба.  
  
 [Веб-службы сервера отчетов](../reporting-services/report-server-web-service/report-server-web-service.md)  
 Веб-служба сервера отчетов предоставляет доступ ко всем функциональным возможностям сервера отчетов. Веб-служба использует протокол SOAP через протокол HTTP и разработана для работы в качестве интерфейса связи между клиентскими программами и сервером отчетов. Веб-служба и ее методы предоставляют доступ к функциям сервера отчетов и позволяют создавать пользовательские средства для любого этапа жизненного цикла отчета, от управления до выполнения.  
  
 [Доступ по URL-адресу (службы SSRS)](../reporting-services/url-access-ssrs.md)  
Службы  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] поддерживают полный набор запросов на основе URL-адреса, которые можно использовать в качестве точки быстрого и простого доступа для перехода по отчетам и их просмотра. Эту технологию можно использовать совместно с веб-службой сервера отчетов, чтобы интегрировать законченное решение по работе с отчетами в пользовательское бизнес-приложение. Доступ по URL-адресу особенно удобен, если отчеты интегрируются в составе веб-портала, а также для просмотра отчета из веб-браузера.  
  
 [Модули служб Reporting Services](../reporting-services/extensions/reporting-services-extensions.md)  
 Модульная архитектура служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] обеспечивает возможность расширения. Доступен API управляемого кода, что позволяет легко разрабатывать, устанавливать модули, используемые многими компонентами служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], а также управлять этими модулями. Можно создавать сборки с помощью [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] и добавить новые [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] подготовки к просмотру, безопасности, доставки и обработки данных функции, чтобы соответствовать растущим требованиям.  
  
 [Пользовательские элементы отчета](../reporting-services/custom-report-items/custom-report-items.md)  
 Описывает создание пользовательских элементов отчета, добавляющих новые функции в язык определения отчетов (RDL) или расширяющих функциональные возможности существующих элементов управления.  
  
 [Использование пользовательских сборок с отчетами](../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
 Описывает использование пользовательских сборок с отчетами путем включения ссылок на код в определение отчета.  
  
 [Доступ к поставщику WMI служб Reporting Services](../reporting-services/tools/access-the-reporting-services-wmi-provider.md)  
 Описывает использование поставщика WMI служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для управления развертыванием сервера отчетов.  
  
## <a name="see-also"></a>См. также:  
 [Службы Reporting Services (SSRS)](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)   
 [Язык определения отчетов &#40; Службы SSRS &#41;](../reporting-services/reports/report-definition-language-ssrs.md)   
 [Технический справочник по &#40; Службы SSRS &#41;](../reporting-services/technical-reference-ssrs.md)   
 [Защита разработки &#40; Службы Reporting Services &#41;](../reporting-services/extensions/secure-development/secure-development-reporting-services.md)  
  
  
