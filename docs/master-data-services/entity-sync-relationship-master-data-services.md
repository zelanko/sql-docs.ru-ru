---
title: "Отношение синхронизации сущностей (Master Data Services) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd627a2d-dc64-47e9-9a71-2d0ad04b4962
caps.latest.revision: "6"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5036605e8d6798430da62fbb22da6c466008bde4
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="entity-sync-relationship-master-data-services"></a>Отношение синхронизации сущностей (Master Data Services)
  Синхронизация сущностей — это односторонняя повторяемая синхронизация между версиями сущности. Она позволяет разным моделям совместно использовать данные сущностей. Можно поддерживать единый источник истины в одной модели и использовать эти основные данные в других моделях. Например, можно хранить данные о штатах США в сущности одной модели и использовать эти данные в других моделях.  
  
 Синхронизация сущностей также позволяет сделать однократную копию данных.  
  
 Все конечные элементы с атрибутами свободных форм и файлов в исходной сущности будут синхронизированы с целевой сущностью в ходе синхронизации. При этом создаются, удаляются и изменяются схема сущности и ее элементы.  
  
 После установления отношения синхронизации целевая сущность может быть изменена только в ходе синхронизации. Отношение синхронизации в любое время можно удалить, чтобы сделать целевую сущность доступной для редактирования.  
  
## <a name="see-also"></a>См. также:  
 [Создание и выполнение отношений синхронизации сущностей (Master Data Services)](../master-data-services/create-and-execute-an-entity-sync-relationship-master-data-services.md)   
 [Создание и удаление отношения синхронизации сущностей (Master Data Services)](../master-data-services/edit-and-delete-an-entity-sync-relationship-master-data-services.md)  
  
  
