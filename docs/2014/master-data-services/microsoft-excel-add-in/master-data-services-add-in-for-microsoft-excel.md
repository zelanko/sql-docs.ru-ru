---
title: Надстройка Master Data Services для Microsoft Excel | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 33d9c8fc-9602-494d-b9ab-8f0f42785974
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: d8bac9ba8afafa6b5141d90c51f8029f596ba8f4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "65482627"
---
# <a name="master-data-services-add-in-for-microsoft-excel"></a>Надстройка Master Data Services для Microsoft Excel
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]можно распространить главные списки ссылочных данных среди всех пользователей в вашей организации, использующих [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]Excel. Какие именно данные пользователь может просматривать и обновлять, определяется системой безопасности.  
  
 Можно загрузить отфильтрованные списки данных из MDS в Excel, где их обработка может выполняться точно так же, как и обработка любых других данных. Завершив работу, можно снова опубликовать данные в MDS, где они централизованно хранятся.  
  
 Администратор может с помощью [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] создавать сущности и атрибуты и загружать в них данные. Это устраняет необходимость использования других средств для загрузки данных в модели.  
  
 В [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]можно с помощью служб Data Quality Services (DQS) сопоставить данные, прежде чем загружать их в MDS. Это поможет предотвратить дублирование данных в MDS.  
  
> [!IMPORTANT]  
>  Можно продолжить использование надстройки служб Master Data Services для Excel версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] с пакетом обновления 1 (SP1) после обновления служб Master Data Services и Data Quality Services до версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2. Однако любая более ранняя версия надстройки служб Master Data Services для Excel перестанет работать после обновления до версии SQL Server 2014 CTP2. Можно загрузить надстройку служб Master Data Services для Excel версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] с пакетом обновления 1 (SP1) по [этой ссылке](https://go.microsoft.com/fwlink/?LinkId=328664).  
  
## <a name="terms"></a>Термины  
 Во время работы с надстройкой вы можете встретить следующие термины.  
  
-   
  *MDS repository* — место, где хранятся все основные данные. Это база данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , настроенная для хранения данных MDS. Чтоб работать с данными из репозитория, их необходимо загрузить в Excel, а после окончания работы опубликовать изменения в репозитории. Администраторы могут добавлять в репозиторий новые сущности и атрибуты.  
  
-   *Данные, управляемые MDS* , — это данные, которые хранятся в репозитории MDS и загружаются в Excel, где данные отображаются в виде выделенных строк. На лист можно добавить данные, которые не управляются MDS, и это никак не повлияет на возможность обновления данных, управляемых MDS.  
  
-   
  *model* — контейнер для данных. Можно создать несколько версий контейнера, и обычно последняя версия является наиболее актуальной. Дополнительные сведения см. в разделе [Модели (службы Master Data Services)](../models-master-data-services.md).  
  
-   
  *entity* — список данных. Можно рассматривать сущность как таблицу в базе данных. Например, сущность **Цвет** может содержать список цветов. Дополнительные сведения см. в разделе [Сущности (службы Master Data Services)](../entities-master-data-services.md).  
  
-   
  *member* — строка данных. Каждая сущность содержит элементы. Пример элемента — **Blue**. Дополнительные сведения см. в разделе [Элементы (службы Master Data Services)](../members-master-data-services.md).  
  
-   
  *attribute* — столбец данных. Каждый элемент имеет атрибуты. Например, атрибут **Code** для **синего** элемента имеет значение **B**. Дополнительные сведения об атрибутах см. в разделе [attributes &#40;Master Data Services&#41;](../attributes-master-data-services.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание соединения с репозиторием [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .|[Подключение к репозиторию MDS &#40;надстройка MDS для Excel&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|Загрузка данных, управляемых MDS, в Excel.|[Загрузка данных из MDS в Excel](export-data-to-excel-from-master-data-services.md)|  
|Сохранение ярлыка запроса, который может быть использован для открытия в будущем текущих отображаемых данных, управляемых MDS.|[Сохранение файла ярлыка запроса &#40;надстройка MDS для Excel&#41;](save-a-shortcut-query-file-mds-add-in-for-excel.md)|  
|Передача ярлыков другим пользователям.|[Отправка надстройка MDS для Excel &#40;файла ярлыка запроса&#41;](email-a-shortcut-query-file-mds-add-in-for-excel.md)|  
|Просмотр всех изменений, сделанных для элемента.|[Просмотр всех заметок или транзакций для элемента &#40;надстройка MDS для Excel&#41;](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)|  
|Перед публикацией новых данных, выясните, имеются ли дублирующиеся значения.|[Сопоставление схожих &#40;данных надстройка MDS для Excel&#41;](match-similar-data-mds-add-in-for-excel.md)|  
|Публикация данных с листа в репозиторий MDS.|[Публикация данных из Excel в службах MDS &#40;надстройка MDS для Excel&#41;](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)|  
|Создание на листе новой сущности с данными. (Только администраторы.)|[Создание сущности &#40;надстройка MDS для Excel&#41;](create-an-entity-mds-add-in-for-excel.md)|  
|Создание атрибута на основе домена, который также называется ограниченным списком. (Только администраторы.)|[Создание атрибута на основе домена &#40;надстройка MDS для Excel&#41;](create-a-domain-based-attribute-mds-add-in-for-excel.md)|  
|Задание свойств для загрузки и публикации данных в надстройке служб Master Data Services для Excel. (Только администраторы.)|[Задание свойств надстройки Master Data Services для Excel](setting-properties-for-master-data-services-add-in-for-excel.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Подключения &#40;надстройка MDS для Excel&#41;](connections-mds-add-in-for-excel.md)  
  
-   [Загрузка надстройка MDS для Excel &#40;данных&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
-   [Файлы ярлыков запросов &#40;надстройка MDS для Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [Сопоставление качества данных в надстройка MDS для Excel](data-quality-matching-in-the-mds-add-in-for-excel.md)  
  
-   [Публикация &#40;данных надстройка MDS для Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
-   [Создание модели &#40;надстройка MDS для Excel&#41;](building-a-model-mds-add-in-for-excel.md)  
  
-   [Master Data Services &#40;безопасности&#41;](../security-master-data-services.md)  
  
  
