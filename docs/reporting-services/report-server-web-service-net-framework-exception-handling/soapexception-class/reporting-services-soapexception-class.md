---
title: Класс SoapException в службах Reporting Services | Документы Майкрософт
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service-net-framework-exception-handling
ms.suite: pro-bi
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- exceptions [Reporting Services], SoapException class
- SoapException class
ms.assetid: 2cec49ee-20b1-40eb-a75b-0908d9c05b34
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1d2039bed34ded12a15db1b6b8192c915a99fb3d
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2018
ms.locfileid: "43275315"
---
# <a name="reporting-services-soapexception-class"></a>Класс SoapException в службах Reporting Services
  Следует устранять конкретные ошибки службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], в отношении которых известно, что они могут возникнуть. Например, если в приложении пользователю передается запрос, согласно которому он должен создать папку, то может оказаться, что пользователь попытается создать уже существующую папку. Разработчик не может управлять тем, какие значения введет пользователь в полях с именем папки и обозначением пути, предусмотренных в приложении, но имеет возможность показать пользователю отрицательные результаты случайной попытки создать объект, который уже существует.  
  
 Чтобы упростить определение конкретных условий ошибки, службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] классифицируют код ошибки, относящейся к конкретному исключению, и возвращают результаты классификации ошибки с использованием свойств класса **SoapException**. Дополнительные сведения см. в разделе "Класс SoapException" в документации по пакету SDK для [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
 В представленной ниже таблице приведен список открытых свойств класса **SoapException**.  
  
|Открытое свойство|Описание|  
|---------------------|-----------------|  
|**Actor**|Код, который вызвал исключение. Это значение представляет собой URL-адрес метода веб-службы.|  
|**Detail**|Сведения об ошибках, определяемые приложением. Значение задается сервером отчетов и имеет формат XML. Дополнительные сведения см. в разделах [Свойство Detail](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/detail-property.md) и [Использование свойства Detail для обработки определенных ошибок](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md).|  
|**HelpLink**|URL-адрес или URN файла справки, связанного с ошибкой. Обычно это значение задается веб-службой, которая определяет URL-адрес для справки и поддержки [!INCLUDE[msCoName](../../../includes/msconame-md.md)]. Службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] предоставляют возможность задавать несколько ссылок на разделы справки, посвященные возникающим ошибкам, поэтому сведения о ссылке на справку на сервере отчетов определяются в свойстве **Detail**. Дополнительные сведения см. в разделе [Элемент HelpLink](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/helplink-element.md).|  
|**Сообщение**|Содержательное, локализованное сообщение с описанием ошибки. Этот текст может отображаться в пользовательском интерфейсе приложения.|  
  
## <a name="see-also"></a>См. также:  
 [Введение в обработку исключений в службах Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Таблица ошибок SoapException](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/soapexception-errors-table.md)  
  
  
