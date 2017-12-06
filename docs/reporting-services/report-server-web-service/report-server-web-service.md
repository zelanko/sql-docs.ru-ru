---
title: "Веб-служба сервера отчетов | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: report-server-web-service
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- SSIS, Web service
- Web service [Reporting Services]
- Reporting Services, extending
- SQL Server Reporting Services, Web service
- Reporting Services, Web service
- XML Web service [Reporting Services]
- Report Server Web service
ms.assetid: 16c21dec-6b46-4497-9a0c-1b0f2b6ab8fc
caps.latest.revision: "47"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 83ffccee4096ba5f0b662834b1316b0dab3ed158
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="report-server-web-service"></a>веб-служба сервера отчетов
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] предоставляют доступ к полному набору функций сервера отчетов с помощью веб-службы сервера отчетов. Веб-службой сервера отчетов является веб-служба XML с API-интерфейсом протокола SOAP. Она применяет протокол SOAP через протокол HTTP и действует как интерфейс связи между клиентскими программами и сервером отчетов. Веб-служба предоставляет две конечные точки — одну для выполнения отчета, а другую для управления отчетом — при помощи методов, которые предоставляют функциональные возможности сервера отчетов и дают возможность создавать пользовательские средства для любого периода жизненного цикла отчетов.  
  
 Имеются три основных способа разработки приложений служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на основе веб-службы. Возможные действия:  
  
-   Разрабатывать приложения с использованием [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] и пакета SDK [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Дополнительные сведения об использовании платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] для создания приложений веб-службы см. в разделе [Построение приложений с помощью веб-службы и платформы .NET Framework](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md).  
  
-   Разрабатывать приложения с использованием программы **rs** (RS.exe), среды скриптов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Скрипты служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] можно использовать для запуска любых операций веб-службы сервера отчетов. Дополнительные сведения о написании скриптов в [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] см. в разделе [Создание скриптов с помощью программы rs.exe и веб-службы](../../reporting-services/tools/script-with-the-rs-exe-utility-and-the-web-service.md).  
  
-   Разрабатывать приложения с использованием любого набора средств разработки с поддержкой протокола SOAP. Дополнительные сведения см. в разделе [Роль протокола SOAP в службах Reporting Services](../../reporting-services/report-server-web-service/the-role-of-soap-in-reporting-services.md).  
  
## <a name="programming-diagram"></a>Диаграмма программирования  
 ![Параметры разработки для веб-службы сервера отчетов](../../reporting-services/report-server-web-service/media/reportserviceswebserviceprog-01.gif "Параметры разработки для веб-службы сервера отчетов")  
Доступные способы разработки веб-службы для служб Reporting Services  
  
## <a name="in-this-section"></a>В этом разделе  
 [Методы веб-службы сервера отчетов](../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)  
 Описывает функции и методы каждой веб-службы сервера отчетов.  
  
 [Роль протокола SOAP в службах Reporting Services](../../reporting-services/report-server-web-service/the-role-of-soap-in-reporting-services.md)  
 Предоставляет общие сведения о протоколе SOAP, дает описание его использования в веб-службах сервера отчетов.  
  
 [Доступ к API SOAP](../../reporting-services/report-server-web-service/accessing-the-soap-api.md)  
 Описывает язык WSDL и предоставляет URL-адреса для доступа к файлу WSDL служб Reporting Services.  
  
 [Создание приложений с помощью веб-службы и .NET Framework](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
 Содержит сведения о разработке приложений и веб-служб, которые вызывают API-интерфейс протокола SOAP служб Reporting Services.  
  
 [Создание скриптов с помощью программы rs.exe и веб-службы](../../reporting-services/tools/script-with-the-rs-exe-utility-and-the-web-service.md)  
 Содержит общие сведения о среде исполнения сценариев служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Технический справочник (службы SSRS)](../../reporting-services/technical-reference-ssrs.md)  
 Содержит справочные материалы по методам веб-служб сервера отчетов и по соответствующим сложным типам.  
  
## <a name="user-requirements-for-web-service-development"></a>Требования к пользователям для разработки с использованием веб-службы  
 Для разработки приложений с использованием веб-службы сервера отчетов необходимо следующее.  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer 5.5 или более поздней версии, установленный на компьютере с подключением к Интернету и доступом к серверу отчетов.  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] или пакет SDK для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], установленный на компьютере, если планируется разработка и развертывание приложений служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] с использованием платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
-   Глубокое понимание функций и возможностей служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
-   Глубокое понимание протокола SOAP и служб [!INCLUDE[vstecwebservices](../../includes/vstecwebservices-md.md)].  
  
-   Опыт разработки на совместимом с [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] языке, например на [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] или [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], если планируется использовать [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] в качестве платформы разработки.  
  
## <a name="see-also"></a>См. также:  
 [Веб-службы сервера отчетов](../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
