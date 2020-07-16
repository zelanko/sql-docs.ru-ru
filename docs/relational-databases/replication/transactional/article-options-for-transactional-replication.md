---
title: Параметры статьи для репликации транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], transactional replication options
- transactional replication, article options
ms.assetid: 3469b185-0ea5-4690-a71c-717230d886b6
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 1b8745e278486d899d070757d58bae326f79551d
ms.sourcegitcommit: 21c14308b1531e19b95c811ed11b37b9cf696d19
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2020
ms.locfileid: "86159442"
---
# <a name="article-options-for-transactional-replication"></a>Параметры статьи для репликации транзакций
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/applies-to-version/sql-asdbmi.md)]
  Для статей в публикациях транзакций существует несколько параметров. Репликация транзакций позволяет выполнять следующее:  
  
-   Задавать способ передачи изменений от издателя подписчикам. Дополнительные сведения см. в статье [Указание способа распространения изменений для статей транзакций](../../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
-   Указывать, что необходима репликация выполнения хранимой процедуры. Это полезно при репликации результатов хранимых процедур, связанных с обслуживанием и работающих с большими объемами данных. Дополнительные сведения см. в статье [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
-   Укажите параметры схемы, например копируются ли ограничения и триггеры на подписчик. Дополнительные сведения см. в разделе [Указание параметров схемы](../../../relational-databases/replication/publish/specify-schema-options.md).  
  
-   Использовать фильтры строк и фильтры столбцов. Фильтрация статей таблиц позволяет создавать секции публикуемых данных. Дополнительные сведения см. в статье [Фильтрация опубликованных данных](../../../relational-databases/replication/publish/filter-published-data.md).  
  
## <a name="see-also"></a>См. также:  
 [Публикация данных и объектов базы данных](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
