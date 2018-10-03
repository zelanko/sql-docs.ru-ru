---
title: Коллекции (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services]
- collections [Master Data Services], about collections
ms.assetid: 5aa1d1e0-b4e5-4897-8e74-01dcf418df73
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 7982f81d5046c0d3c9f23b4357f5b0364603c222
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48203634"
---
# <a name="collections-master-data-services"></a>Коллекции (службы основных данных)
  Коллекция — это группа конечных или консолидированных элементов из одной сущности. Коллекции используются, когда нет необходимости в полной иерархии и нужно просмотреть разные группы элементов для отчетов или анализа или когда необходимо создать классификацию.  
  
## <a name="what-collections-contain"></a>Содержимое коллекций  
 Коллекции не накладывают ограничений на число или тип включаемых элементов, пока эти элементы находятся в одной сущности. Коллекция может содержать конечные и консолидированные элементы из нескольких обязательных и необязательных явных иерархий.  
  
 При создании коллекции создается не иерархическая структура, а плоский список элементов. При выборе узла из иерархии и добавлении его в коллекцию выделенный объединенный элемент является единственным элементом, который добавляется в коллекцию.  
  
 Коллекция также может содержать другие коллекции. Можно использовать коллекции коллекций для создания классификаций.  
  
 Пользователь, создающий коллекцию, автоматически вносится в список ее владельцев. Если вы являетесь администратором, то при необходимости можете создавать другие атрибуты коллекции.  
  
> [!NOTE]  
>  Перед созданием коллекции для сущности необходимо разрешить использование явных иерархий. Дополнительные сведения см. в разделе [активация сущности для явных иерархий и коллекций &#40;службы Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).  
  
## <a name="subscription-views-for-collections"></a>Представления подписки для коллекций  
 Есть два типа представлений подписки, которые отображают коллекции. Формат **Атрибуты коллекций** отображает список коллекций и другие атрибуты, связанные с коллекциями, например описание или владельца. Формат **Коллекции** отображает все элементы во всех коллекциях, а также вес и порядок сортировки каждого элемента. Дополнительные сведения см. в разделе [Экспорт данных &#40;службы Master Data Services&#41;](overview-exporting-data-master-data-services.md).  
  
 Если для определенных элементов в коллекции установлены взвешенные значения, такие значения доступны в связанных представлениях подписки.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Включение сущности для явных иерархий и коллекций.|[Активация сущности для явных иерархий и коллекций &#40;службы Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)|  
|Создание новой коллекции.|[Создание коллекции &#40;службы Master Data Services&#41;](../../2014/master-data-services/create-a-collection-master-data-services.md)|  
|Добавление элементов в существующую коллекцию.|[Добавление элементов в коллекцию &#40;службы Master Data Services&#41;](../../2014/master-data-services/add-members-to-a-collection-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Явные иерархии &#40;службы Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
-   [Экспорт данных &#40;службы Master Data Services&#41;](overview-exporting-data-master-data-services.md)  
  
  
