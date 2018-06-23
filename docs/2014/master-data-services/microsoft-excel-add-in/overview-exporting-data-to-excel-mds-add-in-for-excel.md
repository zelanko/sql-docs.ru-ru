---
title: Загрузка данных (надстройка MDS для Excel) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b628548b-982b-4e45-abf4-c8e83e3ab1c2
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a3b4833208f308acdbbf4a5d7ec2bcfbf8d0706d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191221"
---
# <a name="loading-data-mds-add-in-for-excel"></a>Загрузка данных (надстройка MDS для Excel)
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], необходимо загрузить данные из репозитория MDS на активный лист Excel перед началом работы с ним. Завершив работу с данными, опубликуйте их в репозитории MDS, чтобы они стали доступны другим пользователям.  
  
 Объем данных, доступных для загрузки, ограничен данными, к которым вам разрешен доступ. Разрешение на доступ к данным задается в веб-приложении [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] или программным способом.  
  
 При загрузке больших объемов данных можно задать предупреждения, которые будут отображаться в том случае, если загрузка данных потребует слишком много времени. Для этого в группе **Параметры** нажмите кнопку **Настройки**. На вкладке **Данные** установите флажок **Отображать предупреждение фильтра для больших наборов данных**.  
  
> [!WARNING]  
>  Книга с поддержкой MDS должна открываться и обновляться только в Excel с надстройкой MDS для Excel. Открытие книг с поддержкой MDS в Excel на компьютере, на котором надстройка MDS для Excel не установлена, не поддерживается, более того, файл книги при этом может быть поврежден. Если требуется предоставить доступ к данным другим пользователям, то вместо того, чтобы сохранять и отправлять лист, отправьте им по электронной почте файл ярлыка запроса. Дополнительные сведения о запросе см. в разделе [Отправка файла ярлыка запроса по электронной почте (надстройка MDS для Excel)](email-a-shortcut-query-file-mds-add-in-for-excel.md).  
  
## <a name="filtering-data"></a>Фильтрация данных  
 Можно отфильтровать данные перед загрузкой, чтобы ограничить число загружаемых столбцов и строк. Можно выбрать для загрузки атрибуты (столбцы), порядок отображения атрибутов и элементы (строки данных), с которыми вы собираетесь работать. Дополнительные сведения см. [фильтрации данных перед загрузкой &#40;надстройки MDS для Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md).  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a>Автоматическое соединение и загрузка часто используемых данных  
 Если вы всегда соединяетесь с одним и тем же сервером и загружаете один и тот же набор данных, то можно создать файл ярлыка запроса, который содержит сведения о соединении и фильтрах. Дополнительные сведения о файлах запросов см. в разделе [Shortcut Query Files &#40;MDS Add-in for Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md).  
  
## <a name="refreshing-data"></a>Обновление данных  
 Данные в репозитории MDS могут быть обновлены другими пользователями после того, как вы их загрузили. Эти данные можно загрузить, не отменяя изменения, внесенные в данные, не относящиеся к MDS. Дополнительные сведения см. в разделе [Обновление данных (надстройка MDS для Excel)](refreshing-data-mds-add-in-for-excel.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Фильтрация данных MDS перед их загрузкой в Excel.|[Фильтрация данных перед загрузкой &#40;надстройка MDS для Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md)|  
|Загрузка данных MDS в Excel.|[Загрузка данных из MDS в Excel](export-data-to-excel-from-master-data-services.md)|  
|Изменение порядка столбцов перед загрузкой данных.|[Изменение порядка столбцов &#40;надстройка MDS для Excel&#41;](reorder-columns-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Соединения (надстройка MDS для ExcelExcel)](connections-mds-add-in-for-excel.md)  
  
-   [Файлы ярлыков запросов (надстройка MDS для Excel)](shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [Надстройка служб Master Data Services для Microsoft Excel](master-data-services-add-in-for-microsoft-excel.md)  
  
-   [Безопасность (службы Master Data Services)](../security-master-data-services.md)  
  
  