---
title: Создание детализированного (RDLC) отчета с параметрами с помощью ReportViewer (учебник по службам SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 628c8775-c62d-45ac-b349-23db86fa4e6c
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 0147922c6b52d83cde9dc9a3724e82a5e4f30a3a
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40394554"
---
# <a name="create-a-drillthrough-rdlc-report-with-parameters-using-reportviewer-ssrs-tutorial"></a>Создание детализированного (RDLC) отчета с параметрами с помощью ReportViewer (учебник SSRS)
  [Детализированный](http://technet.microsoft.com/library/ff519554.aspx) отчет — это отчет, открываемый пользователем щелчком по ссылке в другом отчете. Обычно детализированный отчет содержит подробности об элементе, содержащемся в исходном сводном отчете. Этот учебник содержит следующие занятия по созданию детализированного отчета с параметрами и запросом, в [локального режима отчетности](local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md).  
  
## <a name="requirements"></a>Требования  
 Чтобы использовать в этом пошаговом руководстве, необходимо иметь доступ к **AdventureWorks2008** образца базы данных. Запрос, используемый в этом пошаговом руководстве также будут работать с **AdventureWorks2012** базы данных. Дополнительные сведения о том, как получить **AdventureWorks2008** образца базы данных, см. в разделе [Пошаговое руководство: Установка базы данных AdventureWorks](http://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx) для Microsoft Visual Studio 2010.  
  
 В этом пошаговом руководстве предполагается, что вы знакомы с запросами Transact-SQL и ADO.NET [набора данных](http://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) и [DataTable](http://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) объектов.  
  
 Использование Visual Studio 2010 или Visual Studio 2012 и шаблона веб-сайта ASP.NET для создания веб-страницы ASP.NET с элементом управления ReportViewer. Этот элемент управления настраивается для просмотра созданного отчета. По условиям данного пошагового руководства приложение создается на Microsoft Visual C#.  
  
## <a name="tasks"></a>Задания  
 [Занятие 1: Создание нового веб-сайта](../reporting-services/lesson-1-create-a-new-web-site.md)   
 [Занятие 2: Определение подключения к данным и таблицы данных для родительского отчета](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md)   
 [Занятие 3: Проектирование родительского отчета с помощью мастера отчетов](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md)   
 [Занятие 4: Определение подключения к данным и таблицы данных для дочернего отчета](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md)   
 [Занятие 5: Проектирование родительского отчета с помощью мастера отчетов](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md)   
 [Занятие 6: Добавление элемента управления ReportViewer в приложение](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md)   
 [Занятие 7: Добавление операции детализации к родительскому отчету](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md)   
 [Занятие 8: Создание фильтра данных](../reporting-services/lesson-8-create-a-data-filter.md)   
 [Урок 9. Сборка и запуск приложения](../reporting-services/lesson-9-build-and-run-the-application.md)  
  
## <a name="see-also"></a>См. также  
 [Учебники по службам Reporting Services &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md)   
 [Разработка отчетов с использованием конструктора отчетов (SSRS)](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
