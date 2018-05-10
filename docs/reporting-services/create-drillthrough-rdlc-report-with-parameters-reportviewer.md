---
title: Создание детализированного (RDLC) отчета с параметрами с помощью ReportViewer | Документы Майкрософт
ms.custom: ''
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: reporting-services
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 628c8775-c62d-45ac-b349-23db86fa4e6c
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: f90ac792fe849ca91735e5a9b22a399d7798cf23
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="create-drillthrough-rdlc-report-with-parameters---reportviewer"></a>Создание детализированного (RDLC) отчета с параметрами с помощью ReportViewer
[Детализированный](http://technet.microsoft.com/library/ff519554.aspx) отчет — это отчет, открываемый пользователем щелчком по ссылке в другом отчете. Обычно детализированный отчет содержит подробности об элементе, содержащемся в исходном сводном отчете. Этот учебник содержит следующие занятия по созданию детализированного отчета с параметрами и запросом в [локальном режиме составления отчетов](http://msdn.microsoft.com/library/ff487969.aspx).  
  
## <a name="requirements"></a>Требования  
Для использования этого пошагового руководства необходимо иметь доступ к образцу базы данных **AdventureWorks2014** . Дополнительные сведения о получении образца базы данных **AdventureWorks2014** см. на странице [Образцы баз данных AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases).  
  
Для работы с этим пошаговым руководством пользователь должен быть знаком с запросами Transact-SQL и объектами ADO.NET [DataSet](https://msdn.microsoft.com/library/system.data.dataset.aspx) и [DataTable](http://msdn.microsoft.com/library/system.data.datatable.aspx) .  
  
Использование Visual Studio 2015 и веб-приложения ASP.NET для создания веб-страницы ASP.NET с элементом управления ReportViewer. Этот элемент управления настраивается для просмотра созданного отчета. По условиям данного пошагового руководства приложение создается на Microsoft Visual C#.  
  
## <a name="tasks"></a>Задания  
[Урок 1. Создание нового веб-сайта](../reporting-services/lesson-1-create-a-new-web-site.md)  
[Урок 2. Определение подключения к данным и таблицы данных для родительского отчета](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md)  
[Урок 3. Проектирование родительского отчета с использованием мастера отчетов](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md)  
[Урок 4. Определение подключения к данным и таблицы данных для родительского отчета](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md)  
[Урок 5. Проектирование родительского отчета с использованием мастера отчетов](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md)  
[Урок 6. Добавление в приложение элемента управления ReportViewer](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md)  
[Урок 7. Добавление операции детализации к родительскому отчету](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md)  
[Урок 8. Создание фильтра данных](../reporting-services/lesson-8-create-a-data-filter.md)  
[Lesson 9: Build and Run the Application](../reporting-services/lesson-9-build-and-run-the-application.md)  
  
## <a name="see-also"></a>См. также:  
[Учебники по службам Reporting Services (SSRS)](../reporting-services/reporting-services-tutorials-ssrs.md)  
[Разработка отчетов с использованием конструктора отчетов (SSRS)](../reporting-services/tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  

