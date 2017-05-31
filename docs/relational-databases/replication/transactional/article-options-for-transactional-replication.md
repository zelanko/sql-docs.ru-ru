---
title: "Параметры статьи для репликации транзакций | Документация Майкрософт"
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
- articles [SQL Server replication], transactional replication options
- transactional replication, article options
ms.assetid: 3469b185-0ea5-4690-a71c-717230d886b6
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bf9a9b2f8e6d250c313990c384651f0464db777e
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="article-options-for-transactional-replication"></a>Параметры статьи для репликации транзакций
  Для статей в публикациях транзакций существует несколько параметров. Репликация транзакций позволяет выполнять следующее:  
  
-   Задавать способ передачи изменений от издателя подписчикам. Дополнительные сведения см. в статье [Указание способа распространения изменений для статей транзакций](../../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
-   Указывать, что необходима репликация выполнения хранимой процедуры. Это полезно при репликации результатов хранимых процедур, связанных с обслуживанием и работающих с большими объемами данных. Дополнительные сведения см. в статье [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
-   Укажите параметры схемы, например копируются ли ограничения и триггеры на подписчик. Дополнительные сведения см. в разделе [Указание параметров схемы](../../../relational-databases/replication/publish/specify-schema-options.md).  
  
-   Использовать фильтры строк и фильтры столбцов. Фильтрация статей таблиц позволяет создавать секции публикуемых данных. Дополнительные сведения см. в статье [Фильтрация опубликованных данных](../../../relational-databases/replication/publish/filter-published-data.md).  
  
## <a name="see-also"></a>См. также:  
 [Публикация данных и объектов базы данных](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
