---
title: "Создание мобильных отчетов служб Reporting Services | Документы Microsoft"
ms.custom: 
ms.date: 03/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e84dc855-aede-4fb4-b721-e6d8787961f4
caps.latest.revision: 10
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 7fce4526bb296113aedb62e5dcf94b50e198210f
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="create-a-reporting-services-mobile-report"></a>Создание мобильных отчетов служб Reporting Services
SQL Server Mobile Report Publisher можно быстро создать мобильные отчеты SQL Server 2016 Reporting Services, которые масштабируются в соответствии с любой размер экрана в рабочей области конструирования с настраиваемыми строками и столбцами и сетки гибкими элементами мобильных отчетов.  
  
При первом создании мобильных отчетов SQL Server Mobile Report Publisher можно установить на локальном компьютере на веб-портале Reporting Services. Его также можно установить из [Центра загрузки Майкрософт](http://go.microsoft.com/fwlink/?LinkID=733527). Впоследствии вы сможете начинать работу и на веб-портале, и локально.   
    
1. На верхней панели веб-портале Reporting Services, выберите **New** > **мобильным отчетом**.  
  
   ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png)  
     
2. На **макета** в издателе мобильных отчетов выберите навигатора, датчика, диаграммы, карты или сетки данных и перетащите его в бланк запроса.  
  
3. Захватите правый нижний угол элемента и придайте ему необходимый размер.  
  
   ![SSMRP_ResizeChart](../../reporting-services/mobile-reports/media/ssmrp-resizechart.png)  
  
   Это **главный** бланк отчета, где можно создать элементы, которые будут содержаться в отчете. Позже можно будет [разметить отчет для планшета или телефона](../../reporting-services/mobile-reports/lay-out-a-reporting-services-mobile-report-for-phone-or-tablet.md).     
     
   В области **Visual Properties** (Визуальные свойства) под бланком приведены свойства, которые можно задать.  
     
4. Выберите вкладку **Данные** в верхнем левом углу, чтобы просмотреть смоделированные данные, связанные с этой диаграммой.   
  
   ![SSMRP_SimTable](../../reporting-services/mobile-reports/media/ssmrp-simtable.png)  
  
5. Щелкните **Add Data** (Добавить данные) в правом верхнем углу.  
  
6. Затем выберите **Local Excel** (Локальное приложение Excel) или **Report Server**(Сервер отчетов).  
  
   >**Совет**. Добавляя данные из Excel, необходимо следовать следующим требованиям:  
    >* [Подготовьте данные Excel](../../reporting-services/mobile-reports/prepare-excel-data-for-reporting-services-mobile-reports.md) , которые будут использоваться для мобильного отчета.  
    >* Сначала закройте файл.  
7. Выберите нужные листы и нажмите кнопку **Import**(Импорт).   
   Вы можете добавить несколько листов из книги одновременно.  
    
     ![SSMRP_AddExcelData](../../reporting-services/mobile-reports/media/ssmrp-addexceldata.png)  
  
8. На вкладке **Data** (Данные) в полях раздела **Data Properties** (Свойства данных) выберите таблицу и поле для диаграммы.  
  
   ![SSMRP_DataProps](../../reporting-services/mobile-reports/media/ssmrp-dataprops.png)  
  
9. На вкладке **Layout** (Макет) в полях раздела **Visual Properties** (Визуальные свойства) можно задать такие свойства, как **Title**(Название), **Time Unit**(Единицы времени) и **Number Format**(Формат чисел).  
  
   ![SSMRP_ChartVizProps](../../reporting-services/mobile-reports/media/ssmrp-chartvizprops.png)  
    
10. Чтобы просмотреть, как формируется отчет, в верхнем левом углу щелкните **Preview** (Предварительный просмотр).  
  
11. Сохраните отчет. В верхнем левом углу щелкните значок сохранения, а затем выберите **Save Locally** (Сохранить локально) или **Save to Server**(Сохранить на сервер).  
  
   Чтобы сохранить его на сервер, требуется доступ на сервере отчетов SQL Server 2016 Reporting Services.  
     
   ### <a name="see-also"></a>См. также:  
     
-   [Создание и публикация мобильных отчетов с помощью издателя мобильных отчетов SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
-   [Создание макета мобильного отчета служб Reporting Services для телефона или планшета](../../reporting-services/mobile-reports/lay-out-a-reporting-services-mobile-report-for-phone-or-tablet.md)  
  
   
