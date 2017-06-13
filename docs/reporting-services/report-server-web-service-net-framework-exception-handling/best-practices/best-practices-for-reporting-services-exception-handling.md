---
title: "Советы и рекомендации для служб Reporting Services обработки исключений | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
- exceptions [Reporting Services], best practices
ms.assetid: 72fecf28-f02e-4338-b50f-0b21f520302d
caps.latest.revision: 34
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: d7a1557097e118bfc47cb395dc58331ccf3e0817
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="best-practices-for-reporting-services-exception-handling"></a>Рекомендации по обработке исключений в службах Reporting Services
  При разработке приложений служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] существует несколько методик, которые можно использовать для избежания возникновения исключений или сокращения их количества. При возникновении исключений пользователю следует выводить ясное и четкое сообщение об ошибке; кроме того, следует добавить обработку исключений, чтобы приложения не завершались неожиданно.  
  
 Приложение, посылающее запросы веб-службе сервера отчетов должно выполнять следующие действия.  
  
-   Оно должно избегать вызова исключений методом предотвращения создания как можно большего количества недопустимых запросов.  
  
-   Оно должно по возможности перехватывать исключения и предоставлять определенные коды обработки ошибок.  
  
-   Оно должно обрабатывать варианты ошибок, не выдающие исключений.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Предотвращение недопустимых запросов](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/preventing-invalid-requests.md)|Описывает методики предотвращения отправки недопустимых запросов на сервер отчетов.|  
|[С помощью Try и Catch-блоки](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-try-and-catch-blocks.md)|Описывает, как можно увеличить надежность приложения с использованием блоков TRY и CATCH.|  
|[Обработка предупреждений и ситуаций, которые не вызывают исключений](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/handling-warnings-and-cases-that-do-not-cause-exceptions.md)|Объясняет, как следует обрабатывать ошибки, которые не приводят к формированию исключения службами [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Использование свойства Detail для обработки определенных ошибок](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md)|Объясняет, как можно программным образом обрабатывать определенные ошибки с помощью **сведений** свойство **SoapException** объекта.|  
  
## <a name="see-also"></a>См. также:  
 [Свойство Detail](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/detail-property.md)   
 [Введение в обработку исключений в службах Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Класс SoapException служб Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  
