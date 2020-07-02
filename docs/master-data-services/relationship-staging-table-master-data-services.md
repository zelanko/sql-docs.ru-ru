---
title: Промежуточная таблица связей
ms.custom: ''
ms.date: 04/01/2016
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- relationships staging table [Master Data Services]
- database [Master Data Services], relationships table
ms.assetid: e19b6002-67bd-4e7d-9f19-ecb455522b1a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bc1264be90f65ce6e7e523670893177ef78eb646
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85811701"
---
# <a name="relationship-staging-table-master-data-services"></a>Промежуточная таблица связей (службы Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Используйте промежуточную таблицу связей (stg.name_Relationship) в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] для изменения расположения элементов в явной иерархии на основе связей между элементами.  
  
##  <a name="table-columns"></a><a name="TableColumns"></a>Столбцы таблицы  
 В приведенной таблице объясняется, для чего используется каждое поле в промежуточной таблице связей.  
  
|Имя столбца|Описание|Значение|  
|-----------------|-----------------|-----------|  
|**ID**|Автоматически назначенный идентификатор.|Не вводите значение в этом поле. Если пакет не обработан, это поле пустое.|  
|**RelationshipType**|Обязательное<br /><br /> Задаваемый тип связи.|Возможны следующие значения:<br /><br /> **1**: Родительский элемент<br /><br /> **2**: одноуровневый элемент|  
|**ImportStatus_ID**|Обязательное<br /><br /> Состояние процесса импорта.|Возможны следующие значения:<br /><br /> **0**задается для указания готовности записи к промежуточному хранению;<br /><br /> **1**задается автоматически и указывает на успешное завершение промежуточного процесса записи;<br /><br /> **2**задается автоматически и указывает на ошибку промежуточного процесса записи.|  
|**Batch_ID**|Требуется только для веб-службы<br /><br /> Автоматически назначаемый идентификатор, группирующий записи для промежуточного хранения.<br /><br /> Если пакет не обработан, это поле пустое.|Всем элементам в пакете назначен этот идентификатор, который отображается в пользовательском интерфейсе [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] в столбце **ID** .|  
|**BatchTag**|Требуется, за исключением веб-службы<br /><br /> Уникальное имя для данного пакета, до 50 символов.||  
|**HierarchyName**|Обязательное<br /><br /> Имя явной иерархии. Каждый объединенный элемент может принадлежать только одной явной иерархии.||  
|**ParentCode**|Обязательное<br /><br /> Для связи родительский-дочерний элемент код объединенного элемента, который должен стать родительским для дочернего или объединенного элемента.<br /><br /> Для одноуровневых отношений код одного из одноуровневых элементов.||  
|**ChildCode**|Обязательное<br /><br /> Для связи родительский-дочерний элемент код объединенного или конечного элемента, который должен стать дочерним элементом.<br /><br /> Для одноуровневых отношений код одного из одноуровневых элементов.||  
|**Порядок сортировки**|Необязательно<br /><br /> Целое число, указывающее порядковый номер элемента относительно других элементов на уровнях ниже родителя. У всех дочерних элементов должен быть уникальный идентификатор.||  
|**ErrorCode**|Отображает код ошибки. Для всех записей со значением **ImportStatus_ID** , равным **2**, см. раздел [Ошибки промежуточного процесса (службы Master Data Services)](../master-data-services/staging-process-errors-master-data-services.md).||  
  
## <a name="see-also"></a>См. также  
 [Обзор. Импорт данных из таблиц &#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)   
 [Просмотр ошибок, возникающих во время промежуточного хранения &#40;Master Data Services&#41;](../master-data-services/view-errors-that-occur-during-staging-master-data-services.md)   
 [Ошибки промежуточного процесса (службы Master Data Services)](../master-data-services/staging-process-errors-master-data-services.md)  
  
  
