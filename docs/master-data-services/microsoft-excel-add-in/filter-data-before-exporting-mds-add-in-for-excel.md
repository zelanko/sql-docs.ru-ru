---
title: "Фильтрация данных перед экспортом (надстройка MDS для Excel) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e30eae0-776b-4a09-aac3-0c0249d92ca5
caps.latest.revision: 10
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d3bc2b1200364c76321c127823c0b9a6161fe4d0
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="filter-data-before-exporting-mds-add-in-for-excel"></a>Фильтрация данных перед экспортом (надстройка MDS для Excel)
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], отфильтровать данные, если вы хотите ограничить объем данных, экспортируется в Excel.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
### <a name="to-filter-data-before-exporting"></a>Для фильтрации данных перед экспортом  
  
1.  Откройте Excel и на вкладке **Основные данные** установите соединение с репозиторием MDS. Дополнительные сведения см. в разделе [Соединение с репозиторием MDS (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md).  
  
2.  На панели **Обозреватель основных данных** выберите модель и версию. Заполняется список сущностей.  
  
    -   Если панель **Обозреватель основных данных** не видна, в группе **Соединение и загрузка** нажмите **Показать обозреватель**.  
  
    -   Если панель **Обозреватель основных данных** отключена, то причина этого заключается в том, что существующий лист уже содержит данные, управляемые MDS. Чтобы включить эту панель, откройте новый лист.  
  
3.  На панели **Обозреватель основных данных** в списке сущностей выберите сущность, которую нужно отфильтровать.  
  
4.  На ленте в группе **Подключение и загрузка** нажмите кнопку **Фильтр**.  
  
5.  В диалоговом окне **Фильтр** выберите атрибуты (столбцы) для отображения, определите их порядок и при необходимости отфильтруйте данные так, чтобы возвращалось меньшее число строк. На панели **Сводка** можно увидеть, сколько данных будет возвращено. Дополнительные сведения см. в разделе [диалогового окна фильтра &#40; Надстройка MDS для Excel &#41; ](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md).  
  
6.  Нажмите кнопку **Загрузить данные**. Лист заполняется данными, управляемыми MDS.  
  
    > [!NOTE]  
    >  -   В Excel загружается только первый миллион элементов.  
    > -   В столбцах, которые являются ограниченными списками (атрибутами на основе домена), по умолчанию загружаются только первые 25 000 значений.  
  
## <a name="next-steps"></a>Следующие шаги  
 [Импорт данных из Excel в службы Master Data Services (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>См. также:  
 [Обзор экспорта данных в Excel (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Диалоговое окно «Фильтр» &#40; Надстройка MDS для Excel &#41;](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md)   
 [Переупорядочение столбцов (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/reorder-columns-mds-add-in-for-excel.md)  
  
  
