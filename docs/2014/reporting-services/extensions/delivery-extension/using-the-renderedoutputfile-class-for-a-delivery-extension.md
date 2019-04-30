---
title: Использование класса RenderedOutputFile для модуля доставки | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- RenderedOutputFile class
- data streams [Reporting Services]
- delivery extensions [Reporting Services], data streams
ms.assetid: 8b591801-42d5-49fa-b710-bf7e6917accf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1dcbf250a367326e5cad528384e533a9ac9d945b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63180620"
---
# <a name="using-the-renderedoutputfile-class-for-a-delivery-extension"></a>Использование класса RenderedOutputFile для модуля доставки
  Класс <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> представляет поток данных и сведения о свойствах, связанных с ним. Свойство **Data** класса <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> используется для представления подготовленного отчета или ресурса отчета в качестве объекта **Stream**.  
  
 Метод <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> объекта **Report** возвращает массив из одного или нескольких объектов <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>, которые вместе составляют единый подготовленный отчет. Первым объектом <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> является отчет, готовый для просмотра. Все другие объекты <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> представляют ресурсы, которые необходимо доставить вместе с данными отчета (например, HTML-файл и связанные изображения). Однопоточные модули подготовки отчетов (IMAGE, PDF, MHTML и EXCEL) возвращают только один объект <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> в массиве.  
  
 Пример использования класса <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> см. в разделе [Образцы продуктов служб SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>См. также  
 [Реализация модуля доставки](implementing-a-delivery-extension.md)   
 [Библиотека модулей Reporting Services](../reporting-services-extension-library.md)  
  
  
