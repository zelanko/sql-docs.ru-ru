---
title: "Добавление пользовательской карты в мобильных отчет служб Reporting Services | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd259b95-bb58-4eb1-a436-6aa12fc6f5f2
caps.latest.revision: 6
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e38a8b7a03c79a596d2c795b3ee992e974f604cb
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

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
  
### <a name="see-also"></a>См. также:  
- [Custom maps in Reporting Services mobile reports](../../reporting-services/mobile-reports/custom-maps-in-reporting-services-mobile-reports.md)  
- [Карты в мобильных отчетах служб Reporting Services](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)  
- [Создание и публикация мобильных отчетов с помощью издателя мобильных отчетов SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)   
  
  
  
  

