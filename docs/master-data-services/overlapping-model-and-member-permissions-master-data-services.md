---
description: Перекрытие разрешений моделей и элементов (службы основных данных)
title: Пересечение разрешений для моделей и элементов
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
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
ms.openlocfilehash: d3de498043b5be0e6ad71a9e32b5abbc6db7ab21
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88343230"
---
# <a name="overlapping-model-and-member-permissions-master-data-services"></a>Перекрытие разрешений моделей и элементов (службы основных данных)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

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
 [Как определяются разрешения &#40;Master Data Services&#41;](../master-data-services/how-permissions-are-determined-master-data-services.md)   
 [Перекрытие разрешений пользователей и групп (службы основных данных)](../master-data-services/overlapping-user-and-group-permissions-master-data-services.md)  
  
  
