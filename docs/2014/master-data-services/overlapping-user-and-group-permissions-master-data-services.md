---
title: Перекрытие разрешений пользователей и групп (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- users [Master Data Services], resolving permissions
- permissions [Master Data Services], user and group overlaps
- groups [Master Data Services], resolving permissions
ms.assetid: 31c3cf7d-17d4-4474-b6a7-ffcb9fc45b37
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 6523603f7524af93bc21417f378a41bd907532d8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193598"
---
# <a name="overlapping-user-and-group-permissions-master-data-services"></a>Перекрытие разрешений пользователей и групп (службы основных данных)
  Разрешения пользователя основаны:  
  
-   Разрешения, унаследованные от членства в группах.  
  
-   разрешениях, явно назначенных пользователю.  
  
 Если пользователь является членом нескольких групп и эти группы имеют доступ к диспетчеру основных данных, то применяются следующие правила.  
  
-   **Запретить** переопределяет все остальные разрешения.  
  
-   **Обновление** переопределяет **только для чтения**.  
  
 Эти правила применяются к вкладкам **Модели** и **Элементы иерархии** . Разрешения определяются для каждой вкладки, после чего объединяются. Дополнительные сведения см. в разделе [How Permissions Are Determined &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md).  
  
> [!NOTE]  
>  Просмотреть разрешение перекрытия разрешений пользователя и группы можно в пользовательском интерфейсе. На вкладках **Модели** и **Элементы иерархии** есть раскрывающийся список, в котором можно выбрать **Действующие** для просмотра действующих разрешений.  
  
## <a name="example-1"></a>Пример 1  
 ![mds_conc_user_group_ex_1](../../2014/master-data-services/media/mds-conc-user-group-ex-1.gif "mds_conc_user_group_ex_1")  
  
 Пользователь принадлежит к группе 1 и группе 2.  
  
 У пользователя есть **только для чтения** разрешения на сущности «продукт».  
  
 Группа 1 имеет разрешение **Обновить** для сущности Product.  
  
 Группа 2 имеет **только для чтения** разрешения на сущности «продукт».  
  
 Результат: действующим разрешением пользователя для сущности Product будет **Обновить** .  
  
## <a name="example-2"></a>Пример 2  
 ![mds_conc_user_group_ex_2](../../2014/master-data-services/media/mds-conc-user-group-ex-2.gif "mds_conc_user_group_ex_2")  
  
 Пользователь принадлежит к группе 1 и группе 2.  
  
 У пользователя есть **только для чтения** разрешения на сущности «продукт».  
  
 Группа 1 имеет разрешение **Обновить** для сущности Product.  
  
 Группа 2 имеет разрешение **Запретить** для сущности Product.  
  
 Результат: действующим разрешением пользователя для сущности Product будет **Запретить** .  
  
## <a name="example-3"></a>Пример 3  
 ![mds_conc_user_group_ex_3](../../2014/master-data-services/media/mds-conc-user-group-ex-3.gif "mds_conc_user_group_ex_3")  
  
 Пользователь принадлежит к группе 1 и группе 2.  
  
 Пользователь имеет разрешение **Обновить** для группы элементов в узле иерархии.  
  
 Группа 1 имеет **только для чтения** разрешение для группы элементов в узле иерархии.  
  
 Группа 2 имеет **только для чтения** разрешение для группы элементов в узле иерархии.  
  
 Результат: действующее разрешение пользователя для элементов — **Обновить** .  
  
## <a name="see-also"></a>См. также  
 [Способ определения разрешений &#40;службы Master Data Services&#41;](how-permissions-are-determined-master-data-services.md)   
 [Перекрытие разрешений моделей и элементов (службы Master Data Services)](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md)  
  
  