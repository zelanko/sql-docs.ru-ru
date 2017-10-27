---
title: "Веб-служба сервера отчетов | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- SSIS, Web service
- Web service [Reporting Services]
- Reporting Services, extending
- SQL Server Reporting Services, Web service
- Reporting Services, Web service
- XML Web service [Reporting Services]
- Report Server Web service
ms.assetid: 16c21dec-6b46-4497-9a0c-1b0f2b6ab8fc
caps.latest.revision: 47
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 5fd4d415e452549e80aa12b9eb1397bf83ce6557
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="report-server-web-service"></a>веб-служба сервера отчетов
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] предоставляет доступ ко всем функциям сервера отчетов через сервер веб-службы отчетов. Веб-службой сервера отчетов является веб-служба XML с API-интерфейсом протокола SOAP. Она применяет протокол SOAP через протокол HTTP и действует как интерфейс связи между клиентскими программами и сервером отчетов. Веб-служба предоставляет две конечные точки — одну для выполнения отчета, а другую для управления отчетом — при помощи методов, которые предоставляют функциональные возможности сервера отчетов и дают возможность создавать пользовательские средства для любого периода жизненного цикла отчетов.  
  
 Существует три основных способа разработки [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] приложений на основе веб-службы. Возможные действия:  
  
-   Разработка приложений с помощью [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] и [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK. Дополнительные сведения об использовании [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] для построения приложений веб-служб, в разделе [построение приложений с помощью веб-службы и .NET Framework](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md).  
  
-   Разработка приложений с помощью **rs** программа (RS.exe) [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] среду скриптов. С [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] сценариев, можно запустить любую операций отчетов сервера веб-службы. Дополнительные сведения о сценариях в [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], в разделе [создать скрипт rs.exe, программы и веб-службы](../../reporting-services/tools/script-with-the-rs-exe-utility-and-the-web-service.md).  
  
-   Разрабатывать приложения с использованием любого набора средств разработки с поддержкой протокола SOAP. Дополнительные сведения см. в разделе [The Role of SOAP в службах Reporting Services](../../reporting-services/report-server-web-service/the-role-of-soap-in-reporting-services.md).  
  
## <a name="programming-diagram"></a>Диаграмма программирования  
 ![Параметры разработки отчетов веб-сервера службы](../../reporting-services/report-server-web-service/media/reportserviceswebserviceprog-01.gif "Report Server Web service development options")  
Доступные способы разработки веб-службы для служб Reporting Services  
  
## <a name="in-this-section"></a>В этом разделе  
 [Методы веб-службы для сервера отчетов](../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)  
 Описывает функции и методы каждой веб-службы сервера отчетов.  
  
 [Роль протокола SOAP в службах Reporting Services](../../reporting-services/report-server-web-service/the-role-of-soap-in-reporting-services.md)  
 Предоставляет общие сведения о протоколе SOAP, дает описание его использования в веб-службах сервера отчетов.  
  
 [Доступ к API-Интерфейс SOAP](../../reporting-services/report-server-web-service/accessing-the-soap-api.md)  
 Описывает язык WSDL и предоставляет URL-адреса для доступа к файлу WSDL служб Reporting Services.  
  
 [Создание приложений с помощью веб-службы и .NET Framework](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
 Содержит сведения о разработке приложений и веб-служб, которые вызывают API-интерфейс протокола SOAP служб Reporting Services.  
  
 [Сценарий с служебную программу rs.exe и веб-службы](../../reporting-services/tools/script-with-the-rs-exe-utility-and-the-web-service.md)  
 Содержит общие сведения о среде исполнения сценариев служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Технический справочник (службы SSRS)](../../reporting-services/technical-reference-ssrs.md)  
 Содержит справочные материалы по методам веб-служб сервера отчетов и по соответствующим сложным типам.  
  
## <a name="user-requirements-for-web-service-development"></a>Требования к пользователям для разработки с использованием веб-службы  
 Для разработки приложений с использованием веб-службы сервера отчетов необходимо следующее.  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)]Internet Explorer 5.5 или более поздней версии, установленный на компьютере с подключение к Интернету и доступ к серверу отчетов.  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] или [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK, установленных на компьютере, если вы хотите создавать и развертывать [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] приложений с помощью [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
-   Углубленное понимание [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] функций и возможностей.  
  
-   Глубокое понимание протокола SOAP и служб [!INCLUDE[vstecwebservices](../../includes/vstecwebservices-md.md)].  
  
-   Процесс разработки в [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-совместимый язык, такой как [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] или [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], если вы планируете использовать [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] как платформу разработки.  
  
## <a name="see-also"></a>См. также:  
 [Веб-службы сервера отчетов](../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  

