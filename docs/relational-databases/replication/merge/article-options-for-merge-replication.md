---
title: "Параметры статьи для репликации слиянием | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- merge replication [SQL Server replication], article options
- articles [SQL Server replication], merge replication options
ms.assetid: 670abd41-d204-4cd7-a371-7664e603a0ce
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ab39f23acb370612b4579988de20eac85984bb24
ms.lasthandoff: 04/11/2017

---
# <a name="article-options-for-merge-replication"></a>Параметры статьи для репликации слиянием
  Существует много параметров для статей таблицы слияния, позволяющих настроить поведение репликации в соответствии с потребностями приложений. С помощью репликации слиянием можно выполнять следующее.  
  
-   Использовать фильтры строк, фильтры соединения и фильтры столбцов. Фильтрация статей таблиц позволяет создавать секции публикуемых данных. Дополнительные сведения см. в статье [Фильтрация опубликованных данных](../../../relational-databases/replication/publish/filter-published-data.md).  
  
-   Указать, будут ли изменения с подписчика передаваться издателю. Для приложений, в которых некоторые или все данные на подписчике должны быть доступны только для чтения, статьи, доступные только для загрузки, повышают производительность. Дополнительные сведения см. в статье [Оптимизация производительности репликации слиянием при работе со статьями, доступными только для загрузки](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md).  
  
-   Указать, что удаления одной или нескольких статей не должны отслеживаться триггерами репликации и системными таблицами. Этот параметр может оказаться полезным во многих сценариях приложений. В том числе в сценариях, использующих операции пакетного удаления, которые не нужно реплицировать. Дополнительные сведения см. в статье [Оптимизация производительности репликации слиянием с помощью отслеживания условного удаления](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-conditional-delete-tracking.md).  
  
-   Укажите порядок обработки статей, чтобы обеспечить обработку статей в порядке, необходимом приложению. Дополнительные сведения см. в статье [Определение порядка обработки для статей публикации слиянием](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md).  
  
-   Указать, что набор взаимосвязанных записей должен обрабатываться в виде блока (по умолчанию репликация слиянием обрабатывает изменения в таблицах построчно). Дополнительные сведения см. в статье [Группирование изменений в связанных строках с помощью логических записей](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
-   Использовать обнаружение и разрешение конфликтов для случаев, когда одни и те же данные могут быть изменены в нескольких узлах топологии. Дополнительные сведения см. в статье [Detect and Resolve Merge Replication Conflicts](../../../relational-databases/replication/merge/advanced-merge-replication-resolve-merge-replication-conflicts.md).  
  
-   Укажите параметры схемы, например копируются ли ограничения и триггеры на подписчик. Дополнительные сведения см. в разделе [Указание параметров схемы](../../../relational-databases/replication/publish/specify-schema-options.md).  
  
-   Для соблюдения многих условий во время синхронизации используется обработчик бизнес-логики. Эти условия включают изменения данных, конфликты и ошибки. Дополнительные сведения см. в статье [Выполнение бизнес-логики при синхронизации слиянием](../../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md).  
  
## <a name="see-also"></a>См. также:  
 [Публикация данных и объектов базы данных](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
