---
title: "Добавление внешнего изображения (построитель отчетов и службы SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81fd4a1f-79a9-4967-86d6-6229413c0995
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 291a906484a6f7d812d091252802b706d207a69e
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

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
  
     Для изображения, расположенного на сервере отчетов в собственном режиме, введите относительный путь к изображению в поле **Использовать это изображение**, например ../images/image1.jpg.  
  
     Для изображения на сервере отчетов в режиме интеграции с SharePoint или веб-сайт, введите полный URL-адрес изображения в **использовать это изображение** поле — например, http://\<SharePointservername > /\<узел > / Documents/images/image1.jpg.  
  
     Дополнительные сведения см. в разделе [Указание путей к внешним элементам (построитель отчетов и службы SSRS)](../../reporting-services/report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md).  
  
6.  Нажмите кнопку **Размер**, **Видимость**, **Действие** или **Граница**, чтобы задать дополнительные свойства изображения отчета (необязательно).  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Внедрение изображения в отчет &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/embed-an-image-in-a-report-report-builder-and-ssrs.md)   
 [Добавить фоновое изображение &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/add-a-background-image-report-builder-and-ssrs.md)   
 [Диалоговое окно «Свойства изображения», общие &#40; Построитель отчетов и службы SSRS &#41;](http://msdn.microsoft.com/library/c2218b93-f7fe-46ef-995f-d7dadf9752ec)  
  
  
