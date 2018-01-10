---
title: "Добавление пользовательской карты в мобильный отчет Reporting Services | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: mobile-reports
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd259b95-bb58-4eb1-a436-6aa12fc6f5f2
caps.latest.revision: "6"
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4fbd722f5304835d6e288a13054edf9962985889
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="add-a-custom-map-to-a-reporting-services-mobile-report"></a>Добавление пользовательской карты в мобильный отчет служб Reporting Services
Для пользовательской карты требуется два файла:  
* SHP-файл для контуров фигур;  
* DBF-файл для метаданных  
  
Вы можете ознакомиться с дополнительными сведениями о [пользовательских картах в мобильных отчетах служб Reporting Services](../../reporting-services/mobile-reports/custom-maps-in-reporting-services-mobile-reports.md).  
  
Храните эти два файла в одной папке. Их имена должны совпадать (например, canada.shp и canada.dbf). Метаданные (DBF-файл) должны включать в себя поле "NAME" со значением соответствующего имени фигуры (ключа), которое будет использоваться при заполнении карты данными.   
  
## <a name="load-a-custom-map"></a>Загрузка пользовательской карты  
  
1. На вкладке **Макет** выберите тип карты ( **Gradient Heat Map**(Градиентная тепловая карта), **Range Stop Heat Map**(Относительная тепловая карта) или **Пузырьковая карта**), перетащите ее в область конструктора и придайте карте нужный размер.  
  
   ![Коллекция карт SSMRP](../../reporting-services/mobile-reports/media/ssmrp-mapsgallery.png)  
  
2. В представлении **Макет** на панели **Визуальные свойства** в меню **Карта** выберите **Custom Map From File** (Пользовательская карта из файла).   
  
   ![SSMRP_SelectCustomMap](../../reporting-services/mobile-reports/media/ssmrp-selectcustommap.png)  
  
3. В диалоговом окне **Открытие** перейдите к расположению SHP-файла и DBF-файла и выберите их.   
  
   ![SSMRP_SelectDBFandSHP](../../reporting-services/mobile-reports/media/ssmrp-selectdbfandshp.png)  
  
## <a name="connect-data-to-a-custom-map"></a>Подключение данных к пользовательской карте  
Когда пользовательская карта добавляется в отчет впервые, [!INCLUDE[SS_MobileReptPub_Short](../../includes/ss-mobilereptpub-short.md)] добавляет в нее смоделированные географические данные.  
  
![Данные карт SSMRP](../../reporting-services/mobile-reports/media/ssmrp-mapsdata.png)  
  
Реальные данные в пользовательской карте отображаются так же, как и данные во встроенных картах. Следуйте указаниям в разделе [Карты в мобильных отчетах служб Reporting Services](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md) , чтобы отобразить данные.  
  
### <a name="see-also"></a>См. также раздел  
- [Custom maps in Reporting Services mobile reports](../../reporting-services/mobile-reports/custom-maps-in-reporting-services-mobile-reports.md)  
- [Карты в мобильных отчетах служб Reporting Services](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)  
- [Создание и публикация мобильных отчетов с помощью издателя мобильных отчетов SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)   
  
  
  
  
