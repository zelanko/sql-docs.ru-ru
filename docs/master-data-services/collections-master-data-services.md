---
title: "Коллекции (службы Master Data Services) | Документы Майкрософт"
ms.custom: 
ms.date: 04/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- collections [Master Data Services]
- collections [Master Data Services], about collections
ms.assetid: 5aa1d1e0-b4e5-4897-8e74-01dcf418df73
caps.latest.revision: "14"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b613d751fd68818fbee4720254199a701cfb03ba
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="collections-master-data-services"></a>Коллекции (службы основных данных)
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
  
  
