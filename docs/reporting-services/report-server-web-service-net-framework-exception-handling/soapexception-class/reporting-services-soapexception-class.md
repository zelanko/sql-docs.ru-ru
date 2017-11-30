---
title: "Класс SoapException в службах Reporting Services | Документы Майкрософт"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- exceptions [Reporting Services], SoapException class
- SoapException class
ms.assetid: 2cec49ee-20b1-40eb-a75b-0908d9c05b34
caps.latest.revision: "33"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 18fc1caebfceff356a28bfdfdf91d402d2bd6180
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="reporting-services-soapexception-class"></a>Класс SoapException в службах Reporting Services
  Следует устранять конкретные ошибки службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], в отношении которых известно, что они могут возникнуть. Например, если в приложении пользователю передается запрос, согласно которому он должен создать папку, то может оказаться, что пользователь попытается создать уже существующую папку. Разработчик не может управлять тем, какие значения введет пользователь в полях с именем папки и обозначением пути, предусмотренных в приложении, но имеет возможность показать пользователю отрицательные результаты случайной попытки создать объект, который уже существует.  
  
 Чтобы упростить определение конкретных условий ошибки, службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] классифицируют код ошибки, относящейся к конкретному исключению, и возвращают результаты классификации ошибки с использованием свойств класса **SoapException**. Дополнительные сведения см. в разделе "Класс SoapException" в документации по пакету SDK для [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
 В представленной ниже таблице приведен список открытых свойств класса **SoapException**.  
  
|Открытое свойство|Description|  
|---------------------|-----------------|  
|**Actor**|Код, который вызвал исключение. Это значение представляет собой URL-адрес метода веб-службы.|  
|**Detail**|Сведения об ошибках, определяемые приложением. Значение задается сервером отчетов и имеет формат XML. Дополнительные сведения см. в разделах [Свойство Detail](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/detail-property.md) и [Использование свойства Detail для обработки определенных ошибок](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md).|  
|**HelpLink**|URL-адрес или URN файла справки, связанного с ошибкой. Обычно это значение задается веб-службой, которая определяет URL-адрес для справки и поддержки [!INCLUDE[msCoName](../../../includes/msconame-md.md)]. Службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] предоставляют возможность задавать несколько ссылок на разделы справки, посвященные возникающим ошибкам, поэтому сведения о ссылке на справку на сервере отчетов определяются в свойстве **Detail**. Дополнительные сведения см. в разделе [Элемент HelpLink](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/helplink-element.md).|  
|**Сообщение**|Содержательное, локализованное сообщение с описанием ошибки. Этот текст может отображаться в пользовательском интерфейсе приложения.|  
  
## <a name="see-also"></a>См. также:  
 [Введение в обработку исключений в службах Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Таблица ошибок SoapException](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/soapexception-errors-table.md)  
  
  
