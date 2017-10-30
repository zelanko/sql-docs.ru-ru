---
title: "Перекрытие разрешений моделей и элементов (службы Master Data Services) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- models [Master Data Services], effective permissions
- permissions [Master Data Services], model and member overlaps
- members [Master Data Services], effective permissions
ms.assetid: 9fd7a555-43bf-4796-a8b6-1ca63a291216
caps.latest.revision: 7
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: d5c748f2dc89e7b7217408971d70bd95a42af3a2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/07/2017

---
# <a name="overlapping-model-and-member-permissions-master-data-services"></a>Перекрытие разрешений моделей и элементов (службы основных данных)
  Разрешение для элемента может переопределять разрешение для объекта модели. При возникновении перекрытия действует более жесткое разрешение.  
  
 Если разрешение элемента отличается от разрешения соответствующего модельного объекта, то применяются следующие правила.  
  
-   **Запретить** переопределяет все остальные разрешения.  
  
-   Разрешение**Администратор** на уровне модели переопределяет все остальные разрешения и изменяется на разрешение доступа "Все (CRUD)" на подуровнях.  
  
-   Действующее разрешение доступа пересекается с разрешениями для элементов и атрибутов.  
  
     Например, если разрешения элементов включают **Создание** и **Обновление**, разрешением для атрибутов будет **Обновление**. Действующее разрешение — **Обновление**.  
  
 На следующем рисунке показано, какие разрешения влияют на отдельное значение атрибута, если разрешения для атрибутов отличаются от разрешений для элементов.  
  
 ![mds_conc_security_member_overlap_table](../master-data-services/media/mds-conc-security-member-overlap-table.gif "mds_conc_security_member_overlap_table")  
  
## <a name="example-1"></a>Пример 1  
 ![mds_conc_overlap_model_1](../master-data-services/media/mds-conc-overlap-model-1.gif "mds_conc_overlap_model_1")  
  
 На вкладке **Модели** для сущности Product назначено разрешение **Обновление** . Это разрешение наследуют все атрибуты сущности.  
  
 На вкладке **Элементы иерархии** узлу подкатегории Mountain Bikes в производной иерархии назначено разрешение **Обновление** .  
  
 Результат: в **обозревателе**пользователь имеет разрешение **Обновление** для всех значений атрибутов всех элементов узла Mountain Bikes. Все остальные элементы и их атрибуты скрыты.  
  
 ![mds_conc_overlap_model_example_1](../master-data-services/media/mds-conc-overlap-model-example-1.gif "mds_conc_overlap_model_example_1")  
  
## <a name="example-2"></a>Пример 2  
 ![mds_conc_overlap_model_2](../master-data-services/media/mds-conc-overlap-model-2.gif "mds_conc_overlap_model_2")  
  
 На вкладке **Модели** для атрибута Subcategory назначено разрешение **Обновление** .  
  
 На вкладке **Элементы иерархии** узлу подкатегории Mountain Bikes в производной иерархии явно назначено разрешение **Чтение** .  
  
 Результат: в **обозревателе**пользователь имеет разрешение **Чтение** для значений атрибута Subcategory всех элементов узла Mountain Bikes. Все остальные элементы и их атрибуты скрыты.  
  
 ![mds_conc_overlap_model_example_2](../master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")  
  
## <a name="example-3"></a>Пример 3  
 ![mds_conc_overlap_model_3](../master-data-services/media/mds-conc-overlap-model-3.gif "mds_conc_overlap_model_3")  
  
 На вкладке **Модели** для атрибута Subcategory назначено разрешение **Чтение** .  
  
 На вкладке **Элементы иерархии** узлу подкатегории Mountain Bikes в порожденной иерархии явно назначено разрешение **Обновление** .  
  
 Результат: в **обозревателе**пользователь имеет разрешение **Чтение** для значений атрибутов. Все остальные элементы и их атрибуты скрыты.  
  
 ![mds_conc_overlap_model_example_2](../master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")  
  
## <a name="see-also"></a>См. также:  
 [Способ определения разрешений (службы Master Data Services)](../master-data-services/how-permissions-are-determined-master-data-services.md)   
 [Перекрытие разрешений пользователей и групп (службы Master Data Services)](../master-data-services/overlapping-user-and-group-permissions-master-data-services.md)  
  
  

