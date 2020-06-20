---
title: Перекрытие разрешений моделей и элементов (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], effective permissions
- permissions [Master Data Services], model and member overlaps
- members [Master Data Services], effective permissions
ms.assetid: 9fd7a555-43bf-4796-a8b6-1ca63a291216
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9129b2290480287be6188e8bf7b2c3181b42cea1
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84960812"
---
# <a name="overlapping-model-and-member-permissions-master-data-services"></a>Перекрытие разрешений моделей и элементов (службы основных данных)
  Разрешение для элемента может переопределять разрешение для объекта модели. При возникновении перекрытия действует более жесткое разрешение.  
  
 Если разрешение элемента отличается от разрешения соответствующего модельного объекта, то применяются следующие правила.  
  
-   **Запретить** переопределяет все остальные разрешения.  
  
-   Переопределяет **Обновление** **только для чтения** .  
  
 На следующем рисунке показано, какие разрешения влияют на отдельное значение атрибута, если разрешения для атрибутов отличаются от разрешений для элементов.  
  
 ![mds_conc_security_member_overlap_table](../../2014/master-data-services/media/mds-conc-security-member-overlap-table.gif "mds_conc_security_member_overlap_table")  
  
## <a name="example-1"></a>Пример 1  
 ![mds_conc_overlap_model_1](../../2014/master-data-services/media/mds-conc-overlap-model-1.gif "mds_conc_overlap_model_1")  
  
 На вкладке **Модели** для сущности Product назначено разрешение **Обновление** . Это разрешение наследуют все атрибуты сущности.  
  
 На вкладке **Элементы иерархии** узлу подкатегории Mountain Bikes в производной иерархии назначено разрешение **Обновление** .  
  
 Результат: в **обозревателе**пользователь имеет разрешение **Обновление** для всех значений атрибутов всех элементов узла Mountain Bikes. Все остальные элементы и их атрибуты скрыты.  
  
 ![mds_conc_overlap_model_example_1](../../2014/master-data-services/media/mds-conc-overlap-model-example-1.gif "mds_conc_overlap_model_example_1")  
  
## <a name="example-2"></a>Пример 2  
 ![mds_conc_overlap_model_2](../../2014/master-data-services/media/mds-conc-overlap-model-2.gif "mds_conc_overlap_model_2")  
  
 На вкладке **Модели** для атрибута Subcategory назначено разрешение **Обновление** .  
  
 На вкладке **элементы иерархии** узлу Подкатегория горных велосипедов в производной иерархии явным образом назначается разрешение только для **чтения** .  
  
 Результат: в **обозревателе**пользователь имеет разрешение **только на чтение** для значений атрибута Подкатегория для элементов в узле Mountain велосипедов. Все остальные элементы и их атрибуты скрыты.  
  
 ![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")  
  
## <a name="example-3"></a>Пример 3  
 ![mds_conc_overlap_model_3](../../2014/master-data-services/media/mds-conc-overlap-model-3.gif "mds_conc_overlap_model_3")  
  
 На вкладке **модели** атрибут Подкатегория имеет разрешение **только чтение** .  
  
 На вкладке **Элементы иерархии** узлу подкатегории Mountain Bikes в порожденной иерархии явно назначено разрешение **Обновление** .  
  
 Результат: в **обозревателе**пользователь имеет разрешение **только на чтение** значений атрибутов. Все остальные элементы и их атрибуты скрыты.  
  
 ![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")  
  
## <a name="see-also"></a>См. также:  
 [Как определяются разрешения &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md)   
 [Перекрытие разрешений пользователей и групп (службы основных данных)](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md)  
  
  
