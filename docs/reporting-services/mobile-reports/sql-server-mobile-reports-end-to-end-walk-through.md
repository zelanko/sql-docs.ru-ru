---
title: 'Мобильные отчеты SQL Server: руководство по использованию | Документы Майкрософт'
ms.custom: ''
ms.date: 11/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: mobile-reports
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e198575e-b154-4342-b944-2bf19ec49bfd
caps.latest.revision: 14
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 60ce71e2b7a1991b6ebf4b495907c74c1e59c939
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40175301"
---
# <a name="sql-server-mobile-reports-end-to-end-walk-through"></a>Мобильные отчеты SQL Server: руководство по использованию
Используйте пошаговые инструкции по созданию мобильных отчетов для экрана любого размера с помощью [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-long.md)] на веб-портале [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] и по просмотру отчетов в мобильных приложениях Power BI.

Мобильные отчеты можно создавать в области конструктора с настраиваемыми строками и столбцами сетки, а также гибкими элементами мобильных отчетов. Подключайтесь к различным локальным источникам данных или передавайте книги Excel для создания мобильных отчетов. Затем сохраняйте отчеты на веб-портале [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] и просматривайте их в браузере или мобильных приложениях Power BI.  
  
В этой статье рассматриваются такие вопросы:   
  
- создание общего источника данных и набора данных на веб-портале [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] с использованием базы данных AdventureWorks в качестве образца источника данных;  
- создание мобильных отчетов служб Reporting Services в средстве " [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)]";  
- публикация мобильных отчетов на веб-портале [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] ;  
- просмотр мобильных отчетов в мобильном приложении Power BI.  
  
## <a name="before-we-start"></a>Действия перед началом работы  
Для начала вам потребуются такие продукты:  
  
* Для создания источников данных и ключевых показателей эффективности, а также для публикации наборов данных и мобильных отчетов нужен доступ к [!INCLUDE[ssRSCurrent_md](../install-windows/install-reporting-services-native-mode-report-server.md).  
* [Создание общих наборов данных](../install-windows/install-report-builder.md).  
* Для создания мобильных отчетов [установите издатель мобильных отчетов для Microsoft SQL Server](http://go.microsoft.com/fwlink/?LinkId=717766).  
* [Образцы баз данных AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases).  
*  ИЛИ образец базы данных World Wide Importers, доступный на странице [Образцы Microsoft SQL Server](../../sample/microsoft-sql-server-samples.md).
* Для просмотра результата: 
  *   [зарегистрируйтесь в службе Power BI](http://go.microsoft.com/fwlink/?LinkID=513879) и
  *  [скачайте мобильное приложение Power BI](https://powerbi.microsoft.com/en-us/documentation/powerbi-power-bi-apps-for-mobile-devices/) на устройство под управлением iOS, Windows 10 или телефон с Android.  

  
## <a name="create-a-shared-data-source"></a>Создание общего источника данных  
  
Вы можете создать общий источник данных для мобильных отчетов из любого источника данных, поддерживаемого службами Reporting Services. См. [список поддерживаемых источников данных](../report-data/data-sources-supported-by-reporting-services-ssrs.md).  
  
1. На веб-портале [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] щелкните **Создать** > **Источник данных**.  
  
   ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png)  
3. Введите сведения об источнике данных и нажмите кнопку **OК**.  
  
    По умолчанию источники данных не отображаются на портале.    
   
5. Чтобы просмотреть источники данных, щелкните **Отображение** > **Источник данных**.  
  
   ![PBI_SSMRP_DisplayDataSources](../../reporting-services/mobile-reports/media/pbi-ssmrp-displaydatasources.png)  
   
6. Теперь вы видите источник данных на портале [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] .  
  
   ![PBI_SSMRP_PortlDataSource](../../reporting-services/mobile-reports/media/pbi-ssmrp-portldatasource.png)  
  
Дополнительные сведения об [общих источниках данных в службе Reporting Services](../report-data/create-modify-and-delete-shared-data-sources-ssrs.md).  
   
## <a name="shared-dataset">Создание общего набора данных</a>  
  
Для создания общего набора данных используйте существующее клиентское средство [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] , например конструктор отчетов в [!INCLUDE[ssBIDevStudioFull_md](../../includes/ssbidevstudiofull-md.md)].  В этом пошаговом руководстве используется [!INCLUDE[PRODUCT_NAME](../../includes/ssrbnoversion.md)]. [Установите построитель отчетов](../install-windows/install-report-builder.md) или запустите его на своем веб-портале. Вы создадите три набора данных: один для значения ключевого показателя эффективности, второй для тренда ключевого показателя эффективности и один с дополнительными полями для мобильного отчета служб Reporting Services.     
  
1. Чтобы запустить [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] , на веб-портале **щелкните** > **Создать** Отчет с разбивкой на страницы [!INCLUDE[PRODUCT_NAME](../../includes/ssrbnoversion.md)].  
  
   ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png)   
2. Щелкните **Создать набор данных**.  
  
   ![PBI_SSMRP_RBNewDataset](../../reporting-services/mobile-reports/media/pbi-ssmrp-rbnewdataset.png)  
   
3. Щелкните **Просмотр других источников данных**.  
   
4. В поле "Имя" введите имя сервера, на котором сохранен источник данных в таком формате:   
   
   Имя: http://*localhost*/ReportServer  
   Элементы типа: источники данных (*.rsds)  
   
5. Нажмите кнопку **Открыть**и перейдите к источнику данных, созданному на этом сервере.  
   
6. Выберите источник данных и нажмите кнопку **Открыть** еще раз.    
  
7. Создайте набор данных в [!INCLUDE[PRODUCT_NAME](../../includes/ssrbnoversion.md)].  
  
   ![PBI_SSMRP_RB_QueryDesignr600](../../reporting-services/mobile-reports/media/pbi-ssmrp-rb-querydesignr600.png)  
   
8. По завершении сохраните набор данных для сервера отчетов [!INCLUDE[PRODUCT_NAME](../../includes/ssrs.md)] .    
   
Теперь можно использовать набор данных как основу для ключевых показателей эффективности и мобильных отчетов.  Вы можете создать несколько наборов данных в одном источнике данных. Кроме того, вы можете создать несколько ключевых показателей эффективности и мобильных отчетов на основе этих общих наборов данных.   
  
## <a name="create-KPI">Создание ключевых показателей эффективности</a>  
Вы можете создавать ключевые показатели эффективности непосредственно на веб-портале [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] .    
  
1. В правом верхнем углу экрана веб-портала щелкните **Создать** > **Создать ключевой показатель эффективности**.   
  
   ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png)  
      
   В окне создания ключевых показателей эффективности можно ввести значения вручную или использовать общий набор данных.    
2. Для параметра **Значение** вместо значения **Задать вручную** установите значение **Поле набора данных**.  
   
   ![PBI_SSMRP_KPI_DatasetField](../../reporting-services/mobile-reports/media/pbi-ssmrp-kpi-datasetfield.png)  
   
3. Нажмите кнопку с многоточием (**...**) в поле **Выберите поле набора данных** и выберите набор данных, как указано в описании предыдущего шага.  
   
   ![PBI_SSMRP_KPIPickDataset](../../reporting-services/mobile-reports/media/pbi-ssmrp-kpipickdataset.png)  
   
4. Выберите поле в наборе данных.    
   
   ![PBI_SSMRP_KPIPickField](../../reporting-services/mobile-reports/media/pbi-ssmrp-kpipickfield.png)  
     
5. Выберите необходимое агрегирование. Ключевые показатели эффективности могут отображать только одно число, так что поля будут агрегированы для отображения этого числа.

   ![reporting-services-kpi-pick-aggregation](../../reporting-services/mobile-reports/media/reporting-services-kpi-pick-aggregation.png)

6. Нажмите кнопку **ОК**.

7. В поле **Набор трендов** щелкните **Тренд набора данных**.  
  
6. В поле **Выберите тренд набора данных** нажмите кнопку с многоточием (**...**).  
   
7. Выберите поле и нажмите кнопку **ОК**.  

   ![PBI_SSMRP_KPIPickTrend](../../reporting-services/mobile-reports/media/pbi-ssmrp-kpipicktrend.png)  
  
8. Присвойте имя вашему ключевому показателю эффективности и выберите тип визуализации, а затем нажмите кнопку **Создать**.   
  
   Ключевой показатель эффективности отобразится на веб-портале [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] .  
   
    ![PBI_SSMRP_NewKPI](../../reporting-services/mobile-reports/media/pbi-ssmrp-newkpi.png)  
    
## <a name="create-mobile-report">Создание мобильных отчетов Reporting Services</a>  
   
Для создания мобильных отчетов служб Reporting Services [установите издатель мобильных отчетов для Microsoft SQL Server](http://go.microsoft.com/fwlink/?LinkId=717766)или запустите его на веб-портале [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] . 

При первом открытии [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)]отобразится пустой холст, на котором можно создать мобильный отчет. Начните с создания визуальных элементов или выполните запуск с помощью ваших данных. Если сначала создать визуальные элементы, [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] автоматически создает смоделированные данные, привязанные к отчету, и динамически изменяется по мере изменения выбранных визуальных элементов. Попробуйте сделать это сами.   
  
## <a name="start-with-the-visuals"></a>Запуск при помощи визуальных элементов  
  
1. Чтобы запустить [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] , на веб-портале **щелкните** > **Создать** Мобильный отчет [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)].  
  
   ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png)

   [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] открывает сетку с разметкой образца.  
  
2. На вкладке **Макет** прокрутите экран вниз до раздела "Диаграммы".  
  
   ![PBI_SSMRP_LayoutTabCharts2](../../reporting-services/mobile-reports/media/pbi-ssmrp-layouttabcharts2.png)  
  
2. Перетащите **карту дерева** на сетку, а затем перетащите правый нижний угол таким образом, чтобы в окне отображались три столбца и три строки.  
  
   ![PBI_SSMRP_TreeMap](../../reporting-services/mobile-reports/media/pbi-ssmrp-treemap.png)  
  
3. Свойства визуальных элементов можно просмотреть в нижней части страницы. Чтобы увидеть все свойства, возможно, придется прокручивать экран в стороны.   
  
   ![PBI_SSMRP_TreeMapVisProps](../../reporting-services/mobile-reports/media/pbi-ssmrp-treemapvisprops.png)  
  
4. Выберите визуальный элемент карты дерева, а затем в левом верхнем углу откройте вкладку **Данные** .   
  
   Теперь отобразятся смоделированные поля и значения, сформированные средством " [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] ", и будет видно, каким размером и цветом они представлены на карте дерева.  
  
   ![PBI_SSMRP_TreeMapDataProps](../../reporting-services/mobile-reports/media/pbi-ssmrp-treemapdataprops.png)  
  
6. Щелкните вкладку **Макет** .  
  
7. Щелкните переключатель параметров ![PBI_SSMRP_Cog](../../reporting-services/mobile-reports/media/pbi-ssmrp-cog.png) в правом верхнем углу карты дерева, чтобы отобразить его меню.   
  
   ![PBI_SSMRP_OptionsWheel](../../reporting-services/mobile-reports/media/pbi-ssmrp-optionswheel.png)  
  
8. Щелкните стрелку посередине колесика, чтобы закрыть его.  
  
## <a name="add-your-own-data"></a>Добавьте ваши собственные данные  
  
1. Перейдите на вкладку **Данные** .    
   
2. Чтобы добавить свои данные, нажмите кнопку **Добавить данные** в правом верхнем углу, а затем перейдите к вашим данным.    
  
3. Вы можете использовать данные из локальной книги Excel, но в этом случае используются данные из общего набора данных на вашем веб-портале [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] . Отображается сообщение "Добавлен на сервере".  
  
4. Выберите сервер, а затем выберите созданный вами набор данных.  
   
3. Вернитесь на вкладку **Данные** , а затем на панели **Свойства данных** измените свойства **Представления размера**, **Представления цветов**и другие свойства полей ваших данных. 
   
   *  Поля**Представления размера**, **Представления цветов**и **Пользовательское значение центра** должны содержать цифровые значения. 
   *  В поле**Группировать по** отображается категория, поэтому это текстовое поле.
   
   ![ssrs-mobile-report-data-properties](../../reporting-services/mobile-reports/media/ssrs-mobile-report-data-properties.png)
   
6. Щелкните **Предварительный просмотр** для отображения карты дерева с вашими обновленными данными.  

## <a name="add-a-gauge-to-your-mobile-report"></a>Добавление датчика в мобильный отчет

Давайте добавим датчик для сравнения продаж нынешнего и прошлого годов при помощи одного и того же набора данных.

1. На вкладке "Макет" перетащите половину кольца на полотно. Поместите его под картой дерева и перетащите правый нижний угол так, чтобы на экране отображалось три клетки в ширину и две в высоту. 

2. И снова процесс начинается с моделирования данных. 

   Обратите внимание, что в разделе **Свойства визуальных элементов**по умолчанию указано свойство **Предпочтение более высоким значениям**, а для свойства **Разностная метка** задано значение **Процент целевого**. **Остановки диапазона** заданы по умолчанию: вы можете их изменить, но пока можно использовать и их.

   ![ssrs-mobile-report-donut-visual-properties](../../reporting-services/mobile-reports/media/ssrs-mobile-report-donut-visual-properties.png)
   
3. На вкладке **Данные** выберите таблицу с вашими данными, щелкните поле **Основное значение** и поле, с которым нужно его сравнить, в секции **Значение сравнения**.

4. Вы можете выбрать разные агрегирования, чтобы получить одно число для поля **Основное значение** и еще одно для поля **Значение сравнения**. По умолчанию эти числа — суммы.

   ![ssrs-mobile-report-donut-sum](../../reporting-services/mobile-reports/media/ssrs-mobile-report-donut-sum.png)

5. Выберите **Предварительный просмотр** , чтобы посмотреть, как это выглядит. 

   ![ssrs-mobile-report-donut-preview](../../reporting-services/mobile-reports/media/ssrs-mobile-report-donut-preview.png)

## <a name="add-a-selection-list-as-a-filter"></a>Добавление списка выбора в качестве фильтра

Списки выбора действуют как срезы в Power BI и Excel. Такой список можно добавить, чтобы фильтровать другие визуальные элементы в мобильном отчете.

1. На вкладке **Макет** перетащите список выбора в правую часть карты дерева, а затем перетащите правый нижний угол, чтобы на экране отображались две клетки в ширину и пять клеток в высоту (по высоте полотна). 

   ![ssrs-mobile-report-selection-list](../../reporting-services/mobile-reports/media/ssrs-mobile-report-selection-list.png)

2. На вкладке **Данные** в разделе **Свойства данных**задайте для элементов **Ключи** и **Метки** то поле в ваших данных, которое необходимо отфильтровать.

   ![ssrs-mobile-report-selection-list-data-properties](../../reporting-services/mobile-reports/media/ssrs-mobile-report-selection-list-data-properties.png)
   
## <a name="create-a-mobile-report-for-phones"></a>Создание мобильных отчетов для телефонов  
  
Создав визуальные элементы в разметке образца, вы можете теперь создать мобильный отчет с использованием макета, оптимизированного непосредственно для ваших пользователей телефона.    
  
1. В правом верхнем углу щелкните значок холста, а затем элемент **Телефон**.  
  
2. На вкладке "Макет" в разделе **Control Instances**(Управление экземплярами) отображаются две созданные вами диаграммы.   
  
3. Перетащите карту дерева на полотно телефона и разверните его на четыре столбца в ширину и три строки в высоту.  
  

## <a name="save-your-mobile-report"></a>Сохранение мобильного отчета  
Вы можете сохранить отчет локально или на веб-портале [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] . При локальном сохранении [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] сохраняет его с помощью кэшированных данных, чтобы можно было открыть его и продолжить работу. Однако вы не сможете просматривать его на мобильных устройствах.   
  
1. Нажмите значок сохранения в верхнем левом углу.   
   
2. Чтобы использовать его совместно с другими пользователями и просматривать на мобильных устройствах, щелкните **Сохранить на сервере**.  
  
3. На сервере перейдите к папке, в которой нужно сохранить мобильный отчет.  
  
4. Последовательно нажмите **Выбрать папку** > **Сохранить**.  
  
   Вы получите сообщение с подтверждением сохранения отчета.  
    
   После сохранения изменений можно вернуться на портал и просмотреть эскиз мобильного отчета.   
    
5. Коснитесь эскиза, чтобы просмотреть отчет на веб-портале.  
  
## <a name="view-your-report-on-the-web-portal"></a>Просмотр отчета на веб-портале

  
## <a name="view-your-report-on-a-mobile-device"></a>Просмотр отчета на мобильном устройстве   
  
Чтобы просмотреть отчет [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] , сначала необходимо:

*  [зарегистрироваться в службе Power BI](http://go.microsoft.com/fwlink/?LinkID=513879), если у вас еще нет учетной записи;
*  [скачать мобильное приложение Power BI](https://powerbi.microsoft.com/en-us/documentation/powerbi-power-bi-apps-for-mobile-devices/) на мобильное устройство.  

### <a name="view-your-mobile-report"></a>Просмотр мобильного отчета
  
1.  Откройте приложение Power BI на мобильном устройстве и войдите в него.  
    
2.  Чтобы просмотреть мобильные отчеты служб Reporting Services и ключевые показатели эффективности, щелкните **Службы Reporting Services**.  
![PBI_iPad_GetStartedSm](../../reporting-services/mobile-reports/media/pbi-ipad-getstartedsm.png)  
  
3. Коснитесь значка параметров ![PBI_iPad_OptionsIcon](../../reporting-services/mobile-reports/media/pbi-ipad-optionsicon.png) в верхнем левом углу, а затем коснитесь **Подключиться к серверу**.  
  
   ![PBI_iPad_SSMRP_ConnectCrop](../../reporting-services/mobile-reports/media/pbi-ipad-ssmrp-connectcrop.png)  
  
4. Присвойте серверу имя, а затем введите адрес сервера, ваш адрес электронной почты и пароль в следующем формате:  
  
   ![PBI_iPad_SSMRP_ConnectContoso](../../reporting-services/mobile-reports/media/pbi-ipad-ssmrp-connectcontoso.png)   
  
5.  Сервер отобразится на левой навигационной панели.  
  
    ![PBI_iPad_SSMRP_LeftNavBiggr](../../reporting-services/mobile-reports/media/pbi-ipad-ssmrp-leftnavbiggr.png)  
      
>**Совет**. Коснитесь значка параметров ![PBI_iPad_OptionsIcon](../../reporting-services/mobile-reports/media/pbi-ipad-optionsicon.png) в любое время для перехода между мобильными отчетами служб Reporting Services на веб-портале служб Reporting Services и панелями мониторинга в службе Power BI.   
  
## <a name="view-kpis-and-mobile-reports-in-the-power-bi-app"></a>Просмотр ключевых показателей эффективности (КПЭ) и мобильных отчетов в приложении Power BI  
  
Нажмите вкладку **Ключевые показатели эффективности** или **Мобильные отчеты** .   
  
![PBI_iPad_SSMRP_Portal](../../reporting-services/mobile-reports/media/pbi-ipad-ssmrp-portal.png)  
  
- Нажмите ключевой показатель эффективности, чтобы увидеть его в режиме фокусировки.  
  
    ![PBI_iPad_SSMRP_Tile](../../reporting-services/mobile-reports/media/pbi-ipad-ssmrp-tile.png)  
  
- Нажмите мобильный отчет, чтобы открыть его и поработать с ним в приложении Power BI.  
  
Ключевые показатели эффективности и мобильные отчеты отображаются в тех же папках,в которых они хранятся на веб-портале служб Reporting Services.   
  
### <a name="see-also"></a>См. также раздел  
 
-  См. статью [Просмотр мобильных отчетов и ключевых показателей эффективности Reporting Services в приложении для iPad](https://powerbi.microsoft.com/documentation/powerbi-mobile-ipad-kpis-mobile-reports)  (Power BI для iOS).  
-  См. статью [Просмотр мобильных отчетов и ключевых показателей эффективности Reporting Services в приложении для iPhone](https://powerbi.microsoft.com/documentation/powerbi-mobile-iphone-kpis-mobile-reports) (Power BI для iOS).  
-  См. статью [Просмотр мобильных отчетов и ключевых показателей эффективности Reporting Services в приложении Android для Power BI](https://powerbi.microsoft.com/documentation/powerbi-mobile-android-kpis-mobile-reports).
-  См. статью [Просмотр ключевых показателей эффективности и мобильных отчетов Reporting Services в мобильном приложении Power BI для Windows 10](https://powerbi.microsoft.com/documentation/powerbi-mobile-win10-kpis-mobile-reports/).    
  
   

