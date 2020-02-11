---
title: Веб-служба сервера отчетов | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SSIS, Web service
- Web service [Reporting Services]
- Reporting Services, extending
- SQL Server Reporting Services, Web service
- Reporting Services, Web service
- XML Web service [Reporting Services]
- Report Server Web service
ms.assetid: 16c21dec-6b46-4497-9a0c-1b0f2b6ab8fc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b577fd9a78dbb5f12af79e190709065931ec463a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62520572"
---
# <a name="report-server-web-service"></a>веб-служба сервера отчетов
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] предоставляет доступ ко всем функциональным возможностям сервера отчетов через веб-службу сервера отчетов. Веб-службой сервера отчетов является веб-служба XML с API-интерфейсом протокола SOAP. Она применяет протокол SOAP через протокол HTTP и действует как интерфейс связи между клиентскими программами и сервером отчетов. Веб-служба предоставляет две конечные точки — одну для выполнения отчета, а другую для управления отчетом — при помощи методов, которые предоставляют функциональные возможности сервера отчетов и дают возможность создавать пользовательские средства для любого периода жизненного цикла отчетов.  
  
 Имеются три основных способа разработки приложений служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на основе веб-службы. Вы можете:  
  
-   Разрабатывайте приложения [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] с помощью [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] и пакета SDK. Дополнительные сведения об использовании платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] для построения приложений веб-службы, см. в разделе [Building Applications Using the Web Service and the .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md).  
  
-   Разрабатывать приложения с использованием программы **rs** (RS.exe), среды исполнения скриптов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Скрипты служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] можно использовать для запуска любых операций веб-службы сервера отчетов. Дополнительные сведения о написании скриптов в [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] см. в разделе [Создание скриптов с помощью программы rs.exe и веб-службы](../tools/script-with-the-rs-exe-utility-and-the-web-service.md).  
  
-   Разрабатывать приложения с использованием любого набора средств разработки с поддержкой протокола SOAP. Дополнительные сведения см. в разделе [Роль протокола SOAP в службах Reporting Services](../report-server-web-service/the-role-of-soap-in-reporting-services.md).  
  
## <a name="programming-diagram"></a>Диаграмма программирования  
 ![Параметры веб-службы сервера отчетов](../../../2014/reporting-services/media/reportserviceswebserviceprog-01.gif "Параметры веб-службы сервера отчетов")  
Доступные способы разработки веб-службы для служб Reporting Services  
  
## <a name="in-this-section"></a>в этом разделе  
 [Методы веб-службы сервера отчетов](../report-server-web-service/methods/report-server-web-service-methods.md)  
 Описывает функции и методы каждой веб-службы сервера отчетов.  
  
 [The Role of SOAP in Reporting Services](../report-server-web-service/the-role-of-soap-in-reporting-services.md)  
 Предоставляет общие сведения о протоколе SOAP, дает описание его использования в веб-службах сервера отчетов.  
  
 [Доступ к API-интерфейсу SOAP](../report-server-web-service/accessing-the-soap-api.md)  
 Описывает язык WSDL и предоставляет URL-адреса для доступа к файлу WSDL служб Reporting Services.  
  
 [Создание приложений с помощью веб-службы и .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
 Содержит сведения о разработке приложений и веб-служб, которые вызывают API-интерфейс протокола SOAP служб Reporting Services.  
  
 [Создание скриптов с помощью программы rs.exe и веб-службы](../tools/script-with-the-rs-exe-utility-and-the-web-service.md)  
 Содержит общие сведения о среде исполнения сценариев служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 [Технический справочник (службы SSRS)](../../../2014/reporting-services/technical-reference-ssrs.md)  
 Содержит справочные материалы по методам веб-служб сервера отчетов и по соответствующим сложным типам.  
  
## <a name="user-requirements-for-web-service-development"></a>Требования к пользователям для разработки с использованием веб-службы  
 Для разработки приложений с использованием веб-службы сервера отчетов необходимо следующее.  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)]Internet Explorer 5,5 или более поздней версии, установленные на компьютере с подключением к Интернету и доступом к серверу отчетов.  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] или пакет SDK, установленный на компьютере, если требуется разрабатывать и развертывать приложения с помощью [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
-   Глубокое понимание функций и возможностей служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
-   Глубокое понимание протокола SOAP и служб [!INCLUDE[vstecwebservices](../../includes/vstecwebservices-md.md)].  
  
-   Опыт разработки на [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]совместимом языке, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] например [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]или, если вы планируете использовать в [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] качестве платформы разработки.  
  
## <a name="see-also"></a>См. также:  
 [Веб-службы сервера отчетов](../report-server-web-service/report-server-web-service.md)  
  
  
