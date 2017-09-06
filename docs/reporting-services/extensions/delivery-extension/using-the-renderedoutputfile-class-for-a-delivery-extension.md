---
title: "Использование класса RenderedOutputFile для модуля доставки | Документы Microsoft"
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
- RenderedOutputFile class
- data streams [Reporting Services]
- delivery extensions [Reporting Services], data streams
ms.assetid: 8b591801-42d5-49fa-b710-bf7e6917accf
caps.latest.revision: 34
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 35fa7b98c43bb20ef6df30f27ca74a5f2ada1792
ms.contentlocale: ru-ru
ms.lasthandoff: 08/12/2017

---
# <a name="using-the-renderedoutputfile-class-for-a-delivery-extension"></a>Использование класса RenderedOutputFile для модуля доставки
  Класс <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> представляет поток данных и сведения о свойствах, связанных с ним. **Данные** свойство <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> класс используется для представления подготовленного отчета или ресурса отчета в качестве **поток** объекта.  
  
 <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> Метод **отчетов** возвращает массив из одного или нескольких <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> объекты, которые вместе составляют единый подготовленный отчет. Первым объектом <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> является отчет, готовый для просмотра. Все другие объекты <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> представляют ресурсы, которые необходимо доставить вместе с данными отчета (например, HTML-файл и связанные изображения). Однопоточные модули подготовки отчетов (IMAGE, PDF, MHTML и EXCEL) возвращают только один объект <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> в массиве.  
  
 Пример использования <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> см. в описании [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>См. также:  
 [Реализация модуля доставки](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Библиотека служб Reporting Services расширения](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
