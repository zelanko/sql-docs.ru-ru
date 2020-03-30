---
title: Использование класса Report в модуле доставки | Документы Майкрософт
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], report information
- Report class
ms.assetid: 1145ac63-eafd-452a-82af-16f85b1676dd
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 05196a42af159e06a2b740c5671b2892d8362453
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "63193620"
---
# <a name="using-the-report-class-for-a-delivery-extension"></a>Использование класса Report в модуле доставки
  Класс <xref:Microsoft.ReportingServices.Interfaces.Report> представляет отчет в базе данных сервера отчетов. Каждая подписка связывается с определенным отчетом. Отчет содержится в уведомлении. Модули доставки могут использовать объект <xref:Microsoft.ReportingServices.Interfaces.Report>, являющийся частью уведомления, для подготовки отчета к просмотру. Объект <xref:Microsoft.ReportingServices.Interfaces.Report> также содержит свойства, относящиеся к отчету, такие как URL-адреса отчета на сервере отчетов и имя отчета. Все эти свойства можно использовать в составе поставщика доставки.  
  
 Метод <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> класса <xref:Microsoft.ReportingServices.Interfaces.Report> используется для подготовки отчета к просмотру. Метод <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> возвращает массив из одного или нескольких объектов <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>, которые в совокупности представляют отдельный отчет, готовый для просмотра. Первым объектом <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> является отчет, готовый для просмотра. Все другие объекты <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> представляют ресурсы, которые необходимо доставить вместе с данными отчета (например, HTML-файл и связанные изображения). Однопоточные модули подготовки отчетов (IMAGE, PDF, MHTML и Excel) возвращают в массиве только один объект <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>.  
  
 В доставку можно включить объект <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>, содержащий поток отчета.  
  
 Пример использования класса <xref:Microsoft.ReportingServices.Interfaces.Report> см. в разделе [Образцы продуктов служб SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>См. также:  
 [Реализация модуля доставки](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Библиотека модулей Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)   
 [Использование класса RenderedOutputFile для модуля доставки](../../../reporting-services/extensions/delivery-extension/using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
  
  
