---
title: Экспорт данных в Excel из Master Data Services | Документы Майкрософт
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: dd29389b-928c-4e50-995c-c6af27f97805
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 52ff3370fe6e71b6253432c2aa1ec15239b59a53
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600312"
---
# <a name="export-data-to-excel-from-master-data-services"></a>Export Data to Excel from Master Data Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]для работы с данными необходимо сначала экспортировать их из репозитория MDS.  
  
 Если перед загрузкой набора данных нужно отфильтровать его, см. раздел [Фильтрация данных перед их экспортом (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/filter-data-before-exporting-mds-add-in-for-excel.md).  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
### <a name="to-export-data-from-mds-into-excel"></a>Экспорт данных из MDS в Excel  
  
1.  Откройте Excel и на вкладке **Основные данные** установите соединение с репозиторием MDS. Дополнительные сведения см. в разделе [Соединение с репозиторием MDS (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md).  
  
2.  На панели **Обозреватель основных данных** выберите модель и версию. Заполняется список сущностей.  
  
    -   Если панель **Обозреватель основных данных** не видна, в группе **Соединение и загрузка** нажмите **Показать обозреватель**.  
  
    -   Если панель **Обозреватель основных данных** отключена, то причина этого заключается в том, что существующий лист уже содержит данные, управляемые MDS. Чтобы включить эту панель, откройте новый лист.  
  
3.  В области **Обозреватель основных данных** в списке сущностей дважды щелкните сущность, которую нужно загрузить.  
  
    > [!NOTE]  
    >  -   В Excel загружается только первый миллион элементов. Чтобы отфильтровать список перед загрузкой, на ленте в группе **Подключение и загрузка** нажмите кнопку **Фильтр**.  
    > -   В столбцах, которые являются ограниченными списками (атрибутами на основе домена), по умолчанию загружаются только первые 25 000 значений. Это число можно изменить в свойстве MaximumDbaEntitySize в файле excelusersettings.config, расположенном на компьютере, на котором установлена программа Excel. Этот файл расположен в каталоге C:\Users\\<пользователь\>\AppData\Local\Microsoft\Microsoft SQL Server\130\MasterDataServices\\.  
    >   
    >      Если количество значений для атрибута на основе домена превышает настройку свойства MaximumDbEntitySize, список значений не загружается.  
  
    > [!NOTE]  
    >  Если при загрузке разделенных текстом данных с помощью надстройки для Microsoft Excel в 32-разрядную версию Excel свойствам **Число ячеек для загрузки** и **Число ячеек для публикации** присвоено максимальное значение 1000, возникнет ошибка нехватки памяти. Для использования максимальных значений свойств **Число ячеек для загрузки** и **Число ячеек для публикации**необходимо использовать 64-разрядную версию Excel.  
  
## <a name="next-steps"></a>Next Steps  
 [Импорт данных из Excel в службы Master Data Services (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>См. также:  
 [Обзор экспорта данных в Excel (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Диалоговое окно "Фильтр" (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md)   
 [Обзор импорта данных из Excel (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
