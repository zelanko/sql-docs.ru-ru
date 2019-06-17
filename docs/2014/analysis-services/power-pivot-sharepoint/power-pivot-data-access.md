---
title: Доступ к данным PowerPivot | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 83dc82da-91fb-4e47-91a8-0e0db67339b8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 97f5d2045601f72c3536fbf2d4e469eb5eb20fbe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66071244"
---
# <a name="powerpivot-data-access"></a>Доступ к данным PowerPivot
  Данный раздел описывает способы, с помощью которых данные извлекаются из книги PowerPivot, опубликованной в библиотеке SharePoint.  
  
 Данные PowerPivot хранятся в книге Excel. Строка подключения — это URL-адрес книги на сайте SharePoint.  
  
 Данные PowerPivot чаще всего используются книгой, в которой они содержатся, в качестве данных сводных таблиц и диаграмм. Также данные PowerPivot могут быть использованы в качестве внешнего источника данных, когда книга, панель или отчет подключается к отдельному XLSX-файлу Excel на SharePoint и получает данные для последующего использования. Клиентские средства, которые обычно используют данные PowerPivot, — это Excel, [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], другие отчеты служб Reporting Services и PerformancePoint.  
  
 На рабочем столе надстройка PowerPivot использует объекты AMO и ADOMD.NET для создания, обработки и отправки запросов данных PowerPivot в клиентской рабочей области.  
  
 На ферме SharePoint службы Excel используют локальный поставщик MSOLAP OLE DB для подключения к данным PowerPivot. Поставщик отправляет запрос соединения к PowerPivot для SharePoint на ферме. Сервер загружает данные, выполняет запрос и возвращает результирующий набор.  
  
##  <a name="queryproc"></a> Запрос данных PowerPivot в SharePoint  
 При просмотре книги PowerPivot из библиотеки SharePoint данные PowerPivot, содержащиеся в книге, обнаруживаются, извлекаются и обрабатываются отдельными экземплярами сервера служб Analysis Services в ферме, пока службы Excel подготавливают слой представления. Полностью обработанную книгу можно просмотреть в окне браузера или в приложении для настольных компьютеров Excel 2010, имеющем надстройку PowerPivot.  
  
 Следующая диаграмма иллюстрирует путь обработки запроса в ферме. Поскольку данные PowerPivot входят в состав книги Excel 2010, обработка запроса осуществляется при открытии книги Excel из библиотеки SharePoint и обращении к компонентам PivotTable или PivotChart, содержащим данные PowerPivot.  
  
 ![GMNI_DataProcReq](../media/gmni-dataprocreq.gif "GMNI_DataProcReq")  
  
 Компоненты служб Excel и PowerPivot для SharePoint обрабатывают различные фрагменты одного и того же XLSX-файла книги. Службы Excel обнаруживают данные PowerPivot и запрашивают обработку на сервере PowerPivot в ферме. Сервер PowerPivot выделяет запрос к экземпляру [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] , который извлекает данные из книги в библиотеке содержимого и загружает их. Данные, сохраненные в памяти, присоединяются к подготовленной книге и передаются обратно в веб-службу доступа Excel для отображения в окне браузера.  
  
 Не все данные в книге PowerPivot обрабатываются компонентом PowerPivot для SharePoint. Службы Excel обрабатывают данные таблиц и ячеек листа. PowerPivot для SharePoint обрабатывает только сводные таблицы, диаграммы и срезы, связанные с данными PowerPivot.  
  
## <a name="see-also"></a>См. также  
 [Подключение к службам Analysis Services](../instances/connect-to-analysis-services.md)   
 [Доступ к данным табличной модели](../tabular-models/tabular-model-data-access.md)  
  
  
