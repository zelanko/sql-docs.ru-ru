---
title: "Filter Data before Exporting (MDS Add-in for Excel) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9e30eae0-776b-4a09-aac3-0c0249d92ca5
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 10
---
# Filter Data before Exporting (MDS Add-in for Excel)
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], фильтрации данных, когда необходимо ограничить размер или области данных, который экспортируется в Excel.  
  
## Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
### Для фильтрации данных перед экспортом  
  
1.  Откройте Excel и на вкладке **Основные данные** установите соединение с репозиторием MDS. Дополнительные сведения см. в разделе [соединение с репозиторием MDS & #40; Надстройка MDS для Excel & #41;](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md).  
  
2.  На панели **Обозреватель основных данных** выберите модель и версию. Заполняется список сущностей.  
  
    -   Если панель **Обозреватель основных данных** не видна, в группе **Соединение и загрузка** нажмите **Показать обозреватель**.  
  
    -   Если **Обозреватель основных данных** области отключен, поскольку существующий лист уже содержит данные, управляемые MDS. Чтобы включить эту панель, откройте новый лист.  
  
3.  На панели **Обозреватель основных данных** в списке сущностей выберите сущность, которую нужно отфильтровать.  
  
4.  На ленте в группе **Подключение и загрузка** нажмите кнопку **Фильтр**.  
  
5.  Завершить **фильтра** диалоговое окно, выбрав атрибуты (столбцы) для отображения, задание порядка столбцов и при необходимости фильтрации данных, поэтому возвращаются меньшее число строк. На панели **Сводка** можно увидеть, сколько данных будет возвращено. Дополнительные сведения см. в разделе [диалоговое окно Фильтр & #40; Надстройка MDS для Excel & #41;](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md).  
  
6.  Нажмите кнопку **Загрузить данные**. Лист заполняется данными, управляемыми MDS.  
  
    > [!NOTE]  
    >  -   В Excel загружается только первый миллион элементов.  
    > -   В столбцах, которые являются ограниченными списками (атрибутами на основе домена), по умолчанию загружаются только первые 25 000 значений.  
  
## Следующие шаги  
 [Импорт данных из Excel в службы Master Data Services & #40; Надстройка MDS для Excel & #41;](../../master-data-services/microsoft-excel-add-in/import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## См. также:  
 [Обзор: Экспорт данных в Excel и #40; Надстройка MDS для Excel & #41;](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Диалоговое окно Фильтр & #40; Надстройка MDS для Excel & #41;](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md)   
 [Изменение порядка столбцов & #40; Надстройка MDS для Excel & #41;](../../master-data-services/microsoft-excel-add-in/reorder-columns-mds-add-in-for-excel.md)  
  
  