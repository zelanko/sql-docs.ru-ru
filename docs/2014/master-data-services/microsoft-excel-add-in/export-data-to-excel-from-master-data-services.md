---
title: Загрузка данных из MDS в Excel | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: dd29389b-928c-4e50-995c-c6af27f97805
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: acfec7a6d86f55e35ef7b3e6f1fa1af481ef87d0
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84961126"
---
# <a name="load-data-from-mds-into-excel"></a>Загрузка данных из MDS в Excel
  В необходимо [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] загрузить данные из репозитория MDS, чтобы работать с ними.  
  
 Если необходимо отфильтровать набор данных перед загрузкой, см. раздел [Фильтрация данных перед Загрузкой &#40;надстройка MDS для Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md) .  
  
## <a name="prerequisites"></a>Предварительные условия  
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
    > -   В столбцах, которые являются ограниченными списками (атрибутами на основе домена), загружаются только первые 25 000 значений. Это число можно изменить в свойстве MaximumDbaEntitySize в файле excelusersettings.config, расположенном на компьютере, на котором установлена программа Excel. Этот файл находится в папке C:\Users \\<user \> \AppData\Local\Microsoft\Microsoft SQL Server\120\MasterDataServices \\ .  
  
    > [!NOTE]  
    >  Если при загрузке разделенных текстом данных с помощью надстройки для Microsoft Excel в 32-разрядную версию Excel свойствам **Число ячеек для загрузки** и **Число ячеек для публикации** присвоено максимальное значение 1000, возникнет ошибка нехватки памяти. Для использования максимальных значений свойств **Число ячеек для загрузки** и **Число ячеек для публикации**необходимо использовать 64-разрядную версию Excel.  
  
## <a name="next-steps"></a>Next Steps  
 [Публикация данных из Excel в службах MDS &#40;надстройка MDS для Excel&#41;](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>См. также:  
 [Загрузка надстройка MDS для Excel &#40;данных&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Диалоговое окно "фильтр" &#40;надстройка MDS для Excel&#41;](filter-dialog-box-mds-add-in-for-excel.md)   
 [Публикация &#40;данных надстройка MDS для Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
