---
title: Создание детализированного (RDLC) отчета с параметрами с помощью ReportViewer (учебник по службам SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 628c8775-c62d-45ac-b349-23db86fa4e6c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7efb713b5dbf9a3f19118bb3572ccd35778aad19
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66109650"
---
# <a name="create-a-drillthrough-rdlc-report-with-parameters-using-reportviewer-ssrs-tutorial"></a>Создание детализированного (RDLC) отчета с параметрами с помощью ReportViewer (учебник SSRS)
  [Детализированный](https://technet.microsoft.com/library/ff519554.aspx) отчет — это отчет, открываемый пользователем щелчком по ссылке в другом отчете. Обычно детализированный отчет содержит подробности об элементе, содержащемся в исходном сводном отчете. Этот учебник содержит следующие занятия по созданию детализированного отчета с параметрами и запросом в [локальном режиме составления отчетов](local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md).  
  
## <a name="requirements"></a>Требования  
 Чтобы использовать это пошаговое руководство, необходимо иметь доступ к образцу базы данных **AdventureWorks2008** . Запрос, используемый в этом пошаговом руководстве, также будет работать с базой данных **AdventureWorks2012** . Дополнительные сведения о том, как получить образец базы данных **AdventureWorks2008** , см. [в разделе Пошаговое руководство. Установка базы данных AdventureWorks](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx) для Microsoft Visual Studio 2010.  
  
 Для работы с этим пошаговым руководством пользователь должен быть знаком с запросами Transact-SQL и объектами ADO.NET [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) и [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) .  
  
 Использование Visual Studio 2010 или Visual Studio 2012 и шаблона веб-сайта ASP.NET для создания веб-страницы ASP.NET с элементом управления ReportViewer. Этот элемент управления настраивается для просмотра созданного отчета. По условиям данного пошагового руководства приложение создается на Microsoft Visual C#.  
  
## <a name="tasks"></a>Задания  
 [Занятие 1. Создание нового веб-сайта](../reporting-services/lesson-1-create-a-new-web-site.md)   
 [Занятие 2. Определение подключения к данным и таблицы данных для родительского отчета](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md)   
 [Занятие 3. Проектирование родительского отчета с помощью мастера отчетов](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md)   
 [Занятие 4. Определение подключения к данным и таблицы данных для дочернего отчета](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md)   
 [Занятие 5. Проектирование дочернего отчета с помощью мастера отчетов](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md)   
 [Занятие 6. Добавление элемента управления ReportViewer в приложение](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md)   
 [Занятие 7. Добавление действия детализации в родительский отчет](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md)   
 [Занятие 8. Создание фильтра данных](../reporting-services/lesson-8-create-a-data-filter.md)   
 [Урок 9. Сборка и запуск приложения](../reporting-services/lesson-9-build-and-run-the-application.md)  
  
## <a name="see-also"></a>См. также:  
 [Reporting Services учебники &#40;службы SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md)   
 [Разработка отчетов с использованием конструктора отчетов (SSRS)](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
