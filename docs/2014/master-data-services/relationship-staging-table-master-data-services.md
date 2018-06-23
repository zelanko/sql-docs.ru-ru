---
title: Промежуточная таблица связей (службы Master Data Services) | Документы Майкрософт
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
- relationships staging table [Master Data Services]
- database [Master Data Services], relationships table
ms.assetid: e19b6002-67bd-4e7d-9f19-ecb455522b1a
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c5d37385494fc4853f47ec8e1fe883d3ff00f0e2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36086699"
---
# <a name="relationship-staging-table-master-data-services"></a>Промежуточная таблица связей (службы Master Data Services)
  Используйте промежуточную таблицу связей (stg.name_Relationship) в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] для изменения расположения элементов в явной иерархии на основе связей между элементами.  
  
##  <a name="TableColumns"></a> Столбцы таблицы  
 В приведенной таблице объясняется, для чего используется каждое поле в промежуточной таблице связей.  
  
|Имя столбца|Описание|  
|-----------------|-----------------|  
|**Идентификатор**|Автоматически назначенный идентификатор. Не вводите значение в этом поле. Если пакет не обработан, это поле пустое.|  
|**RelationshipType**<br /><br /> Обязательно|Задаваемый тип связи. Возможны следующие значения:<br /><br /> **1**: Родительский элемент<br /><br /> **2**: одноуровневый элемент|  
|**ImportStatus_ID**<br /><br /> Обязательно|Состояние процесса импорта. Возможны следующие значения:<br /><br /> **0**задается для указания готовности записи к промежуточному хранению;<br /><br /> **1**задается автоматически и указывает на успешное завершение промежуточного процесса записи;<br /><br /> **2**задается автоматически и указывает на ошибку промежуточного процесса записи.|  
|**Batch_ID**<br /><br /> Требуется только для веб-службы|Автоматически назначаемый идентификатор, группирующий записи для промежуточного хранения. Всем элементам в пакете назначен этот идентификатор, который отображается в пользовательском интерфейсе [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] в столбце **ID** .<br /><br /> Если пакет не обработан, это поле пустое.|  
|**BatchTag**<br /><br /> Требуется, за исключением веб-службы|Уникальное имя для данного пакета, до 50 символов.|  
|**HierarchyName**<br /><br /> Обязательно|Имя явной иерархии. Каждый объединенный элемент может принадлежать только одной явной иерархии.|  
|**ParentCode**<br /><br /> Обязательно|Для связи родительский-дочерний элемент код объединенного элемента, который должен стать родительским для дочернего или объединенного элемента.<br /><br /> Для одноуровневых отношений код одного из одноуровневых элементов.|  
|**ChildCode**<br /><br /> Обязательно|Для связи родительский-дочерний элемент код объединенного или конечного элемента, который должен стать дочерним элементом.<br /><br /> Для одноуровневых отношений код одного из одноуровневых элементов.|  
|**Порядок сортировки**<br /><br /> Необязательно|Целое число, указывающее порядковый номер элемента относительно других элементов на уровнях ниже родителя. У всех дочерних элементов должен быть уникальный идентификатор.|  
|**ErrorCode**|Отображает код ошибки. Для всех записей со значением **ImportStatus_ID** , равным **2**, см. раздел [Staging Process Errors &#40;Master Data Services&#41;](staging-process-errors-master-data-services.md).|  
  
## <a name="see-also"></a>См. также  
 [Перемещение элементов явной иерархии с помощью промежуточного процесса &#40;службы Master Data Services&#41;](/sql/2014/master-data-services/add-update-and-delete-data-master-data-services)   
 [Импорт данных &#40;службы Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)   
 [Просмотр ошибок, возникших в процессе промежуточного хранения &#40;службы Master Data Services&#41;](view-errors-that-occur-during-staging-master-data-services.md)   
 [Промежуточные ошибки процесса &#40;службы Master Data Services&#41;](staging-process-errors-master-data-services.md)  
  
  
