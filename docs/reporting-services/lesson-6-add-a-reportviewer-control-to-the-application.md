---
title: "Урок 6: Добавление элемента управления ReportViewer в приложение | Документы Microsoft"
ms.custom: 
ms.date: 05/18/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: f9492a97-5609-4059-ae76-0fba111d4968
caps.latest.revision: 7
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 914d8abf2ad7b72b5ce1035da2867c47b67dfa14
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="lesson-6-add-a-reportviewer-control-to-the-application"></a>Урок 6. Добавление в приложение элемента управления ReportViewer
После завершения проектирования дочернего отчета с помощью мастера отчетов далее необходимо добавить в приложение веб-сайта элемент управления ReportViewer. Если вы используете веб-сайт отчетов ASP.NET, элемент управления ReportViewer будет добавлен на страницу default.aspx.   
  
### <a name="to-add-a-reportviewer-control-to-the-application"></a>Добавление элемента управления ReportViewer в приложение  
  
1.  В **обозревателе решений**щелкните правой кнопкой мыши **Default.aspx**и выберите пункт **Конструктор представлений**.  
  
2.  Если на странице default.aspx уже есть элемент управления ReportViewer, перейдите к **шагу 4**. В противном случае из группы **Расширения AJAX** в окне **Панель элементов** перетащите элемент управления **ScriptManager** в область конструктора.  
  
3.  Из группы **Отчетность** перетащите элемент управления **ReportViewer** в область конструктора, расположив его ниже элемента управления **ScriptManager** .  
  
4.  Откройте окно **Задачи ReportViewer** , щелкнув стрелку в правом верхнем углу элемента управления **ReportViewer** .  
  
5.  В поле **Выбор отчета** выберите созданный родительский отчет.  
  
    После выбора отчета экземпляры источников данных, используемых в отчете, будут созданы автоматически. Будет сформирован код для создания экземпляра каждого объекта DataTable (и его контейнера [DataSet](http://msdn.microsoft.com/library/system.data.dataset.aspx) ). В область конструктора будут добавлены элементы управления [ObjectDataSource](http://msdn.microsoft.com/library/system.web.ui.webcontrols.objectdatasource.aspx) , соответствующие каждому источнику данных, который используется в отчете. Настройка этих элементов управления источником данных осуществляется автоматически.  
  
6.  В меню «Построение» выберите команду «Построить веб-сайт».  
  
    Отчет компилируется, и все ошибки, такие как синтаксические ошибки в выражениях отчета, появляются в области **Список ошибок** . Щелкните **Список ошибок** в нижней части окна Visual Studio, чтобы отобразить область **Список ошибок** .  
  
## <a name="next-task"></a>Следующая задача  
Тем самым в приложение веб-сайта был успешно добавлен элемент управления ReportViewer. Затем необходимо добавить операцию детализации в родительский отчет. См. [Занятие 7. Добавление операции детализации к родительскому отчету](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md).  
  


