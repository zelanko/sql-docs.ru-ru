---
title: "Добавление привязки к данным изображения (построитель отчетов и службы SSRS) | Документы Microsoft"
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
ms.assetid: df4c38d4-bfcc-41c4-aa6d-952ca6fd7a2e
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 253d3abfffae056d6300e2203623e7af023a2476
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="add-a-data-bound-image-report-builder-and-ssrs"></a>Добавление привязанного к данным изображения (построитель отчетов и службы SSRS)
  Отчет может включать ссылку на изображение, хранящееся в базе данных. Такое изображение называется *изображением, привязанным к данным*. Примерами изображений, привязанных к данным, служат картинки, выводящиеся вместе с наименованиями товаров в списке товаров.  
  
 Чтобы добавить привязанное к данным изображение к верхнему или нижнему колонтитулу страницы, необходимы дополнительные шаги. Дополнительные сведения см. в разделе [Верхние и нижние колонтитулы страницы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/page-headers-and-footers-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-data-bound-image"></a>Добавление привязанного к данным изображения  
  
1.  В режиме конструктора отчетов создайте таблицу с соединением с источником данных и набор данных с полем, содержащим двоичные данные изображения. Дополнительные сведения см. в разделе [Таблицы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tables-report-builder-and-ssrs.md).  
  
2.  Вставьте столбец в таблицу. Дополнительные сведения см. в разделе [Вставка или удаление столбца (построитель отчетов и службы SSRS)](../../reporting-services/report-design/insert-or-delete-a-column-report-builder-and-ssrs.md).  
  
3.  В меню **Вставка** выберите **Изображение**, а затем щелкните строку данных нового столбца.  
  
4.  На странице «Общие» диалогового окна **Свойства изображения** введите имя в текстовое поле **Имя** или примите имя по умолчанию.  
  
5.  В текстовом поле **Подсказка** введите текст, отображаемый при наведении курсора мыши на изображение в отчете, подготовленном к просмотру в формате HTML (необязательно).  
  
6.  В списке **Выберите источник изображения**выберите пункт **База данных**.  
  
7.  В списке **Использовать это поле**выберите поле, содержащее изображения в отчете.  
  
8.  В списке **Использовать этот тип MIME**выберите тип MIME или формат файла, соответствующий изображению, например BMP.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     В области конструктора отчета появится заполнитель изображения.  
  
## <a name="see-also"></a>См. также:  
 [Образы &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/images-report-builder-and-ssrs.md)   
 [Внедрение изображения в отчет &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/embed-an-image-in-a-report-report-builder-and-ssrs.md)   
 [Добавление внешнего изображения &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/add-an-external-image-report-builder-and-ssrs.md)   
 [Диалоговое окно «Свойства изображения», общие &#40; Построитель отчетов и службы SSRS &#41;](http://msdn.microsoft.com/library/c2218b93-f7fe-46ef-995f-d7dadf9752ec)  
  
  

