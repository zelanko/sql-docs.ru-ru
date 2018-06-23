---
title: Создание отчета о детализации (RDLC) с параметрами с помощью ReportViewer (учебник по службам SSRS) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 628c8775-c62d-45ac-b349-23db86fa4e6c
caps.latest.revision: 8
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 2124efb2b773f76b6d117d9163b159affb79ffac
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189713"
---
# <a name="create-a-drillthrough-rdlc-report-with-parameters-using-reportviewer-ssrs-tutorial"></a>Создание детализированного (RDLC) отчета с параметрами с помощью ReportViewer (учебник SSRS)
  [Детализированный](http://technet.microsoft.com/library/ff519554.aspx) отчет — это отчет, открываемый пользователем щелчком по ссылке в другом отчете. Обычно детализированный отчет содержит подробности об элементе, содержащемся в исходном сводном отчете. Этот учебник содержит следующие занятия по созданию детализированного отчета с параметрами и запросом в [локальном режиме составления отчетов](http://msdn.microsoft.com/library/ff487969.aspx).  
  
## <a name="requirements"></a>Требования  
 Для использования этого пошагового руководства, необходимо иметь доступ к **AdventureWorks2008** образца базы данных. Запрос, используемый в этом пошаговом руководстве также будет работать с **AdventureWorks2012** базы данных. Дополнительные сведения о том, как получить **AdventureWorks2008** образца базы данных см. в разделе [Пошаговое руководство: Установка базы данных AdventureWorks](http://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx) для Microsoft Visual Studio 2010.  
  
 В этом пошаговом руководстве предполагается, что вы знакомы с запросами Transact-SQL и ADO.NET [DataSet](http://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) и [DataTable](http://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) объектов.  
  
 Использование Visual Studio 2010 или Visual Studio 2012 и шаблона веб-сайта ASP.NET для создания веб-страницы ASP.NET с элементом управления ReportViewer. Этот элемент управления настраивается для просмотра созданного отчета. По условиям данного пошагового руководства приложение создается на Microsoft Visual C#.  
  
## <a name="tasks"></a>Задания  
 [Урок 1: Создание нового веб-узла](../reporting-services/lesson-1-create-a-new-web-site.md)   
 [Занятие 2: Определение подключения к данным и таблицы данных для родительского отчета](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md)   
 [Занятие 3: Проектирование родительского отчета с помощью мастера отчетов](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md)   
 [Урок 4: Определение подключения к данным и таблицы данных для дочернего отчета](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md)   
 [Занятие 5: Проектирование дочернего отчета с помощью мастера отчетов](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md)   
 [Урок 6: Добавление элемента управления ReportViewer в приложение](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md)   
 [Занятие 7: Добавление действия детализации к родительскому отчету](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md)   
 [Занятие 8: Создание фильтра данных](../reporting-services/lesson-8-create-a-data-filter.md)   
 [Урок 9. Сборка и запуск приложения](../reporting-services/lesson-9-build-and-run-the-application.md)  
  
## <a name="see-also"></a>См. также  
 [Учебники по службам Reporting Services &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md)   
 [Разработка отчетов с использованием конструктора отчетов (SSRS)](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  