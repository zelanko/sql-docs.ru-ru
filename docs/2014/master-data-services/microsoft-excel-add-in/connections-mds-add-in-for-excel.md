---
title: Соединения (надстройка MDS для Excel) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 2f2b2f9d-7744-460e-83cd-56d34ea70ff0
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: a7d336e777f4f6bf00310cbadfed75987ba45252
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65478915"
---
# <a name="connections-mds-add-in-for-excel"></a>Соединения (настройка MDS для Excel)
  Для скачивания данных в [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]необходимо сначала создать соединение. Соединение — это данные, по которым веб-служба [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] узнает, с какой базой данных MDS нужно устанавливать соединение.  
  
 Строкой подключения обычно является URL-адрес веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], например http://contoso/mds.  
  
 При каждом запуске Excel необходимо устанавливать соединение с репозиторием MDS. Единственное исключение — когда активный лист уже содержит данные, управляемые MDS. В этом случае соединение устанавливается автоматически при каждом обновлении и при каждой публикации данных на листе.  
  
 Можно создать несколько соединений. Последнее соединение, к которому было обращение, считается соединением по умолчанию.  
  
 Одновременно могут быть соединены несколько пользователей. Но если несколько пользователей попытаются опубликовать одни и те же данные, могут возникнуть конфликты. Дополнительные сведения см. в разделе [публикации данных &#40;надстройки MDS для Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md).  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a>Автоматическое соединение и загрузка часто используемых данных  
 Если вы всегда соединяетесь с одним и тем же сервером и загружаете один и тот же набор данных, то можно создать файл ярлыка запроса, который содержит сведения о соединении и фильтрах. Дополнительные сведения о файлах запросов см. в разделе [Файлы ярлыков запросов (надстройка MDS для Excel)](shortcut-query-files-mds-add-in-for-excel.md).  
  
## <a name="data-quality-services"></a>Data Quality Services  
 [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] включает функциональные возможности служб Data Quality Services, которые помогут сопоставить данные, прежде чем публиковать их в репозитории MDS. Если при установлении соединения база данных DQS установлена на том же экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , что и база данных MDS, то на ленте появятся кнопки служб DQS. Если база данных DQS_Main не существует на этом экземпляре, то эти кнопки не отображаются и функции качества данных будут недоступны.  
  
## <a name="troubleshooting-connections"></a>Устранение неполадок с соединениями  
 При подключении к MDS, при возникновении любой проблемы см. в разделе [ https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx ](https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx) советы по устранению неполадок.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Установите соединение с базой данных служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .|[Соединение с репозиторием MDS (надстройка MDS для Excel)](connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|Загрузка данных MDS в Excel.|[Загрузка данных из MDS в Excel](export-data-to-excel-from-master-data-services.md)|  
|Фильтрация данных MDS перед их загрузкой в Excel.|[Фильтрация данных перед загрузкой &#40;надстройка MDS для Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Загрузка данных &#40;надстройка MDS для Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
-   [Файлы ярлыков запросов (надстройка MDS для Excel)](shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [Надстройка Master Data Services для Microsoft Excel](master-data-services-add-in-for-microsoft-excel.md)  
  
  
