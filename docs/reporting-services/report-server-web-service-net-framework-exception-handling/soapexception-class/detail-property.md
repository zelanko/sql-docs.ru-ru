---
title: "Подробные сведения о свойстве | Документы Microsoft"
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
- Detail property
- SoapException class
ms.assetid: c1ddaeb6-c540-49fa-b06e-b6359d377ee8
caps.latest.revision: 33
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 51b99212acac0029bf246ce1668cd3a8b474fb84
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="detail-property"></a>Свойство Detail
  **Сведений** свойство [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] **SoapException** класс имеет следующую структуру XML:  
  
## <a name="elements"></a>Элементы  
 **Подробности**  
 Элемент верхнего уровня, содержащий все остальные элементы данных об ошибке.  
  
 **ErrorCode**  
 Код ошибки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 **HttpStatus**  
 Код состояния HTTP.  
  
 **Сообщение**  
 Сообщение об ошибке и код ошибки, присвоенный сервером отчетов.  
  
 **HelpLink**  
 URL-адрес справочной ссылки на веб-сайт, где находятся дополнительные сведения об ошибке. Дополнительные сведения см. в разделе [элемент HelpLink](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/helplink-element.md).  
  
 **LinkID**  
 Идентификатор, присвоенный ссылке.  
  
 **ProductName**  
 Имя продукта. Значение по умолчанию — **Microsoft SQL Server Reporting Services**.  
  
 **ProductVersion**  
 Версия служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Максимальная длина составляет 15 символов. Формат номера версии должен быть следующим: 8.00.0xxx.00.  
  
 **ProductLocaleId**  
 Идентификатор локали или идентификатор языка библиотеки INTL приложения (например, 0x41A).  
  
 **Операционная система**  
 Операционная система, в которой установлены службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Допустимые значения: **0** для операционной системы независимо, **1** для [!INCLUDE[win2kfamily](../../../includes/win2kfamily-md.md)], и **16** для Windows XP.  
  
 **CountryLocaleId**  
 Идентификатор локали или идентификатор языка операционной системы. Например, для французской версии Windows используется значение 0x040c.  
  
 **Дополнительные сведения**  
 XML-строка, содержащая вложенные исключения, сформированные во время выполнения метода.  
  
 **Source**  
 Дочерний элемент элемента **MoreInformation**. Источник ошибки.  
  
 **Сообщение**  
 Дочерний элемент элемента **MoreInformation**. Сообщение ошибки для вложенного исключения. Этот элемент включает атрибуты XML для **ErrorCode** и **HelpLink**.  
  
 **Предупреждения**  
 XML-строка, содержащая предупреждения, возвращенные при обработке отчета.  
  
## <a name="see-also"></a>См. также:  
 [Введение в обработку исключений в службах Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Класс SoapException служб Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)   
 [Использование свойства Detail для обработки определенных ошибок](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  
