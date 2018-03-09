---
title: "Перекрытие разрешений пользователей и групп (службы Master Data Services) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- users [Master Data Services], resolving permissions
- permissions [Master Data Services], user and group overlaps
- groups [Master Data Services], resolving permissions
ms.assetid: 31c3cf7d-17d4-4474-b6a7-ffcb9fc45b37
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8463cac31df359be235b872d289f3a3d97864491
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2018
---
# <a name="overlapping-user-and-group-permissions-master-data-services"></a>Перекрытие разрешений пользователей и групп (службы основных данных)
  Разрешения пользователя основаны:  
  
-   Разрешения, унаследованные от членства в группах.  
  
-   разрешениях, явно назначенных пользователю.  
  
 Если пользователь является членом нескольких групп и эти группы имеют доступ к [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], применяются указанные ниже правила.  
  
-   **Запретить** переопределяет все остальные разрешения. Если для объекта установлено разрешение **Запретить** в одной группе, действующим разрешением будет запрет.  
  
-   Разрешение доступа — это объединение всех действующих разрешений для группы. Если разрешение для объекта в одной группе — **Создание** , а в другой **Обновление** , действующим разрешением будет **Создание** и **Обновление**.  
  
 Эти правила применяются к вкладкам **Модели** и **Элементы иерархии** . Разрешения определяются для каждой вкладки, после чего объединяются. Дополнительные сведения см. в разделе [Способ определения разрешений (службы Master Data Services)](../master-data-services/how-permissions-are-determined-master-data-services.md).  
  
> [!NOTE]  
>  Просмотреть разрешение перекрытия разрешений пользователя и группы можно в пользовательском интерфейсе. На вкладках **Модели** и **Элементы иерархии** есть раскрывающийся список, в котором можно выбрать **Действующие** для просмотра действующих разрешений.  
  
## <a name="example-1"></a>Пример 1  
 ![mds_conc_user_group_ex_1](../master-data-services/media/mds-conc-user-group-ex-1.gif "mds_conc_user_group_ex_1")  
  
 Пользователь принадлежит к группе 1 и группе 2.  
  
 Пользователь имеет разрешение **Чтение** для сущности Product.  
  
 Группа 1 имеет разрешение **Обновить** для сущности Product.  
  
 Группа 2 имеет разрешение **Чтение** для сущности Product.  
  
 Результат: действующим разрешением пользователя для сущности Product будет **Обновить** .  
  
## <a name="example-2"></a>Пример 2  
 ![mds_conc_user_group_ex_2](../master-data-services/media/mds-conc-user-group-ex-2.gif "mds_conc_user_group_ex_2")  
  
 Пользователь принадлежит к группе 1 и группе 2.  
  
 Пользователь имеет разрешение **Чтение** для сущности Product.  
  
 Группа 1 имеет разрешение **Обновить** для сущности Product.  
  
 Группа 2 имеет разрешение **Запретить** для сущности Product.  
  
 Результат: действующим разрешением пользователя для сущности Product будет **Запретить** .  
  
## <a name="example-3"></a>Пример 3  
 ![mds_conc_user_group_ex_3](../master-data-services/media/mds-conc-user-group-ex-3.gif "mds_conc_user_group_ex_3")  
  
 Пользователь принадлежит к группе 1 и группе 2.  
  
 Пользователь имеет разрешение **Обновить** для группы элементов в узле иерархии.  
  
 Группа 1 имеет разрешение **Чтение** для группы элементов в узле иерархии.  
  
 Группа 2 имеет разрешение **Чтение** для группы элементов в узле иерархии.  
  
 Результат: действующее разрешение пользователя для элементов — **Обновить** .  
  
## <a name="see-also"></a>См. также:  
 [Способ определения разрешений (службы Master Data Services)](../master-data-services/how-permissions-are-determined-master-data-services.md)   
 [Перекрытие разрешений моделей и элементов (службы Master Data Services)](../master-data-services/overlapping-model-and-member-permissions-master-data-services.md)  
  
  
