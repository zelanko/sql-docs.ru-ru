---
description: Фильтрация данных перед экспортом (надстройка MDS для Excel)
title: Фильтрация данных перед экспортом
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9e30eae0-776b-4a09-aac3-0c0249d92ca5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 37cf62c1a0a64e8e9ab09c216f053a4eef98e084
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "92257681"
---
# <a name="filter-data-before-exporting-mds-add-in-for-excel"></a>Фильтрация данных перед экспортом (надстройка MDS для Excel)

[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] можно отфильтровать данные, если нужно ограничить объем данных, экспортируемых в Excel.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
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
  
## <a name="next-steps"></a>Next Steps  
 [Импорт данных из Excel в службы Master Data Services (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>См. также:  
 [Обзор: экспорт данных в надстройка MDS для Excel &#40;Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Диалоговое окно "фильтр" &#40;надстройка MDS для Excel&#41;](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md)   
 [Переупорядочение столбцов (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/reorder-columns-mds-add-in-for-excel.md)  
  
  
