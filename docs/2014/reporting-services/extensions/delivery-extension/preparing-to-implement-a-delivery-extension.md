---
title: Подготовка к реализации модуля доставки | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- interfaces [Reporting Services]
- delivery extensions [Reporting Services], implementing
ms.assetid: aee1608d-374f-4ad3-bc23-fe07fdaa52b7
caps.latest.revision: 33
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 1f03d017d7e154a77baa1da47905c8badf256bbb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087557"
---
# <a name="preparing-to-implement-a-delivery-extension"></a>Подготовка к реализации модуля доставки
  Перед реализацией модуля доставки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] следует определить реализуемые интерфейсы. Вначале необходимо решить, как будет использоваться модуль доставки, какие параметры будут необходимы для модуля и какие функции будет необходимо реализовать для доставки уведомлений об отчетах.  
  
 Каждый модуль доставки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] должен предоставлять следующие возможности:  
  
-   реализацию интерфейса <xref:Microsoft.ReportingServices.Interfaces.IExtension>, который представляет модуль и локализованное имя модуля;  
  
-   реализацию интерфейса <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>, который создает модуль доставки, используемый для доставки пользователям уведомлений об отчетах;  
  
-   возможность обработки пользовательских данных для подписки.  
  
 Каждый модуль доставки можно улучшить, добавив следующие возможности:  
  
-   реализацию пользовательского элемента управления [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], которая дает пользователям возможность использовать диспетчер отчетов для создания подписок на отчеты, использующих модуль доставки.  
  
 В следующей таблице описаны доступные интерфейсы и классы для модулей доставки.  
  
|Интерфейс или класс|Описание|  
|------------------------|-----------------|  
|<xref:Microsoft.ReportingServices.Interfaces.IExtension> Интерфейс|Представляет модуль в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> Интерфейс|Представляет модуль доставки в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|<xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> Интерфейс|Содержит сведения о сервере отчетов, которые необходимы модулям доставки (например, список доступных модулей подготовки отчетов).|  
|Класс <xref:Microsoft.ReportingServices.Interfaces.Setting>|Представляет параметр модуля.|  
|Класс <xref:Microsoft.ReportingServices.Interfaces.Notification>|Содержит сведения о подписке, используемые модулями доставки для доставки отчетов.|  
|Класс <xref:Microsoft.ReportingServices.Interfaces.Report>|Представляет сведения об отчете и методы, которые позволяют модулям доставки доставлять пользователям отчеты.|  
|Класс <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>|Представляет выходной файл модуля подготовки отчетов. Объект <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> содержит имя связанного файла и сведения о типе, необходимые модулю доставки для обработки потока, возвращаемого модулем подготовки отчетов.|  
|<xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> Интерфейс|Пользовательский элемент управления, служащий средством получения данных о подписке, относящихся к модулю доставки, от пользователя в диспетчере отчетов (например, адрес электронной почты или путь в общую папку).|  
  
## <a name="see-also"></a>См. также  
 [Модули служб Reporting Services](../reporting-services-extensions.md)   
 [Реализация модуля доставки](implementing-a-delivery-extension.md)   
 [Библиотека модулей Reporting Services](../reporting-services-extension-library.md)  
  
  