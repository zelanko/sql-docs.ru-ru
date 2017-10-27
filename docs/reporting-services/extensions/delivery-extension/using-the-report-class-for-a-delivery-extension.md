---
title: "Использование класса Report в модуле доставки | Документы Microsoft"
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
- delivery extensions [Reporting Services], report information
- Report class
ms.assetid: 1145ac63-eafd-452a-82af-16f85b1676dd
caps.latest.revision: 34
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 2cbf3f1a1ffeb702551a2aa0ff94134867cb1786
ms.contentlocale: ru-ru
ms.lasthandoff: 08/12/2017

---
# <a name="using-the-report-class-for-a-delivery-extension"></a>Использование класса Report в модуле доставки
  Класс <xref:Microsoft.ReportingServices.Interfaces.Report> представляет отчет в базе данных сервера отчетов. Каждая подписка связывается с определенным отчетом. Отчет содержится в уведомлении. Модули доставки могут использовать объект <xref:Microsoft.ReportingServices.Interfaces.Report>, являющийся частью уведомления, для подготовки отчета к просмотру. Объект <xref:Microsoft.ReportingServices.Interfaces.Report> также содержит свойства, относящиеся к отчету, такие как URL-адреса отчета на сервере отчетов и имя отчета. Все эти свойства можно использовать в составе поставщика доставки.  
  
 Метод <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> класса <xref:Microsoft.ReportingServices.Interfaces.Report> используется для подготовки отчета к просмотру. Метод <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> возвращает массив из одного или нескольких объектов <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>, которые в совокупности представляют отдельный отчет, готовый для просмотра. Первым объектом <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> является отчет, готовый для просмотра. Все другие объекты <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> представляют ресурсы, которые необходимо доставить вместе с данными отчета (например, HTML-файл и связанные изображения). Однопоточные модули подготовки отчетов (IMAGE, PDF, MHTML и Excel) возвращают в массиве только один объект <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>.  
  
 В доставку можно включить объект <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>, содержащий поток отчета.  
  
 Пример использования <xref:Microsoft.ReportingServices.Interfaces.Report> см. в описании [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889)  
  
## <a name="see-also"></a>См. также:  
 [Реализация модуля доставки](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Библиотека служб Reporting Services расширения](../../../reporting-services/extensions/reporting-services-extension-library.md)   
 [Использование класса RenderedOutputFile для модуля доставки](../../../reporting-services/extensions/delivery-extension/using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
  
  

