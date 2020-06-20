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
ms.openlocfilehash: e4457412f39b6dbaa86154dc6068527d7b2095d3
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972329"
---
# <a name="add-attributes-to-a-change-tracking-group-master-data-services"></a>Добавление атрибутов в группу отслеживания изменений (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]атрибуты можно добавить в группу отслеживания изменений, чтобы отслеживать изменение значений атрибута.  
  
> [!NOTE]  
>  Если после добавления атрибута в группу отслеживания изменений значения атрибута изменяются, атрибут помечается как измененный в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Создайте бизнес-правило, чтобы предпринимать действия в соответствии с произведенным изменением.  
  
## <a name="prerequisites"></a>Предварительные условия  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** .  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   для добавления в группу отслеживания изменений атрибуты должны уже существовать. Дополнительные сведения см. в статье [Создание текстового атрибута (службы Master Data Services)](../../2014/master-data-services/create-a-text-attribute-master-data-services.md).  
  
### <a name="to-add-attributes-to-a-change-tracking-group"></a>Добавление атрибутов в группу отслеживания изменений  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Обозреватель моделей** в строке меню наведите указатель мыши на пункт **Управление** и щелкните **сущности**.  
  
3.  На странице **Обслуживание сущности** выберите модель из списка **Модель** .  
  
4.  Выберите строку сущности, для которой необходимо отслеживать значения атрибутов.  
  
5.  Щелкните **Изменить выбранную сущность**.  
  
6.  На странице **Изменение сущности** :  
  
    -   Если атрибут предназначен для конечных элементов, выберите атрибут в области **конечные атрибуты** и нажмите кнопку **Изменить конечный атрибут**.  
  
    -   Если атрибут предназначен для консолидированных элементов, в области **консолидированные атрибуты** выберите атрибут и щелкните **изменить консолидированный атрибут**.  
  
    -   Если атрибут предназначен для коллекций, на панели **атрибуты коллекции** выберите атрибут и щелкните **изменить атрибут коллекции**.  
  
7.  Установите флажок **Включить отслеживание изменений** .  
  
8.  В поле **Группа отслеживания изменений** введите номер группы.  
  
9. Нажмите кнопку **Сохранить атрибут**.  
  
10. На странице **Обслуживание сущности** нажмите кнопку **Сохранить сущность**.  
  
11. Повторяйте эти шаги для всех атрибутов, которые необходимо включить в группу. Используйте для каждого атрибута в группе один и тот же номер группы отслеживания изменений.  
  
## <a name="next-steps"></a>Next Steps  
  
-   [Инициирование действия на основе значения атрибута (службы Master Data Services)](../../2014/master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Создание текстового атрибута &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)   
 [Создание атрибута на основе домена (службы Master Data Services)](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
  
