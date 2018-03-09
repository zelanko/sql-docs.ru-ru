---
title: "Отношение синхронизации сущностей (Master Data Services) | Документы Майкрософт"
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
ms.assetid: bd627a2d-dc64-47e9-9a71-2d0ad04b4962
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5981022c301b8fab4ae0d6c3f250b7ddae5b93db
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2018
---
# <a name="entity-sync-relationship-master-data-services"></a>Отношение синхронизации сущностей (Master Data Services)
  Синхронизация сущностей — это односторонняя повторяемая синхронизация между версиями сущности. Она позволяет разным моделям совместно использовать данные сущностей. Можно поддерживать единый источник истины в одной модели и использовать эти основные данные в других моделях. Например, можно хранить данные о штатах США в сущности одной модели и использовать эти данные в других моделях.  
  
 Синхронизация сущностей также позволяет сделать однократную копию данных.  
  
 Все конечные элементы с атрибутами свободных форм и файлов в исходной сущности будут синхронизированы с целевой сущностью в ходе синхронизации. При этом создаются, удаляются и изменяются схема сущности и ее элементы.  
  
 После установления отношения синхронизации целевая сущность может быть изменена только в ходе синхронизации. Отношение синхронизации в любое время можно удалить, чтобы сделать целевую сущность доступной для редактирования.  
  
## <a name="see-also"></a>См. также:  
 [Создание и выполнение отношений синхронизации сущностей (Master Data Services)](../master-data-services/create-and-execute-an-entity-sync-relationship-master-data-services.md)   
 [Создание и удаление отношения синхронизации сущностей (Master Data Services)](../master-data-services/edit-and-delete-an-entity-sync-relationship-master-data-services.md)  
  
  
