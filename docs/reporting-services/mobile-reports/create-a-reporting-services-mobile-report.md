---
title: Создание мобильных отчетов служб Reporting Services | Документы Майкрософт
ms.date: 03/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: e84dc855-aede-4fb4-b721-e6d8787961f4
author: markingmyname
ms.author: maghan
ms.openlocfilehash: d3e35d889db2cbfa8eaead8f1f0e9a2015e007b5
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56295210"
---
# <a name="create-a-reporting-services-mobile-report"></a>Создание мобильных отчетов служб Reporting Services
С помощью издателя мобильных отчетов для Microsoft SQL Server в рабочей области конструирования с настраиваемыми строками и столбцами сетки, а также гибкими элементами мобильных отчетов можно быстро создавать мобильные отчеты SQL Server Reporting Services, которые масштабируются в соответствии с любым размером экрана.  
  
Прежде чем начать создание мобильного отчета впервые, можно установить издатель мобильных отчетов для SQL Server на локальном компьютере с веб-портала служб Reporting Services. Его также можно установить из [Центра загрузки Майкрософт](https://go.microsoft.com/fwlink/?LinkID=733527). Впоследствии вы сможете начинать работу и на веб-портале, и локально.   
    
1. На верхней панели веб-портала Reporting Services выберите **Создать** > **Мобильный отчет**.  
  
   ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png)  
     
2. На вкладке **Макет** в издателе мобильных отчетов выберите значок навигатора, датчика, диаграммы, карты или сетки данных и перетащите его в бланк.  
  
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
  
   Чтобы сохранить отчет на сервере, требуется доступ к серверу отчетов служб SQL Server Reporting Services.  
     
   ### <a name="see-also"></a>См. также раздел  
     
-   [Создание и публикация мобильных отчетов с помощью издателя мобильных отчетов SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
-   [Создание макета мобильного отчета служб Reporting Services для телефона или планшета](../../reporting-services/mobile-reports/lay-out-a-reporting-services-mobile-report-for-phone-or-tablet.md)  
  
   
