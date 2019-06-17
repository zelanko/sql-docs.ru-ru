---
title: Добавление атрибутов в группу отслеживания изменений (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- change tracking groups [Master Data Services]
- attributes [Master Data Services], change tracking groups
- change tracking groups [Master Data Services], adding attributes
ms.assetid: e153eb5f-70ca-4c6f-89d8-1f937ed3917d
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 8e700942f9cebc08241cf4e159dceedc7d515a94
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65480127"
---
# <a name="add-attributes-to-a-change-tracking-group-master-data-services"></a>Добавление атрибутов в группу отслеживания изменений (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]атрибуты можно добавить в группу отслеживания изменений, чтобы отслеживать изменение значений атрибута.  
  
> [!NOTE]  
>  Если после добавления атрибута в группу отслеживания изменений значения атрибута изменяются, атрибут помечается как измененный в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Создайте бизнес-правило, чтобы предпринимать действия в соответствии с произведенным изменением.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](administrators-master-data-services.md).  
  
-   для добавления в группу отслеживания изменений атрибуты должны уже существовать. Дополнительные сведения см. в статье [Create a Text Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md).  
  
### <a name="to-add-attributes-to-a-change-tracking-group"></a>Добавление атрибутов в группу отслеживания изменений  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На **обозревателя моделей** страницы, на панели меню наведите указатель мыши на **управление** и нажмите кнопку **сущностей**.  
  
3.  На странице **Обслуживание сущности** выберите модель из списка **Модель** .  
  
4.  Выберите строку сущности, для которой необходимо отслеживать значения атрибутов.  
  
5.  Щелкните **Изменить выбранную сущность**.  
  
6.  На странице **Изменение сущности** :  
  
    -   Если атрибут предназначен для конечных элементов, в **конечные атрибуты** области, выберите атрибут и нажмите кнопку **изменить конечный атрибут**.  
  
    -   Если атрибут предназначен для консолидированных элементов в **консолидированные атрибуты** области, выберите атрибут и нажмите кнопку **изменить объединенный атрибут**.  
  
    -   Если атрибут предназначен для коллекций, в **атрибуты коллекции** области, выберите атрибут и нажмите кнопку **изменить атрибут коллекции**.  
  
7.  Установите флажок **Включить отслеживание изменений** .  
  
8.  В поле **Группа отслеживания изменений** введите номер группы.  
  
9. Нажмите кнопку **Сохранить атрибут**.  
  
10. На странице **Обслуживание сущности** нажмите кнопку **Сохранить сущность**.  
  
11. Повторяйте эти шаги для всех атрибутов, которые необходимо включить в группу. Используйте для каждого атрибута в группе один и тот же номер группы отслеживания изменений.  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   [Инициирование действия на основе значения атрибута (службы Master Data Services)](../../2014/master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)  
  
## <a name="see-also"></a>См. также  
 [Создание текстового атрибута (службы Master Data Services)](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)   
 [Создание атрибута на основе домена (службы Master Data Services)](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
  
