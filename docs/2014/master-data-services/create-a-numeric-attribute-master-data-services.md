---
title: Создание числового атрибута (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], creating number attributes
- creating number attributes [Master Data Services]
ms.assetid: c0dbb6d8-ba78-485a-a40d-6d5cb7e75d0a
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 484774165ea1997b98fc9dc0919f5be7450dd4c7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "65483364"
---
# <a name="create-a-numeric-attribute-master-data-services"></a>Создание числового атрибута (службы Master Data Services)
  В службах [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]числовой атрибут создается, если нужно, чтобы пользователи вводили число в качестве значения атрибута.  
  
> [!NOTE]  
>  На числовые атрибуты налагаются определенные ограничения. Дополнительные сведения см. в разделе [Атрибуты (службы Master Data Services)](attributes-master-data-services.md).  
  
## <a name="prerequisites"></a>Предварительные условия  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** .  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).  
  
-   должна существовать сущность, для которой создается атрибут. Дополнительные сведения см. в разделе [Создание сущности (службы Master Data Services)](../../2014/master-data-services/create-an-entity-master-data-services.md).  
  
### <a name="to-create-a-numeric-attribute"></a>Создание числового атрибута  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Представление модели** в строке меню наведите курсор на **Управление** и щелкните **Сущности**.  
  
3.  На странице **Обслуживание сущности** выберите модель из списка **Модель** .  
  
4.  Выберите строку сущности, для которой необходимо создать атрибут.  
  
5.  Щелкните **Изменить выбранную сущность**.  
  
6.  На странице **Изменение сущности** :  
  
    -   если атрибут предназначен для конечных элементов, выберите команду **Добавить конечный атрибут** на панели **Атрибуты конечных элементов**;  
  
    -   если атрибут предназначен для объединенных элементов, выберите команду **Добавить объединенный атрибут** на панели **Атрибуты консолидированных элементов**;  
  
    -   если атрибут предназначен для коллекций, выберите команду **Добавить атрибут коллекции** на панели **Атрибуты коллекций**.  
  
7.  Выберите параметр **В свободной форме** на странице **Добавить атрибут** .  
  
8.  Введите имя атрибута в поле **Имя** . Список слов, которые не должны использоваться в качестве имен атрибутов, см. в разделе [зарезервированные слова &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md).  
  
9. В поле **Ширина отображаемой области (в пикселях)** введите ширину столбца атрибута для отображения в сетке **обозревателя** .  
  
10. В списке **Тип данных** выберите **Число**.  
  
11. В поле **Знаки после запятой** укажите количество знаков, которые можно ввести после десятичной запятой.  
  
12. В списке **Маска ввода** выберите формат отрицательных чисел.  
  
13. По желанию установите флажок **Включить отслеживание изменений** , чтобы отслеживать изменения в группах атрибутов. Дополнительные сведения см. в разделе [Добавление атрибутов в группу отслеживания изменений (службы Master Data Services)](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) .  
  
14. Нажмите кнопку **Сохранить атрибут**.  
  
15. На странице **Обслуживание сущности** нажмите кнопку **Сохранить сущность**.  
  
## <a name="see-also"></a>См. также  
 [Master Data Services &#40;атрибутов&#41;](attributes-master-data-services.md)   
 [Измените имя атрибута &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md)   
 [Создание атрибута на основе домена &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)   
 [Создание файлового атрибута (службы Master Data Services)](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
  
