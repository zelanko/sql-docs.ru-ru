---
description: Коллекции (службы основных данных)
title: Коллекции
ms.custom: ''
ms.date: 04/01/2016
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services]
- collections [Master Data Services], about collections
ms.assetid: 5aa1d1e0-b4e5-4897-8e74-01dcf418df73
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 75036d4713000b05052c2094e7d8ba8d23c65f25
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500716"
---
# <a name="collections-master-data-services"></a>Коллекции (службы основных данных)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Коллекция — это группа конечных или консолидированных элементов из одной сущности. Коллекции используются, когда нет необходимости в полной иерархии и нужно просмотреть разные группы элементов для отчетов или анализа или когда необходимо создать классификацию.  
  
> [!NOTE]  
>  Коллекция является нерекомендуемой.  
  
## <a name="what-collections-contain"></a>Содержимое коллекций  
 Коллекции не накладывают ограничений на число или тип включаемых элементов, пока эти элементы находятся в одной сущности. Коллекция может содержать конечные и консолидированные элементы из нескольких обязательных и необязательных явных иерархий.  
  
 При создании коллекции создается не иерархическая структура, а плоский список элементов. При выборе узла из иерархии и добавлении его в коллекцию выделенный объединенный элемент является единственным элементом, который добавляется в коллекцию.  
  
 Коллекция также может содержать другие коллекции. Можно использовать коллекции коллекций для создания классификаций.  
  
 Пользователь, создающий коллекцию, автоматически вносится в список ее владельцев. Если вы являетесь администратором, то при необходимости можете создавать другие атрибуты коллекции.  
  
## <a name="subscription-views-for-collections"></a>Представления подписки для коллекций  
 Есть два типа представлений подписки, которые отображают коллекции. Формат **Атрибуты коллекций** отображает список коллекций и другие атрибуты, связанные с коллекциями, например описание или владельца. Формат **Коллекции** отображает все элементы во всех коллекциях, а также вес и порядок сортировки каждого элемента. Дополнительные сведения см. в разделе [Обзор. Экспорт данных (службы Master Data Services)](../master-data-services/overview-exporting-data-master-data-services.md).  
  
 Если для определенных элементов в коллекции установлены взвешенные значения, такие значения доступны в связанных представлениях подписки.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание новой коллекции.|[Создание коллекции (службы Master Data Services)](../master-data-services/create-a-collection-master-data-services.md)|  
|Добавление элементов в существующую коллекцию.|[Добавление элементов в коллекцию (службы Master Data Services)](../master-data-services/add-members-to-a-collection-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Явные иерархии (службы Master Data Services)](../master-data-services/explicit-hierarchies-master-data-services.md)  
  
-   [Обзор. Экспорт данных (службы Master Data Services)](../master-data-services/overview-exporting-data-master-data-services.md)  
  
  
