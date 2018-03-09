---
title: "Свойство Detail | Документы Майкрософт"
ms.custom: 
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: report-server-web-service-net-framework-exception-handling
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- Detail property
- SoapException class
ms.assetid: c1ddaeb6-c540-49fa-b06e-b6359d377ee8
caps.latest.revision: "33"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9178a7767e95d39ff380fd79fc72964571a5ddbb
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="detail-property"></a>Свойство Detail
  Свойство **Detail** класса [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]SoapException **служб**  имеет следующую структуру XML:  
  
## <a name="elements"></a>Элементы  
 **Detail**  
 Элемент верхнего уровня, содержащий все остальные элементы данных об ошибке.  
  
 **ErrorCode**  
 Код ошибки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 **HttpStatus**  
 Код состояния HTTP.  
  
 **Сообщение**  
 Сообщение об ошибке и код ошибки, присвоенный сервером отчетов.  
  
 **HelpLink**  
 URL-адрес справочной ссылки на веб-сайт, где находятся дополнительные сведения об ошибке. Дополнительные сведения см. в разделе [Элемент HelpLink](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/helplink-element.md).  
  
 **LinkID**  
 Идентификатор, присвоенный ссылке.  
  
 **ProductName**  
 Имя продукта. Значение по умолчанию — **Microsoft SQL Server Reporting Services**.  
  
 **ProductVersion**  
 Версия служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Максимальная длина составляет 15 символов. Номер версии должен иметь следующий формат: 8.00.0xxx.00.  
  
 **ProductLocaleId**  
 Идентификатор локали или идентификатор языка библиотеки INTL приложения (например, 0x41A).  
  
 **OperatingSystem**  
 Операционная система, в которой установлены службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Допустимыми являются значение **0** (независимость от операционной системы), значение **1** ([!INCLUDE[win2kfamily](../../../includes/win2kfamily-md.md)]) и значение **16** (Windows XP).  
  
 **CountryLocaleId**  
 Идентификатор локали или идентификатор языка операционной системы. Например, для французской версии Windows используется значение 0x040c.  
  
 **MoreInformation**  
 XML-строка, содержащая вложенные исключения, сформированные во время выполнения метода.  
  
 **Source**  
 Дочерний элемент для элемента **MoreInformation**. Источник ошибки.  
  
 **Сообщение**  
 Дочерний элемент для элемента **MoreInformation**. Сообщение ошибки для вложенного исключения. Этот элемент включает XML-атрибуты для элементов **ErrorCode** и **HelpLink**.  
  
 **Предупреждения**  
 XML-строка, содержащая предупреждения, возвращенные при обработке отчета.  
  
## <a name="see-also"></a>См. также:  
 [Введение в обработку исключений в службах Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Класс SoapException в службах Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)   
 [Использование свойства Detail для обработки определенных ошибок](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  
