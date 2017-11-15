---
title: "Фильтрация данных перед экспортом (надстройка MDS для Excel) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e30eae0-776b-4a09-aac3-0c0249d92ca5
caps.latest.revision: "10"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 315b6f76b95bce7a0cbcdc3823890dd1172255ae
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="filter-data-before-exporting-mds-add-in-for-excel"></a>Фильтрация данных перед экспортом (надстройка MDS для Excel)
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] можно отфильтровать данные, если нужно ограничить объем данных, экспортируемых в Excel.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
### <a name="to-filter-data-before-exporting"></a>Фильтрация данных перед экспортом  
  
1.  Откройте Excel и на вкладке **Основные данные** установите соединение с репозиторием MDS. Дополнительные сведения см. в разделе [Соединение с репозиторием MDS (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md).  
  
2.  На панели **Обозреватель основных данных** выберите модель и версию. Заполняется список сущностей.  
  
    -   Если панель **Обозреватель основных данных** не видна, в группе **Соединение и загрузка** нажмите **Показать обозреватель**.  
  
    -   Если панель **Обозреватель основных данных** отключена, то причина этого заключается в том, что существующий лист уже содержит данные, управляемые MDS. Чтобы включить эту панель, откройте новый лист.  
  
3.  На панели **Обозреватель основных данных** в списке сущностей выберите сущность, которую нужно отфильтровать.  
  
4.  На ленте в группе **Подключение и загрузка** нажмите кнопку **Фильтр**.  
  
5.  В диалоговом окне **Фильтр** выберите атрибуты (столбцы) для отображения, определите их порядок и при необходимости отфильтруйте данные так, чтобы возвращалось меньшее число строк. На панели **Сводка** можно увидеть, сколько данных будет возвращено. Дополнительные сведения см. в разделе [Диалоговое окно "Фильтр" (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md).  
  
6.  Нажмите кнопку **Загрузить данные**. Лист заполняется данными, управляемыми MDS.  
  
    > [!NOTE]  
    >  -   В Excel загружается только первый миллион элементов.  
    > -   В столбцах, которые являются ограниченными списками (атрибутами на основе домена), по умолчанию загружаются только первые 25 000 значений.  
  
## <a name="next-steps"></a>Следующие шаги  
 [Импорт данных из Excel в службы Master Data Services (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>См. также:  
 [Обзор экспорта данных в Excel (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Диалоговое окно "Фильтр" (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md)   
 [Переупорядочение столбцов (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/reorder-columns-mds-add-in-for-excel.md)  
  
  
