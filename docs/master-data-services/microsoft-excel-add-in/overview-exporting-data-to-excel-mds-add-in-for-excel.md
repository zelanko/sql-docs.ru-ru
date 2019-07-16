---
title: Общие сведения. Экспорт данных в Excel (надстройка MDS для Excel) | Документация Майкрософт
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b628548b-982b-4e45-abf4-c8e83e3ab1c2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 75a23041a3e822ec103012aa18475a092b27b816
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68074499"
---
# <a name="overview-exporting-data-to-excel-mds-add-in-for-excel"></a>Общие сведения. Экспорт данных в Excel (надстройка MDS для Excel)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]необходимо экспортировать данные из репозитория MDS в активный лист Excel, прежде чем можно будет работать с ними. Завершив работу с данными, импортируйте их в репозиторий MDS, чтобы они стали доступны другим пользователям.  
  
 Объем данных, доступных для экспорта, ограничен данными, к которым вам разрешен доступ. Разрешение на доступ к данным задается в веб-приложении [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] или программным способом.  
  
 При экспорте больших объемов данных можно задать предупреждения, которые будут отображаться в том случае, если загрузка данных потребует слишком много времени. Для этого в группе **Параметры** нажмите кнопку **Настройки**. На вкладке **Данные** установите флажок **Отображать предупреждение фильтра для больших наборов данных**.  
  
> [!WARNING]  
>  Книга с поддержкой MDS должна открываться и обновляться только в Excel с надстройкой MDS для Excel. Открытие книг с поддержкой MDS в Excel на компьютере, на котором надстройка MDS для Excel не установлена, не поддерживается, более того, файл книги при этом может быть поврежден. Если требуется предоставить доступ к данным другим пользователям, то вместо того, чтобы сохранять и отправлять лист, отправьте им по электронной почте файл ярлыка запроса. Дополнительные сведения о запросе см. в разделе [Отправка файла ярлыка запроса по электронной почте (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/email-a-shortcut-query-file-mds-add-in-for-excel.md).  
  
## <a name="filtering-data"></a>Фильтрация данных  
 Вы можете отфильтровать данные перед экспортом, чтобы ограничить объем скачиваемых данных. Можно выбрать для загрузки атрибуты (столбцы), порядок отображения атрибутов и элементы (строки данных), с которыми вы собираетесь работать. Дополнительные сведения см. в разделе [Фильтрация данных перед их экспортом (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/filter-data-before-exporting-mds-add-in-for-excel.md).  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a>Автоматическое соединение и загрузка часто используемых данных  
 Если вы всегда соединяетесь с одним и тем же сервером и экспортируете один и тот же набор данных, то можно создать файлы ярлыков запросов, которые содержат сведения о соединениях и фильтрах. Дополнительные сведения о файлах запросов см. в разделе [файлы ярлыков запросов &#40;надстройки MDS для Excel&#41;](../../master-data-services/microsoft-excel-add-in/shortcut-query-files-mds-add-in-for-excel.md).  
  
## <a name="refreshing-data"></a>Обновление данных  
 Данные в репозитории MDS могут быть обновлены другими пользователями после того, как вы их экспортировали. Эти данные можно загрузить, не отменяя изменений, внесенных в данные, не относящиеся к MDS. Дополнительные сведения см. в разделе [Обновление данных (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/refreshing-data-mds-add-in-for-excel.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Фильтрация данных MDS перед их загрузкой в Excel.|[Фильтрация данных перед их экспортом (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/filter-data-before-exporting-mds-add-in-for-excel.md)|  
|Загрузка данных MDS в Excel.|[Экспорт данных в Excel из Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)|  
|Изменение порядка столбцов перед загрузкой данных.|[Переупорядочение столбцов (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/reorder-columns-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Соединения (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/connections-mds-add-in-for-excel.md)  
  
-   [Файлы ярлыков запросов (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [Надстройка Master Data Services для Microsoft Excel](../../master-data-services/microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)  
  
-   [Безопасность (службы Master Data Services)](../../master-data-services/security-master-data-services.md)  
  
  
