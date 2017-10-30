---
title: "Добавление атрибутов в группу отслеживания изменений (службы Master Data Services) | Документы Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- change tracking groups [Master Data Services]
- attributes [Master Data Services], change tracking groups
- change tracking groups [Master Data Services], adding attributes
ms.assetid: e153eb5f-70ca-4c6f-89d8-1f937ed3917d
caps.latest.revision: 7
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 468d6712a515336fb60717ed1ba5c46cf644ca49
ms.contentlocale: ru-ru
ms.lasthandoff: 09/07/2017

---
# <a name="add-attributes-to-a-change-tracking-group-master-data-services"></a>Добавление атрибутов в группу отслеживания изменений (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]атрибуты можно добавить в группу отслеживания изменений, чтобы отслеживать изменение значений атрибута.  
  
> [!NOTE]  
>  Если после добавления атрибута в группу отслеживания изменений значения атрибута изменяются, атрибут помечается как измененный в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Создайте бизнес-правило, чтобы предпринимать действия в соответствии с произведенным изменением.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   для добавления в группу отслеживания изменений атрибуты должны уже существовать. Дополнительные сведения см. в статье [Создание текстового атрибута (службы Master Data Services)](../master-data-services/create-a-text-attribute-master-data-services.md).  
  
### <a name="to-add-attributes-to-a-change-tracking-group"></a>Добавление атрибутов в группу отслеживания изменений  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Manage Model** (Управление моделью) выберите в сетке модель и щелкните **Сущности**.  
  
3.  На странице **Управление сущностью** выберите строку сущности, для которой необходимо создать атрибут.  
  
4.  Нажмите **Атрибуты**.  
  
5.  На странице **Управление атрибутами** выполните одно из следующих действий:  
  
    -   Если атрибут предназначен для конечных элементов, в списке **Типы членов** выберите **Конечный элемент** .  
  
    -   Если атрибут предназначен для консолидированных элементов, в списке **Типы членов** выберите **Консолидированный элемент** .  
  
    -   Если атрибут предназначен для коллекций, в списке **Типы членов** выберите **Коллекция** .  
  
6.  Выберите строку для атрибута, который необходимо изменить, а затем нажмите **Изменить**.  
  
7.  Установите флажок **Включить отслеживание изменений** .  
  
8.  В поле **Группа отслеживания изменений** введите номер группы.  
  
9. Нажмите кнопку **Сохранить атрибут**.  
  
     Для измененного атрибута значение в столбце **Включить группу отслеживания изменений** в сетке изменяется на **Да (группа: введен номер группы)**.  
  
10. Повторяйте эти шаги для всех атрибутов, которые необходимо включить в группу. Используйте для каждого атрибута в группе один и тот же номер группы отслеживания изменений.  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   [Инициирование действия на основе значения атрибута (службы Master Data Services)](../master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Создание текстового атрибута (службы Master Data Services)](../master-data-services/create-a-text-attribute-master-data-services.md)   
 [Создание атрибута на основе домена (службы Master Data Services)](../master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
  

