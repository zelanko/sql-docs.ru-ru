---
title: Введение в обработку исключений в службах Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: report-server-web-service-net-framework-exception-handling
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Web service [Reporting Services], exception handling
- errors [Reporting Services]
- exceptions [Reporting Services]
- Report Server Web service, exception handling
- XML Web service [Reporting Services], exception handling
ms.assetid: 54381870-ce67-482b-aa83-6a838cdbf9b9
caps.latest.revision: 29
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 589a7350778afea966db0ce7754ad196ed28fc5f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33024271"
---
# <a name="introducing-exception-handling-in-reporting-services"></a>Знакомство с обработкой исключений в службах Reporting Services
  Если приложение службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] направляет веб-службе сервера отчетов запрос, который эта служба не в состоянии обработать, служба возвращает клиенту исключение SOAP. Обработка исключений, формируемых веб-службой сервера отчетов, играет важную роль в создаваемых разработчиками приложениях, поскольку при возникновении ошибок приложения могут возвращать пользователям важные сведения.  
  
 В этом разделе содержатся конкретные данные, касающиеся обработки исключений, предотвращения ввода пользователями недопустимых значений и возврата пользователям значимых сведений об ошибках. Общие сведения об обработке исключений см. в разделе "Обработка и активизация исключений" документации пакета SDK [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Обработка исключений в службах Reporting Services](../../reporting-services/report-server-web-service-net-framework-exception-handling/handling-exceptions-in-reporting-services.md)|Содержит общие сведения об исключениях в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и о роли SOAP в возврате ошибок веб-служб.|  
|[Рекомендации по обработке исключений в службах Reporting Services](../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/best-practices-for-reporting-services-exception-handling.md)|Содержит рекомендации по обработке исключений в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
|[Класс SoapException в службах Reporting Services](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)|Описывает класс **SoapException** в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью веб-службы и .NET Framework](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
