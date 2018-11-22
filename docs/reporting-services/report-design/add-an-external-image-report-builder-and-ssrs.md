---
title: Добавление внешнего изображения (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 81fd4a1f-79a9-4967-86d6-6229413c0995
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c42c413e235abd758d51a76b1726e0c35e3ff758
ms.sourcegitcommit: 9ece10c2970a4f0812647149d3de2c6b75713e14
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51812297"
---
# <a name="add-an-external-image-report-builder-and-ssrs"></a>Добавление внешнего изображения (построитель отчетов и службы SSRS)
  Внешние изображения могут находиться на сервере отчетов в собственном режиме или в режиме интеграции с SharePoint либо находиться на любом другом веб-сайте. При включении внешних изображений в отчет необходимо проверить, что изображение существует и читатель отчета имеет разрешения на доступ к изображению. Дополнительные сведения см. в разделе [Изображения (построитель отчетов и службы SSRS)](../../reporting-services/report-design/images-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-external-image"></a>Добавление внешнего изображения  
  
1.  В режиме конструктора отчетов нажмите на вкладке **Вставка** кнопку **Изображение**.  
  
2.  В области конструктора щелкните и перетащите рамку, чтобы получилось изображение нужного размера.  
  
3.  На вкладке **Общие** диалогового окна **Свойства изображения** введите имя в текстовое поле **Имя** или примите имя по умолчанию.  
  
4.  В текстовом поле **Подсказка** введите текст, отображаемый при наведении курсора на изображение в отчете, подготовленном к просмотру в формате HTML (необязательно).  
  
5.  В списке **Выберите источник изображения**выберите **Внешний**.  
  
     Для изображения, расположенного на сервере отчетов в собственном режиме, введите относительный путь к изображению в поле **Использовать это изображение** , например ../images/image1.jpg.  
  
     Для изображения на сервере отчетов в режиме интеграции с SharePoint или на любом другом веб-сайте укажите полный URL-адрес изображения в окне **Использовать это изображение**, например https://\<имя_сервера_SharePoint>/\<сайт>/Documents/images/image1.jpg.  
  
     Дополнительные сведения см. в разделе [Указание путей к внешним элементам (построитель отчетов и службы SSRS)](../../reporting-services/report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md).  
  
6.  Нажмите кнопку **Размер**, **Видимость**, **Действие**или **Граница** , чтобы задать дополнительные свойства изображения отчета (необязательно).  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Внедрение изображения в отчет (построитель отчетов и службы SSRS)](../../reporting-services/report-design/embed-an-image-in-a-report-report-builder-and-ssrs.md)   
 [Добавление фонового изображения (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-a-background-image-report-builder-and-ssrs.md)   
 [Диалоговое окно "Свойства изображения" — "Общие" (построитель отчетов и службы SSRS)](https://msdn.microsoft.com/library/c2218b93-f7fe-46ef-995f-d7dadf9752ec)  
  
  
