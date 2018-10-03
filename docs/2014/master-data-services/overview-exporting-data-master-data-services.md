---
title: Экспорт данных (Master Data Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- exporting data [Master Data Services]
- subscription views [Master Data Services]
- subscription views [Master Data Services], about subscription views
ms.assetid: 8b74409a-ea70-45f8-84c7-da6905e4901a
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 3e7a228062035772b9c394a246de0452f36239b1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48158644"
---
# <a name="exporting-data-master-data-services"></a>Экспорт данных (службы Master Data Services)
  Вы можете экспортировать [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] данных в системы-подписчики путем создания представлений подписки. После этого любая система-подписчик может просматривать опубликованные данные в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Дополнительные сведения о представлениях см. в разделе [Представления](../relational-databases/views/views.md).  
  
## <a name="subscription-view-formats"></a>Форматы представлений подписки  
 При создании представления [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]на выбор предлагается набор стандартных форматов представлений, предоставляемых службами [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Эти форматы используются для создания представлений, которые содержат:  
  
-   все конечные элементы и их атрибуты;  
  
-   все консолидированные элементы и их атрибуты;  
  
-   все коллекции и их атрибуты;  
  
-   элементы, явно добавленные в коллекцию;  
  
-   элементы в производной иерархии многоуровневого типа или типа «родители-потомки»;  
  
-   элементы во всех явных иерархиях многоуровневого типа или типа «родители-потомки» для сущности.  
  
## <a name="subscription-views-can-become-out-of-date"></a>Представления подписки могут устаревать  
 После создания представления подписки для сущности или иерархии изменения связанных объектов модели не будут автоматически отображаться в представлении. Может потребоваться повторное создание представления подписки в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , чтобы в ней отразились изменения в объектах модели. При изменении объектов модели значение в столбце **Изменено** на странице **Экспорт** меняется на **True** . Значение**True** указывает на необходимость изменить представление подписки и сохранить его, после чего оно будет создано повторно.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание представления подписки основных данных.|[Создание представления подписки &#40;службы Master Data Services&#41;](create-a-subscription-view-to-export-data-master-data-services.md)|  
|Удаление существующих представлений подписки.|[Удаление представления подписки &#40;службы Master Data Services&#41;](../../2014/master-data-services/delete-a-subscription-view-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Форматы представления подписки &#40;службы Master Data Services&#41;](../../2014/master-data-services/subscription-view-formats-master-data-services.md)  
  
-   [Представления](../relational-databases/views/views.md)  
  
  
