---
title: "Перекрытие разрешений моделей и элементов (службы основных данных) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "модели [Master Data Services], действующие разрешения"
  - "разрешения [Master Data Services], пересечение моделей и элементов"
  - "элементы [Master Data Services], действующие разрешения"
ms.assetid: 9fd7a555-43bf-4796-a8b6-1ca63a291216
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Перекрытие разрешений моделей и элементов (службы основных данных)
  Разрешение для элемента может переопределять разрешение для объекта модели. При возникновении перекрытия действует более жесткое разрешение.  
  
 Если разрешение элемента отличается от разрешения соответствующего модельного объекта, то применяются следующие правила.  
  
-   **Запретить** переопределяет все остальные разрешения.  
  
-   **Администратор** разрешение на уровне модели переопределяет все остальные разрешения и изменить все (CRUD) право доступа на уровнях sub.  
  
-   Действующее разрешение доступа пересекается с разрешениями для элементов и атрибутов.  
  
     Например, если элемент разрешения включают **Создать** и **обновление**, разрешение для атрибутов **обновление**. Действующим разрешением будет **обновление**.  
  
 На следующем рисунке показано, какие разрешения влияют на отдельное значение атрибута, если разрешения для атрибутов отличаются от разрешений для элементов.  
  
 ![mds_conc_security_member_overlap_table](../master-data-services/media/mds-conc-security-member-overlap-table.gif "mds_conc_security_member_overlap_table")  
  
## Пример 1  
 ![mds_conc_overlap_model_1](../master-data-services/media/mds-conc-overlap-model-1.gif "mds_conc_overlap_model_1")  
  
 На **моделей** вкладке сущности «продукт» имеет **обновление** назначено разрешение. Это разрешение наследуют все атрибуты сущности.  
  
 На **элементы иерархии** вкладке подкатегории Mountain Bikes в производной иерархии имеет **обновление** назначено разрешение.  
  
 Результат: В **Explorer**, у пользователя есть **обновление** разрешения на все значения атрибутов для всех элементов узла Mountain Bikes. Все остальные элементы и их атрибуты скрыты.  
  
 ![mds_conc_overlap_model_example_1](../master-data-services/media/mds-conc-overlap-model-example-1.gif "mds_conc_overlap_model_example_1")  
  
## Пример 2  
 ![mds_conc_overlap_model_2](../master-data-services/media/mds-conc-overlap-model-2.gif "mds_conc_overlap_model_2")  
  
 На **моделей** атрибут «Подкатегория» имеет **обновление** назначено разрешение.  
  
 На **элементы иерархии** вкладке подкатегории Mountain Bikes в производной иерархии явно назначено **чтения** разрешение.  
  
 Результат: В **Explorer**, у пользователя есть **чтения** разрешения для значений атрибута Subcategory всех элементов узла Mountain Bikes. Все остальные элементы и их атрибуты скрыты.  
  
 ![mds_conc_overlap_model_example_2](../master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")  
  
## Пример 3  
 ![mds_conc_overlap_model_3](../master-data-services/media/mds-conc-overlap-model-3.gif "mds_conc_overlap_model_3")  
  
 На **моделей** атрибут «Подкатегория» имеет **чтения** назначено разрешение.  
  
 На **элементы иерархии** вкладке подкатегории Mountain Bikes в производной иерархии явно назначено **обновление** разрешение.  
  
 Результат: В **Explorer**, у пользователя есть **чтения** разрешения для значений атрибутов. Все остальные элементы и их атрибуты скрыты.  
  
 ![mds_conc_overlap_model_example_2](../master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")  
  
## См. также:  
 [Способ определения разрешений & #40; Службы Master Data Services & #41;](../master-data-services/how-permissions-are-determined-master-data-services.md)   
 [Перекрывающиеся пользователя и группы разрешений и #40; Службы Master Data Services & #41;](../master-data-services/overlapping-user-and-group-permissions-master-data-services.md)  
  
  