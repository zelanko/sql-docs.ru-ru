---
title: Загрузка данных из MDS в Excel | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: dd29389b-928c-4e50-995c-c6af27f97805
caps.latest.revision: 12
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: b74f5fc00ea25f434a4191c04b0f890e04d8aca0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37316554"
---
# <a name="load-data-from-mds-into-excel"></a>Загрузка данных из MDS в Excel
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], необходимо загрузить данные из репозитория MDS для работы с ним.  
  
 Если вы хотите отфильтровать перед загрузкой набора данных, см. в разделе [фильтрация данных перед загрузкой &#40;надстройки MDS для Excel&#41; ](filter-data-before-exporting-mds-add-in-for-excel.md) вместо этого.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
### <a name="to-load-data-from-mds-into-excel"></a>Загрузка данных из MDS в Excel  
  
1.  Откройте Excel и на вкладке **Основные данные** установите соединение с репозиторием MDS. Дополнительные сведения см. в разделе [Соединение с репозиторием MDS (надстройка MDS для Excel)](connect-to-an-mds-repository-mds-add-in-for-excel.md).  
  
2.  На панели **Обозреватель основных данных** выберите модель и версию. Заполняется список сущностей.  
  
    -   Если панель **Обозреватель основных данных** не видна, в группе **Соединение и загрузка** нажмите **Показать обозреватель**.  
  
    -   Если панель **Обозреватель основных данных** отключена, то причина этого заключается в том, что существующий лист уже содержит данные, управляемые MDS. Чтобы включить эту панель, откройте новый лист.  
  
3.  В области **Обозреватель основных данных** в списке сущностей дважды щелкните сущность, которую нужно загрузить.  
  
    > [!NOTE]  
    >  -   В Excel загружается только первый миллион элементов. Чтобы отфильтровать список перед загрузкой, на ленте в группе **Подключение и загрузка** нажмите кнопку **Фильтр**.  
    > -   В столбцах, которые являются ограниченными списками (атрибутами на основе домена), загружаются только первые 25 000 значений. Это число можно изменить в свойстве MaximumDbaEntitySize в файле excelusersettings.config, расположенном на компьютере, на котором установлена программа Excel. Этот файл находится в C:\Users\\< пользователя\>\AppData\Local\Microsoft\Microsoft SQL Server\120\MasterDataServices\\.  
  
    > [!NOTE]  
    >  Если при загрузке разделенных текстом данных с помощью надстройки для Microsoft Excel в 32-разрядную версию Excel свойствам **Число ячеек для загрузки** и **Число ячеек для публикации** присвоено максимальное значение 1000, возникнет ошибка нехватки памяти. Для использования максимальных значений свойств **Число ячеек для загрузки** и **Число ячеек для публикации**необходимо использовать 64-разрядную версию Excel.  
  
## <a name="next-steps"></a>Следующие шаги  
 [Публикация данных из Excel в MDS &#40;надстройка MDS для Excel&#41;](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>См. также  
 [Загрузка данных &#40;надстройка MDS для Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Диалоговое окно "Фильтр" (надстройка MDS для Excel)](filter-dialog-box-mds-add-in-for-excel.md)   
 [Публикация данных &#40;надстройка MDS для Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
