---
title: "Параметры статьи для репликации транзакций | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "статьи [репликация SQL Server], параметры репликации транзакций"
  - "репликация транзакций, параметры статьи"
ms.assetid: 3469b185-0ea5-4690-a71c-717230d886b6
caps.latest.revision: 30
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 30
---
# Параметры статьи для репликации транзакций
  Для статей в публикациях транзакций существует несколько параметров. Репликация транзакций позволяет выполнять следующее:  
  
-   Задавать способ передачи изменений от издателя подписчикам. Дополнительные сведения см. в разделе [указания способа распространения изменений для транзакционных статей](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
-   Указывать, что необходима репликация выполнения хранимой процедуры. Это полезно при репликации результатов хранимых процедур, связанных с обслуживанием и работающих с большими объемами данных. Дополнительные сведения см. в статье [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
-   Укажите параметры схемы, например копируются ли ограничения и триггеры на подписчик. Дополнительные сведения см. в разделе [Указание параметров схемы](../../../relational-databases/replication/publish/specify-schema-options.md).  
  
-   Использовать фильтры строк и фильтры столбцов. Фильтрация статей таблиц позволяет создавать секции публикуемых данных. Дополнительные сведения см. в разделе [Фильтрация опубликованных данных](../../../relational-databases/replication/publish/filter-published-data.md).  
  
## См. также:  
 [Публикация данных и объектов базы данных](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  