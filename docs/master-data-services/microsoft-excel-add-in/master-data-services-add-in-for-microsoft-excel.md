---
title: "Надстройка Master Data Services для Microsoft Excel | Документы Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/25/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33d9c8fc-9602-494d-b9ab-8f0f42785974
caps.latest.revision: 30
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 07ec9e7ae52bb7adb85c2908c4b9b6da87e6ab19
ms.contentlocale: ru-ru
ms.lasthandoff: 09/07/2017

---
# <a name="master-data-services-add-in-for-microsoft-excel"></a>Надстройка Master Data Services для Microsoft Excel
  Благодаря [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]вы можете загружать отфильтрованные списки данных из Master Data Services (MDS) в Excel, где с ними можно работать так же, как и с любыми другими данными. Завершив работу, можно снова опубликовать данные в MDS, где они централизованно хранятся. Система безопасности определяет, какие именно данные вы можете просматривать и изменять.  
  
 Администратор может с помощью [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] создавать сущности и атрибуты и загружать в них данные. Это устраняет необходимость использования других средств для загрузки данных в модели.  
  
 В [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]можно с помощью служб Data Quality Services (DQS) сопоставить данные, прежде чем загружать их в MDS. Это поможет предотвратить дублирование данных в MDS.  

## <a name="downloads"></a>Файлы для загрузки 
>*  Скачайте надстройку служб Master Data Services для Excel для пакета обновления 1 (SP1) SQL Server 2016 с [этой страницы Центра загрузки Майкрософт](https://go.microsoft.com/fwlink/?linkid=836866). 
>* Скачайте [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] для ознакомительной версии для сообщества 1 (CTP1) SQL Server 2017 с [этой страницы Центра загрузки Майкрософт](https://go.microsoft.com/fwlink/?linkid=836867). Эта надстройка также подходит для релиз-кандидата 1 (RC1) SQL Server 2017.

 
  
## <a name="terms"></a>Термины  
 Во время работы с надстройкой вы можете встретить следующие термины. Дополнительные сведения об этих понятиях см. в разделе [Общие сведения о службах Master Data Services (MDS)](../../master-data-services/master-data-services-overview-mds.md).  
  
-   *MDS repository* — место, где хранятся все основные данные. Это база данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , настроенная для хранения данных MDS. Чтоб работать с данными из репозитория, их необходимо загрузить в Excel, а после окончания работы опубликовать изменения в репозитории. Администраторы могут добавлять в репозиторий новые сущности и атрибуты.  
  
-   *Данные, управляемые службами MDS* , — это данные, которые хранятся в репозитории MDS и которые можно загрузить в Excel, где они отображаются в виде выделенных строк. На лист можно добавить данные, которые не управляются MDS, и это никак не повлияет на возможность обновления данных, управляемых MDS.  
  
-   *model* — контейнер для данных. Можно создать несколько версий контейнера, и обычно последняя версия является наиболее актуальной. Дополнительные сведения см. в разделе [Модели (службы Master Data Services)](../../master-data-services/models-master-data-services.md).  
  
-   *entity* — список данных. Можно рассматривать сущность как таблицу в базе данных. Например, сущность **Цвет** может содержать список цветов. Дополнительные сведения см. в разделе [Сущности (службы Master Data Services)](../../master-data-services/entities-master-data-services.md).  
  
-   *Элемент* — это строка данных (запись). Каждая сущность содержит элементы. Пример элемента — **Blue**. Дополнительные сведения см. в разделе [Элементы (службы Master Data Services)](../../master-data-services/members-master-data-services.md).  
  
-   *attribute* — столбец данных. Каждый элемент имеет атрибуты. Например, атрибутом **Code** для элемента **Blue** будет **B**. Дополнительные сведения об атрибутах см. в разделе [Атрибуты (службы Master Data Services)](../../master-data-services/attributes-master-data-services.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание соединения с репозиторием [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .|[Соединение с репозиторием MDS (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|Загрузка данных, управляемых MDS, в Excel.|[Export Data to Excel from Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)|  
|Сохранение ярлыка запроса, который может быть использован для открытия в будущем текущих отображаемых данных, управляемых MDS.|[Сохранение файла ярлыка запроса (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/save-a-shortcut-query-file-mds-add-in-for-excel.md)|  
|Передача ярлыков другим пользователям.|[Отправка файла ярлыка запроса по электронной почте (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/email-a-shortcut-query-file-mds-add-in-for-excel.md)|  
|Просмотр всех изменений, сделанных для элемента.|[Просмотр всех заметок или транзакций для элемента (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)|  
|Перед публикацией новых данных, выясните, имеются ли дублирующиеся значения.|[Сопоставление схожих данных (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/match-similar-data-mds-add-in-for-excel.md)|  
|Публикация данных с листа в репозиторий MDS.|[Импорт данных из Excel в службы Master Data Services (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)|  
|Создание на листе новой сущности с данными. (Только администраторы.)|[Создание сущности (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/create-an-entity-mds-add-in-for-excel.md)|  
|Создание атрибута на основе домена, который также называется ограниченным списком. (Только администраторы.)|[Создание атрибута на основе домена (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/create-a-domain-based-attribute-mds-add-in-for-excel.md)|  
|Задание свойств для загрузки и публикации данных в надстройке служб Master Data Services для Excel. (Только администраторы.)|[Задание свойств надстройки Master Data Services для Excel](../../master-data-services/microsoft-excel-add-in/setting-properties-for-master-data-services-add-in-for-excel.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Соединения (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/connections-mds-add-in-for-excel.md)  
  
-   [Overview: Exporting Data to Excel (MDS Add-in for Excel)](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md) (Обзор экспорта данных в Excel (надстройка MDS для Excel))  
  
-   [Файлы ярлыков запросов (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [Обновление данных (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/refreshing-data-mds-add-in-for-excel.md)  
  
-   [Обзор импорта данных из Excel (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
-   [Проверка данных (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/validating-data-mds-add-in-for-excel.md)  
  
-   [Сопоставление качества данных в надстройке MDS для Excel](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)  
  
-   [Построение модели (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/building-a-model-mds-add-in-for-excel.md)  
  
-   [Задание свойств надстройки Master Data Services для Excel](../../master-data-services/microsoft-excel-add-in/setting-properties-for-master-data-services-add-in-for-excel.md)  
  
-   [Безопасность (службы Master Data Services)](../../master-data-services/security-master-data-services.md)  
  
  

